---
title: Protected – klíčové slovo (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: f25e692430f876ec384971079d6d0aa2c97e967b
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47070572"
---
# <a name="protected-c-reference"></a>protected (Referenční dokumentace jazyka C#)

`protected` – Klíčové slovo je modifikátor přístupu členu.

 > Tato stránka popisuje `protected` přístup. `protected` – Klíčové slovo je také součástí [ `protected internal` ](protected-internal.md) a [ `private protected` ](private-protected.md) modifikátorů přístupu.

Chráněný člen je přístupný v rámci své třídy a instance odvozené třídy.

Porovnání `protected` jiných přístupu modifikátory přístupu, najdete v článku [úrovní přístupu](accessibility-levels.md).

## <a name="example"></a>Příklad

Chráněný člen základní třídy je přístupný v odvozené třídě pouze v případě, že dojde k přístup až po typ odvozené třídy. Představte si třeba následující segment kódu:

[!code-csharp[csrefKeywordsModifiers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#11)]

Příkaz `a.x = 10` dojde k chybě, protože se provádí v rámci statickou metodu Main, a ne instance třídy B.

Členy struktury nejde chránit, protože struktura nemůže dědit.

## <a name="example"></a>Příklad

V tomto příkladu třída `DerivedPoint` je odvozen z `Point`. Proto můžete přistupovat k chráněným členům základní třídy přímo z odvozené třídy.

[!code-csharp[csrefKeywordsModifiers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#12)]  

Pokud změníte úrovně přístupu `x` a `y` k [privátní](private.md), kompilátor vydá chybové zprávy:

`'Point.y' is inaccessible due to its protection level.`

`'Point.x' is inaccessible due to its protection level.`

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Modifikátory přístupu](access-modifiers.md)
- [Úrovně přístupnosti](accessibility-levels.md)
- [Modifikátory](modifiers.md)
- [public](public.md)
- [private](private.md)
- [internal](internal.md)
- [Zajištění zabezpečení pro klíčových slov internal virtual](https://docs.microsoft.com/en-us/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))