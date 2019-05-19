---
title: Úvod do delegátů
description: Další informace o delegátech v tomto úvodním tématu, který představuje základní koncepty a popisuje cíle návrhu jazyk pro delegáty.
ms.date: 06/20/2016
ms.assetid: 59b61d77-84e5-457b-8da5-fb5f24ca6ed6
ms.openlocfilehash: 43cdf9345f0bae9d5c4d0e6a31d80bc269c37fec
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65879033"
---
# <a name="introduction-to-delegates"></a>Úvod do delegátů

Delegáti poskytují *pozdní vazby* mechanismus v rozhraní .NET. Pozdní vazby znamená, že vytvoříte algoritmus kde volající také poskytuje alespoň jednu metodu, která implementuje část algoritmus.

Představte si třeba seznam hvězdiček v aplikaci astronomii řazení.
Můžete seřadit tyto hvězdiček podle jejich vzdálenost od země nebo velikost na hvězdičku nebo jejich vnímaná jasu.

V těchto případech se metoda Sort() provede v podstatě totéž: Uspořádá položky v seznamu na základě některých porovnání. Kód, který porovná dvě hvězdičky se liší pro každý z pořadí řazení.

Tyto druhy řešení se používají v softwaru pro polovinu století.
C# Konceptu jazyka delegáta poskytuje prvotřídní podporu a bezpečnost typů kolem koncepce.

Jak uvidíte později v tomto seriálu C# kód, který píšete pro algoritmy, jako to je typově bezpečný a využívá jazyk, a kompilátor zajistíte, že typy odpovídají pro argumenty a vrátí typy.

## <a name="language-design-goals-for-delegates"></a>Cíle návrhu jazyk pro delegáty

Návrháři jazyka Výčtový několik cílů pro funkci, která se nakonec začal být delegáti.

Tým chtěla při podpoře běžné konstrukce jazyka, která se dá použít pro jakékoli pozdní vazby algoritmů. Který umožňuje vývojářům další jeden koncept a použijte tento stejný koncept napříč řadou různých softwarových problémů.

Za druhé tým chtěli podporu obou volání metody single a vícesměrového vysílání. (Vícesměroví Delegáti jsou delegáty, kteří zřetězit více volání metody. Zobrazí se vám příklady [dále v této sérii](delegate-class.md).) 

Tým chtěla delegáty pro podporu stejné bezpečnost typů, který vývojářům ze všech C# vytvoří. 

Nakonec tým rozpoznat, že vzor události je jeden konkrétní vzor, kde je velmi užitečné delegáty nebo libovolný algoritmus pozdní vazbu. Tým chtěli Ujistěte se, že kód pro delegáty, může být základem pro vzor události .NET.

Výsledek všechnu tu práci byla podpora delegátů a událostí v C# a .NET. Zbývající články v této části probereme funkce jazyka, podpora knihovny a společné idiomy, které se používají při práci s delegátů.

Seznámí vás `delegate` – klíčové slovo a co kódu generuje. Se dozvíte o funkcích `System.Delegate` třídy a jak se používají tyto funkce. Dozvíte se, jak vytvořit typ bezpečné delegáty a vytvoření metody, které mohou být vyvolány prostřednictvím delegátů. Budete se také dozvíte, jak pracovat s Delegáti a události pomocí výrazů Lambda. Uvidíte, kde delegáti stal jednou z stavební bloky pro funkci LINQ. Dozvíte se, jak Delegáti jsou základem pro vzor události .NET a jak se liší.

Celkově uvidíte, jak Delegáti jsou nedílnou součástí programování v rozhraní .NET a používání rozhraní API.

Pusťme se do práce.

[Next](delegate-class.md)
