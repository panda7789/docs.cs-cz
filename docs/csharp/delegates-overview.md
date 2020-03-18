---
title: Úvod do delegátů
description: Další informace o delegátech v tomto tématu přehledu, který představuje základní koncepty a popisuje cíle návrhu jazyka pro delegáty.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 59b61d77-84e5-457b-8da5-fb5f24ca6ed6
ms.openlocfilehash: fd594f77c034533a1d5aee1d8279e9b727284311
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146226"
---
# <a name="introduction-to-delegates"></a>Úvod do delegátů

Delegáti poskytují *mechanismus pozdní vazby* v rozhraní .NET. Pozdní vazba znamená, že vytvoříte algoritmus, kde volající také poskytuje alespoň jednu metodu, která implementuje část algoritmu.

Zvažte například seřazení seznamu hvězd v aplikaci astronomie.
Můžete se rozhodnout třídit tyto hvězdy podle jejich vzdálenosti od Země, nebo velikosti hvězdy, nebo jejich vnímaný jas.

Ve všech těchto případech Sort() metoda v podstatě totéž: uspořádá položky v seznamu na základě některých porovnání. Kód, který porovnává dvě hvězdičky se liší pro každé řazení řazení.

Tyto druhy řešení byly použity v softwaru po dobu půl století.
Koncept delegáta jazyka C# poskytuje prvotřídní jazykovou podporu a bezpečnost typů kolem konceptu.

Jak uvidíte dále v této řadě, kód Jazyka C#, který napíšete pro algoritmy, jako je tento, je typově bezpečný a využívá jazyk a kompilátor k zajištění, že typy odpovídají argumentům a návratovým typům.

## <a name="language-design-goals-for-delegates"></a>Cíle jazykového návrhu pro delegáty

Návrháři jazyka vyjmenovalněkolik cílů pro funkci, která se nakonec stala delegáty.

Tým chtěl společnou jazykovou konstrukci, která by mohla být použita pro všechny algoritmy pozdní vazby. To umožňuje vývojářům naučit se jeden koncept a používat stejný koncept v mnoha různých softwarových problémech.

Za druhé, tým chtěl podporovat volání metod jednoho i vícesměrového vysílání. (Vícesměrové vysílání delegáti jsou delegáti, které řetěz dohromady více volání metody.
Příklady uvidíte [dále v této sérii](delegate-class.md).)

Tým chtěl delegáty podporovat stejný typ bezpečnosti, které vývojáři očekávají od všech c# konstrukce.

Nakonec tým rozpoznal, že vzor události je jeden konkrétní vzor, kde delegáti nebo jakýkoli algoritmus pozdní vazby je velmi užitečné. Tým chtěl zajistit, že kód pro delegáty může poskytnout základ pro vzor události .NET.

Výsledkem všech těchto prací byla podpora delegáta a události v c# a .NET. Zbývající články v této části se bude týkat funkce jazyka, podporu knihovny a společné idiomy, které se používají při práci s delegáty.

Dozvíte se o `delegate` klíčovéslovo a jaký kód generuje. Dozvíte se o funkcích `System.Delegate` ve třídě a o tom, jak se tyto funkce používají. Dozvíte se, jak vytvořit typ bezpečné delegáty a jak vytvořit metody, které lze vyvolat prostřednictvím delegátů. Dozvíte se také, jak pracovat s delegáty a události pomocí Lambda výrazy. Uvidíte, kde delegáti stanou jedním ze stavebních bloků pro LINQ. Dozvíte se, jak delegáti jsou základem pro vzor události .NET a jak se liší.

Celkově uvidíte, jak delegáti jsou nedílnou součástí programování v rozhraní .NET a práce s rozhraní API rozhraní API architektury.

Pusťme se do toho.

[Další](delegate-class.md)
