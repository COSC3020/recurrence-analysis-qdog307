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

The solution is 3t(n/3)+C(n^5) where C is a constant, I solved this by first looking at the recurive calls that are made which is three. Then looking at the nested loop
it is n^2*n*n^2 which equals n^5.
Using the backwards substituon method, first unfolding we get 9T(n/9)+O(n^5/3)+O(n^5) then we do a second unfolding we get 27T(n/27)+O(n^5/3^2)+O(n^5/3)+O(n^5), so the general form that we get is 3^kT(n/3^k)+O(n^5/(3^(k-1))+...+O(n^5/3)+O(n^5). If we simplify the gernal form 3^k=n => k= log3N, then we sub into summation, O 
​
O (n^5 i=0∑log 3n−1 1/3^i) =O(n^5⋅1)=O(n^5)


I certify that I have listed all sources used to complete this exercise, including the use of any Large Language Models. All of the work is my own, except where stated otherwise. I am aware that plagiarism carries severe penalties and that if plagiarism is suspected, charges may be filed against me without prior notice.
