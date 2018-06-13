---
title: Framework typy podpůrné stromů výrazů
description: Informace o typech framework podpora stromů výrazů vytváření stromů výrazů a postupy pro práci se strom výrazu rozhraní API.
ms.date: 06/20/2016
ms.assetid: e9c85021-0d36-48af-91b7-aaaa66f22654
ms.openlocfilehash: 3110f2a9534085aba95fcb5c8e76f66229e79f86
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33214942"
---
# <a name="framework-types-supporting-expression-trees"></a>Framework typy podpůrné stromů výrazů

[Předchozí – Vysvětlení stromů výrazů](expression-trees-explained.md)

Existuje velký seznam tříd v rozhraní .NET Core, které pracují s stromů výrazů.
Zobrazí úplný seznam [zde](/dotnet/core/api/System.Linq.Expressions).
Místo spuštění prostřednictvím úplný seznam, probereme, jak byly navrženy třídy rozhraní framework.

V návrhu jazyka je výraz text kódu, který se vyhodnotí a vrátí hodnotu. Může být velmi jednoduché výrazy: konstantní výraz `1` vrátí na konstantní hodnotu 1. Mohou být složitější: výraz `(-B + Math.Sqrt(B*B + 4 * A * C)) / (2 * A)` vrátí jeden kořenový pro Kvadratická rovnice (v případě, kde má rovnice řešení).  

## <a name="it-all-starts-with-systemlinqexpression"></a>Všechny začíná System.Linq.Expression

Jedním z složitosti práce stromů výrazů je, že různé druhy výrazů jsou platné na mnoha místech programy. Vezměte v úvahu výraz přiřazení. Pravé straně přiřazení může být konstantní hodnota, proměnné, výraz volání metody nebo jiné. Tento jazyk flexibilitě mnoho typů jiný výraz kdekoli v uzlu stromu může dojít, když procházejí strom výrazu se nezdařilo. Proto když můžete pracovat s typem základní výraz, který je nejjednodušší způsob, jak pracovat. Ale někdy potřebujete další informace.
Obsahuje základní třídy výraz `NodeType` vlastnost pro tento účel.
Vrátí `ExpressionType` tedy výčet typů možné výraz.
Jakmile znáte typ uzlu, můžete ho převést na tento typ a provedení určitých akcí s jistotou typ uzlu výrazu. Můžete vyhledat určité typy uzlů a pak pracovat s konkrétní vlastnosti tohoto typu výrazu.

Tento kód bude například vytisknout název proměnné pro výraz proměnné přístup. Jste postupovali podle postup kontrolou typu uzlu, pak přetypování výrazu proměnné přístup a pak zkontroluje vlastnosti konkrétní výraz typu:

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

`System.Linq.Expression` Třída také obsahuje mnoho statické metody pro vytváření výrazů. Tyto metody vytvoření do uzlu výraz pomocí zadané argumenty pro své podřízené objekty. Tímto způsobem můžete vytvořit výraz z jeho uzlů listu. Např. Tento kód vytvoří výraz přidat:

```csharp
// Addition is an add expression for "1 + 2"
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
```

Je vidět na tomto jednoduchém příkladu mnoho typů jsou součástí vytváření a práci s stromů výrazů. Aby složitost je potřeba zadat možnosti bohaté termínů poskytované jazyka C#.

## <a name="navigating-the-apis"></a>Navigace rozhraní API
Existují uzlu typy výrazů, které jsou mapovány na téměř všechny prvky syntaxe jazyka C#. Každý typ má konkrétní metody pro tento typ elementu jazyk. Je mnoho zajišťující ve vaší head najednou. Místo pokusí pamatovat vše, zde jsou technik, které používám k práci s stromů výrazů:
1. Podívejte se na členy `ExpressionType` výčtu k určení možných uzlů by měl zkoumání. To opravdu pomáhá při chcete procházení a porozumění strom výrazu se nezdařilo.
2. Podívejte se na statické členy `Expression` třída výraz. Tyto metody můžete vytvořit libovolný typ výrazu ze sady jeho podřízené uzly.
3. Podívejte se na `ExpressionVisitor` třída Sestavit strom upravené výrazu.

Najdete tu informace, jako je podívejte se na každý z těchto tří oblastí. Vždy zjistíte, co potřebujete, když začínáte s jedním z těchto tří kroků.
 
 [Další – Provádění stromů výrazů](expression-trees-execution.md)
 
