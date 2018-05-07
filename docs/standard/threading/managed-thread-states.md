---
title: Stavy spravovaných vláken
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], states
ms.assetid: 63890d5e-6025-4a7c-aaf0-d8bfd54b455f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4266aea9bf206d127e2837955dcc00cc23f4119b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="managed-thread-states"></a>Stavy spravovaných vláken
Vlastnost <xref:System.Threading.Thread.ThreadState%2A?displayProperty=nameWithType> poskytuje bitová maska určující, aktuální stav vlákna. Vlákno je vždy alespoň v jedné z možných stavů v <xref:System.Threading.ThreadState> výčtu a může být ve více státech ve stejnou dobu.  
  
> [!IMPORTANT]
>  Stav vlákna je pouze zájem o několik ladění scénáře. Váš kód by měl stav vlákna nikdy používat k synchronizaci aktivity vláken.  
  
 Když vytvoříte spravované vlákno, je v <xref:System.Threading.ThreadState.Unstarted> stavu. Vlákno zůstane v <xref:System.Threading.ThreadState.Unstarted> stavu, dokud je přesunut do spuštěného stavu v operačním systému. Volání metody <xref:System.Threading.Thread.Start%2A> umožňuje operační systém vědět, že lze spustit vlákno; nezmění stav vlákno.  
  
 Nespravované vláken, která zadejte spravované prostředí jsou již ve stavu spuštěna. Jakmile vlákno spuštěného stavu, může způsobit několik akcí změnit stavy. V následující tabulce jsou uvedeny akce, které způsobit změnu stavu, spolu s odpovídající nový stav.  
  
|Akce|Výsledný nový stav|  
|------------|-------------------------|  
|V konstruktoru pro <xref:System.Threading.Thread> třídy se nazývá.|<xref:System.Threading.ThreadState.Unstarted>|  
|Jiné vlákno volání <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.Unstarted>|  
|Vlákno odpoví na <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> a spuštění.|<xref:System.Threading.ThreadState.Running>|  
|Přístup z více vláken volání <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|Přístup z více vláken volání <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> na jiném objektu.|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|Přístup z více vláken volání <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> na jiné vlákno.|<xref:System.Threading.ThreadState.WaitSleepJoin>|  
|Jiné vlákno volání <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.SuspendRequested>|  
|Vlákno odpoví <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> požadavku.|<xref:System.Threading.ThreadState.Suspended>|  
|Jiné vlákno volání <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.Running>|  
|Jiné vlákno volání <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.AbortRequested>|  
|Vlákno odpoví <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType>.|<xref:System.Threading.ThreadState.Aborted>, pak <xref:System.Threading.ThreadState.Stopped>|  
  
 Protože <xref:System.Threading.ThreadState.Running> stavu má hodnotu 0, není možné provést bit test ke zjištění tento stav. Místo toho se dají použít následující testovací (v pseudo kód):  
  
```  
if ((state & (Unstarted | Stopped)) == 0)   // implies Running     
```  
  
 Vlákna jsou ve více než jeden stavu v každém okamžiku často. Například, pokud vlákno je na zablokovaný <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> volání a jiného vlákna volání <xref:System.Threading.Thread.Abort%2A> v daném vláknu stejné vlákno bude v obou <xref:System.Threading.ThreadState.WaitSleepJoin> a <xref:System.Threading.ThreadState.AbortRequested> stavy ve stejnou dobu. V takovém případě také vlákno vrátí z volání <xref:System.Threading.Monitor.Wait%2A> nebo přerušit, se zobrazí <xref:System.Threading.ThreadAbortException>.  
  
 Jakmile opustí vlákna <xref:System.Threading.ThreadState.Unstarted> stavu v důsledku volání <xref:System.Threading.Thread.Start%2A>, se nikdy může vrátit do <xref:System.Threading.ThreadState.Unstarted> stavu. Vlákno můžete nikdy neopustí <xref:System.Threading.ThreadState.Stopped> stavu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Threading.ThreadAbortException>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadState>  
 [Dělení na vlákna](../../../docs/standard/threading/index.md)
