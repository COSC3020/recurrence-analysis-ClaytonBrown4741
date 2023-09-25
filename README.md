[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-718a45dd9cf7e7f842a935f5ebbe5719a5e09af4491e668f4dbf3b35d5cca122.svg)](https://classroom.github.com/online_ide?assignment_repo_id=11857668&assignment_repo_type=AssignmentRepo)
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

**ANSWER**  
THIS IS NOT FINISHED! IF YOU NOTICE ANYTHING WRONG WITH MY REASONING THUS FAR, PLEASE  
LET ME KNOW!  

To begin, we start with defining the recurrence relation. In this case, it would  
look as follows:  
T(n) = 1 if n <= 1. Otherwise, T(n)= $3T(n/3)+n^5+1$  

In this case, the base case is 1, because when n is less than or equal to 0, it simply returns which is  
one action. In the other case, the 3T stands for the 3 recursive calls that have to be made. The n/3  
is put in in order to account for the fact that the value of n is divided by 3 every time it is called  
recursively. The $n^5$ represents the for loops in the center of the function. And finally, the +1 at the  
end is put in in order to account for the initialization of the count variable. Using this information, the  
proof can be shown as follows:  

T(n)= $3T(n/3)+n^5+1$  
= $3(3T(n/9)+(n/3)^5+1)+n^5+1$  
= $9T(n/9)+(n/3)^5+n^5+2$  
= $9(3T(n/27)+(n/9)^5+1)+(n/3)^5+n^5+2$  

