# short-circuit-code
link:https://www.tinkercad.com/things/1DNeCmPKgDf-short-circuit-task/editel?returnTo=https%3A%2F%2Fwww.tinkercad.com%2Fdashboard%2Fdesigns%2Fcircuits&sharecode=iWs3niu3ycopJIr7kgzTFxS4_7xcoYi-Ggg2fpAu_7Q 
    code: 
    int green_led = 9;
    int yellow_led = 10;
    int red_led = 11;
    int buttonPin = 3;

    unsigned long start = 0;
    int state = 0;

    void setup(){
    pinMode(green_led, OUTPUT);
    pinMode(yellow_led, OUTPUT);
    pinMode(red_led, OUTPUT);
    pinMode(buttonPin, INPUT); 
    }

    void loop(){
    
    if (digitalRead(buttonPin) == HIGH){
        
    digitalWrite(green_led,LOW);
    digitalWrite(yellow_led,LOW);
    digitalWrite(red_led,HIGH);
    start = millis();
    state = 0;
    } 
    else{
        switch (state){
            case 0: digitalWrite(green_led,HIGH);
                    digitalWrite(yellow_led,LOW);
                    digitalWrite(red_led,LOW);
                if(millis() - start >= 3000){
                    start = millis();
                    state = 1;
                }
                break;
            case 1: digitalWrite(green_led,LOW);
                    digitalWrite(yellow_led,HIGH);
                    digitalWrite(red_led,LOW);  
                if(millis() - start >= 2000){
                    start = millis();
                    state = 2;
                }
                break;
            case 2: digitalWrite(green_led,LOW);
                    digitalWrite(yellow_led,LOW);
                    digitalWrite(red_led,HIGH); 
                if(millis() - start >= 5000){
                    start = millis();
                    state = 0;
                }
                break;
        }
    }
    }
