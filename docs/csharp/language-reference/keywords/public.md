---
title: Public – klíčové slovo (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: 84a3bc49b6eea047d518edc01dab7f2301854b6a
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2018
ms.locfileid: "43256125"
---
# <a name="public-c-reference"></a>public (Referenční dokumentace jazyka C#)

`public` – Klíčové slovo je modifikátor přístupu pro typy a členy typu. Veřejný přístup je nejvíce omezující úroveň přístupu. Neexistují žádná omezení na přístup k veřejným členům, jako v následujícím příkladu:

```csharp
class SampleClass
{
    public int x; // No access restrictions.
}
```

Zobrazit [modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md) a [úrovní přístupu](accessibility-levels.md) Další informace.

## <a name="example"></a>Příklad

V následujícím příkladu se deklarovat dvě třídy, `PointTest` a `MainClass`. Veřejné členy `x` a `y` z `PointTest` přistupují přímo z `MainClass`.

[!code-csharp[csrefKeywordsModifiers#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#13)]

Pokud změníte `public` úroveň přístupu k [privátní](private.md) nebo [chráněné](protected.md), zobrazí se chybová zpráva:

"PointTest.y" je vzhledem k úrovni ochrany nepřístupný.

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md)
- [Klíčová slova jazyka C#](index.md)
- [Modifikátory přístupu](access-modifiers.md)
- [Úrovně přístupnosti](accessibility-levels.md)
- [Modifikátory](modifiers.md)
- [private](private.md)
- [protected](protected.md)
- [internal](internal.md)