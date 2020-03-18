---
title: Typy architektur podporující stromy výrazů
description: Další informace o typech architektury podporujících stromy výrazů, vytváření stromů výrazů a technikách pro práci s rozhraními API stromu výrazů.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: e9c85021-0d36-48af-91b7-aaaa66f22654
ms.openlocfilehash: 8483c46dde3ea97138e55ab84a5924a3d2578730
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146083"
---
# <a name="framework-types-supporting-expression-trees"></a>Typy architektur podporující stromy výrazů

[Předchozí -- Vysvětlení stromů výrazů](expression-trees-explained.md)

Existuje velký seznam tříd v rozhraní .NET Core framework, které pracují se stromy výrazů.
Celý seznam naleznete na <xref:System.Linq.Expressions>adrese .
Spíše než spustit úplný seznam, pojďme pochopit, jak byly navrženy framework třídy.

V návrhu jazyka výraz je tělo kódu, který vyhodnocuje a vrací hodnotu. Výrazy mohou být velmi jednoduché: konstantní výraz `1` vrátí konstantní hodnotu 1. Mohou být složitější: Výraz `(-B + Math.Sqrt(B*B - 4 * A * C)) / (2 * A)` vrátí jeden kořen pro kvadratickou rovnici (v případě, kdy rovnice má řešení).  

## <a name="it-all-starts-with-systemlinqexpression"></a>Vše začíná System.Linq.Expression

Jednou ze složitostí práce se stromy výrazů je, že mnoho různých druhů výrazů je platných na mnoha místech v programech. Zvažte výraz přiřazení. Pravá strana přiřazení může být konstantní hodnota, proměnná, výraz volání metody nebo jiné. Tato flexibilita jazyka znamená, že můžete setkat s mnoha různými typy výrazů kdekoli v uzlech stromu při procházení stromu výrazů. Proto při práci s typem základního výrazu, to je nejjednodušší způsob práce. Někdy však potřebujete vědět více.
Základní třída Expression `NodeType` obsahuje vlastnost pro tento účel.
Vrátí což `ExpressionType` je výčet možných typů výrazů.
Jakmile znáte typ uzlu, můžete jej přetypovat na tento typ a provést určité akce s vědomím typu uzlu výrazu. Můžete vyhledat určité typy uzlů a potom pracovat s konkrétními vlastnostmi tohoto druhu výrazu.

Tento kód například vytiskne název proměnné pro výraz přístupu proměnné. Sledoval jsem praxi kontroly typu uzlu, potom přetypování na výraz přístupu proměnné a následné kontrole vlastností konkrétního typu výrazu:

```csharp
Expression<Func<int, int>> addFive = (num) => num + 5;

if (addFive.NodeType == ExpressionType.Lambda)
{
    var lambdaExp = (LambdaExpression)addFive;

    var parameter = lambdaExp.Parameters.First();

    Console.WriteLine(parameter.Name);
    Console.WriteLine(parameter.Type);
}
```

## <a name="creating-expression-trees"></a>Vytváření stromů výrazů

Třída `System.Linq.Expression` také obsahuje mnoho statických metod pro vytvoření výrazů. Tyto metody vytvořit uzel výrazu pomocí argumentů zadaných pro jeho podřízené objekty. Tímto způsobem vytvoříte výraz z jeho listových uzlů. Například tento kód vytvoří výraz Add:

```csharp
// Addition is an add expression for "1 + 2"
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
```

Z tohoto jednoduchého příkladu můžete vidět, že mnoho typů se podílí na vytváření a práci se stromy výrazů. Tato složitost je nezbytné poskytnout možnosti bohaté slovní zásoby poskytované jazykem C#.

## <a name="navigating-the-apis"></a>Navigace v prostředí API
Existují typy uzlů výraz, které mapují téměř všechny prvky syntaxe jazyka C#. Každý typ má specifické metody pro tento typ prvku jazyka. Je toho hodně, co si najednou necháváš v hlavě. Spíše než se snažit zapamatovat všechno, zde jsou techniky, které používám pro práci se stromy výrazů:

1. Podívejte se na `ExpressionType` členy výčtu k určení možných uzlů, které byste měli zkoumat. To opravdu pomáhá, když chcete procházet a pochopit strom výrazů.
2. Podívejte se na statické `Expression` členy třídy k vytvoření výrazu. Tyto metody můžete vytvořit libovolný typ výrazu ze sady jeho podřízených uzlů.
3. Podívejte se `ExpressionVisitor` na třídu k vytvoření stromu upraveného výrazu.

Najdete více, jak se podíváte na každou z těchto tří oblastí. Vždy najdete to, co potřebujete, když začnete s jedním z těchto tří kroků.

 [Další -- Provádění stromů výrazů](expression-trees-execution.md)
