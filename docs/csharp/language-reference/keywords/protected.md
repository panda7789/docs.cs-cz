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
ms.openlocfilehash: f54c3f36e5aeb428815d1c49cd797e559d156ea7
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422568"
---
# <a name="protected-c-reference"></a>protected (Referenční dokumentace jazyka C#)

Klíčové slovo `protected` je modifikátor přístupu ke členu.

 > Tato stránka pokrývá přístup `protected`. Klíčové slovo `protected` je také součástí [`protected internal`](protected-internal.md) a [`private protected`](private-protected.md) modifikátory přístupu.

Chráněný člen je přístupný v rámci své třídy a odvozené instance třídy.

Porovnání `protected` s dalšími modifikátory přístupu najdete v tématu [úrovně usnadnění](accessibility-levels.md).

## <a name="example"></a>Příklad

Chráněný člen základní třídy je přístupný v odvozené třídě pouze v případě, že k přístupu dojde prostřednictvím odvozené třídy typu. Zvažte například následující segment kódu:

[!code-csharp[csrefKeywordsModifiers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#11)]

Příkaz `a.x = 10` vygeneruje chybu, protože je vytvořena v rámci statické metody Main a nikoli instance třídy B.

Členy struktury nelze chránit, protože strukturu nelze zdědit.

## <a name="example"></a>Příklad

V tomto příkladu je třída `DerivedPoint` odvozena od `Point`. Proto máte přístup k chráněným členům základní třídy přímo z odvozené třídy.

[!code-csharp[csrefKeywordsModifiers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#12)]  

Pokud změníte úrovně přístupu `x` a `y` na [soukromou](private.md), kompilátor vydá chybové zprávy:

`'Point.y' is inaccessible due to its protection level.`

`'Point.x' is inaccessible due to its protection level.`

## <a name="c-language-specification"></a>specifikace jazyka C#  

Další informace najdete v tématu [deklarované přístupnosti](~/_csharplang/spec/basic-concepts.md#declared-accessibility) ve [ C# specifikaci jazyka](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Modifikátory přístupu](access-modifiers.md)
- [Úrovně přístupnosti](accessibility-levels.md)
- [Modifikátory](index.md)
- [public](public.md)
- [private](private.md)
- [internal](internal.md)
- [Problémy se zabezpečením pro interní virtuální klíčová slova](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))
