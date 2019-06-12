---
title: = > – operátor - C# odkaz
ms.custom: seodec18
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: a7fea9810cb02269278638ec71cd106463b029e9
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025025"
---
# <a name="-operator-c-reference"></a>= > – operátor (C# odkaz)

`=>` Token je podporován ve dvou formách: jako operátor lambda a jako oddělovač názvu členu a implementace členu v definici tělo výrazu.

## <a name="lambda-operator"></a>Lambda – operátor

V [výrazy lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md), operátor lambda `=>` odděluje vstupních proměnných na levé straně od hlavní část výrazu lambda na pravé straně.

V následujícím příkladu [LINQ](../../programming-guide/concepts/linq/index.md) funkce pomocí syntaxe metody k předvedení použití lambda výrazů:

[!code-csharp-interactive[infer types of input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#InferredTypes)]

Vstupních proměnných, výrazů lambda jsou silného typu v době kompilace. Když kompilátor může odvodit typ vstupních proměnných, stejně jako v předchozím příkladu, můžete vynechat deklarace typů. Pokud je třeba zadat typ vstupních proměnných, je nutné použít pro každou proměnnou, jako v následujícím příkladu:

[!code-csharp-interactive[specify types of input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#ExplicitTypes)]

Následující příklad ukazuje, jak definovat výraz lambda bez vstupních proměnných:

[!code-csharp-interactive[without input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#WithoutInput)]

Další informace najdete v tématu [výrazy Lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md).

## <a name="expression-body-definition"></a>Definice textu výrazu

Definice těla výrazu má následující obecnou syntaxi:

```csharp
member => expression;
```

kde *výraz* je platný výraz. Všimněte si, že *výraz* může být *výrazu příkazu* pouze pokud je člen návratový typ je `void`, nebo pokud je člen konstruktoru, finalizační metodu nebo vlastnost `set` přistupujícího objektu.

Následující příklad ukazuje definici tělo výrazu pro `Person.ToString` metody:

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

Definice těla výrazu pro metody a vlastnosti jen pro čtení jsou podporovány od verze C# 6. Definice těla výrazu pro konstruktory, finalizační metody, přistupující objekty vlastnosti a indexery jsou podporovány od verze C# 7.0.

Další informace najdete v tématu [členové tvoření](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).

## <a name="operator-overloadability"></a>Overloadability – operátor

`=>` Operátor nelze přetížit.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [výrazy anonymní funkce](~/_csharplang/spec/expressions.md#anonymous-function-expressions) část [ C# specifikace jazyka](../language-specification/index.md).

## <a name="see-also"></a>Viz také:

- [C#referenční dokumentace](../index.md)
- [Operátory jazyka C#](index.md)
- [Výrazy lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md)
- [Členové tvoření výrazy](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)
