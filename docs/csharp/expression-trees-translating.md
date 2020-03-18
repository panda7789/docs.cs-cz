---
title: Překlad stromů výrazů
description: Zjistěte, jak navštívit každý uzel ve stromu výrazů při vytváření upravené kopie tohoto stromu výrazů.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: b453c591-acc6-4e08-8175-97e5bc65958e
ms.openlocfilehash: f60c447d5c89aa83f85073e642e621608131ed8d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76115772"
---
# <a name="translate-expression-trees"></a>Přeložit stromy výrazů

[Předchozí -- Výrazy budovy](expression-trees-building.md)

V této poslední části se dozvíte, jak navštívit každý uzel ve stromu výrazů při vytváření upravené kopie tohoto stromu výrazů. Jedná se o techniky, které budete používat ve dvou důležitých scénářích. Prvním z toho je pochopit algoritmy vyjádřené stromem výrazů tak, aby mohl být přeložen do jiného prostředí. Druhý je, když chcete změnit algoritmus, který byl vytvořen. To může být přidat protokolování, volání metody zachycení a sledovat je nebo jiné účely.

## <a name="translating-is-visiting"></a>Překládání je na návštěvě

Kód, který vytvoříte k překladu stromu výrazů, je rozšířením toho, co jste již viděli k návštěvě všech uzlů ve stromu. Při překladu stromu výrazů navštívíte všechny uzly a při jejich návštěvě vytvoříte nový strom. Nový strom může obsahovat odkazy na původní uzly nebo nové uzly, které jste umístili do stromu.

Podívejme se na to v akci návštěvou stromu výrazů a vytvořením nového stromu s některými náhradními uzly. V tomto příkladu nahradíme libovolnou konstantu konstantou, která je desetkrát větší.
Jinak necháme strom výrazu neporušený. Spíše než čtení hodnoty konstanty a nahrazení nové konstanty, provedeme toto nahrazení nahrazením konstantní uzel s novým uzlovým, který provádí násobení.

Zde, jakmile najdete konstantní uzel, vytvoříte nový uzel násobení, jehož podřízené `10`jsou původní konstanta a konstanta :

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

Nahrazením původního uzlu náhražkou se vytvoří nový strom, který obsahuje naše modifikace. Můžeme ověřit, že kompilací a provedením nahrazený strom.

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

Vytvoření nového stromu je kombinací návštěvy uzlů v existujícím stromu a vytvoření nových uzlů a jejich vložení do stromu.

Tento příklad ukazuje důležitost výrazstromy jsou neměnné. Všimněte si, že nový strom vytvořený výše obsahuje směs nově vytvořených uzlů a uzlů z existujícího stromu. To je bezpečné, protože uzly v existujícím stromu nelze změnit. To může mít za následek významné účinnosti paměti.
Stejné uzly lze použít v celém stromu nebo ve více stromech výrazů. Vzhledem k tomu, že uzly nelze změnit, stejný uzel lze znovu použít vždy, když je to potřeba.

## <a name="traversing-and-executing-an-addition"></a>Procházení a provádění sčítání

Ověřme to vytvořením druhého návštěvníka, který projde stromem uzlů sčítání a vypočítá výsledek. Můžete to udělat tím, že pár úprav návštěvníka, které jste viděli tak daleko. V této nové verzi návštěvník vrátí částečný součet operace sčítání až do tohoto bodu. Pro konstantní výraz, který je jednoduše hodnota konstantní výraz. Pro výraz sčítání je výsledkem součet levého a pravého operandu, jakmile jsou tyto stromy projety.

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

Je tu docela dost kódu, ale pojmy jsou velmi přístupný.
Tento kód navštíví děti v hloubce první vyhledávání. Když narazí na konstantní uzel, návštěvník vrátí hodnotu konstanty. Poté, co návštěvník navštíví obě děti, tyto děti vypočítají součet vypočítaný pro tento podstrom. Uzel sčítání nyní můžete vypočítat jeho součet.
Po navštívení všech uzlů ve stromu výrazů bude součet vypočítán. Spuštění můžete sledovat spuštěním ukázky v ladicím programu a sledováním spuštění.

Usnadněme sledování toho, jak jsou analyzovány uzly a jak se vypočítá součet procházením stromu. Zde je aktualizovaná verze metody Aggregate, která obsahuje poměrně dost informací o trasování:

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

Spuštění ve stejném výrazu dává následující výstup:

```output
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

Sledujte výstup a postupujte podle výše uvedeného kódu. Měli byste být schopni zjistit, jak kód navštíví každý uzel a vypočítá součet, jak prochází stromem a najde součet.

Nyní se podívejme na jiný běh, s `sum1`výrazem daný :

```csharp
Expression<Func<int> sum1 = () => 1 + (2 + (3 + 4));
```

Zde je výstup z zkoumání tohoto výrazu:

```output
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

Zatímco konečná odpověď je stejná, strom traversal je zcela odlišný. Uzly jsou prohledány v jiném pořadí, protože strom byl vytvořen s různými operacemi, které se vyskytly jako první.

## <a name="learning-more"></a>Další informace

Tato ukázka ukazuje malou podmnožinu kódu, který byste vytvořili k procházení a interpretaci algoritmů reprezentovaných stromem výrazů. Pro úplnou diskusi o všech pracích potřebných k vybudování univerzální knihovny, která překládá výraz stromy do jiného jazyka, přečtěte si [prosím tuto sérii](https://docs.microsoft.com/archive/blogs/mattwar/linq-building-an-iqueryable-provider-series) Matt Warren. To jde do velkých podrobností o tom, jak přeložit některý z kódu, který můžete najít ve stromu výrazů.

Doufám, že jste teď viděli skutečnou sílu výrazových stromů.
Můžete zkontrolovat sadu kódu, provést změny, které chcete k tomuto kódu, a spustit změněnou verzi. Vzhledem k tomu, že stromy výrazů jsou neměnné, můžete vytvořit nové stromy pomocí součástí existujících stromů. Tím se minimalizuje množství paměti potřebné k vytvoření změněných stromů výrazů.

[Další - Shrnutí](expression-trees-summary.md)
