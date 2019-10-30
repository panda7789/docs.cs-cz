---
title: Úvod do delegátů
description: Přečtěte si o delegátech v tomto přehledovém tématu, které přináší základní koncepty a popisuje jazykové cíle návrhu pro delegáty.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 59b61d77-84e5-457b-8da5-fb5f24ca6ed6
ms.openlocfilehash: deff297ccce6cd14a7cd21c49638a9c6030a9996
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73037405"
---
# <a name="introduction-to-delegates"></a>Úvod do delegátů

Delegáti poskytují v .NET mechanismus *pozdní vazby* . Pozdní vazba znamená, že vytvoříte algoritmus, kde volající také dodá alespoň jednu metodu, která implementuje část algoritmu.

Zvažte například řazení seznamu hvězdiček v aplikaci astronomická aplikace.
Tyto hvězdy můžete seřadit podle jejich vzdálenosti od země nebo podle velikosti hvězdičky nebo jejich vypozorovaného jasu.

Ve všech těchto případech metoda sort () má v podstatě stejnou věc: Uspořádá položky v seznamu na základě nějakého porovnání. Kód, který porovnává dvě hvězdičky, se liší pro každé pořadí řazení.

Tyto druhy řešení se používají v softwaru pro polovinu století.
Koncept C# delegáta jazyka poskytuje prvotřídní podporu pro jazyky a bezpečnost typů kolem konceptu.

Jak uvidíte později v této sérii, C# kód, který napíšete pro algoritmy jako je typově bezpečný, a využívá jazyk a kompilátor k zajištění shody typů pro argumenty a návratové typy.

## <a name="language-design-goals-for-delegates"></a>Cíle návrhu jazyka pro delegáty

Návrháři jazyka vyčíslují několik cílů pro funkci, která se nakonec stala delegáty.

Tým chtěl, aby se vytvořila společná jazyková konstrukce, která by se dala použít pro všechny algoritmy s pozdní vazbou. To umožňuje vývojářům naučit se jeden koncept a stejný koncept používat v mnoha různých problémech se softwarem.

Za druhé tým chtěl podporovat volání metody Single i Multicast. (Delegáti vícesměrového vysílání jsou delegáti, kteří zřetězit dohromady více volání metody. [V této sérii](delegate-class.md)uvidíte příklady později.) 

Tým chtěl, aby podporoval stejnou bezpečnost typů, kterou vývojáři očekávají ze všech C# konstrukcí. 

Nakonec tým rozpoznal, že vzor události je jeden konkrétní vzor, ve kterém jsou delegáti nebo jakékoli pozdní vazby algoritmu velmi užitečné. Tým chtěl zajistit, aby kód pro delegáty mohl poskytnout základ pro vzor události .NET.

Výsledek všechny této práce byl delegát a podpora událostí v C# a .NET. Zbývající články v této části se týkají funkcí jazyka, podpory knihoven a běžných idiomy, které se používají při práci s delegáty.

Dozvíte se o klíčovém slově `delegate` a o tom, jaký kód generuje. Dozvíte se o funkcích ve třídě `System.Delegate` a o tom, jak se tyto funkce používají. Naučíte se, jak vytvořit typy bezpečných delegátů a jak vytvořit metody, které mohou být vyvolány prostřednictvím delegátů. Naučíte se také, jak pracovat s delegáty a událostmi pomocí výrazů lambda. Uvidíte, kde se delegáti stanou jedním ze stavebních bloků pro LINQ. Dozvíte se, jak jsou delegáti základem pro vzorec události .NET a jak se liší.

Celkově vidíte, jak jsou delegáti nedílnou součástí programování v rozhraní .NET a pracují s rozhraními API rozhraní Framework.

Pojďme začít.

[Next](delegate-class.md)
