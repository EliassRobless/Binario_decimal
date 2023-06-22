# Binario_decimal
El siguiente programa esta hecho en lenguaje C. Tiene el proposito de convertir un numero de base 10 a binario (base dos) y viceversa. El proceso de conversion de un numero decimal a binario puede sere tedioso o lento para algunas personas y es por eso que este programa es una util solucion a dicha problematica.

Para ejecutar el programa es necesario utilizar cualquier compilador de lenguaje C (online o aplicacion) como lo son Dev C++, Compiler Code C, etc.

Algunos ejemplos de valores de entrada y salida esperados son:

1.- 

2.- 

3.- 

Integrantes Equipo 5: Robles Ramirez Angel Elias, Bazan Tehuitzil Oscar Damian, Ortiz Martinez Isai Eliezer, Santiago Guerrero Isaac Alejandro, Solares Velasco Arturo.

 
    #include <iostream>
    #include <string>
    #include <cmath>

    using namespace std;

     // Esta funcion revisa si un numero esta en base 2
    bool correcto(string numero) {
    for (char digito : numero) {
        if (digito != '0' && digito != '1') {
            return false;
        }
    }
    return true;
    }
   
    // Esta funcion convierte de base 10 a base 2
    void dab(int decimal) {
    int binario[32];
    int i = 0;
    while (decimal > 0) {
        binario[i] = decimal % 2;
        decimal = decimal / 2;
        i++;
    }
    cout << "El numero en binario es: ";
    for (int j = i - 1; j >= 0; j--) {
        cout << binario[j];
    }
    cout << endl;
    }

    // Esta funcion convierte de base 2 a base 10
    void bad(string binario) {
    int decimal = 0;
    int base = 1;
    int length = binario.length();
    for (int i = length - 1; i >= 0; i--) {
        if (binario[i] == '1') {
            decimal += base;
        } else if (binario[i] != '0') {
            cout << "El numero ingresado no pertenece a base 2." << endl;
            return;
        }
        base *= 2;
    }
    cout << "El numero en decimal es: " << decimal << endl;
    }

    int main() { //Esta es la funcion principal
    int opcion;
    string numero;

    do { // Repite el menu hasta ingresar la opcion 3
        cout << "=== Conversor de bases ===" << endl;
        cout << "1. Convertir de base 10 a base 2" << endl;
        cout << "2. Convertir de base 2 a base 10" << endl;
        cout << "3. Salir" << endl;
        cout << "Ingrese una opcion: ";
        cin >> opcion;

        switch (opcion) {
            case 1:
                cout << "Ingrese un nÃºmero en base 10: ";
                cin >> numero;
                if (!numero.empty() && numero.find_first_not_of("0123456789") == string::npos) { //Verifica si esta en decimal
                    int decimal = stoi(numero);
                    dab(decimal);
                } else {
                    cout << "El numero ingresado no pertenece a base 10." << endl;
                }
                break;
            case 2:
                cout << "Ingrese un numero en base 2: ";
                cin >> numero;
                if (correcto(numero)) {
                    bad(numero);
                } else {
                    cout << "El numero ingresado no pertenece a base 2." << endl;
                }
                break;
            case 3:
                cout << "Saliendo del programa..." << endl;
                break;
            default:
                cout << "Opcion invalida. Por favor, intente nuevamente." << endl;
                break;
        }
        cout << endl;
    } while (opcion != 3);

    return 0;
    }

