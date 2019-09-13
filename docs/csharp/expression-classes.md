---
title: Typy architektur podporující stromy výrazů
description: Seznamte se s typy architektury, které podporují stromy výrazů, vytváření stromů výrazů a techniky pro práci s rozhraními API stromu výrazů.
ms.date: 06/20/2016
ms.assetid: e9c85021-0d36-48af-91b7-aaaa66f22654
ms.openlocfilehash: d11a13000019faf2ab5c35d41d48fa199e901d1c
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70925973"
---
# <a name="framework-types-supporting-expression-trees"></a>Typy architektur podporující stromy výrazů

[Vysvětlení stromů předchozí--výraz](expression-trees-explained.md)

V rozhraní .NET Core Framework je rozsáhlý seznam tříd, které pracují se stromy výrazů.
Úplný seznam najdete na adrese <xref:System.Linq.Expressions>.
Místo toho, aby procházely prostřednictvím úplného seznamu, porozuměli tomu, jak byly navrženy třídy rozhraní.

V návrhu jazyka je výraz tělo kódu, který vyhodnocuje a vrací hodnotu. Výrazy můžou být velmi jednoduché: konstantní výraz `1` vrací konstantní hodnotu 1. Můžou být složitější: Výraz `(-B + Math.Sqrt(B*B - 4 * A * C)) / (2 * A)` vrátí jeden kořen pro kvadratickou rovnici (v případě, kdy má rovnice řešení).  

## <a name="it-all-starts-with-systemlinqexpression"></a>Vše začíná řetězcem System. Linq. Expression.

Jednou ze složitých prací se stromy výrazů je, že mnoho různých druhů výrazů je platných na mnoha místech v programech. Vezměte v úvahu výraz přiřazení. Pravá strana přiřazení může být konstantní hodnota, proměnná, výraz volání metody nebo jiné. Tato flexibilita jazyka znamená, že se můžete setkat s mnoha různými typy výrazů kdekoli v uzlech stromu při procházení stromu výrazu. Proto když můžete pracovat s typem základního výrazu, je to nejjednodušší způsob, jak pracovat. Někdy ale potřebujete znát ještě více.
Třída základního výrazu obsahuje `NodeType` vlastnost pro tento účel.
Vrátí hodnotu `ExpressionType` , která je výčtem možných typů výrazů.
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

`System.Linq.Expression` Třída také obsahuje mnoho statických metod pro vytváření výrazů. Tyto metody vytvoří uzel výrazu pomocí argumentů dodaných pro své podřízené položky. Tímto způsobem sestavíte výraz z jeho listových uzlů. Například tento kód vytvoří výraz Add:

```csharp
// Addition is an add expression for "1 + 2"
var one = Expression.Constant(1, typeof(int));
var two = Expression.Constant(2, typeof(int));
var addition = Expression.Add(one, two);
```

Můžete si prohlédnout z tohoto jednoduchého příkladu, který je součástí vytváření a práce se stromy výrazů. Tato složitá složitost je nutná k zajištění schopností bohatých slovníků poskytovaných C# jazykem.

## <a name="navigating-the-apis"></a>Navigace v rozhraních API
Existují typy uzlů výrazů, které jsou namapovány na skoro všechny prvky syntaxe C# jazyka. Každý typ má konkrétní metody pro tento typ elementu jazyka. Je to hodně, co je potřeba v hlavě uchovávat najednou. Místo toho, abyste se pokusili nepamatují vše, jsou zde postupy, které mám použít pro práci s stromy výrazů:

1. Podívejte se na členy `ExpressionType` výčtu a určete možné uzly, které byste měli prošetřit. To skutečně pomáhá při procházení a pochopení stromu výrazů.
2. Pokud chcete vytvořit výraz, podívejte se `Expression` na statické členy třídy. Tyto metody mohou sestavit libovolný typ výrazu ze sady svých podřízených uzlů.
3. Podívejte se `ExpressionVisitor` na třídu a sestavte upravený strom výrazů.

Další informace najdete v každé z těchto tří oblastí. Invariably zjistíte, co potřebujete, když začnete s jedním z těchto tří kroků.
 
 [Další – spouštění stromů výrazů](expression-trees-execution.md)
