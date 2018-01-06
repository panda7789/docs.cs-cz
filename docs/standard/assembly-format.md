---
title: "Formát souboru sestavení rozhraní .NET"
description: "Další informace o formátu souborů sestavení .NET, který slouží k označení a obsahovat aplikace .NET a knihovny."
keywords: "Rozhraní .NET, .NET core"
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 6520323e-ff28-4c8a-ba80-e64a413199e6
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cdd76558852992a5c2f6b7def83e30fb004f93b6
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/05/2018
---
# <a name="net-assembly-file-format"></a>Formát souboru sestavení rozhraní .NET

Rozhraní .NET definuje binárního souboru formátu – "sestavení" -, který se používá k plně popisují a obsahovat programy .NET. Sestavení se používají pro samotné programy a také všechny závislé knihovny. Program rozhraní .NET můžete provést, protože jeden nebo více sestavení s žádné další požadované artefakty, nad rámec odpovídající implementace rozhraní .NET. Nativní závislosti, včetně operačního systému rozhraní API, jsou samostatné problém a nejsou obsaženy v rámci formátu sestavení .NET, i když jsou popsány někdy se tento formát (například WinRT).

> Jednotlivé komponenty rozhraní příkazového řádku představuje metadata pro deklarace, implementace a odkazy na specifické pro danou součást. Proto metadata specifická pro součást se označuje jako součást metadata a výsledné komponenty říká, že je možné popisující samy sebe – od ECMA 335 I.9.1, komponenty a sestavení.

Formát je plně zadaný a standardizované jako ECMA 335. Všechny moduly runtime a kompilátory .NET použijte tento formát. Přítomnost zdokumentovaných a zřídka aktualizované binární formát byl hlavní výhody (pravděpodobně požadavek) pro – interoperabilita. Formát byl naposledy aktualizován podstatné způsobem 2005 (rozhraní .NET 2.0) pro přizpůsobení obecné typy a architekturu procesoru.

Formát je nezávislá na procesoru a operačního systému. Používá se jako součást implementací rozhraní .NET, které cílí na mnoha čipy a procesory. Formát samotné má dědictví Windows, je implementable v jakémkoliv operačním systému. Jeho pravděpodobně nejvýznamnějších volba interoperability operačního systému je, že většina hodnot jsou uložené ve formátu little endian. Nemá konkrétní spřažení k velikosti ukazatel počítače (například 32bitové, 64bitové).

Formát sestavení .NET je také velmi popisný o struktuře daný program nebo knihovny. Popisuje interní součástí sestavení, konkrétně: odkazy na sestavení a definované typy a jejich interní struktury. Rozhraní API nebo nástroje můžete číst a zpracovat informace pro zobrazení nebo programové rozhodnutí.

## <a name="format"></a>Formát

Binární formát .NET je založena na systému Windows [PE souboru](http://en.wikipedia.org/wiki/Portable_Executable) formátu. Ve skutečnosti knihovny tříd rozhraní .NET jsou vyhovující Windows PEs a zobrazí na první pohled na Windows dynamické knihovny (DLL) nebo spustitelné soubory aplikace (souborů exe). To je velmi užitečná vlastnosti v systému Windows, kde můžete maskovat jako nativní spustitelné binární soubory a získat některé stejným způsobem (například zatížení operačního systému, PE nástroje).

![Sestavení hlavičky](./media/assembly-format/assembly-headers.png)

Sestavení hlavičky z ECMA 335 II.25.1, struktura formátu souborů modulu runtime.

## <a name="processing-the-assemblies"></a>Zpracování sestavení

Je možné zapsat do procesu sestavení nástroje nebo rozhraní API. Informace o sestavení umožňuje programový rozhodování za běhu, přepisovat sestavení, poskytuje rozhraní API technologie IntelliSense v editoru a generování dokumentace. <xref:System.Reflection?displayProperty=nameWithType>a [Mono.Cecil](http://www.mono-project.com/docs/tools+libraries/libraries/Mono.Cecil/) jsou dobrými příklady nástrojů, které se často používají pro tento účel.
