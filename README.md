# tema1 Desenarea paralelă de curbe contur folosind algoritmul Marching Squares

Implementarea constă în paralelizarea funcției seriale `rescale_image` care are ca rol scalarea imaginilor ce depășesc dimensiunea dată de 2048x2048. Pentru a obține paralelizarea s-au realizat următorii pași, respectiv modificări:

1. **Identificarea porțiunii de paralelizat din cadrul funcției**: scalarea imaginii folosind funcția `sample_bicubic` a fost împărțită în mod egal tuturor celor P thread-uri.
2. **Implementarea thread-urilor folosind Pthreads și inițializarea parametrilor din structura de thread-uri în `main`**.
3. **În varianta secvențială alocarea memoriei pentru imaginea ce urma a fi scalată avea loc în cadrul funcției `rescale_image`**. În varianta paralelă, alocarea se face în `main`, o singură dată pentru toate cele P thread-uri.
4. **Thread-urile execută funcția `thread_function` care apelează de fapt funcția paralelă `rescale_image`**.
