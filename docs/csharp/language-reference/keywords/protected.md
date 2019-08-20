---
title: chráněné klíčové slovo C# – referenční informace
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: a0420dd10d81c4ae893ab0447244a611091ed7b0
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69601970"
---
# <a name="protected-c-reference"></a>protected (Referenční dokumentace jazyka C#)

`protected` Klíčové slovo je modifikátor přístupu ke členu.

 > Tato stránka se `protected` zabývá přístupem. Klíčové slovo je také součástí [`protected internal`](protected-internal.md) modifikátorů a [`private protected`](private-protected.md) přístupu. `protected`

Chráněný člen je přístupný v rámci své třídy a odvozené instance třídy.

Porovnání `protected` s dalšími modifikátory přístupu najdete v tématu [úrovně usnadnění](accessibility-levels.md).

## <a name="example"></a>Příklad

Chráněný člen základní třídy je přístupný v odvozené třídě pouze v případě, že k přístupu dojde prostřednictvím odvozené třídy typu. Zvažte například následující segment kódu:

[!code-csharp[csrefKeywordsModifiers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#11)]

Příkaz `a.x = 10` vygeneruje chybu, protože je vytvořena v rámci statické metody Main a nikoli instance třídy B.

Členy struktury nelze chránit, protože strukturu nelze zdědit.

## <a name="example"></a>Příklad

V tomto příkladu je třída `DerivedPoint` odvozena z. `Point` Proto máte přístup k chráněným členům základní třídy přímo z odvozené třídy.

[!code-csharp[csrefKeywordsModifiers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#12)]  

Pokud změníte úrovně přístupu u `x` a `y` na [Private](private.md), kompilátor vydá chybové zprávy:

`'Point.y' is inaccessible due to its protection level.`

`'Point.x' is inaccessible due to its protection level.`

## <a name="c-language-specification"></a>specifikace jazyka C#  

Další informace najdete v tématu [deklarované](~/_csharplang/spec/basic-concepts.md#declared-accessibility) přístupnosti ve [ C# specifikaci jazyka](../language-specification/index.md). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Modifikátory přístupu](access-modifiers.md)
- [Úrovně přístupnosti](accessibility-levels.md)
- [Modifikátory](modifiers.md)
- [public](public.md)
- [private](private.md)
- [internal](internal.md)
- [Problémy se zabezpečením pro interní virtuální klíčová slova](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))
