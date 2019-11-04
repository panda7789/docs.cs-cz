---
title: klíčové slovo Public C# – reference
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: dfb6e341ea0740225d7600f07af2813d39141b45
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422560"
---
# <a name="public-c-reference"></a>public (Referenční dokumentace jazyka C#)

Klíčové slovo `public` je modifikátor přístupu pro typy a členy typů. Veřejný přístup je nejpřísnější úroveň přístupu. Pro přístup k veřejným členům neexistují žádná omezení, jako v tomto příkladu:

```csharp
class SampleClass
{
    public int x; // No access restrictions.
}
```

Další informace najdete v tématu [modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md) a [úrovně přístupnosti](accessibility-levels.md) .

## <a name="example"></a>Příklad

V následujícím příkladu jsou deklarovány dvě třídy, `PointTest` a `MainClass`. Veřejné členy `x` a `y` `PointTest` jsou přístupné přímo ze `MainClass`.

[!code-csharp[csrefKeywordsModifiers#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#13)]

Pokud změníte úroveň přístupu `public` na [soukromou](private.md) nebo [chráněnou](protected.md), zobrazí se chybová zpráva:

' PointTest. y ' je z důvodu úrovně ochrany nedostupné.

## <a name="c-language-specification"></a>specifikace jazyka C#  

Další informace najdete v tématu [deklarované přístupnosti](~/_csharplang/spec/basic-concepts.md#declared-accessibility) ve [ C# specifikaci jazyka](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md)
- [Klíčová slova jazyka C#](index.md)
- [Modifikátory přístupu](access-modifiers.md)
- [Úrovně přístupnosti](accessibility-levels.md)
- [Modifikátory](index.md)
- [private](private.md)
- [protected](protected.md)
- [internal](internal.md)
