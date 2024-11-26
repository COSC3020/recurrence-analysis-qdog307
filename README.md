# Recurrence Analysis -- Mystery Function

Analyze the running time of the following recursive procedure as a function of
$n$ and find a tight big $O$ bound on the runtime for the function. You may
assume that each operation takes unit time. You do not need to provide a formal
proof, but you should show your work: at a minimum, show the recurrence relation
you derive for the runtime of the code, and then how you solved the recurrence
relation.

```javascript
function mystery(n) {
    if(n <= 1)
        return;
    else {
        mystery(n / 3);
        var count = 0;
        mystery(n / 3);
        for(var i = 0; i < n*n; i++) {
            for(var j = 0; j < n; j++) {
                for(var k = 0; k < n*n; k++) {
                    count = count + 1;
                }
            }
        }
        mystery(n / 3);
    }
}
```

Add your answer to this markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions. 

Recurrence Analysis
The solution to the recurrence is $T(n) = 3T\left(\frac{n}{3}\right) + Cn^5$, where $C$ is a constant. Here's how this is derived:
1.	Recursive Calls:
	The function makes three recursive calls, each on an input size of $n/3$. This contributes $3T\left(\frac{n}{3}\right)$ to the recurrence.
2.	Nested Loops:
	The triple-nested for loop runs:
	Outer loop: $n^2$ iterations.
	Middle loop: $n$ iterations.
	Inner loop: $n^2$ iterations.
	This results in $n^2 \times n \times n^2 = n^5$ iterations.
	Thus, the work done by the nested loops contributes $Cn^5$, where $C$ is a constant.
Combining these, the recurrence relation becomes:
T(n)=3T(n3)+Cn5T(n) = 3T\left(\frac{n}{3}\right) + Cn^5T(n)=3T(3n)+Cn5
________________________________________
Solving the Recurrence
Using backward substitution, we expand the recurrence:
1.	First Expansion:
T(n)=3(3T(n9)+Cn53)+Cn5T(n) = 3\left(3T\left(\frac{n}{9}\right) + \frac{Cn^5}{3}\right) + Cn^5T(n)=3(3T(9n)+3Cn5)+Cn5 T(n)=9T(n9)+Cn53+Cn5T(n) = 9T\left(\frac{n}{9}\right) + C\frac{n^5}{3} + Cn^5T(n)=9T(9n)+C3n5+Cn5
2.	Second Expansion:
T(n)=9(3T(n27)+Cn532)+Cn53+Cn5T(n) = 9\left(3T\left(\frac{n}{27}\right) + \frac{Cn^5}{3^2}\right) + C\frac{n^5}{3} + Cn^5T(n)=9(3T(27n)+32Cn5)+C3n5+Cn5 T(n)=27T(n27)+Cn532+Cn53+Cn5T(n) = 27T\left(\frac{n}{27}\right) + C\frac{n^5}{3^2} + C\frac{n^5}{3} + Cn^5T(n)=27T(27n)+C32n5+C3n5+Cn5
3.	General Form: After $k$ expansions, the recurrence becomes:
T(n)=3kT(n3k)+Cn5∑i=0k−113iT(n) = 3^k T\left(\frac{n}{3^k}\right) + Cn^5 \sum_{i=0}^{k-1} \frac{1}{3^i}T(n)=3kT(3kn)+Cn5i=0∑k−13i1
4.	Stopping Condition: When $3^k = n$, we have $k = \log_3 n$, and $T(1)$ is a constant:
T(n)=n⋅T(1)+Cn5∑i=0log⁡3n−113iT(n) = n \cdot T(1) + Cn^5 \sum_{i=0}^{\log_3 n - 1} \frac{1}{3^i}T(n)=n⋅T(1)+Cn5i=0∑log3n−13i1
5.	Simplifying the Summation: The summation $\sum_{i=0}^{\log_3 n - 1} \frac{1}{3^i}$ is a geometric series that converges to 1 as $n$ grows:
T(n)=n⋅Θ(1)+n5⋅1T(n) = n \cdot \Theta(1) + n^5 \cdot 1T(n)=n⋅Θ(1)+n5⋅1
6.	Final Complexity: Since $\Theta(n)$ is negligible compared to $\Theta(n^5)$, the overall runtime is:
T(n)∈Θ(n5)T(n) \in \Theta(n^5)T(n)∈Θ(n5)
________________________________________
Conclusion
The final time complexity of the function is:
T(n)∈Θ(n5)T(n) \in \Theta(n^5)T(n)∈Θ(n5)

Sources: Word Doc to fromat this. Lecture sldies for backwards substitution. Professor Lars Office hours to better understand notation and equations. ChatGPT to better understand notation and backwards substitution.  https://www.geeksforgeeks.org/recurrence-relations-a-complete-guide/?ref=header_outind. To double check math I used wolfram alpha. 




I certify that I have listed all sources used to complete this exercise, including the use of any Large Language Models. All of the work is my own, except where stated otherwise. I am aware that plagiarism carries severe penalties and that if plagiarism is suspected, charges may be filed against me without prior notice.
