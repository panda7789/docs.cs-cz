---
title: přepsání modifikátor - C# Reference
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: acad3aa3b196c184132ad1acdf52b18a799b0896
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713245"
---
# <a name="override-c-reference"></a>override (Referenční dokumentace jazyka C#)

Modifikátor `override` je nutné rozšířit nebo upravit abstraktní nebo virtuální implementaci zděděné metody, vlastnosti, indexeru nebo události.

## <a name="example"></a>Příklad

V `Square` tomto příkladu musí třída poskytnout `GetArea` potlačenou implementaci, protože `GetArea` je zděděna z abstraktní `Shape` třídy:

[!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]

`override` Metoda poskytuje novou implementaci člena, který je zděděn ze základní třídy. Metoda, která je přepsána `override` deklarací, se označuje jako přepisovaná základní metoda. Přepsána základní metoda musí mít `override` stejný podpis jako metoda. Informace o dědičnosti naleznete v tématu [Dědičnost](../../programming-guide/classes-and-structs/inheritance.md).

Nelze přepsat nevirtuální nebo statickou metodu. Přepsání základní metody `virtual` `abstract`musí `override`být , , nebo .

Deklarace `override` nemůže změnit usnadnění `virtual` přístupu metody. `override` Metoda i `virtual` metoda musí mít stejný [modifikátor úrovně přístupu](access-modifiers.md).

Metodu `new` `static`nelze použít `virtual` pomocí modifikátorů , nebo modifikátorů. `override`

Deklarace vlastnosti overriding musí určit přesně stejný modifikátor přístupu, typ a název `virtual` `abstract`jako `override`zděděná vlastnost a přepsána vlastnost musí být , , nebo .

Další informace o použití `override` klíčového slova naleznete v [tématu Správa verzí s přepsáním a Nová klíčová slova](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) a Informace o [tom, kdy použít přepsání a nová klíčová slova](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).

## <a name="example"></a>Příklad

Tento příklad definuje základní `Employee`třídu s názvem `SalesEmployee`a odvozenou třídu s názvem . Třída `SalesEmployee` obsahuje další pole `salesbonus`, a přepíše metodu, `CalculatePay` aby se v úvahu.

[!code-csharp[csrefKeywordsModifiers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#9)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [Dědičnost](../../programming-guide/classes-and-structs/inheritance.md)
- [C# Klíčová slova](index.md)
- [Modifikátory](index.md)
- [Abstraktní](abstract.md)
- [virtual](virtual.md)
- [nový (modifikátor)](new-modifier.md)
- [Polymorfismus](../../programming-guide/classes-and-structs/polymorphism.md)
