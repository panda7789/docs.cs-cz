---
title: =&gt; Operator - C# odkaz
ms.custom: seodec18
ms.date: 10/02/2017
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: c193a91eaffe2e56a5df2afa8d66989981123a48
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238790"
---
# <a name="gt-operator-c-reference"></a>=&gt; – Operátor (referenční dokumentace jazyka C#)

`=>` Dvě možnosti, jak v jazyce C# lze použít operátor:

- Jako [operátor lambda](#lamba-operator) v [výraz lambda](../../lambda-expressions.md), rozděluje vstupní proměnné z hlavní část výrazu lambda.
 
- V [definice těla výrazu](#expression-body-definition), název člena ho odděluje od implementace členu. 

## <a name="lambda-operator"></a>Lambda – operátor

`=>` Token se nazývá operátor lambda. Používá se v *výrazy lambda* oddělení vstupních proměnných na levé straně od hlavní část výrazu lambda na pravé straně. Výrazy lambda jsou vložené výrazy podobné anonymní metody, ale flexibilnější; často se používají v dotazech LINQ, které jsou vyjádřeny syntaxe využívající metody. Další informace najdete v tématu [výrazy Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 Následující příklad ukazuje dva způsoby, jak vyhledat a zobrazit délku nejkratší řetězce v poli řetězců. První část v příkladu platí výrazu lambda (`w => w.Length`) ke každému prvku objektu `words` pole a pak použije <xref:System.Linq.Enumerable.Min%2A> metody k vyhledání minimální délku. Pro porovnání druhá část tento příklad ukazuje delší dobu řešení, které používá syntaxi dotazu pro stejnou věc udělat.  
  
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
 `=>` Operátor má stejnou prioritu jako operátor přiřazení (`=`) a je asociativní zprava.  
  
 Můžete explicitně zadat typ je vstupní proměnná nebo umožnili kompilátoru odvodit. v obou případech je proměnná silného typu v době kompilace. Při zadávání typu musíte uvést název typu a název proměnné v závorkách, jak ukazuje následující příklad.  
  
```csharp  
int shortestWordLength = words.Min((string w) => w.Length);  
```  
  
### <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zapsat lambda výraz pro přetížení operátoru standardního dotazu <xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType> , který přebírá dva argumenty. Vzhledem k tomu, že výraz lambda má více než jeden parametr, parametry musí být uzavřen v závorkách. Druhý parametr `index`, představuje index aktuálního prvku kolekce. `Where` Výraz vrátí všechny řetězce, jejichž délky mají hodnotu menší než index pozice v poli.  
  
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
## <a name="expression-body-definition"></a>Definice textu výrazu

Definice těla výrazu obsahuje implementace člena ve vysoce zhuštěnému čitelné formy. Má následující obecnou syntaxi:

```csharp
member => expression;
```
kde *výraz* je platný výraz. Všimněte si, že *výraz* může být *výrazu příkazu* pouze pokud je člen návratový typ je `void`, nebo pokud je člen konstruktoru nebo finalizační metodu.

Definice textu výrazu pro metody a vlastnosti get příkazy jsou podporovány od verze C# 6. Definice těla výrazu pro konstruktory, finalizační metody, nastavte vlastnost příkazy a indexery jsou podporovány od verze C# 7.

Tady je definice těla výrazu pro `Person.ToString` metody:

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

Je zkrácená verze následující definici metody:

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```
Podrobnější informace o definicích tělo výrazu, najdete v článku [členové tvoření](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)   
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)   
- [Výrazy lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)   
- [Členové tvoření](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).