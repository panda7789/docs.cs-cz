---
title: "Co je spravovaný kód?"
description: "Zjistěte, jak spravovaný kód je kód, jejichž spuštění je spravován nástrojem modul runtime, Common Language Runtime (CLR)."
keywords: "Rozhraní .NET, .NET core"
author: blackdwarf
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 20bb7ea8-192e-4a96-8ef3-e10e1950fd3d
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ca2ae076229a1726d3a25a84e358f9cfb623a297
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="what-is-managed-code"></a>Co je "spravovaný kód"?

Při práci s rozhraní .NET Framework, se setkají často termín "spravovaného kódu". Tento dokument vysvětluje, co znamená tento termín a další informace o kolem něj.

Uvést velmi jednoduše, spravovaný kód je, že právě: kód, jejichž spuštění je spravuje modulu runtime. V takovém případě je volána v modulu runtime **modul Common Language Runtime** nebo CLR, bez ohledu na implementaci ([Mono](http://www.mono-project.com/) nebo rozhraní .NET Framework nebo .NET Core). CLR má na starosti trvá spravovaného kódu, kompilace do kódu počítače a její provedení. Nad, runtime nabízí několik důležité služby, jako je například automatická správa paměti, hranice zabezpečení typ zabezpečení atd.

Protějšek to způsobem, jakým byste spustili programu C/C++, označované taky jako "nespravovaného kódu". Nespravované světě programátorů má na starosti prakticky vše. Skutečný program je v podstatě binární soubor, který načte do paměti operačního systému (OS) a spustí. Všem ostatním ze správy paměti na aspekty zabezpečení jsou zatížení programátora.

Spravovaný kód je zapsán v jednom z vysoké úrovně jazyků, které se dají spustit na rozhraní .NET, například C#, Visual Basic, F # a ostatní. Když zkompilujete kód napsaný v těchto jazyků s jejich odpovídajících kompilátoru, neobdržíte zkompilovaný kód. Můžete získat **Intermediate Language** kód, který modul runtime pak zkompiluje a spustí. C++ je jedinou výjimkou tohoto pravidla, jak ho můžete také vytvořit několik nativní, nespravované binární soubory, které běží v systému Windows.

## <a name="intermediate-language--execution"></a>Zprostředkující jazyk a provádění

Co je "Intermediate Language" (nebo IL pro zkrácení)? Je produkt kompilace kód napsaný v souhrnné jazyky rozhraní .NET. Jednou kompilaci zapisují v jednom z těchto jazyků, zobrazí se binární soubor, který je vytvořil mimo IL kódu. Je důležité si uvědomit, že IL je nezávislé na žádné konkrétní jazyk, který spouští nad modulu runtime; je i samostatné specifikace pro něj, který může číst, pokud jste tak sklon.

Po IL můžete vytvořit z vašeho kódu vysoké úrovně, budete pravděpodobně chtít ji spustit. Toto je, kde modulu CLR převezme a spustí proces **pouze za běhu** kompilování, nebo **JIT-ing** svůj kód IL zkompilovaný kód, který lze spustit ve skutečnosti na procesor. Tímto způsobem modulu CLR zná přesně co kód dělá a může efektivně _spravovat_ ho.

Převodní jazyk někdy se také nazývá Common mezilehlá jazyk souboru CIL () nebo Microsoft Intermediate Language (MSIL).

## <a name="unmanaged-code-interoperability"></a>Interoperabilita s nespravovaným kódem

Samozřejmě modulu CLR umožňuje předávání hranice mezi spravovanými a nespravovanými world, a je mnoha kód, který nemá tedy i při [základní knihovny tříd](framework-libraries.md). To se označuje jako **interoperabilita** nebo právě **zprostředkovatel komunikace s objekty** pro krátké. Tato ustanovení by umožnilo, například zabalit do nespravovaných knihovny a volání do ní. Je ale důležité si uvědomit, že jakmile to uděláte, když kód předá hranice modul runtime, skutečných spuštění je znovu ruční nespravovaného kódu a proto klesne pod stejná omezení.

Podobně jako tento, C# je jeden jazyk, který umožňuje používat nespravované konstrukce, jako je například ukazatele přímo v kódu s využitím, která se označuje jako **unsafe kontextu** který označí úsek kódu, pro který není spravuje provádění CLR.

## <a name="more-resources"></a>Další prostředky

*   [Koncepční přehled rozhraní .NET framework](https://msdn.microsoft.com/library/zw4w595w.aspx)
*   [Nebezpečný kód a ukazatele](../../docs/csharp/programming-guide/unsafe-code-pointers/index.md)
*   [Interoperabilita (Průvodce programováním C#)](https://msdn.microsoft.com/library/ms173184.aspx)
