---
title: přepis – modifikátor C# – referenční informace
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: 699887d635ab074fc9ffa4cd7fa354372eb82f25
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422637"
---
# <a name="override-c-reference"></a>override (Referenční dokumentace jazyka C#)

Modifikátor `override` je vyžadován pro rozšiřování nebo úpravu abstraktní nebo virtuální implementace zděděné metody, vlastnosti, indexeru nebo události.

## <a name="example"></a>Příklad

V tomto příkladu musí třída `Square` poskytovat přepsanou implementaci `GetArea`, protože `GetArea` dědí z abstraktní `Shape` třídy:

[!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]

Metoda `override` poskytuje novou implementaci člena, který je zděděn ze základní třídy. Metoda, která je přepsána deklarací `override`, je označována jako přepsaná základní metoda. Přepsaná základní metoda musí mít stejnou signaturu jako metoda `override`. Informace o dědičnosti naleznete v tématu [Dědičnost](../../programming-guide/classes-and-structs/inheritance.md).

Nemůžete přepsat nevirtuální nebo statickou metodu. Přepsaná základní metoda musí být `virtual`, `abstract`nebo `override`.

Deklarace `override` nemůže změnit přístupnost metody `virtual`. Jak metoda `override`, tak metoda `virtual` musí mít stejný [Modifikátor úrovně přístupu](access-modifiers.md).

Nemůžete použít modifikátory `new`, `static`nebo `virtual` pro úpravu metody `override`.

Přepsání deklarace vlastnosti musí přesně určovat stejný modifikátor přístupu, typ a název jako zděděnou vlastnost a přepsanou vlastnost musí být `virtual`, `abstract`nebo `override`.

Další informace o použití klíčového slova `override` naleznete v tématu [Správa verzí pomocí klíčových slov override a New](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) a [znalost, kdy použít klíčová slova override a New](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).

## <a name="example"></a>Příklad

Tento příklad definuje základní třídu s názvem `Employee`a odvozenou třídu s názvem `SalesEmployee`. Třída `SalesEmployee` obsahuje pole navíc, `salesbonus`a přepisuje metodu `CalculatePay`, aby ji bylo možné vzít v úvahu.

[!code-csharp[csrefKeywordsModifiers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#9)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Dědičnost](../../programming-guide/classes-and-structs/inheritance.md)
- [Klíčová slova jazyka C#](index.md)
- [Modifikátory](index.md)
- [abstract](abstract.md)
- [virtual](virtual.md)
- [New (modifikátor)](new-modifier.md)
- [Polymorfismus](../../programming-guide/classes-and-structs/polymorphism.md)
