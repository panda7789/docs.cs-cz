---
title: Vlákna v popředí a v pozadí
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], foreground
- threading [.NET Framework], background
- foreground threads
- background threads
ms.assetid: cfe0d632-dd35-47e0-91ad-f742a444005e
ms.openlocfilehash: 9e93f07b3b84264373db0317919b6ee519c8127c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138054"
---
# <a name="foreground-and-background-threads"></a>Vlákna v popředí a v pozadí
Spravované vlákno je vlákno na pozadí nebo vlákno v popředí. Vlákna na pozadí jsou shodné s vlákny na popředí s jednou výjimkou: vlákno na pozadí neudržuje spuštěné prostředí spravovaného spuštění. Jakmile jsou všechna vlákna popředí zastavena ve spravovaném procesu (kde soubor EXE je spravované sestavení), systém zastaví všechna vlákna na pozadí a vypne se.  
  
> [!NOTE]
> Když zaběhu zastaví vlákno na pozadí, protože proces se vypíná, není vyvolána žádná výjimka ve vlákně. Však při podprocesů jsou <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> zastaveny, protože metoda <xref:System.Threading.ThreadAbortException> uvolní doménu aplikace, a je vyvolána v popředí a podprocesů na pozadí.  
  
 Pomocí <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> vlastnosti můžete určit, zda je vlákno podproces emblémem nebo podprocesem v popředí, nebo změnit jeho stav. Vlákno lze kdykoli změnit na vlákno na pozadí <xref:System.Threading.Thread.IsBackground%2A> nastavením jeho vlastnosti na `true`.  
  
> [!IMPORTANT]
> Stav popředí nebo pozadí vlákna nemá vliv na výsledek neošetřené výjimky ve vlákně. V rozhraní .NET Framework verze 2.0 neošetřené výjimky v popředí nebo podprocesy na pozadí má za následek ukončení aplikace. Viz [Výjimky ve spravovaných vláknech](../../../docs/standard/threading/exceptions-in-managed-threads.md).  
  
 Vlákna, která patří do fondu spravovaných <xref:System.Threading.Thread.IsThreadPoolThread%2A> vláken `true`(to znamená, že vlákna, jejichž vlastnost je ) jsou vlákna na pozadí. Všechna vlákna, která vstupují do prostředí spravovaného spuštění z nespravovaného kódu, jsou označena jako vlákna na pozadí. Všechna vlákna generovaná vytvořením <xref:System.Threading.Thread> a spuštěním nového objektu jsou ve výchozím nastavení vlákny v popředí.  
  
 Pokud používáte vlákno ke sledování aktivity, jako je <xref:System.Threading.Thread.IsBackground%2A> například připojení soketu, nastavte jeho vlastnost tak, aby `true` vlákno nebránilo ukončení procesu.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>
- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadAbortException>
