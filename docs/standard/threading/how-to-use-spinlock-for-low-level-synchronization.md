---
title: "Postupy: Použití SpinLock pro synchronizaci nízké úrovně"
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
helpviewer_keywords: SpinLock, how to use
ms.assetid: a9ed3e4e-4f29-4207-b730-ed0a51ecbc19
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 30ddc7d340b210aaad4a04ea43e89555d2701f20
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-use-spinlock-for-low-level-synchronization"></a>Postupy: Použití SpinLock pro synchronizaci nízké úrovně
Následující příklad ukazuje, jak používat <xref:System.Threading.SpinLock>.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu kritická sekce provede minimální množství práce, což usnadňuje vhodným kandidátem <xref:System.Threading.SpinLock>. Zvýšení práce malou zvyšuje výkon <xref:System.Threading.SpinLock> ve srovnání s standardní zámku. Je však bod, ve kterém bude SpinLock dražší než standardní zámku. Profilace funkce v nástrojích pro profilaci souběžného zpracování můžete zobrazit, jaký typ zámku poskytuje lepší výkon v programu. Další informace najdete v tématu [vizualizér souběžnosti](/visualstudio/profiling/concurrency-visualizer).  
  
 [!code-csharp[CDS_SpinLock#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#02)]
 [!code-vb[CDS_SpinLock#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_vb.vb#02)]  
  
 <xref:System.Threading.SpinLock>můžou být užitečné při uzamčení sdíleného prostředku není budete mít velmi náročná. V takových případech na počítačích s více jádry může být efektivní pro blokované vlákno k číselníku po několik cyklů, dokud se uvolní zámek. Podle roztočený, vlákno stane neblokován, což je proces náročná na prostředky procesoru. <xref:System.Threading.SpinLock>Zastaví roztočený za určitých podmínek, aby se zabránilo nedostatku prostředků logických procesorů nebo v inverzi priority na systémy s technologií Hyper-Threading.  
  
 Tento příklad používá <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> třídy, která vyžaduje synchronizaci uživatelů pro vícevláknové přístup. V aplikacích, které cílí na rozhraní .NET Framework verze 4, Další možností je použít <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>, který nevyžaduje žádné uživatele zámky.  
  
 Všimněte si použití `false` (`False` v jazyce Visual Basic) ve volání <xref:System.Threading.SpinLock.Exit%2A>. To poskytuje nejlepší výkon. Zadejte `true` (`True`) na architektury IA64 používat ochranná paměti, která vyprázdní vyrovnávací paměti zápisu zajistit, že zámek je nyní k dispozici pro další vlákna ukončíte.  
  
## <a name="see-also"></a>Viz také  
 [Dělení na vlákna objektů a funkcí](../../../docs/standard/threading/threading-objects-and-features.md)
