---
title: Typy architektur podporující stromy výrazů
description: Seznamte se s typy architektury, které podporují stromy výrazů, vytváření stromů výrazů a techniky pro práci s rozhraními API stromu výrazů.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: e9c85021-0d36-48af-91b7-aaaa66f22654
ms.openlocfilehash: 157e97594f27345ac96fe91f7dd6f29907c2c7ac
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73037622"
---
# <a name="framework-types-supporting-expression-trees"></a>Typy architektur podporující stromy výrazů

[Vysvětlení stromů předchozí--výraz](expression-trees-explained.md)

V rozhraní .NET Core Framework je rozsáhlý seznam tříd, které pracují se stromy výrazů.
Úplný seznam najdete na stránce <xref:System.Linq.Expressions>.
Místo toho, aby procházely prostřednictvím úplného seznamu, porozuměli tomu, jak byly navrženy třídy rozhraní.

V návrhu jazyka je výraz tělo kódu, který vyhodnocuje a vrací hodnotu. Výrazy můžou být velmi jednoduché: konstantní výraz `1` vrací konstantní hodnotu 1. Můžou být složitější: výraz `(-B + Math.Sqrt(B*B - 4 * A * C)) / (2 * A)` vrátí jeden kořen pro kvadratickou rovnici (v případě, kdy rovnice obsahuje řešení).  

## <a name="it-all-starts-with-systemlinqexpression"></a>Vše začíná řetězcem System. Linq. Expression.

Jednou ze složitých prací se stromy výrazů je, že mnoho různých druhů výrazů je platných na mnoha místech v programech. Vezměte v úvahu výraz přiřazení. Pravá strana přiřazení může být konstantní hodnota, proměnná, výraz volání metody nebo jiné. Tato flexibilita jazyka znamená, že se můžete setkat s mnoha různými typy výrazů kdekoli v uzlech stromu při procházení stromu výrazu. Proto když můžete pracovat s typem základního výrazu, je to nejjednodušší způsob, jak pracovat. Někdy ale potřebujete znát ještě více.
Třída Base Expression obsahuje vlastnost `NodeType` pro tento účel.
Vrátí `ExpressionType`, který je výčtem možných typů výrazů.
Jakmile znáte typ uzlu, můžete ho přetypovat na tento typ a provádět konkrétní akce, které budou znát typ uzlu výrazu. Můžete hledat určité typy uzlů a pak pracovat s konkrétními vlastnostmi tohoto typu výrazu.

Například tento kód vytiskne název proměnné pro výraz přístupu proměnné. Použil jsem postup kontroly typu uzlu, následné přetypování do výrazu přístupu k proměnné a následné kontrole vlastností konkrétního typu výrazu:

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

Třída `System.Linq.Expression` také obsahuje mnoho statických metod pro vytváření výrazů. Tyto metody vytvoří uzel výrazu pomocí argumentů dodaných pro své podřízené položky. Tímto způsobem sestavíte výraz z jeho listových uzlů. Například tento kód vytvoří výraz Add:

```csharp
// Addition is an add expression for "1 + 2"
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
```

Můžete si prohlédnout z tohoto jednoduchého příkladu, který je součástí vytváření a práce se stromy výrazů. Tato složitá složitost je nutná k zajištění schopností bohatých slovníků poskytovaných C# jazykem.

## <a name="navigating-the-apis"></a>Navigace v rozhraních API
Existují typy uzlů výrazů, které jsou namapovány na skoro všechny prvky syntaxe C# jazyka. Každý typ má konkrétní metody pro tento typ elementu jazyka. Je to hodně, co je potřeba v hlavě uchovávat najednou. Místo toho, abyste se pokusili nepamatují vše, jsou zde postupy, které mám použít pro práci s stromy výrazů:

1. Podívejte se na členy výčtu `ExpressionType` a určete možné uzly, které byste měli prošetřit. To skutečně pomáhá při procházení a pochopení stromu výrazů.
2. Pokud chcete vytvořit výraz, podívejte se na statické členy třídy `Expression`. Tyto metody mohou sestavit libovolný typ výrazu ze sady svých podřízených uzlů.
3. Podívejte se na třídu `ExpressionVisitor` a vytvořte upravený strom výrazů.

Další informace najdete v každé z těchto tří oblastí. Invariably zjistíte, co potřebujete, když začnete s jedním z těchto tří kroků.
 
 [Další – spouštění stromů výrazů](expression-trees-execution.md)
