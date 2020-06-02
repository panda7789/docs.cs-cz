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
ms.openlocfilehash: 5e7ec9e2c2a5ba3de1b4518cea15eb5f512640d3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279682"
---
# <a name="foreground-and-background-threads"></a>Vlákna v popředí a v pozadí
Spravované vlákno je vlákno na pozadí nebo vlákno na popředí. Vlákna na pozadí jsou shodná s vlákny na popředí s jednou výjimkou: vlákno na pozadí neudržuje spravované prostředí pro spuštění. Jakmile jsou všechna vlákna na popředí zastavena ve spravovaném procesu (kde soubor. exe je spravované sestavení), systém zastaví všechna vlákna na pozadí a ukončí činnost.  
  
> [!NOTE]
> Když modul runtime zastaví vlákno na pozadí, protože probíhá ukončování procesu, ve vlákně není vyvolána žádná výjimka. Nicméně při zastavení vlákna, protože <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> metoda uvolní aplikační doménu, <xref:System.Threading.ThreadAbortException> je vyvolána v vláknech v popředí i na pozadí.  
  
 Pomocí <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> vlastnosti určíte, zda je vlákno pozadí nebo vlákno na popředí nebo zda chcete změnit jeho stav. Vlákno lze kdykoli změnit na vlákno na pozadí nastavením jeho <xref:System.Threading.Thread.IsBackground%2A> vlastnosti na hodnotu `true` .  
  
> [!IMPORTANT]
> Stav popředí nebo pozadí vlákna nemá vliv na výsledek neošetřené výjimky ve vlákně. V .NET Framework verze 2,0 způsobí Neošetřená výjimka v obou vláknech popředí nebo na pozadí ukončení aplikace. Viz [výjimky ve spravovaných vláknech](exceptions-in-managed-threads.md).  
  
 Vlákna, která patří do spravovaného fondu vláken (tj. vlákna, jejichž <xref:System.Threading.Thread.IsThreadPoolThread%2A> vlastnost je `true` ), jsou vlákna na pozadí. Všechna vlákna, která vstupují do spravovaného prostředí pro spuštění z nespravovaného kódu, jsou označena jako vlákna na pozadí. Všechna vlákna vygenerovaná vytvořením a spuštěním nového <xref:System.Threading.Thread> objektu jsou ve výchozím nastavení vlákna na popředí.  
  
 Použijete-li vlákno k monitorování aktivity, jako je například připojení soketu, nastavte jeho <xref:System.Threading.Thread.IsBackground%2A> vlastnost na `true` tak, aby vlákno nebránilo ukončení procesu.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>
- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadAbortException>
