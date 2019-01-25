---
title: SpinWait
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- synchronization primitives, SpinWait
ms.assetid: 36012f42-34e5-4f86-adf4-973f433ed6c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9b66ec913a6e8726710d90737f97c04335ae6e4f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54676429"
---
# <a name="spinwait"></a>SpinWait
<xref:System.Threading.SpinWait?displayProperty=nameWithType> je zjednodušené synchronizace typ, který můžete použít ve scénářích nízké úrovně, aby nákladné kontextu a přechody jádra, které jsou požadovány pro události jádra. Na vícejádrových počítačích když prostředek neočekává se bude vysílat pro dlouhou dobu, může být efektivnější pro čekání vlákno aktivovat v uživatelském režimu pro několik desítek nebo několik stovek cykly a pak zkuste získat prostředek. Pokud prostředek je k dispozici po pokryjte, jste uložili několik tisíc cyklů. Pokud je zdroj stále nejsou k dispozici, pak strávila pouze několik cyklů a můžete také zadat čekání na základě jádra. Tato kombinace pokryjte. potom čekání se někdy označuje jako *dvoufázové operace čekání*.  
  
 <xref:System.Threading.SpinWait> je určen pro použití ve spojení s typy rozhraní .NET Framework, které balí události jádra například <xref:System.Threading.ManualResetEvent>. <xref:System.Threading.SpinWait> lze také samostatně pro základní pokryjte funkce v jediné aplikaci.  
  
 <xref:System.Threading.SpinWait> je víc než jenom do prázdné smyčky. Pečlivě implementaci poskytnout správné pokryjte chování pro případ, obecné a samotné zahájí přepnutí kontextu pokud ho přede dostatečně dlouho (přibližně délka čas potřebný pro přechod jádra). Třeba na počítačích jedním jádrem <xref:System.Threading.SpinWait> vrací časovém intervalu vlákna okamžitě, protože pokryjte bloky dál probíhá na všech vláknech. <xref:System.Threading.SpinWait> také poskytuje i na vícejádrových počítačích zabránit vlákno čekání blokování vlákna s vyšší prioritou nebo systému uvolňování paměti. Proto pokud používáte <xref:System.Threading.SpinWait> v dvoufázové operace čekání, doporučujeme vyvolání jádra čekání před <xref:System.Threading.SpinWait> samotný zahájí přepnutí kontextu. <xref:System.Threading.SpinWait> poskytuje <xref:System.Threading.SpinWait.NextSpinWillYield%2A> vlastnost, která můžete zkontrolovat, že před všechna volání <xref:System.Threading.SpinWait.SpinOnce%2A>. Když vlastnost vrací `true`, zahájit operaci čekání. Příklad najdete v tématu [jak: Použití objektu SpinWait pro implementaci dvoufázové operace čekání](../../../docs/standard/threading/how-to-use-spinwait-to-implement-a-two-phase-wait-operation.md).  
  
 Pokud nejsou provádění dvoufázové operace čekání, ale jsou právě zprovozňování, dokud je splněna některá podmínka, můžete povolit <xref:System.Threading.SpinWait> provádět jeho kontextu přepnout, kde je dobré občanem v prostředí operačního systému Windows. Následující základní příklad ukazuje <xref:System.Threading.SpinWait> v zásobníku bez zámku. Pokud budete potřebovat zásobníku vysoce výkonné, bezpečná pro vlákno, zvažte použití <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType>.  
  
 [!code-csharp[CDS_SpinWait#05](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait.cs#05)]
 [!code-vb[CDS_SpinWait#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/cds_spinwait1.vb#05)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Thread.SpinWait%2A>
- [Funkce a objekty dělení na vlákna](../../../docs/standard/threading/threading-objects-and-features.md)
