let lixoX, lixoY; // Posição do nosso "lixo" (um ponto)

let lixeiraCorretaX, lixeiraCorretaY; // Posição da "lixeira"

let acertou = false; // Para saber se o lixo está na lixeira

function setup() {

  createCanvas(400, 300);

  lixoX = width / 2;

  lixoY = height / 4;

  lixeiraCorretaX = width / 2;

  lixeiraCorretaY = height / 2 + 50;

  textAlign(CENTER, CENTER);

  textSize(16);

  noStroke()

}

function draw() {

  background(220); // Cor de fundo


  fill(0, 100, 0); // Lixeira verde

  rectMode(CENTER); // Desenha o retângulo a partir do centro

  rect(lixeiraCorretaX, lixeiraCorretaY, 100, 80); // Lixeira

  fill(255);

  text("LIXEIRA", lixeiraCorretaX, lixeiraCorretaY);


  fill(255, 0, 0); // Lixo vermelho (o ponto)

  ellipse(lixoX, lixoY, 20, 20); // O lixo é um círculo pequeno


  fill(0);

  text("Arrume o lixo na lixeira!", width / 2, 20);


  if (acertou) {

    fill(0, 150, 0); // Verde para sucesso

    text("🎉 Acertou! 🎉", width / 2, height - 20);

  } else {

    fill(150, 0, 0); // Vermelho para "quase lá"

    text("Mova o lixo para a lixeira.", width / 2, height - 20);

  }

}

function mouseDragged() {

  // O lixo segue o mouse enquanto arrastado

  lixoX = mouseX;

  lixoY = mouseY;

  

  // Verifica se o lixo está dentro da lixeira

  if (dist(lixoX, lixoY, lixeiraCorretaX, lixeiraCorretaY) < 50) { // Verifica a distância do centro

    acertou = true;

  } else {

    acertou = false;

  }

}

function mouseReleased() {

  // Ao soltar o mouse, se acertou, podemos reiniciar ou deixar lá

  if (acertou) {

  } else {

    // Se soltou fora, ele volta para a posição inicial

    lixoX = width / 2;

    lixoY = height / 4;

  }

}
