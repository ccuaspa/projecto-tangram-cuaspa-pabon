# projecto-tangram-cuaspa-pabon
projecto creacion tangram
int tg1x=0;
int tg1y=0;
int tg2x=0;
int tg2y=0;
int tmx=0;
int tmy=0;
int tp1x=0;
int tp1y=0;
int c1x=0;
int c1y=0;
int tp2x=0;
int tp2y=0;
int c2x=0;
int c2y=0;
/////////////////////////////////////////
int contadortg1=0;
int angulotg1=0;
int prueba=0;
int contadortg2=0;
int contadortm=0;
int contadortp1=0;
int contadorc1=0;
int contadortp2=0;
int contadorc2=0;
//////////////////////////////////////
float bx;
float by;
int boxSize = 75;
int Wheel;
boolean overBox = false;
boolean locked = false;
float xOffset = 0.0; 
float yOffset = 0.0; 
float angle;

boolean teclado, mouse, arriba, abajo, izquierda, derecha, tg1, tg2, tm, tp1, tp2, cuadrado, cuadrilatero, rd, ri;

void setup() {
  size(1240, 720);
  bx = width/2;
  by = height/2;
  rectMode(RADIUS);
}
void draw() {
  background(255);
  if (mouse==true) {
    background(0);

    // Test if the cursor is over the box 
    if (mouseX > bx-boxSize && mouseX < bx+boxSize && 
      mouseY > by-boxSize && mouseY < by+boxSize) {
      overBox = true;
      if (!locked) { 
        stroke(255); 
        fill(255);
      }
    } else {
      stroke(255);
      fill(255);
      overBox = false;
    }

    rotar(bx, by);
  }


  if (teclado==true) { 

    //movimientos triangulo grande 1
    if (derecha==true && tg1==true) {
      tg1x+=5;
    }
    if (izquierda==true && tg1==true) {
      tg1x-=5;
    }
    if (arriba==true && tg1==true) {
      tg1y-=5;
    }
    if (abajo==true && tg1==true) {
      tg1y+=5;
    }
    //triangulo grande 1
    if (tg1==true && rd==true) {
      prueba+=45;
    } 
    if (tg1==true && key=='i') {
      prueba-=45;
    } 
    
    fill(255, 0, 0);
    push();
    translate(tg1x, tg1y);
    rotate(prueba); 
    triangle(0, 0, 200, 0, 100, 100);
    pop();
    contadortg1=0;
    


    //movimientos triangulo grande 2
    if (derecha==true && tg2==true) {
      tg2x+=5;
    }
    if (izquierda==true && tg2==true) {
      tg2x-=5;
    }
    if (arriba==true && tg2==true) {
      tg2y-=5;
    }
    if (abajo==true && tg2==true) {
      tg2y+=5;
    }
    //triangulo grande 2
    if (tg2==true && key=='d') {
      fill(0, 255, 0);
      push();
      translate(tg2x, tg2y);
      rotate(PI/4);      
      triangle(0, 200, 0, 0, 100, 100);
      pop();
    } else {
      fill(0, 255, 0);
      triangle(tg2x, tg2y+200, tg2x, tg2y, tg2x+100, tg2y+100);
    }


    //triangulo mediano
    fill(0, 0, 255);
    triangle(tmx+200, tmy+200, tmx+200, tmy+100, tmx+100, tmy+200);

    //triangulo pequeño 1
    fill(255, 100, 255);
    triangle(tp1x+200, tp1y, tp1x+200, tp1y+100, tp1x+150, tp1y+50);

    //cuadrado
    fill(255, 255, 0);
    quad(c1x+100, c1y+100, c1x+150, c1y+50, c1x+200, c1y+100, c1x+150, c1y+150);

    //triangulo pequeño2
    fill(255, 100, 0);
    triangle(tp2x+100, tp2y+100, tp2x+50, tp2y+150, tp2x+150, tp2y+150);

    //cuadrilatero
    fill(0, 255, 255);
    quad(c2x, c2y+200, c2x+100, c2y+200, c2x+150, c2y+150, c2x+50, c2y+150);





    //movimientos triengulo mediano
    if (derecha==true && tm==true) {
      tmx+=5;
    }
    if (izquierda==true && tm==true) {
      tmx-=5;
    }
    if (arriba==true && tm==true) {
      tmy-=5;
    }
    if (abajo==true && tm==true) {
      tmy+=5;
    }

    //movimientos triangulo pequeño 1
    if (derecha==true && tp1==true) {
      tp1x+=5;
    }
    if (izquierda==true && tp1==true) {
      tp1x-=5;
    }
    if (arriba==true && tp1==true) {
      tp1y-=5;
    }
    if (abajo==true && tp1==true) {
      tp1y+=5;
    }

    //movimientos triangulo pequeño 2
    if (derecha==true && tp2==true) {
      tp2x+=5;
    }
    if (izquierda==true && tp2==true) {
      tp2x-=5;
    }
    if (arriba==true && tp2==true) {
      tp2y-=5;
    }
    if (abajo==true && tp2==true) {
      tp2y+=5;
    }

    //movimientos cuadrado
    if (derecha==true && cuadrado==true) {
      c1x+=5;
    }
    if (izquierda==true && cuadrado==true) {
      c1x-=5;
    }
    if (arriba==true && cuadrado==true) {
      c1y-=5;
    }
    if (abajo==true && cuadrado==true) {
      c1y+=5;
    }

    //movimientos cuadrilatero
    if (derecha==true && cuadrilatero==true) {
      c2x+=5;
    }
    if (izquierda==true && cuadrilatero==true) {
      c2x-=5;
    }
    if (arriba==true && cuadrilatero==true) {
      c2y-=5;
    }
    if (abajo==true && cuadrilatero==true) {
      c2y+=5;
    }
  }
}
void keyPressed() {
  if (keyCode== LEFT) izquierda =true;
  if (keyCode==RIGHT) derecha=true;
  if (keyCode== DOWN) abajo=true;
  if (keyCode==UP) arriba=true;
  if (key=='1') {
    tg1=true; 
    tg2=false;
    tm=false;
    tp1=false;
    tp2=false;
    cuadrado=false;
    cuadrilatero=false;
  }
  if (key=='2') {
    tg1=false; 
    tg2=true;
    tm=false;
    tp1=false;
    tp2=false;
    cuadrado=false;
    cuadrilatero=false;
  }
  if (key=='3') {
    tg1=false; 
    tg2=false;
    tm=true;
    tp1=false;
    tp2=false;
    cuadrado=false;
    cuadrilatero=false;
  } 
  if (key=='4') {
    tg1=false; 
    tg2=false;
    tm=false;
    tp1=true;
    tp2=false;
    cuadrado=false;
    cuadrilatero=false;
  }
  if (key=='5') {
    tg1=false; 
    tg2=false;
    tm=false;
    tp1=false;
    tp2=true;
    cuadrado=false;
    cuadrilatero=false;
  } 
  if (key=='6') {
    tg1=false; 
    tg2=false;
    tm=false;
    tp1=false;
    tp2=false;
    cuadrado=true;
    cuadrilatero=false;
  }
  if (key=='7') {
    tg1=false; 
    tg2=false;
    tm=false;
    tp1=false;
    tp2=false;
    cuadrado=false;
    cuadrilatero=true;
  }
  if (key=='t'||key=='T') {
    teclado =true;
    mouse=false;
  }
  if (key=='m'||key=='M') {
    mouse=true;
    teclado=false;
  }
  if (key=='d'||key=='D'){
    rd=true;
  }
}

void keyReleased() {
  if (keyCode== LEFT) izquierda =false;
  if (keyCode==RIGHT) derecha=false;
  if (keyCode== DOWN) abajo=false;
  if (keyCode==UP) arriba=false;
  if (key=='d'||key=='D')rd=false;
}
void mousePressed() {
  if (overBox) { 
    locked = true; 
    fill(255, 255, 255);
  } else {
    locked = false;
  }
  xOffset = mouseX-bx; 
  yOffset = mouseY-by;
}

void mouseWheel(MouseEvent event) {

  Wheel = event.getCount();
  if (locked) {
    switch(Wheel) {
    case -1: 
      angle = angle + 15;
      break;
    case 1: 
      angle = angle - 15;
      break;
    case 0:
      break;
    }
  }
  println(Wheel);
}

void mouseDragged() {
  if (locked) {
    bx = mouseX-xOffset; 
    by = mouseY-yOffset;
  }
}

void mouseReleased() {
  locked = false;
}

void rotar(float x, float y)
{
  pushMatrix();
  translate(x, y);
  rotate(radians(angle));
  rect(0, 0, boxSize, boxSize);
  popMatrix();
}
