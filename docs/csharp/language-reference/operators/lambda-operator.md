---
title: = > – odkaz C# na operátora
ms.custom: seodec18
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: 3b3a5c2e96e92271da66cbd8f1039a9ec97544fa
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971223"
---
# <a name="-operator-c-reference"></a>= > – operátorC# (Referenční dokumentace)

`=>` Token je podporován ve dvou formách: jako operátor lambda a jako oddělovač názvu člena a implementace člena v definici těla výrazu.

## <a name="lambda-operator"></a>Lambda – operátor

Ve [výrazech lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md)operátor `=>` lambda odděluje vstupní proměnné na levé straně od těla lambda na pravé straně.

Následující příklad používá funkci [LINQ](../../programming-guide/concepts/linq/index.md) s syntaxí Method k předvedení použití výrazů lambda:

[!code-csharp-interactive[infer types of input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#InferredTypes)]

Vstupní proměnné výrazů lambda jsou silného typu v době kompilace. Když kompilátor může odvodit typy vstupních proměnných, jako v předchozím příkladu, můžete vynechat deklarace typu. Pokud potřebujete zadat typ vstupních proměnných, je nutné provést tento postup pro každou proměnnou, jak ukazuje následující příklad:

[!code-csharp-interactive[specify types of input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#ExplicitTypes)]

Následující příklad ukazuje, jak definovat výraz lambda bez vstupních proměnných:

[!code-csharp-interactive[without input variables](~/samples/csharp/language-reference/operators/LambdaOperator.cs#WithoutInput)]

Další informace naleznete v tématu [lambda výrazy](../../programming-guide/statements-expressions-operators/lambda-expressions.md).

## <a name="expression-body-definition"></a>Definice těla výrazu

Definice těla výrazu má následující obecnou syntaxi:

```csharp
member => expression;
```

kde `expression` je platný výraz. Návratový typ `expression` musí být implicitně převoditelný na návratový typ člena. Pokud je `void` návratový typ člena nebo je-li členem konstruktor, finalizační metoda nebo vlastnost `set` přistupující objekt, `expression` musí být [*výraz příkazu*](~/_csharplang/spec/statements.md#expression-statements), který může být libovolného typu.

Následující příklad ukazuje definici těla výrazu pro `Person.ToString` metodu:

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

Tato definice metody je zkráceným zněním:

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```

Definice textu výrazu pro metody a vlastnosti jen pro čtení jsou podporovány od C# 6. Definice textu výrazu pro konstruktory, finalizační metody, přistupující objekty vlastnosti a indexery jsou podporovány od C# 7,0.

Další informace naleznete v tématu [Expression-těle Members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).

## <a name="operator-overloadability"></a>Přetížení operátoru

`=>` Operátor nemůže být přetížený.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [výrazy anonymní funkce](~/_csharplang/spec/expressions.md#anonymous-function-expressions) [ C# specifikace jazyka](../language-specification/index.md).

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Operátory jazyka C#](index.md)
- [Výrazy lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md)
- [Členové tvoření výrazy](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)
