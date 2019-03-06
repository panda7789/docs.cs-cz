---
title: Formát souborů sestavení .NET
description: Další informace o formátu souborů sestavení .NET, který se používá k popisu a obsahovat .NET aplikací a knihoven.
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 6520323e-ff28-4c8a-ba80-e64a413199e6
ms.openlocfilehash: 0bde31a004b1952be488569f89cfd3b129c82771
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369075"
---
# <a name="net-assembly-file-format"></a>Formát souborů sestavení .NET

.NET definuje binárním formátu – "sestavení" –, který se používá k plně popisu a obsahovat programy .NET. Sestavení jsou používána pro samotné programy, stejně jako všechny závislé knihovny. .NET program můžete provést, protože jeden nebo více sestavení se žádné další požadované artefakty, nad rámec vhodné implementaci rozhraní .NET. Nativní závislostí, včetně rozhraní API, operačního systému jsou samostatný problém a nejsou obsaženy v rámci formátu sestavení .NET, i když jsou někdy popsané v tomto formátu (například WinRT).

> Jednotlivé komponenty rozhraní příkazového řádku představuje metadata pro deklarace, implementace a odkazy na specifické pro tuto součást. Proto metadata specifická pro součást se označuje jako součást metadat a výsledné komponenty se říká, že se popisující samy sebe – od I.9.1 335 Standard ECMA, komponenty a sestavení.

Formát je plně zadaný a standardizované jako [335 Standard ECMA](https://www.ecma-international.org/publications/standards/Ecma-335.htm). Všechny kompilátory .NET a moduly runtime použijte tento formát. Přítomnost binární formát zdokumentované a zřídka aktualizované byl hlavní výhoda (pravděpodobně požadavek) pro spolupráci. Formát poslední aktualizace podstatné způsobem v roce 2005 (.NET 2.0) tak, aby vyhovovaly obecné typy a architekturu procesoru.

Formát je bez ohledu na využití procesoru a operačního systému. Se použil jako součást implementace .NET, které se zaměřují mnoho čipy a procesorů. Formát samotné má dědictví Windows, je implementable pro všechny operační systémy. Jeho pravděpodobně nejdůležitější interoperability operačního systému je, že většina hodnoty jsou uloženy ve formátu little endian. Nemá konkrétní spřažení s velikost ukazatele počítače (například 32-bit, 64 bitů).

Formát sestavení .NET je také velmi popisné informace o struktuře danou aplikaci nebo knihovny. Popisuje vnitřní součástí sestavení, konkrétně: odkazy na sestavení a typy definované a jejich vnitřní struktury. Nástroje nebo rozhraní API může číst a zpracovat informace pro zobrazení nebo programové rozhodnutí.

## <a name="format"></a>Formát

Binární formát .NET je založen na Windows [přenositelný Spustitelný soubor](https://en.wikipedia.org/wiki/Portable_Executable) formátu. Ve skutečnosti knihovny tříd .NET jsou splňující podmínky Windows PEs a zobrazují na první pohled Windows dynamické knihovny (DLL) nebo aplikací spustitelných souborů (exe). To je velmi užitečné charakteristické na Windows, ve kterém můžete maskovat jako nativní spustitelný soubor binární soubory a získat některé stejným způsobem (třeba zatížení operačního systému, nástroje PE).

![Záhlaví sestavení](../media/assembly-format/assembly-headers.png)

Sestavení hlavičky z ECMA 335 II.25.1 struktura formát souboru modulu runtime.

## <a name="processing-the-assemblies"></a>Zpracování sestavení

Je možné zapisovat nástrojů nebo rozhraní API do procesu sestavení. Informace o sestavení umožňuje programový rozhodování v době běhu, přepisovat sestavení, poskytuje rozhraní API technologie IntelliSense v editoru a generování dokumentace. <xref:System.Reflection?displayProperty=nameWithType> a [Mono.Cecil](https://www.mono-project.com/docs/tools+libraries/libraries/Mono.Cecil/) jsou dobrým příkladem nástroje, které se často používají pro tento účel.
