---
title: Stavy spravovaných vláken
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], states
ms.assetid: 63890d5e-6025-4a7c-aaf0-d8bfd54b455f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a55409cd2c3bed2bc09db10622de1cceab934112
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46287647"
---
# <a name="managed-thread-states"></a>Stavy spravovaných vláken
Vlastnost <xref:System.Threading.Thread.ThreadState%2A?displayProperty=nameWithType> poskytuje bitová maska, která označuje aktuální stav vlákna. Vlákno je vždy alespoň jedním z možných stavů v <xref:System.Threading.ThreadState> výčtu a může být ve více státech ve stejnou dobu.  
  
> [!IMPORTANT]
>  Stav vlákna je pouze relevantní v několika ladění scénářů. Váš kód byste nikdy neměli používat stav vlákna pro synchronizaci činností vlákna.  
  
 Při vytváření spravované vlákno je v <xref:System.Threading.ThreadState.Unstarted> stavu. Vlákno zůstává ve <xref:System.Threading.ThreadState.Unstarted> stavu, dokud nebude přesunuta do stavu spuštěno v operačním systému. Volání <xref:System.Threading.Thread.Start%2A> umožňuje operačního systému vědět, že vlákno může být spuštěna; nezmění stav vlákna.  
  
 Nespravovaná vlákna, zadejte spravované prostředí jsou již ve spuštěném stavu. Jakmile vlákno je ve spuštěném stavu, akcí může způsobit, že chcete-li změnit stavy. V následující tabulce jsou uvedeny akce, které způsobit změnu stavu, společně s odpovídající nový stav.  
  
|Akce|Výsledný nový stav|  
|------------|-------------------------|  
|Konstruktor pro <xref:System.Threading.Thread> třída se nazývá.|<xref:System.Threading.ThreadState.Unstarted>|  
|Jiné vlákno hovory <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.Unstarted>|  
|Vlákna jsou reaguje na <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> a spuštění.|<xref:System.Threading.ThreadState.Running>|  
|Vlákno vyvolá <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|Vlákno vyvolá <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> na jiný objekt.|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|Vlákno vyvolá <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> v jiném vlákně.|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|Jiné vlákno hovory <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.SuspendRequested>|  
|Vlákno odpovídá <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> požadavku.|<xref:System.Threading.ThreadState.Suspended>|  
|Jiné vlákno hovory <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.Running>|  
|Jiné vlákno hovory <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.AbortRequested>|  
|Vlákna jsou reaguje na <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.Aborted>, pak <xref:System.Threading.ThreadState.Stopped>|  
  
 Vzhledem k tomu, <xref:System.Threading.ThreadState.Running> stavu má hodnotu 0, není možné provést test bit zjistit tento stav. Místo toho je možné použít následující testovací (v pseudo kód):  
  
```  
if ((state & (Unstarted | Stopped)) == 0)   // implies Running     
```  
  
 Vlákna jsou ve více než jeden stavu v daném okamžiku často. Například, pokud je vlákno blokováno <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> volání a jiné vlákno použije <xref:System.Threading.Thread.Abort%2A> ve stejném vlákně, vlákno bude v obou <xref:System.Threading.ThreadState.WaitSleepJoin> a <xref:System.Threading.ThreadState.AbortRequested> stavů ve stejnou dobu. V takovém případě nejdříve podproces vrací z volání <xref:System.Threading.Monitor.Wait%2A> nebo je přerušeno, se zobrazí <xref:System.Threading.ThreadAbortException>.  
  
 Jakmile opustí vlákno <xref:System.Threading.ThreadState.Unstarted> stavu jako výsledek volání <xref:System.Threading.Thread.Start%2A>, nikdy mohli vrátit k <xref:System.Threading.ThreadState.Unstarted> stavu. Vlákno může nikdy neopustí <xref:System.Threading.ThreadState.Stopped> stavu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.ThreadAbortException>  
- <xref:System.Threading.Thread>  
- <xref:System.Threading.ThreadState>  
- [Dělení na vlákna](../../../docs/standard/threading/index.md)
