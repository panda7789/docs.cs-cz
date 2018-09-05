---
title: Typy architektur podporující stromy výrazů
description: Další informace o rozhraní framework typy podporující stromy výrazů, vytváření stromů výrazů a techniky pro práci s strom výrazu rozhraní API.
ms.date: 06/20/2016
ms.assetid: e9c85021-0d36-48af-91b7-aaaa66f22654
ms.openlocfilehash: 687b521c52c1ca380a12e18469b5f66000049d3c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43735329"
---
# <a name="framework-types-supporting-expression-trees"></a>Typy architektur podporující stromy výrazů

[Předchozí – Vysvětlení stromů výrazů](expression-trees-explained.md)

Existuje dlouhý seznam tříd v rozhraní .NET Core, které pracují s stromy výrazů.
Podívejte se na seznam v <xref:System.Linq.Expressions>.
Nespouštějte ho pomocí úplného seznamu, nyní se pokusíme pochopit, jak byly navrženy tříd rozhraní framework.

V návrhu jazyka je výraz tělo kód, který se vyhodnotí a vrátí hodnotu. Výrazy mohou být velmi jednoduchý: konstantní výraz `1` vrací konstantní hodnotu 1. Mohou být složitější: výraz `(-B + Math.Sqrt(B*B - 4 * A * C)) / (2 * A)` vrátí jeden kořenový adresář pro kvadratické rovnice (v případě, kdy má rovnice řešení).  

## <a name="it-all-starts-with-systemlinqexpression"></a>Všechno začíná System.Linq.Expression

Jedním ze složitých úkolů při práci s stromů výrazů je, že jsou různé druhy výrazů platný na mnoha místech v aplikacích. Vezměte v úvahu výraz přiřazení. Pravá strana přiřazení může být konstantní hodnotu, proměnné, výraz volání metody nebo jiné. Flexibilita z jazyka znamená, že mnoho typů jiný výraz kdekoli v uzly stromu mohou nastat, když procházejí strom výrazu. Proto můžete pracovat s typem základní výraz, který při nejjednodušší způsob, jak pracovat. Ale někdy potřebujete další informace.
Obsahuje základní třídy výraz `NodeType` vlastnost pro tento účel.
Vrátí `ExpressionType` což je výčet typy výrazů je to možné.
Jakmile budete znát typ uzlu, můžete přetypovat na daný typ a provádět konkrétní akce znalost typ uzlu výrazu. Můžete vyhledat určité typy uzlů a poté pracovat s určitými vlastnostmi tohoto typu výrazu.

Tento kód například vytiskne název proměnné pro přístup k proměnným výraz. Jste postupovali podle postupů kontrola typu uzlu, pak přetypování výrazu přístup k proměnným a následnou kontrolou vlastnosti typu určité výraz:

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

`System.Linq.Expression` Třída také obsahuje mnoho statické metody pro vytváření výrazů. Tyto metody vytvoří uzlu výraz pomocí zadané pro podřízené argumenty. Tímto způsobem můžete vytvořit výraz z jeho uzly typu list. Například tento kód vytvoří přidat výraz:

```csharp
// Addition is an add expression for "1 + 2"
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
```

Zobrazí se v tomto jednoduchém příkladu mnoho typů jsou součástí vytváření a práci s stromy výrazů. Složitost je potřeba zadat možnosti bohaté slovníku k dispozici v jazyce C#.

## <a name="navigating-the-apis"></a>Procházení rozhraní API
Existují výraz typy uzlů, které mapují na téměř všechny prvky syntaxe jazyka C#. Každý typ má specifické metody pro daný typ prvku jazyka. Je mnoho dalších zachovat v hlavě najednou. Namísto pokusu o všechno, co učit nazpaměť, tady jsou techniky využité pro práci s stromů výrazů:
1. Podívejte se na členy `ExpressionType` výčtu k určení možných uzly by měl zkoumání. To opravdu pomáhá při procházení a porozumění strom výrazu.
2. Podívejte se na statické členy třídy `Expression` třída výraz. Tyto metody můžete vytvořit jakýkoli typ výrazu ze sady jeho podřízené uzly.
3. Podívejte se na `ExpressionVisitor` třídy k sestavení stromu upravené výrazem.

Najdete tu informace, jako je podívejte se na každý z těchto tří oblastí. Vždy zjistíte, co potřebujete, když začínáte s jeden z těchto tří kroků.
 
 [Další – Provádění stromů výrazů](expression-trees-execution.md)
 
