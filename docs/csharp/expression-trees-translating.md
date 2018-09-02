---
title: Překlad stromů výrazů
description: Zjistěte, jak chcete navštívit každý uzel ve stromu výrazů při sestavování upravenou kopii tohoto stromu výrazu.
ms.date: 06/20/2016
ms.assetid: b453c591-acc6-4e08-8175-97e5bc65958e
ms.openlocfilehash: bd4aec2ef34e4dc972ae867c6b5070f92dcbc498
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43463720"
---
# <a name="translating-expression-trees"></a>Překlad stromů výrazů

[Předchozí – Vytváření výrazů](expression-trees-building.md)

V této závěrečné sekci dozvíte, jak chcete navštívit každý uzel ve stromu výrazů při sestavování upravenou kopii tohoto stromu výrazu. Jedná se o techniky, které budete používat v dva důležité scénáře. Prvním je pochopit algoritmy vyjádřená strom výrazu tak, aby jej lze přeložit do jiného prostředí. Druhým je, když chcete změnit algoritmus, který byl vytvořen. To může být přidání protokolování, zachytí volání metod a sledovat jejich, nebo pro jiné účely.

## <a name="translating-is-visiting"></a>Překlad je návštěva

Kód sestavení pro převod strom výrazu je rozšířením co jste viděli již k navštívení všechny uzly ve stromu. Když jste přeložit strom výrazu, najdete všechny uzly a při jejich návštěvě, vytváření nového stromu. Nové stromové struktury mohou obsahovat odkazy na původní uzly nebo nové uzly, které jste umístili ve stromové struktuře.

Podívejme se to v praxi navštívit strom výrazů a vytvořením nové větve s některé uzly nahrazení. V tomto příkladu podíváme nahradit libovolná konstanta s konstantou, která je větší, desetkrát.
V opačném případě Ponecháme stromu výrazů beze změn. Namísto hodnotou konstanty pro čtení a jeho nahrazení atributem nové konstantou, uděláme toto nahrazení nahrazením konstantního uzlu nový uzel, který provede násobení.

Jakmile najdete konstantního uzlu, můžete zde vytvářet nový uzel násobení, jehož potomci se původní konstantní a konstanty `10`:

```csharp
private static Expression ReplaceNodes(Expression original)
{
    if (original.NodeType == ExpressionType.Constant)
    {
        return Expression.Multiply(original, Expression.Constant(10));
    }
    else if (original.NodeType == ExpressionType.Add)
    {
        var binaryExpression = (BinaryExpression)original;
        return Expression.Add(
            ReplaceNodes(binaryExpression.Left),
            ReplaceNodes(binaryExpression.Right));
    }
    return original;
}
```

Nahrazením původní uzel dosadit, je vytvořen nový stromu, který obsahuje úpravy. Abychom mohli ověřit, který kompilaci a spouštění stromu nahrazené.

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
var sum = ReplaceNodes(addition);
var executableFunc = Expression.Lambda(sum);

var func = (Func<int>)executableFunc.Compile();
var answer = func();
Console.WriteLine(answer);
```

Vytvoření nové větve je kombinací navštívit uzlů ve stromu existující a vytváření nových uzlů a jejich vložení do stromu.

Tento příklad ukazuje důležitost stromů výrazů jsou neměnné. Všimněte si, že nové větve vytvořené výše obsahuje kombinaci nově vytvořené uzly a uzly ze stávající strom. Který je bezpečné, protože uzly ve stromu existující nelze upravovat. To může způsobit velké paměti efektivitu.
Stejné uzly je možné v rámci stromu, nebo více stromy výrazů. Protože uzly nelze upravovat, může být stejném uzlu znovu použít vždy, když své potřeby.

## <a name="traversing-and-executing-an-addition"></a>Procházení a provádění doplněk

Můžeme to ověřit tak vytváření druhé návštěvníka, který vás provede přidáním uzlů stromu a vypočítá výsledek. Můžete to provést tak, že několik úprav vistor, které jste zatím viděli. V této nové verzi návštěvníka vrátí částečného součtu operace přidání do této chvíle. Pro konstantní výraz, který je jednoduše hodnotu konstantní výraz. Pro přidání výrazu výsledkem je součet operandů levé a pravé, jakmile byla z těchto stromů provázány.

```csharp
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var three= Expression.Constant(3, typeof(int));
var four = Expression.Constant(4, typeof(int));
var addition = Expression.Add(one, two);
var add2 = Expression.Add(three, four);
var sum = Expression.Add(addition, add2);

// Declare the delegate, so we can call it 
// from itself recursively:
Func<Expression, int> aggregate = null;
// Aggregate, return constants, or the sum of the left and right operand.
// Major simplification: Assume every binary expression is an addition.
aggregate = (exp) =>
    exp.NodeType == ExpressionType.Constant ?
    (int)((ConstantExpression)exp).Value :
    aggregate(((BinaryExpression)exp).Left) + aggregate(((BinaryExpression)exp).Right);

