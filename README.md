public class App{[App.java](https://github.com/user-attachments/files/24695680/App.java)
package lessonfifteenth;

import java.util.Scanner;

public class App {

	public static void main(String[] args) {
		// Uygulama: GCD(Greatest Common Divisor), LCM(Least Upper Multiple)
		// and Relatively prime(Aralarında asal)
		// Ekrandan iki sayı alınız
		// a) GCD
		// b) LCM (hint: a.b/gcd(a,b) = lcm(a,b))
		// c) Relatively prime

		Scanner s = new Scanner(System.in);

		System.out.print("Input the first number: ");
		int number1 = s.nextInt();
		System.out.print("Input the second number: ");
		int number2 = s.nextInt();

		int resultGcd = gcd(number1, number2);
		System.out.println("gcd(" + number1 + "," + number2 + ") = " + resultGcd);
		
		int gcdWithEuclidianAlgorithm = gcdWithEuclidianAlgorithm(number1, number2);
		System.out.println("gcdWithEuclidianAlgorithm(" + number1 + "," + number2 + ") = " + gcdWithEuclidianAlgorithm);

		int resultLcm = lcm(number1, number2);
		System.out.println("lcm(" + number1 + "," + number2 + ") = " + resultLcm);

		System.out.println((isRelativelyPrime(number1, number2)));

	}

	// standart yöntem
	public static int gcd(int number1, int number2) {
		int gcd = 1;
		int counter = 0;
		int smallest = Math.min(number1, number2);
		for (int i = 1; i <= smallest; i++) {
			counter++;
			if (number1 % i == 0 && number2 % i == 0) {
				gcd = i;
			}
		}
		System.out.println("öklidsiz"+counter);
		return gcd;
	}

	// Öklid algoritması
	public static int gcdWithEuclidianAlgorithm(int number1, int number2) {
		int largest = Math.max(number1, number2);
		int smallest = Math.min(number1, number2);
		int temp = largest;
		largest = smallest;
		int counter = 0;
		while (temp % smallest != 0) {
			counter++;
			smallest = temp % smallest;
		}
		System.out.println("öklidle:"+counter);
		return smallest;

	}

	public static int lcm(int number1, int number2) {
		int lcm = number1 * number2 / gcdWithEuclidianAlgorithm(number1, number2);
		return lcm;
	}

	public static String isRelativelyPrime(int number1, int number2) {
		return gcdWithEuclidianAlgorithm(number1, number2) == 1 ? "Relatively prime numbers" : "NOT relatively prime numbers";
	}

}
