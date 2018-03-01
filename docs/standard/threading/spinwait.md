---
title: SpinWait
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- synchronization primitives, SpinWait
ms.assetid: 36012f42-34e5-4f86-adf4-973f433ed6c6
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 1e67dd59464de09a35941d91ef984db6b7779b8c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="spinwait"></a>SpinWait
<xref:System.Threading.SpinWait?displayProperty=nameWithType>je typ zjednodušené synchronizace, můžete použít ve scénářích nízké úrovně, aby se zabránilo nákladné kontextu přepínače a přechody jádra, které jsou požadovány pro události kernel. Na počítačích vícejádrovými když prostředek neočekává se, že uchovávat po delší dobu, může být efektivnější pro čekání na vlákno číselníku v uživatelském režimu pro několik set desítek nebo několik cyklů a poté opakujte získat prostředek. Pokud daný prostředek k dispozici po roztočený, byla uložena několik cyklů tisíců. Pokud prostředek je stále není k dispozici, pak jste utratili jenom několik cyklů a stále zadat čekání základě jádra. Tato kombinace roztočený. potom čekání se někdy označuje jako *dvoufázové operace čekání*.  
  
 <xref:System.Threading.SpinWait>je určen k použití ve spojení s typy rozhraní .NET Framework, které balí události kernel například <xref:System.Threading.ManualResetEvent>. <xref:System.Threading.SpinWait>lze také samostatně pro základní roztočený funkce pouze jedné aplikace.  
  
 <xref:System.Threading.SpinWait>je více než jen smyčky prázdný. Je pečlivě implementovaný zajistit správné roztočený chování pro případ, obecné a sám zahájí kontext přepínače pokud ho otáčí dostatečně dlouho (přibližně délka čas potřebný pro přechod jádra). Například v počítačích jedním jádrem <xref:System.Threading.SpinWait> vypočítá časového intervalu vlákna okamžitě, protože roztočený bloky předávat průběh na všechna vlákna. <xref:System.Threading.SpinWait>také poskytuje i na počítače s více jádry zabránit blokování vláken s vyšší prioritou nebo má systém uvolňování čekání na vlákno. Proto pokud používáte <xref:System.Threading.SpinWait> v dvoufázové operace čekání, doporučujeme vyvolání jádra čekání před <xref:System.Threading.SpinWait> samotné zahájí kontext přepínače. <xref:System.Threading.SpinWait>poskytuje <xref:System.Threading.SpinWait.NextSpinWillYield%2A> vlastnosti, která můžete zkontrolovat před každé volání <xref:System.Threading.SpinWait.SpinOnce%2A>. Pokud vlastnost vrací `true`, inicializace vlastní operace čekání. Příklad, naleznete v části [postupy: použití objektu SpinWait implementovat operaci čekat na dvoufázový](../../../docs/standard/threading/how-to-use-spinwait-to-implement-a-two-phase-wait-operation.md).  
  
 Pokud nejsou provádění dvoufázové operace čekání, ale jsou právě otáčet, dokud nebude nějaká podmínka true, můžete povolit <xref:System.Threading.SpinWait> provést jeho kontextu přepne tak, aby se dobrý občanem v prostředí operačního systému Windows. Následující základní příklad ukazuje <xref:System.Threading.SpinWait> v zásobníku se uvolnění zámku. Pokud budete potřebovat zásobníku vysoce výkonné, bezpečné pro přístup z více vláken, zvažte použití <xref:System.Collections.Concurrent.ConcurrentStack%601?displayProperty=nameWithType>.  
  
 [!code-csharp[CDS_SpinWait#05](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait.cs#05)]
 [!code-vb[CDS_SpinWait#05](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/cds_spinwait1.vb#05)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Threading.Thread.SpinWait%2A>  
 [Funkce a objekty dělení na vlákna](../../../docs/standard/threading/threading-objects-and-features.md)
