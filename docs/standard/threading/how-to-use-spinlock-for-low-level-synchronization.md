---
title: 'Postupy: Použití SpinLock pro synchronizaci nízké úrovně'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinLock, how to use
ms.assetid: a9ed3e4e-4f29-4207-b730-ed0a51ecbc19
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 216480e893f6dbebbb204cbf2bfebae8dc139ec4
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44705424"
---
# <a name="how-to-use-spinlock-for-low-level-synchronization"></a>Postupy: Použití SpinLock pro synchronizaci nízké úrovně
Následující příklad ukazuje, jak používat <xref:System.Threading.SpinLock>.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu kritický oddíl provádí minimální množství práce, je vhodným kandidátem pro <xref:System.Threading.SpinLock>. Zvýšení práce s krátkým zvyšuje výkon <xref:System.Threading.SpinLock> oproti standardní zámku. Je však bod, ve kterém bude dražší než standardní zámek struktuře SpinLock. Pokud chcete zobrazit, jaký typ zámku poskytuje lepší výkon ve svém programu můžete použít funkce v nástrojích pro profilaci profilace souběžného zpracování. Další informace najdete v tématu [Vizualizátor souběžnosti](/visualstudio/profiling/concurrency-visualizer).  
  
 [!code-csharp[CDS_SpinLock#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#02)]
 [!code-vb[CDS_SpinLock#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_vb.vb#02)]  
  
 <xref:System.Threading.SpinLock> můžou být užitečné při zámek sdíleného prostředku není budete mít velmi dlouho. V takových případech na vícejádrových počítačích může být efektivnější blokovaná vlákna aktivovat pro několik cyklů, dokud se zámek je uvolněn. Která umožňuje, vlákno není stát blokované, což je proces náročnou na procesor. <xref:System.Threading.SpinLock> pokryjte za určitých podmínek, aby se zabránilo starvation logických procesorů nebo inverzi priority v systémech s technologií Hyper-Threading se zastaví.  
  
 V tomto příkladu <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> třídy, které vyžaduje synchronizaci uživatelů pro vícevláknový přístup. V aplikacích, které jsou cíleny rozhraní .NET Framework verze 4, Další možností je použít <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>, který nevyžaduje žádné uzamčení uživatele.  
  
 Všimněte si použití `false` (`False` v jazyce Visual Basic) při volání funkce <xref:System.Threading.SpinLock.Exit%2A>. To poskytuje nejlepší výkon. Zadejte `true` (`True`) na architektury IA64 používat ohrazení paměti, která vyprázdní vyrovnávací paměti zápis k zajištění, že zámek je teď k dispozici pro ostatní vlákna ukončíte.  
  
## <a name="see-also"></a>Viz také:

- [Funkce a objekty dělení na vlákna](../../../docs/standard/threading/threading-objects-and-features.md)
