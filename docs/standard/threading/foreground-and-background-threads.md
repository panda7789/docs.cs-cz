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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138054"
---
# <a name="foreground-and-background-threads"></a>Vlákna v popředí a v pozadí
Spravované vlákno je vlákno na pozadí nebo vlákno na popředí. Vlákna na pozadí jsou shodná s vlákny na popředí s jednou výjimkou: vlákno na pozadí neudržuje spravované prostředí pro spuštění. Jakmile jsou všechna vlákna na popředí zastavena ve spravovaném procesu (kde soubor. exe je spravované sestavení), systém zastaví všechna vlákna na pozadí a ukončí činnost.  
  
> [!NOTE]
> Když modul runtime zastaví vlákno na pozadí, protože probíhá ukončování procesu, ve vlákně není vyvolána žádná výjimka. Nicméně při zastavení vlákna, protože metoda <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> uvolní doménu aplikace, <xref:System.Threading.ThreadAbortException> je vyvolána v podprocesech popředí a na pozadí.  
  
 Pomocí vlastnosti <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> určete, zda je vlákno pozadí nebo vlákno na popředí nebo zda má být změněn stav. Vlákno lze kdykoli změnit na vlákno na pozadí nastavením jeho vlastnosti <xref:System.Threading.Thread.IsBackground%2A> na hodnotu `true`.  
  
> [!IMPORTANT]
> Stav popředí nebo pozadí vlákna nemá vliv na výsledek neošetřené výjimky ve vlákně. V .NET Framework verze 2,0 způsobí Neošetřená výjimka v obou vláknech popředí nebo na pozadí ukončení aplikace. Viz [výjimky ve spravovaných vláknech](../../../docs/standard/threading/exceptions-in-managed-threads.md).  
  
 Vlákna, která patří do spravovaného fondu vláken (to znamená, vlákna, jejichž vlastnost <xref:System.Threading.Thread.IsThreadPoolThread%2A> je `true`), jsou vlákna na pozadí. Všechna vlákna, která vstupují do spravovaného prostředí pro spuštění z nespravovaného kódu, jsou označena jako vlákna na pozadí. Všechna vlákna generovaná vytvořením a spuštěním nového objektu <xref:System.Threading.Thread> jsou ve výchozím nastavení vlákna na popředí.  
  
 Pokud používáte vlákno k monitorování aktivity, například připojení soketu, nastavte jeho vlastnost <xref:System.Threading.Thread.IsBackground%2A> na `true`, aby vlákno nebránilo procesu ukončení.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>
- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadAbortException>
