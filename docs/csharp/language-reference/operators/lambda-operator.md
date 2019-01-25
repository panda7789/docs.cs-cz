---
title: =&gt; Operator - C# odkaz
ms.custom: seodec18
ms.date: 01/22/2019
f1_keywords:
- =>_CSharpKeyword
helpviewer_keywords:
- lambda operator [C#]
- => operator [C#]
- lambda expressions [C#], => operator
ms.openlocfilehash: fa2e149f5b19e80e3171d08519be3ae249d2a112
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540803"
---
# <a name="gt-operator-c-reference"></a>=&gt; – Operátor (referenční dokumentace jazyka C#)

`=>` Token je podporován ve dvou formách: jako operátor lambda a jako oddělovač názvu členu a implementace členu v definici tělo výrazu.

## <a name="lambda-operator"></a>Lambda – operátor

V [výrazy lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md), operátor lambda `=>` odděluje vstupních proměnných na levé straně od hlavní část výrazu lambda na pravé straně.

V následujícím příkladu [LINQ](../../programming-guide/concepts/linq/index.md) funkce pomocí syntaxe metody k předvedení použití lambda výrazů:

[!code-csharp-interactive[infer types of input variables](~/samples/snippets/csharp/language-reference/operators/LambdaOperatorExamples.cs#InferredTypes)]

Vstupních proměnných, výrazů lambda jsou silného typu v době kompilace. Když kompilátor může odvodit typ vstupních proměnných, stejně jako v předchozím příkladu, můžete vynechat deklarace typů. Pokud je třeba zadat typ vstupních proměnných, je nutné použít pro každou proměnnou, jako v následujícím příkladu:

[!code-csharp-interactive[specify types of input variables](~/samples/snippets/csharp/language-reference/operators/LambdaOperatorExamples.cs#ExplicitTypes)]

Následující příklad ukazuje, jak definovat výraz lambda bez vstupních proměnných:

[!code-csharp-interactive[without input variables](~/samples/snippets/csharp/language-reference/operators/LambdaOperatorExamples.cs#WithoutInput)]

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

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
- [Výrazy lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md)
- [Členové tvoření výrazy](../../programming-guide/statements-expressions-operators/expression-bodied-members.md)