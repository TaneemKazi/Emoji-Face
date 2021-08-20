#include<GL/gl.h>
#include<GL/glut.h>
#include<math.h>
#include<stdlib.h>
#include<windows.h>
void init (void)
{
    glClearColor(1.0,1.0,1.0,1.0);
    glMatrixMode(GL_PROJECTION);
    glLoadIdentity();
    gluOrtho2D(-20,20,-20,20);
}

void circle(GLfloat rx,GLfloat ry,GLfloat cx,GLfloat cy)
{
    glBegin(GL_TRIANGLE_FAN);
    for(int i = 0; i<=100; i++)
    {
        float angle = 2*3.1416*i/100;
        float x = rx*cosf(angle);
        float y=ry*sinf(angle);
        glVertex2f(x+cx,y+cy);

    }
    glEnd();
}

void display(void)
{

    glClear(GL_COLOR_BUFFER_BIT);
    glColor3f(1.0, 0.9, 0.0);
    circle   (8,8,1,1);

    //smile
    glColor3f(0.0, 0.0, 0.0);
    circle   (4, 4, 1, 0);

    glColor3f(1.0, 0.9, 0.0);
    circle   (5, 4, 1, 1);

    //left eye
    glColor3f(1.0,1.0,1.0);
    circle   (1.5, 1.5, -2, 3);
    // eye ball brown
    glColor3f(0.36, 0.25, 0.20);
    circle   (1.2, 1.2, -2, 3);
    // black lens
    glColor3f(0.0, 0.0, 0.0);
    circle   (0.7, 0.7, -2, 3);

    // right eye
    glColor3f(1.0, 1.0, 1.0);
    circle   (1.5, 1.5, 4.5, 3);
    // eye ball brown
    glColor3f(0.36, 0.25, 0.20);
    circle   (1.2, 1.2, 4.5, 3);
    // black lens
    glColor3f(0.0, 0.0, 0.0);
    circle   (0.7, 0.7, 4.5, 3);

    glFlush();
}

int main(int argc, char** argv)
{
    glutInit(&argc, argv);
    glutInitDisplayMode (GLUT_SINGLE | GLUT_RGB);
    glutInitWindowSize (600, 600);
    glutInitWindowPosition (550,150);
    glutCreateWindow ("Emoji");
    init ();
    glutDisplayFunc(display);
    glutMainLoop();
    return 0;
}
