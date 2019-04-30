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
ms.openlocfilehash: c6605fa1923dc4fdaf4f12a7c8fc7c1e344673b5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925369"
---
# <a name="foreground-and-background-threads"></a>Vlákna v popředí a v pozadí
Spravované vlákno je vlákno na pozadí nebo vlákno na popředí. Vlákna na pozadí jsou shodné s vlákna na popředí s jednou výjimkou: vlákno na pozadí neudržuje spravovaném spouštěcím prostředí spuštění. Po ukončení všech vláken v popředí v spravovaného procesu (kde soubor .exe je spravovaná sestavení) systému všechna vlákna na pozadí se zastaví a ukončí.  
  
> [!NOTE]
>  Když modul runtime zastaví vlákna na pozadí, protože proces se vypíná, není vyvolána žádná výjimka ve vlákně. Ale když vlákna se zastavila, protože <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> metoda uvolnění domény aplikace <xref:System.Threading.ThreadAbortException> je vyvolána v popředí a pozadí podprocesů.  
  
 Použití <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> vlastnosti k určení, zda je vlákno na pozadí nebo vlákno na popředí nebo na změnu stavu. Vlákno lze změnit na vlákně na pozadí v každém okamžiku nastavením jeho <xref:System.Threading.Thread.IsBackground%2A> vlastnost `true`.  
  
> [!IMPORTANT]
>  Popředí nebo pozadí stav vlákna nemá vliv na výsledek neošetřené výjimce ve vlákně. V rozhraní .NET Framework verze 2.0 neošetřené výjimky v popředí nebo pozadí vláken výsledkem ukončení aplikace. Zobrazit [výjimky ve spravovaných vláknech](../../../docs/standard/threading/exceptions-in-managed-threads.md).  
  
 Vlákna, které patří do spravovaný fond vláken (to znamená, jehož vlákna <xref:System.Threading.Thread.IsThreadPoolThread%2A> vlastnost `true`) jsou vlákna na pozadí. Všechna vlákna, zadejte spravovaném spouštěcím prostředí z nespravovaného kódu jsou označeny jako vláken na pozadí. Všechna vlákna generovaných vytváření a spouštění nového <xref:System.Threading.Thread> objektu jsou ve výchozí vláken v popředí.  
  
 Pokud použijete vlákno k monitorování aktivity, jako je například připojení soketu, nastavte jeho <xref:System.Threading.Thread.IsBackground%2A> vlastnost `true` tak, aby vlákno nebrání váš proces se ukončuje.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>
- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadAbortException>
