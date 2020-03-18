---
title: veřejné klíčové slovo - C# Reference
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: 19906d7fd0f7d41ef9e4cdaf951c77825e0bbead
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713167"
---
# <a name="public-c-reference"></a>public (Referenční dokumentace jazyka C#)

Klíčové `public` slovo je modifikátor přístupu pro typy a členy typu. Přístup veřejnosti je nejtolerantnější úroveň přístupu. Neexistují žádná omezení přístupu k veřejným členům, jako v tomto příkladu:

```csharp
class SampleClass
{
    public int x; // No access restrictions.
}
```

Další informace najdete [v tématu Modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md) a [úrovně usnadnění.](accessibility-levels.md)

## <a name="example"></a>Příklad

V následujícím příkladu jsou deklarovány dvě třídy `PointTest` a `MainClass`. Veřejnost `x` a `y` z `PointTest` nich jsou `MainClass`přístupné přímo z .

[!code-csharp[csrefKeywordsModifiers#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#13)]

Pokud změníte `public` úroveň přístupu na [soukromou](private.md) nebo [chráněnou](protected.md), zobrazí se chybová zpráva:

'PointTest.y' je nepřístupný kvůli jeho úrovni ochrany.

## <a name="c-language-specification"></a>specifikace jazyka C#  

For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [Modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md)
- [C# Klíčová slova](index.md)
- [Modifikátory přístupu](access-modifiers.md)
- [Úrovně přístupnosti](accessibility-levels.md)
- [Modifikátory](index.md)
- [Soukromé](private.md)
- [protected](protected.md)
- [Vnitřní](internal.md)
