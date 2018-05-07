---
title: =&gt; Operátor (referenční dokumentace jazyka C#)
ms.date: 10/02/2017
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: d1565e262fbd3ebcee2d1576a2a0c8ed3ba8ce38
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="gt-operator-c-reference"></a>=&gt; Operátor (referenční dokumentace jazyka C#)

`=>` Operátor lze použít dvěma způsoby v jazyce C#:

- Jako [lambda operátor](#lamba-operator) v [výrazu lambda](../../lambda-expressions.md), ji odděluje vstupní proměnné z textu lambda.
 
- V [výraz text definice](#expression-body-definition), ji odděluje název člena z implementace člen. 

## <a name="lambda-operator"></a>Lambda – operátor

`=>` Token se označuje jako operátor lambda. Používá se v *výrazy lambda* oddělit vstupní proměnné na levé straně z textu lambda na pravé straně. Lambda – výrazy jsou podobná anonymní metody ale flexibilnější; vložené výrazy používají se hojně v dotazech LINQ, které jsou vyjádřeny v syntaxe využívající metody. Další informace najdete v tématu [výrazy Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 Následující příklad ukazuje dva způsoby, jak vyhledat a zobrazit délky řetězce nejkratší v poli řetězců. První část příkladu platí výrazu lambda (`w => w.Length`) pro každý element `words` pole a pak používá <xref:System.Linq.Enumerable.Min%2A> metody k vyhledání nejmenší délka. Pro porovnání druhou částí příklad ukazuje delší řešení, které používá syntaxi dotazu pro stejnou věc udělat.  
  
```csharp  
string[] words = { "cherry", "apple", "blueberry" };  
  
// Use method syntax to apply a lambda expression to each element  
// of the words array.   
int shortestWordLength = words.Min(w => w.Length);  
Console.WriteLine(shortestWordLength);  
  
// Compare the following code that uses query syntax.  
// Get the lengths of each word in the words array.  
var query = from w in words  
            select w.Length;  
// Apply the Min method to execute the query and get the shortest length.  
int shortestWordLength2 = query.Min();  
Console.WriteLine(shortestWordLength2);  
  
// Output:   
// 5  
// 5  
```  
  
### <a name="remarks"></a>Poznámky  
 `=>` Operátor má stejnou prioritu jako operátor přiřazení (`=`) a je zprava asociativní.  
  
 Můžete zadat typ vstupní proměnné explicitně nebo to kompilátoru odvození. v obou případech je proměnná silného typu v době kompilace. Když zadáte typu, je nutné uzavřít název typu a název proměnné v závorkách, jak ukazuje následující příklad.  
  
```csharp  
int shortestWordLength = words.Min((string w) => w.Length);  
```  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak napsat výrazu lambda pro přetížení operátoru standardní dotazu <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> , která má dva argumenty. Protože výrazu lambda má více než jeden parametr, parametry musí být uzavřena v závorkách. Druhý parametr `index`, představuje index aktuální element v kolekci. `Where` Výraz vrátí všechny řetězce, jejichž délky mají hodnotu menší než jejich pozic index v poli.  
  
```csharp  
static void Main(string[] args)  
{  
    string[] digits = { "zero", "one", "two", "three", "four", "five",   
            "six", "seven", "eight", "nine" };  
  
    Console.WriteLine("Example that uses a lambda expression:");  
    var shortDigits = digits.Where((digit, index) => digit.Length < index);  
    foreach (var sD in shortDigits)  
    {  
        Console.WriteLine(sD);  
    }  
  
    // Output:  
    // Example that uses a lambda expression:  
    // five  
    // six  
    // seven  
    // eight  
    // nine  
}  
```  
## <a name="expression-body-definition"></a>Výraz definice textu

Definici textu výraz poskytuje implementaci člena ve formuláři vysoce zhuštěné a čitelné. Má následující obecné syntaxi:

```csharp
member => expression;
```
kde *výraz* je platný výraz. Všimněte si, že *výraz* může být *příkaz výraz* pouze pokud je člen návratový typ je `void`, nebo pokud je člen konstruktor nebo finalizační metody.

Výraz definice textu pro metody a vlastnosti příkazy get jsou podporované od verze jazyka C# 6. Výraz definice textu pro konstruktory, finalizační metody, vlastnosti nastavte příkazy a indexery jsou podporované od verze jazyka C# 7.

Následuje definici textu výraz `Person.ToString` metoda:

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

Je sdružená verzi následující definici metody:

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```
Podrobnější informace o výraz text definice, najdete v části [výraz vozidlo členy](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).

## <a name="see-also"></a>Viz také  
[Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)   
[Průvodce programováním v C#](../../../csharp/programming-guide/index.md)   
[Lambda – výrazy](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)   
[Výraz vozidlo členy](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).