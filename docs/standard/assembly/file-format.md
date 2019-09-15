---
title: Formát souborů sestavení .NET
description: Přečtěte si o formátu souboru sestavení .NET, který se používá k popisu a zahrnutí aplikací a knihoven .NET.
author: richlander
ms.author: mairaw
ms.date: 08/20/2019
ms.technology: dotnet-standard
ms.assetid: 6520323e-ff28-4c8a-ba80-e64a413199e6
ms.openlocfilehash: c9396c45e3c6cdbc9360485f6286a1746bf81fdd
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970157"
---
# <a name="net-assembly-file-format"></a>Formát souborů sestavení .NET

Rozhraní .NET definuje formát binárního souboru *, který se používá*k úplnému popisu a zahrnutí programů rozhraní .NET. Sestavení se používají pro samotné programy i pro všechny závislé knihovny. Program .NET může být spuštěn jako jedno nebo více sestavení, bez jiných požadovaných artefaktů, kromě příslušné implementace rozhraní .NET. Nativní závislosti, včetně rozhraní API operačního systému, jsou samostatné a nejsou součástí formátu sestavení .NET, i když jsou někdy popsány v tomto formátu (například WinRT).

> Každá komponenta rozhraní příkazového řádku poskytuje metadata pro deklarace, implementace a odkazy, které jsou specifické pro danou komponentu. Proto se metadata specifická pro komponentu označují jako metadata komponenty a výsledná komponenta je označována jako samo-popisující – od ECMA 335 I. 9.1, komponent a sestavení.

Formát je plně určen a standardizován jako [ECMA 335](https://www.ecma-international.org/publications/standards/Ecma-335.htm). Tento formát používají všechny kompilátory a moduly runtime rozhraní .NET. Existence dokumentovaného a zřídka aktualizovaného binárního formátu byla významnou výhodou (pravděpodobně a požadavku) pro interoperabilitu. Formát byl naposledy aktualizován způsobem v 2005 (.NET 2,0), aby se vešel na obecné typy a architekturu procesoru.

Formát je CPU a OS-nezávislá. Byl použit jako součást implementací rozhraní .NET, která cílí na mnoho čipy a procesorů. I když má vlastní formát Windows dědictví, dá se implementovat v jakémkoli operačním systému. Jeho pravděpodobně nejvýznamnější volbou pro interoperabilitu OS je, že většina hodnot je uložená ve formátu Little endian. Nemá konkrétní spřažení pro velikost ukazatele na počítač (například 32-bit, 64 bitů).

Formát sestavení .NET je také velmi popisný o struktuře daného programu nebo knihovny. Popisuje interní součásti sestavení, konkrétně odkazy na sestavení a definované typy a jejich vnitřní strukturu. Nástroje nebo rozhraní API mohou číst a zpracovávat tyto informace pro zobrazení nebo pro provádění programových rozhodnutí.

## <a name="format"></a>Formát

Binární formát .NET je založen na formátu souboru Windows [PE](https://en.wikipedia.org/wiki/Portable_Executable) . Knihovny tříd .NET ve skutečnosti mají vyhovující Windows PEs a zobrazují se na první pohled na použití knihoven DLL (Windows Dynamic Link Library) nebo spustitelných souborů aplikace (exe). To je velmi užitečná vlastnost ve Windows, kde se dá maskovat jako nativní spustitelné binární soubory a získat některé ze stejných úprav (například zatížení operačního systému, nástroje PE).

![Hlavičky sestavení](../media/assembly-format/assembly-headers.png)

Hlavičky sestavení z ECMA 335 II. 25.1, struktura formátu běhového souboru.

## <a name="process-the-assemblies"></a>Zpracování sestavení

Je možné zapisovat nástroje nebo rozhraní API pro zpracování sestavení. Informace o sestavení umožňují provádět programová rozhodnutí za běhu, přepisování sestavení a poskytování technologie IntelliSense pro rozhraní API v editoru a generování dokumentace. <xref:System.Reflection?displayProperty=nameWithType>, <xref:System.Reflection.MetadataLoadContext?displayProperty=nameWithType>a [mono. Cecil](https://www.mono-project.com/docs/tools+libraries/libraries/Mono.Cecil/) jsou vhodné příklady nástrojů, které se často používají k tomuto účelu.
