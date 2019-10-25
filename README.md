#include <kipr/botball.h>
//DECLARE VARIABLES
int l_motor = 0; 
int r_motor = 3; 
int range_side = 4;
int range_front = 0;
int f_average = 2910;
int s_average = 2900;
int forward = -25;
int f_speed = -75;
int s_speed = -75;
int backward = 25;
int speed_r = -55;
int five_minutes = 300.0;
int pause = 1000;
int main()
{
    printf("Find the wall/n");
    wall_run();
    printf("Following wall/n");
    turn();
    printf("Turning/n");
    wall_run();
    printf("following wall/n");
}
//FUNCTION DEFINITIONS//
void forwards(){
    motor(l_motor,forward);
    motor(r_motor,forward);
    ao();
}
void f_turn(){
    motor(l_motor,f_speed);
    motor(r_motor,forward);
}
void s_turn(){
    motor(l_motor,forward);
    motor(r_motor,s_speed);
}
void turn(){
    motor(l_motor,backward);
    motor(r_motor,speed_r);
    msleep(pause);
    ao();
}
void wall_run(){
    while (analog(range_front) <= f_average){
     	forwards();
    if (analog(range_side) >= s_average){
     	s_turn();
    }
    if (analog(range_side) <= s_average){
        f_turn();
    }
    }
}

