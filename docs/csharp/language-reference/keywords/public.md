---
description: Public – klíčové slovo – Referenční dokumentace jazyka C#
title: Public – klíčové slovo – Referenční dokumentace jazyka C#
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: 26edaf7538d11d082a4b8863228213c3ebc46937
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89122339"
---
# <a name="public-c-reference"></a>public (Referenční dokumentace jazyka C#)

`public`Klíčové slovo je modifikátor přístupu pro typy a členy typů. Veřejný přístup je nejpřísnější úroveň přístupu. Pro přístup k veřejným členům neexistují žádná omezení, jako v tomto příkladu:

```csharp
class SampleClass
{
    public int x; // No access restrictions.
}
```

Další informace najdete v tématu [modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md) a [úrovně přístupnosti](accessibility-levels.md) .

## <a name="example"></a>Příklad

V následujícím příkladu jsou deklarovány dvě třídy, `PointTest` a `MainClass` . Veřejné členy `x` a `y` `PointTest` jsou přístupné přímo z `MainClass` .

[!code-csharp[csrefKeywordsModifiers#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#13)]

Pokud změníte `public` úroveň přístupu na [soukromou](private.md) nebo [chráněnou](protected.md), zobrazí se chybová zpráva:

' PointTest. y ' je z důvodu úrovně ochrany nedostupné.

## <a name="c-language-specification"></a>specifikace jazyka C#  

Další informace najdete v tématu [deklarovaná přístupnost](~/_csharplang/spec/basic-concepts.md#declared-accessibility) ve [specifikaci jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md)
- [Klíčová slova jazyka C#](index.md)
- [Modifikátory přístupu](access-modifiers.md)
- [Úrovně přístupnosti](accessibility-levels.md)
- [Modifikátory](index.md)
- [private](private.md)
- [protected](protected.md)
- [internal](internal.md)
