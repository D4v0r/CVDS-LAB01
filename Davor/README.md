# __Readme__

Hola,  mi nombre es ***Davor Javier Cortés Cardozo*** soy estudiante de la [Escuela Colombiana de Ingeniería Julio Garavito](https://www.escuelaing.edu.co/es/), ubicada en la ciudad de Bogotá.

## Acerca de mi
___
Me gusta leer acerca de nuevas tecnologias, especialmente si esta relacionado con el mundo de la Inteligencia Artificial.


![alt](https://d3njjcbhbojbot.cloudfront.net/api/utilities/v1/imageproxy/https://coursera-course-photos.s3.amazonaws.com/de/8a87108f2211e7b04e29ba33dce228/Deep-learning-for-computer-vision2.png?auto=format%2Ccompress&dpr=1)

Actualmente me encuentro en Octavo semestre cursando las siguientes materias:
* __CVDS (Ciclos de Vida del Desarrollo de Software)__
* __AUPN (Automatización de Procesos de Negocio)__
* __SPTI (Seguridad y Privacidad de TI)__
* __IAIA (Introducción a la Inteligencia Artificial)__
* __EGI2 (English 2)__

### Scripts
___
1. Solución al problema 11110 Equidivisions de Uva
   ```
   from sys import stdin
    def reg_search(mat,i,j,reg): #Algoritmo flooad-fill
    global conta 
    if mat[i][j] == reg:
        mat[i][j] = 0
        conta += 1
        try:
            if mat[i][j-1] == reg:
                reg_search(mat, i, j-1, reg)
        except IndexError:
            pass
        try:
            if mat[i-1][j] == reg:
                reg_search(mat, i-1, j, reg)
        except IndexError:
            pass
        try:
            if mat[i][j+1] == reg:
                reg_search(mat, i, j+1, reg)
        except IndexError:
            pass
        try:
            if mat[i+1][j] == reg:
                reg_search(mat, i+1, j, reg)
        except IndexError:
            pass
    else:
        return
    def main():
        global conta
        n = int(stdin.readline().strip())
        while True:
            if n == 0:
                break
            flag = True
            regiones = [r+1 for r in range(n)]
            mat = [[n for i in range(n)]for i in range(n)]
            casos_base = {}
            for y in range(n-1):
                l = [int(x) for x in stdin.readline().strip().split()]
                if l == []:
                    break
                casos_base[y+1] = [l[0]-1,l[1]-1]
                for x in range(0,len(l),2):
                    i, j = l[x]-1, l[x+1]-1
                    mat[i][j] = y+1
            if n == 1:
                flag = True
            elif l != []:
                for i in range(len(mat)):
                    for j in range(len(mat)):
                        if mat[i][j] == n:
                            casos_base[n] = [i,j]
                for region in regiones:
                    conta = 0
                    reg_search(mat,casos_base[region][0],casos_base[region][1],region)
                    for fila in mat:
                        if region in fila or conta != n:
                            flag = False
                            break
                        else: continue
            else: flag = False
            if flag: print('good')
            else: print('wrong')
            n = int(stdin.readline().strip())
                
    main()
   ```
2. Implementación de un Trigger con pl/sql
    ```
    CREATE TRIGGER TG_OPINION_NUMERO_FECHA
    BEFORE INSERT 
    ON opinion
    FOR EACH ROW
    DECLARE
    num NUMBER(5);
    fecha DATE;
    BEGIN
        SELECT max(numero) INTO num FROM opinion;
        SELECT TO_DATE(sysdate,'DD-MM-YYYY') INTO fecha FROM dual;
        IF (num is NULL) THEN
            :new.numero := 1;
        ELSE
            :new.numero := num+1;
        END IF;
        :new.fecha := fecha;
    END TG_OPINION_NUMERO_FECHA;
    ```