var theSum = aggregate(sum);
Console.WriteLine(theSum);
```

Je hodně Zde uveďte kód, ale popsané koncepty se velmi přístupné.
Tento kód navštíví podřízené objekty první hledání hloubku. Pokud se setká konstantního uzlu, návštěvníka hodnotu konstanty. Poté, co návštěvníka navštíví i podřízené položky, tyto podřízené objekty se vypočítat součet vypočítat pro dílčí stromové struktuře. Přidání uzlu můžete nyní výpočetní jeho součet.
Jakmile navštívili všech uzlů ve stromu výrazu součet bude vypočítání. Sledování spuštění spuštěním ukázky v ladicím programu a trasování provádění.

Pojďme usnadňují sledování, jak se analyzují uzly a jak se počítají součet tak, že travsersing stromu. Tady je aktualizovanou verzi agregační metoda, která obsahuje hodně trasovací informace:

```csharp
private static int Aggregate(Expression exp)
{
    if (exp.NodeType == ExpressionType.Constant)
    {
        var constantExp = (ConstantExpression)exp;
        Console.Error.WriteLine($"Found Constant: {constantExp.Value}");
        return (int)constantExp.Value;
    }
    else if (exp.NodeType == ExpressionType.Add)
    {
        var addExp = (BinaryExpression)exp;
        Console.Error.WriteLine("Found Addition Expression");
        Console.Error.WriteLine("Computing Left node");
        var leftOperand = Aggregate(addExp.Left);
        Console.Error.WriteLine($"Left is: {leftOperand}");
        Console.Error.WriteLine("Computing Right node");
        var rightOperand = Aggregate(addExp.Right);
        Console.Error.WriteLine($"Right is: {rightOperand}");
        var sum = leftOperand + rightOperand;
        Console.Error.WriteLine($"Computed sum: {sum}");
        return sum;
    }
    else throw new NotSupportedException("Haven't written this yet");
}
```

Spuštění ve stejném výrazu poskytuje následující výstup:

```
10
Found Addition Expression
Computing Left node
Found Addition Expression
Computing Left node
Found Constant: 1
Left is: 1
Computing Right node
Found Constant: 2
Right is: 2
Computed sum: 3
Left is: 3
Computing Right node
Found Addition Expression
Computing Left node
Found Constant: 3
Left is: 3
Computing Right node
Found Constant: 4
Right is: 4
Computed sum: 7
Right is: 7
Computed sum: 10
10
```

Trasování výstupu a můžete pokračovat ve výše uvedeném kódu. Je třeba možnost pracovat na více systémů jak kód navštíví každý uzel a kód vypočítá součet prochází stromu a zjistí součet.

Teď se podívejme se na různé spuštěný proces, pomocí výrazu Dal `sum1`:

```csharp
Expression<Func<int> sum1 = () => 1 + (2 + (3 + 4));
```

Zde se nachází výstup z zkoumání tento výraz:

```
Found Addition Expression
Computing Left node
Found Constant: 1
Left is: 1
Computing Right node
Found Addition Expression
Computing Left node
Found Constant: 2
Left is: 2
Computing Right node
Found Addition Expression
Computing Left node
Found Constant: 3
Left is: 3
Computing Right node
Found Constant: 4
Right is: 4
Computed sum: 7
Right is: 7
Computed sum: 9
Right is: 9
Computed sum: 10
10
```

I když je poslední odpovědí je stejný, přechod zálohovaných stromové struktury se úplně. Uzly se přesunul v jiném pořadí, protože stromu byl zkonstruován pomocí různých operací, ke kterým dochází poprvé.

## <a name="learning-more"></a>Další informace

Tento příklad ukazuje malou část kódu, který by sestavení k procházení a interpretovat algoritmy reprezentována strom výrazu. Úplné informace veškeré práce potřebné k vytvoření knihovny obecné účely, který překládá stromů výrazů do jiného jazyka, přečtěte si prosím [tuto řadu](https://blogs.msdn.com/b/mattwar/archive/2008/11/18/linq-links.aspx) podle Matt Warren. To obsahuje skvělé podrobnosti o tom, jak přeložit některý kód, který může pro vás ve stromu výrazu.

Doufám, že už teď víte, výkon služby stromy výrazů.
Můžete prozkoumat sadu kódu, proveďte požadované změny by rádi, že kód a provést změny verze. Protože jsou neměnné stromů výrazů, můžete vytvořit nové stromové struktury pomocí komponenty větvích. Tím se minimalizují množství paměti, které jsou potřebné k vytvoření stromů výrazu upravené.

[Další--Sečetl](expression-trees-summary.md)
