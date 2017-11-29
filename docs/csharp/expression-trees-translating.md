---
title: "Překladu stromů výrazů"
description: "Naučte se navštívit každý uzel ve stromu výrazů při sestavování upravené kopie tento strom výrazu."
keywords: "Rozhraní .NET, .NET core"
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: b453c591-acc6-4e08-8175-97e5bc65958e
ms.openlocfilehash: 602a17591d27ebfd098516453b9028bca37ad5e3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="translating-expression-trees"></a>Překladu stromů výrazů

[Předchozí – Vytváření výrazů](expression-trees-building.md)

V této části konečné naučíte navštívit každý uzel ve stromu výrazů při sestavování upravené kopie tento strom výrazu. Jedná se o techniky, které budete používat ve dvou scénářích důležité. Prvním je pochopit algoritmy vyjádřená strom výrazu, aby ji lze přeložit do jiného prostředí. Druhá je, když chcete změnit algoritmus, který byl vytvořen. To může být přidat protokolování, zachytí volání metod a sledovat, nebo pro jiné účely.

## <a name="translating-is-visiting"></a>Překladu je návštěvou

Kód sestavení přeložit strom výrazu je rozšířením co jste viděli již k navštívení všechny uzly ve stromu. Když je přeložit strom výrazu, navštivte všechny uzly a při návštěvě je, vytvářet novou větev. Novou větev může obsahovat odkazy na původní uzlů nebo nové uzly, které jste umístili ve stromové struktuře.

Podíváme se to v praxi návštěvou strom výrazu a vytvoření nového stromu s některé uzly nahrazení. V tomto příkladu budeme nahraďte všechny konstanta konstanta, která je větší desetkrát.
V opačném necháme strom výrazu beze změn. Namísto čtení hodnoty konstanty a nahraďte ji nové konstanta, uděláme toto nahrazení nahrazením konstantního uzlu nový uzel, který provádí násobení.

Zde, jakmile zjistíte konstantního uzlu, vytvořit nový uzel násobení jehož podřízené objekty jsou původní konstanta a konstantu `10`:

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

Nahrazením původní uzel dosadit, je vytvořen novou větev obsahující naše úpravy. Abychom mohli ověřit, která kompilování a provádění stromu nahrazené.

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

Vytvoření nové větve je kombinací návštěvou uzly ve stromu existující a vytváření nových uzlů a jejich vložení do stromu.

Tento příklad ukazuje význam stromů výrazů se nedá změnit. Všimněte si, že novou větev vytvořili výše obsahuje směs nově vytvořený uzlů a uzly z na stávající strom. Který je bezpečné, protože uzly ve stromu existující nemůže být upraven. To může způsobit velké paměti efektivitu.
Stejným uzlům lze použít v rámci stromu, nebo více stromy výrazů. Vzhledem k tomu, že uzly nemůže být upraven, může být stejném uzlu znovu použít vždy, když jeho potřebné.

## <a name="traversing-and-executing-an-addition"></a>Procházení a provádění doplněk

Umožňuje ověřit vytváření druhé návštěvníka, který provede stromu přidání uzlů a vypočítá výsledek. To provedete tak, že několik změny vistor, který jste se seznámili s dosavadní práce. V této nové verzi návštěvníka vrátí součet částečné operace přidání až tento bod. Pro konstantní výraz, který je jednoduše hodnota konstantní výraz. Pro přidání výrazu výsledkem je součet operandy levé a pravé po stromů mít byl vyčerpán.

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

Je celkem kousek sem kód, ale koncepty jsou velmi přístupný.
Tento kód navštíví podřízené objekty do hloubky první hledání. Pokud se setká s konstantního uzlu, návštěvníka vrací hodnotu konstanty. Poté, co návštěvníka navštíví i podřízené objekty, tyto děti se počítá součet vypočítanou pro dílčí stromové struktuře. Přidání uzlu můžete nyní výpočetní jeho součet.
Jakmile navštívili všechny uzly ve stromu výraz součet bude vypočítání. Můžete sledovat spuštění spuštěním ukázky v ladicím programu a trasování provádění.

Pojďme usnadňují trasovat, jak se analyzují uzly a jak jsou součet vypočítána pomocí travsersing stromu. Zde je aktualizovaná verze agregační metody, která zahrnuje s bit informace trasování:

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

Spuštění ve stejném výrazu vypočítá následující výstup:

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

Výstup trasování a podle nich zorientujete ve výše uvedeném kódu. Nyní byste měli mít vycházejí jak kód navštíví každý uzel a vypočítá součet jak prochází stromu a vyhledá součet.

Nyní se podívejme na spuštění různých pomocí výrazu poskytují `sum1`:

```csharp
Expression<Func<int> sum1 = () => 1 + (2 + (3 + 4));
```

Toto je výstup z zkoumání výrazu:

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

Při poslední odpověď je stejný, je úplně jiné traversal stromu. Uzly jsou cesty v jiném pořadí, protože stromu byl zkonstruován pomocí různých operací, které provádí nejdřív.

## <a name="learning-more"></a>Více učení

Tento příklad ukazuje malou část kódu, který by sestavení k procházení a interpretovat algoritmy reprezentována strom výrazu se nezdařilo. Úplné informace práce potřebné k vytvoření knihovnu obecné účely, který překládá stromů výrazů v jiném jazyce, přečtěte si prosím [této série](http://blogs.msdn.com/b/mattwar/archive/2008/11/18/linq-links.aspx) podle Matt Warren. Přejde do skvělé podrobnosti o tom, jak převede kód, které je možné nalézt v strom výrazu se nezdařilo.

Snad že nyní jste viděli true sílu stromů výrazů.
Můžete zkontrolovat sadu kódu, proveďte požadované změny by chtěli tento kód a spouštět změněné verze. Protože jsou neměnné stromů výrazů, můžete vytvořit nové stromy pomocí součásti existující stromy. To minimalizuje množství paměti nutné k vytváření stromů výrazů upravené.

[Další – Součet](expression-trees-summary.md)
