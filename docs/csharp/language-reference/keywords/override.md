---
description: override – modifikátor – reference jazyka C#
title: override – modifikátor – reference jazyka C#
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: 51ca806310214981b7ff24a796fe078d902dca4d
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134455"
---
# <a name="override-c-reference"></a>override (Referenční dokumentace jazyka C#)

`override`Modifikátor je vyžadován pro rozšiřování nebo úpravu abstraktní nebo virtuální implementace zděděné metody, vlastnosti, indexeru nebo události.

## <a name="example"></a>Příklad

V tomto příkladu `Square` Třída musí poskytovat přepsanou implementaci, `GetArea` protože `GetArea` je zděděna z abstraktní `Shape` třídy:

[!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]

`override`Metoda poskytuje novou implementaci člena, který je zděděn ze základní třídy. Metoda, která je přepsána `override` deklarací, je označována jako přepsaná základní metoda. Přepsaná základní metoda musí mít stejnou signaturu jako `override` metoda. Informace o dědičnosti naleznete v tématu [Dědičnost](../../programming-guide/classes-and-structs/inheritance.md).

Nemůžete přepsat nevirtuální nebo statickou metodu. Přepsaná základní metoda musí být `virtual` , `abstract` nebo `override` .

`override`Deklarace nemůže změnit přístupnost `virtual` metody. `override`Metoda i `virtual` Metoda musí mít stejný [Modifikátor úrovně přístupu](access-modifiers.md).

Nemůžete použít `new` `static` `virtual` modifikátory, nebo pro úpravu `override` metody.

Přepisující deklaraci vlastnosti musí jako zděděné vlastnosti zadat přesně stejný modifikátor přístupu, typ a název a přepsanou vlastnost musí být `virtual` , `abstract` nebo `override` .

Další informace o použití `override` klíčového slova naleznete v tématu [Správa verzí pomocí klíčových slov override a New](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) a [znalost, kdy použít klíčová slova override a New](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).

## <a name="example"></a>Příklad

Tento příklad definuje základní třídu s názvem `Employee` a odvozenou třídu s názvem `SalesEmployee` . `SalesEmployee`Třída obsahuje pole navíc, `salesbonus` a přepisuje metodu, `CalculatePay` aby ji bylo možné vzít v úvahu.

[!code-csharp[csrefKeywordsModifiers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#9)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Dědičnost](../../programming-guide/classes-and-structs/inheritance.md)
- [Klíčová slova jazyka C#](index.md)
- [Modifikátory](index.md)
- [Výtah](abstract.md)
- [virtual](virtual.md)
- [New (modifikátor)](new-modifier.md)
- [Polymorfismus](../../programming-guide/classes-and-structs/polymorphism.md)
