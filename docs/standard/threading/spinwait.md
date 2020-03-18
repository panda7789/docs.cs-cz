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
ms.openlocfilehash: 91588fc6e9c3c8e85de6a315c0743efb0137ecd5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73128988"
---
# <a name="spinwait"></a>SpinWait
<xref:System.Threading.SpinWait?displayProperty=nameWithType>je zjednodušený typ synchronizace, který můžete použít ve scénářích nižší úrovně, abyste se vyhnuli drahým přepnutím kontextu a přechodům jádra, které jsou vyžadovány pro události jádra. V počítačích s více jádry, pokud se neočekává, že prostředek bude držen po dlouhou dobu, může být efektivnější pro čekající vlákno, které se může otáčet v uživatelském režimu po dobu několika desítek nebo několika set cyklů a pak se znovu pokusit získat prostředek. Pokud je zdroj k dispozici po odstřeďování, pak jste uložili několik tisíc cyklů. Pokud prostředek stále není k dispozici, pak jste strávili pouze několik cyklů a stále můžete zadat čekání na základě jádra. Tato kombinace spinning-then-waiting se někdy označuje jako *dvoufázová čekací operace*.  
  
 <xref:System.Threading.SpinWait>je určen k použití ve spojení s typy rozhraní .NET Framework, které zalamují události jádra, například <xref:System.Threading.ManualResetEvent>. <xref:System.Threading.SpinWait>lze také použít sám o sobě pro základní funkce spřádání pouze v jednom programu.  
  
 <xref:System.Threading.SpinWait>je víc než jen prázdná smyčka. Je pečlivě implementována tak, aby poskytovala správné chování při odstřeďování pro obecný případ, a sama zahájí přepnutí kontextu, pokud se otáčí dostatečně dlouho (zhruba doba potřebná pro přechod jádra). Například v počítačích s <xref:System.Threading.SpinWait> jedním jádrem poskytuje časový úsek vlákna okamžitě, protože předení blokuje průběh vpřed ve všech vláknech. <xref:System.Threading.SpinWait>také poskytuje i na vícejádrových počítačích, aby se zabránilo čekání vlákno blokování podprocesů s vyšší prioritou nebo uvolňování paměti. Proto pokud používáte <xref:System.Threading.SpinWait> v operaci dvoufázové čekání, doporučujeme vyvolat čekání <xref:System.Threading.SpinWait> jádra před sám zahájí přepínač kontextu. <xref:System.Threading.SpinWait>poskytuje <xref:System.Threading.SpinWait.NextSpinWillYield%2A> vlastnost, kterou můžete zkontrolovat před <xref:System.Threading.SpinWait.SpinOnce%2A>každým voláním do . Když se `true`vrátí vlastnost , iniciujte vlastní operaci Čekání. Příklad najdete v [tématu How to: Use SpinWait to Implement a Two-Phase Wait Operation](../../../docs/standard/threading/how-to-use-spinwait-to-implement-a-two-phase-wait-operation.md).  
  
 Pokud neprovádíte dvoufázové čekání operace, ale jsou jen spinning, dokud <xref:System.Threading.SpinWait> některé podmínky je pravda, můžete povolit provádět jeho přepnutí kontextu tak, aby je dobrým občanem v prostředí operačního systému Windows. Následující základní příklad <xref:System.Threading.SpinWait> ukazuje v zásobníku bez zámku. Pokud požadujete vysoce výkonný zásobník bezpečný pro <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType>přístup z více vláken, zvažte použití .  
  
 [!code-csharp[CDS_SpinWait#05](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait.cs#05)]
 [!code-vb[CDS_SpinWait#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/cds_spinwait1.vb#05)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Threading.Thread.SpinWait%2A>
- [Objekty a prvky zřetězení](../../../docs/standard/threading/threading-objects-and-features.md)
