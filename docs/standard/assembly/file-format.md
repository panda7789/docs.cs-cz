---
title: Formát souborů sestavení .NET
description: Informace o formátu souboru sestavení .NET, který se používá k popisu a obsahují aplikace a knihovny .NET.
author: richlander
ms.date: 08/20/2019
ms.technology: dotnet-standard
ms.assetid: 6520323e-ff28-4c8a-ba80-e64a413199e6
ms.openlocfilehash: 4cf6522d66d7a1efccde45078768a773db6e6cb0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711581"
---
# <a name="net-assembly-file-format"></a>Formát souborů sestavení .NET

Rozhraní .NET definuje binární formát souboru, *sestavení*, který slouží k úplnému popisu a obsahují programy .NET. Sestavení se používají pro samotné programy, stejně jako všechny závislé knihovny. Program .NET lze spustit jako jedno nebo více sestavení bez dalších požadovaných artefaktů nad rámec příslušné implementace rozhraní .NET. Nativní závislosti, včetně rozhraní API operačního systému, jsou samostatným problémem a nejsou obsaženy ve formátu sestavení .NET, i když jsou někdy popsány v tomto formátu (například WinRT).

> Každá komponenta CLI nese metadata pro deklarace, implementace a odkazy specifické pro tuto komponentu. Proto metadata specifická pro komponentu se označují jako metadata komponenty a výsledná komponenta je označována jako vlastní popisující – z ECMA 335 I.9.1, Komponenty a sestavy.

Formát je plně specifikován a standardizován jako [ECMA 335](https://www.ecma-international.org/publications/standards/Ecma-335.htm). Tento formát používají všechny kompilátory rozhraní .NET a runtimes. Přítomnost zdokumentovaného a zřídka aktualizovaného binárního formátu byla hlavní výhodou (pravděpodobně požadavkem) pro interoperabilitu. Formát byl naposledy aktualizován podstatným způsobem v roce 2005 (.NET 2.0) tak, aby vyhovoval obecným typům a architektuře procesoru.

Formát je cpu- a OS-agnostik. Používá se jako součást implementací rozhraní .NET, které cílí na mnoho čipů a procesorů. Zatímco samotný formát má dědictví systému Windows, je implementovatelný v libovolném operačním systému. Jeho pravděpodobně nejvýznamnější volbou pro interoperabilitu operačního operačního spoje je, že většina hodnot je uložena ve formátu little-endian. Nemá specifickou spřažení velikosti ukazatele počítače (například 32bitová, 64bitová).

Formát sestavení rozhraní .NET je také velmi popisný o struktuře daného programu nebo knihovny. Popisuje vnitřní součásti sestavy, konkrétně odkazy na sestavení a definované typy a jejich vnitřní strukturu. Nástroje nebo api mohou číst a zpracovávat tyto informace pro zobrazení nebo pro programová rozhodnutí.

## <a name="format"></a>Formát

Binární formát .NET je založen na formátu souboru prostředí Windows [PE.](https://en.wikipedia.org/wiki/Portable_Executable) Knihovny tříd .NET jsou ve skutečnosti konformní windows pes a na první pohled se zobrazují jako knihovny dynamických odkazů systému Windows (DLL) nebo spustitelné soubory aplikací (EXEs). To je velmi užitečná charakteristika na Windows, kde se mohou maskovat jako nativní spustitelné binární soubory a získat některé stejné zacházení (například zatížení operačního systému, PE nástroje).

![Záhlaví sestavení](../media/assembly-format/assembly-headers.png)

Záhlaví sestavení z ECMA 335 II.25.1, Struktura formátu souboru runtime.

## <a name="process-the-assemblies"></a>Zpracování sestavení

Je možné psát nástroje nebo api pro zpracování sestavení. Informace o sestavení umožňují provádět programová rozhodnutí za běhu, přepisovat sestavení, poskytovat rozhraní API IntelliSense v editoru a generovat dokumentaci. <xref:System.Reflection?displayProperty=nameWithType>, <xref:System.Reflection.MetadataLoadContext?displayProperty=nameWithType>, a [Mono.Cecil](https://www.mono-project.com/docs/tools+libraries/libraries/Mono.Cecil/) jsou dobrým příkladem nástrojů, které jsou často používány pro tento účel.
