---
title: = operátor> - odkaz Jazyka C#
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: 15c02e11610866f359e3e3a7e2751ded918154b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846246"
---
# <a name="-operator-c-reference"></a>= operátor> (odkaz C#)

Token `=>` je podporován ve dvou formách: jako [operátor lambda](#lambda-operator) a jako oddělovač názvu člena a implementace člena v [definici těla výrazu](#expression-body-definition).

## <a name="lambda-operator"></a>Lambda operátor

V [lambda výrazy](../../programming-guide/statements-expressions-operators/lambda-expressions.md), lambda operátor `=>` odděluje vstupní parametry na levé straně od lambda těla na pravé straně.

Následující příklad používá funkci [LINQ](../../programming-guide/concepts/linq/index.md) se syntaxí metody k předvedení použití výrazů lambda:

[!code-csharp-interactive[infer types of input variables](snippets/LambdaOperator.cs#InferredTypes)]

Vstupní parametry výrazu lambda jsou silně zadány v době kompilace. Když kompilátor můžete odvodit typy vstupních parametrů, jako v předchozím příkladu, můžete vynechat deklarace typu. Pokud potřebujete zadat typ vstupních parametrů, musíte to udělat pro každý parametr, jak ukazuje následující příklad:

[!code-csharp-interactive[specify types of input variables](snippets/LambdaOperator.cs#ExplicitTypes)]

Následující příklad ukazuje, jak definovat výraz lambda bez vstupních parametrů:

[!code-csharp-interactive[without input variables](snippets/LambdaOperator.cs#WithoutInput)]

Další informace naleznete v tématu [Lambda výrazy](../../programming-guide/statements-expressions-operators/lambda-expressions.md).

## <a name="expression-body-definition"></a>Definice těla výrazu

Definice těla výrazu má následující obecnou syntaxi:

```csharp
member => expression;
```

kde `expression` je platný výraz. Návratový typ `expression` musí být implicitně převoditelný na návratový typ člena. Pokud je návratový typ `void` člena nebo pokud je člen konstruktorem, `set` finalizační `expression` metoda nebo přistupující objekt vlastnosti musí být [*výraz emisi ,*](~/_csharplang/spec/statements.md#expression-statements)který může být libovolného typu.

Následující příklad ukazuje definici těla výrazu pro metodu: `Person.ToString`

```csharp
public override string ToString() => $"{fname} {lname}".Trim();
```

Jedná se o zkrácenou verzi následující definice metody:

```csharp
public override string ToString()
{
   return $"{fname} {lname}".Trim();
}
```

Definice těla výrazu pro metody, operátory a vlastnosti jen pro čtení jsou podporovány počínaje C# 6. Definice těla výrazu pro konstruktory, finalizační metody a přístupové objekty vlastností a indexeru jsou podporovány počínaje C# 7.0.

Další informace naleznete v [tématu Expression-tělesně členy](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).

## <a name="operator-overloadability"></a>Přetížení obsluhy

Operátor `=>` nemůže být přetížen.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace o operátoru lambda naleznete v části [Anonymní výrazy funkcí](~/_csharplang/spec/expressions.md#anonymous-function-expressions) [ve specifikaci jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory jazyka C#](index.md)
