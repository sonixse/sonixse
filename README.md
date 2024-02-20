/* Returns either the index of the location in the array,
  or -1 if the array did not contain the targetValue */
var doSearch = function(array, targetValue) {
	var min = 0;
	var max = array.length - 1;
    var guess;
    var i = 1; //crear una nueva variable iterativa para el bucle While
    
    while(max >= min){ 
        //entra si cumple la condición, que es el contrario de max < min (fuera bucle While)
        
        guess = floor((max + min) / 2);
        
        if(array[guess] === targetValue){
            println("Número total de intentos: " + i);
            return guess;
            
        }else if(array[guess] < targetValue){
            min = guess + 1;

        }else{
            max = guess - 1;
        }
        
        i += 1; //calcular índices del nuevo punto medio
        println(guess); //escribe el intento en cada paso, es el índice del intento
        // no el valor del elemento al que apunta
    }


	return -1; //cuando max < min
};

var primes = [2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 
		41, 43, 47, 53, 59, 61, 67, 71, 73, 79, 83, 89, 97];

var result = doSearch(primes, 73);
println("Found prime at index " + result);

Program.assertEqual(doSearch(primes, 73), 20); 
//descomentar assertEqual() para comprobar que está regresando el valor esperado
Program.assertEqual(doSearch(primes, 5), 2);
Program.assertEqual(doSearch(primes, 83), 22);

