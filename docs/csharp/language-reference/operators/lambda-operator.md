---
title: => – operátor – Referenční dokumentace jazyka C#
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: 30e1a3546f83a0a1ba5b1363238878868e94ab93
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063130"
---
# <a name="-operator-c-reference"></a>=> – operátor (Referenční dokumentace jazyka C#)

`=>`Token je podporován ve dvou formách: jako [operátor lambda](#lambda-operator) a jako oddělovač názvu člena a implementace člena v [definici těla výrazu](#expression-body-definition).

## <a name="lambda-operator"></a>Lambda – operátor

Ve [výrazech lambda](lambda-expressions.md)operátor lambda `=>` odděluje vstupní parametry na levé straně těla výrazu lambda na pravé straně.

Následující příklad používá funkci [LINQ](../../programming-guide/concepts/linq/index.md) s syntaxí Method k předvedení použití výrazů lambda:

[!code-csharp-interactive[infer types of input variables](snippets/shared/LambdaOperator.cs#InferredTypes)]

Vstupní parametry výrazu lambda jsou silného typu v době kompilace. Pokud kompilátor může odvodit typy vstupních parametrů, jako v předchozím příkladu, můžete vynechat deklarace typu. Pokud potřebujete zadat typ vstupních parametrů, je nutné provést tento postup pro každý parametr, jak ukazuje následující příklad:

[!code-csharp-interactive[specify types of input variables](snippets/shared/LambdaOperator.cs#ExplicitTypes)]

Následující příklad ukazuje, jak definovat výraz lambda bez vstupních parametrů:

[!code-csharp-interactive[without input variables](snippets/shared/LambdaOperator.cs#WithoutInput)]

Další informace naleznete v tématu [lambda výrazy](lambda-expressions.md).

## <a name="expression-body-definition"></a>Definice těla výrazu

Definice těla výrazu má následující obecnou syntaxi:

```csharp
member => expression;
```

kde `expression` je platný výraz. Návratový typ `expression` musí být implicitně převoditelný na návratový typ člena. Pokud je návratový typ člena nebo je `void` -li členem konstruktor, finalizační metoda nebo vlastnost nebo `set` přistupující objekt indexeru, `expression` musí být [*výraz příkazu*](~/_csharplang/spec/statements.md#expression-statements). Vzhledem k tomu, že výsledek výrazu je zahozen, návratový typ tohoto výrazu může být libovolný typ.

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

Definice textu výrazu pro metody, operátory a vlastnosti jen pro čtení jsou podporovány od verze C# 6. Definice textu výrazu pro konstruktory, finalizační metody a vlastnosti a přistupující objekty indexeru jsou podporované od jazyka C# 7,0.

Další informace naleznete v tématu [Expression-těle Members](../../programming-guide/statements-expressions-operators/expression-bodied-members.md).

## <a name="operator-overloadability"></a>Přetížení operátoru

`=>`Operátor nemůže být přetížený.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace o operátoru lambda naleznete v části [výrazy anonymní funkce](~/_csharplang/spec/expressions.md#anonymous-function-expressions) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory a výrazy v C#](index.md)
