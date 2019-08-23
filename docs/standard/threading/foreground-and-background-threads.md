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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8dbad5da42f5ed4e03751534a3a183615a9757cc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960024"
---
# <a name="foreground-and-background-threads"></a>Vlákna v popředí a v pozadí
Spravované vlákno je vlákno na pozadí nebo vlákno na popředí. Vlákna na pozadí jsou shodná s vlákny na popředí s jednou výjimkou: vlákno na pozadí neudržuje spravované prostředí pro spuštění. Jakmile jsou všechna vlákna na popředí zastavena ve spravovaném procesu (kde soubor. exe je spravované sestavení), systém zastaví všechna vlákna na pozadí a ukončí činnost.  
  
> [!NOTE]
> Když modul runtime zastaví vlákno na pozadí, protože probíhá ukončování procesu, ve vlákně není vyvolána žádná výjimka. Nicméně při zastavení vlákna, protože <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> metoda uvolní aplikační doménu <xref:System.Threading.ThreadAbortException> , je vyvolána v vláknech v popředí i na pozadí.  
  
 <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> Pomocí vlastnosti určíte, zda je vlákno pozadí nebo vlákno na popředí nebo zda chcete změnit jeho stav. Vlákno lze kdykoli změnit na vlákno na pozadí nastavením jeho <xref:System.Threading.Thread.IsBackground%2A> vlastnosti na `true`hodnotu.  
  
> [!IMPORTANT]
> Stav popředí nebo pozadí vlákna nemá vliv na výsledek neošetřené výjimky ve vlákně. V .NET Framework verze 2,0 způsobí Neošetřená výjimka v obou vláknech popředí nebo na pozadí ukončení aplikace. Viz [výjimky ve spravovaných vláknech](../../../docs/standard/threading/exceptions-in-managed-threads.md).  
  
 Vlákna, která patří do spravovaného fondu vláken (tj. vlákna, <xref:System.Threading.Thread.IsThreadPoolThread%2A> jejichž vlastnost `true`je), jsou vlákna na pozadí. Všechna vlákna, která vstupují do spravovaného prostředí pro spuštění z nespravovaného kódu, jsou označena jako vlákna na pozadí. Všechna vlákna vygenerovaná vytvořením a spuštěním nového <xref:System.Threading.Thread> objektu jsou ve výchozím nastavení vlákna na popředí.  
  
 Použijete-li vlákno k monitorování aktivity, jako je například připojení soketu, nastavte jeho <xref:System.Threading.Thread.IsBackground%2A> vlastnost na `true` tak, aby vlákno nebránilo ukončení procesu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>
- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadAbortException>
