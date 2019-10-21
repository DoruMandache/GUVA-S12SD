int indice_uv [12] = {50,227,318,408,503,606,696,795,881,976,1079,1170}; 
    float Valori_MiniVolti_Senzor;

void setup() {
    Serial.begin(9600);
}
 
void loop() {
    float Valori_Volti_Senzor;
    float Valori_Analogice_Senzor;
    float Index_UV;
 
    Valori_Analogice_Senzor = analogRead(A0);
    Valori_Volti_Senzor = Valori_Analogice_Senzor * (5.0 / 1023.0);
    Valori_MiniVolti_Senzor = Valori_Volti_Senzor * 1000;
    //Index_UV = (0.0106 * Valori_MiniVolti_Senzor) - 1.3577;

    Index_UV = Calculeaza_Indice_UV(); 
  
    Serial.print("Valori analogice = ");
    Serial.print(Valori_Analogice_Senzor);
    Serial.print("; ");
  
    Serial.print("Valori convertite in mV = ");
    Serial.print(Valori_Volti_Senzor * 1000);
    Serial.print(" mV;          ");
  
    Serial.print("Index UV = ");
    Serial.print(Index_UV);
    Serial.println();
    delay(1000);
}

float Calculeaza_Indice_UV() {
    float uvIndex;
    int i;
    for (i = 0; i < 12; i++) {
        if (Valori_MiniVolti_Senzor <= indice_uv[i]) {
            uvIndex = i;
            break;
        }
    }

    if (i>0) {
        float Medie = indice_uv[i] - indice_uv[i-1];
        float vCalc=Valori_MiniVolti_Senzor - indice_uv[i-1];
        uvIndex+=(1.0/Medie*vCalc)-1.0;
    }

    return uvIndex;
}  
