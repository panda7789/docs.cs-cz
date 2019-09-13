---
title: Překládání stromů výrazů
description: Naučte se navštívit jednotlivé uzly ve stromové struktuře výrazů a přitom sestavovat upravenou kopii tohoto stromu výrazů.
ms.date: 06/20/2016
ms.assetid: b453c591-acc6-4e08-8175-97e5bc65958e
ms.openlocfilehash: a12c4d7fe9f65d6e9598259de1504b6f9987f38e
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70925844"
---
# <a name="translating-expression-trees"></a>Překládání stromů výrazů

[Předchozí výrazy sestavení](expression-trees-building.md)

V této poslední části se dozvíte, jak při sestavování upravené kopie stromu výrazu navštívit jednotlivé uzly ve stromové struktuře výrazů. Jedná se o techniky, které použijete ve dvou důležitých scénářích. První je pochopit algoritmy vyjádřené stromem výrazu, aby bylo možné je přeložit do jiného prostředí. Druhá je, když chcete změnit algoritmus, který byl vytvořen. To může být přidání protokolování, zachytávání volání metod a jejich sledování nebo jiné účely.

## <a name="translating-is-visiting"></a>Probíhá překládání.

Kód, který sestavíte k překladu stromu výrazů, je rozšířením toho, co jste už viděli pro návštěvě všech uzlů ve stromu. Při převodu stromu výrazu navštívíte všechny uzly a při jejich návštěvě sestavíte nový strom. Nový strom může obsahovat odkazy na původní uzly nebo nové uzly, které jste umístili do stromu.

Pojďme to vidět v akci návštěvou stromu výrazů a vytvořením nového stromu s některými náhradními uzly. V tomto příkladu nahradíme všechny konstanty konstantou, která je desetkrát větší.
V opačném případě ponecháme strom výrazu beze změny. Místo přečtení hodnoty konstanty a její nahrazení novou konstantou provedeme tuto náhradu nahrazením konstantního uzlu novým uzlem, který provede násobení.

Zde můžete po nalezení konstantního uzlu vytvořit nový uzel násobení, jehož podřízené položky jsou původní konstantou, a konstanta `10`:

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

Nahrazením původního uzlu nahraďte nový strom, který obsahuje naše úpravy. Můžeme ověřit, že kompilování a provádění nahrazeného stromu.

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

Sestavování nového stromu je kombinace návštěvy uzlů v existujícím stromu a vytvoření nových uzlů a jejich vložení do stromu.

Tento příklad ukazuje důležitost stromů výrazů, které jsou neměnné. Všimněte si, že nový strom vytvořený výše obsahuje kombinaci nově vytvořených uzlů a uzlů z existujícího stromu. To je bezpečné, protože uzly ve stávajícím stromu nelze upravovat. To může mít za následek výrazné zvýšení efektivity paměti.
Stejné uzly lze použít v celém stromu nebo v několika stromech výrazů. Vzhledem k tomu, že uzly nelze upravovat, lze stejný uzel znovu použít vždy, když je to potřeba.

## <a name="traversing-and-executing-an-addition"></a>Procházení a provádění přidání

Pojďme to ověřit vytvořením druhého návštěvníka, který projde stromem přidaných uzlů a vypočítá výsledek. Můžete to udělat tak, že provedete několik úprav návštěvníka, který jste doposud viděli. V této nové verzi návštěvník vrátí částečný součet operace sčítání do tohoto bodu. Pro konstantní výraz, který je jednoduše hodnotou konstantního výrazu. Pro výraz sčítání je výsledkem součet levého a pravého operandu, jakmile byly tyto stromy přecházet.

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

Tady je trochu kód, ale koncepty jsou velmi dostupné.
Tento kód po prvním hledání navštíví podřízené objekty. Když narazí na konstantní uzel, návštěvník vrátí hodnotu konstanty. Po navštívení návštěvníka budou tyto podřízené položky vypočítány součtem vypočítaným pro tento dílčí strom. Uzel sčítání teď může vypočítat jeho součet.
Po navštívení všech uzlů ve stromu výrazů bude součet vypočítán. Spuštění můžete trasovat spuštěním ukázky v ladicím programu a trasováním provádění.

Podívejme se, jak sledovat, jak se uzly analyzují, a jak se součet vypočítává pomocí procházení stromu. Zde je aktualizovaná verze agregované metody, která obsahuje poměrně bitovou část trasovacích informací:

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

Spuštění na stejném výrazu vrací následující výstup:

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

Sledujte výstup a sledujte v kódu výše. Měli byste být schopni pracovat s tím, jak kód navštíví každý uzel, a vypočítat součet při jeho průchodu stromovou strukturou a vyhledá součet.

Nyní se podívejme na jiný běh s výrazem zadaným `sum1`:

```csharp
Expression<Func<int> sum1 = () => 1 + (2 + (3 + 4));
```

Zde je výstup prozkoumání tohoto výrazu:

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

I když je konečná odpověď stejná, je procházení stromové struktury zcela jiné. Uzly se cestují v jiném pořadí, protože strom byl vytvořen s různými operacemi, které nastaly jako první.

## <a name="learning-more"></a>Učení více

Tato ukázka ukazuje malou podmnožinu kódu, který byste vytvořili pro procházení a interpretaci algoritmů, které jsou zastoupeny stromem výrazů. Kompletní diskuzi o všech potřebách potřebných k sestavení knihovny pro obecné účely, která překládá stromy výrazů do jiného jazyka, si prosím přečtěte v [této řadě](https://blogs.msdn.microsoft.com/mattwar/2008/11/18/linq-building-an-iqueryable-provider-series/) podkladem Warren. To je velmi podrobné informace o tom, jak přeložit libovolný kód, který můžete najít ve stromu výrazu.

Doufám, že teď jste viděli skutečnou sílu stromů výrazů.
Můžete zkontrolovat sadu kódu, provést všechny změny, které byste chtěli v kódu, a provést změněnou verzi. Vzhledem k tomu, že stromy výrazů jsou neměnné, můžete vytvořit nové stromy pomocí komponent existujících stromů. Tím se minimalizuje množství paměti potřebné k vytvoření upravených stromů výrazů.

[Další – součet](expression-trees-summary.md)
