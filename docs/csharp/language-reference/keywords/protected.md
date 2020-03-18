---
title: chráněné klíčové slovo - C# Reference
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: bec619d4f49bd26daa742c18c830909c14948adf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713180"
---
# <a name="protected-c-reference"></a>protected (Referenční dokumentace jazyka C#)

Klíčové `protected` slovo je modifikátor přístupu člena.

 > Tato stránka `protected` se týká přístupu. Klíčové `protected` slovo je také [`protected internal`](protected-internal.md) [`private protected`](private-protected.md) součástí modifikátorů a přístup.

Chráněný člen je přístupný v rámci své třídy a podle odvozených instancí třídy.

Porovnání `protected` s ostatními modifikátory přístupu naleznete v [tématu Úrovně usnadnění přístupu](accessibility-levels.md).

## <a name="example"></a>Příklad

Chráněný člen základní třídy je přístupný v odvozené třídě pouze v případě, že přístup probíhá prostřednictvím odvozeného typu třídy. Zvažte například následující segment kódu:

[!code-csharp[csrefKeywordsModifiers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#11)]

Příkaz `a.x = 10` generuje chybu, protože je provedena v rámci statické metody Main a není instancí třídy B.

Členy struktury nelze chránit, protože strukturu nelze zdědit.

## <a name="example"></a>Příklad

V tomto příkladu `DerivedPoint` je třída `Point`odvozena od . Proto můžete přistupovat k chráněným členům základní třídy přímo z odvozené třídy.

[!code-csharp[csrefKeywordsModifiers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#12)]  

Pokud změníte úrovně `x` přístupu a `y` [soukromé](private.md), kompilátor vydá chybové zprávy:

`'Point.y' is inaccessible due to its protection level.`

`'Point.x' is inaccessible due to its protection level.`

## <a name="c-language-specification"></a>specifikace jazyka C#  

For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](index.md)
- [Modifikátory přístupu](access-modifiers.md)
- [Úrovně přístupnosti](accessibility-levels.md)
- [Modifikátory](index.md)
- [Veřejné](public.md)
- [Soukromé](private.md)
- [Vnitřní](internal.md)
- [Obavy o zabezpečení interních virtuálních klíčových slov](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))
