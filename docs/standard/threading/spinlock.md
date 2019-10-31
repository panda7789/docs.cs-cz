---
title: SpinLock
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization primitives, SpinLock
ms.assetid: f9af93bb-7a0d-4ba5-afe8-74f48b6b6958
ms.openlocfilehash: eac9a1be38ea81e8ccee1d05d9061ceeb597627f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73106173"
---
# <a name="spinlock"></a>SpinLock
Struktura <xref:System.Threading.SpinLock> je základní, vzájemně vyloučená synchronizační primitiva, která se při čekání na získání zámku. U vícejádrových počítačů, pokud se očekává, že čekací časy budou krátké a když je spory minimální, může <xref:System.Threading.SpinLock> provádět lepší fungování než jiné druhy zámků. Doporučujeme však použít <xref:System.Threading.SpinLock> pouze v případě, že určíte profilování, že metoda <xref:System.Threading.Monitor?displayProperty=nameWithType> nebo <xref:System.Threading.Interlocked> metody výrazně zpomaluje výkon programu.  
  
 <xref:System.Threading.SpinLock> může vracet časové období vlákna i v případě, že ještě zámek nezískal. Dělá to tak, aby nedocházelo k inverze priority vlákna, a aby systém uvolňování paměti mohl provádět. Když použijete <xref:System.Threading.SpinLock>, zajistěte, aby žádné vlákno nemohlo uchovávat zámek více než velmi krátkého časového intervalu a aby se žádné vlákno neblokovalo při blokování zámku.  
  
 Vzhledem k tomu, že struktuře SpinLock je hodnotový typ, je nutné explicitně předat odkaz, pokud chcete, aby tyto dvě kopie odkazovaly na stejný zámek.  
  
 Další informace o tom, jak tento typ použít, naleznete v tématu <xref:System.Threading.SpinLock?displayProperty=nameWithType>. Příklad naleznete v tématu [How to: use struktuře SpinLock for the low-level Synchronization](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md).  
  
 <xref:System.Threading.SpinLock> podporuje režim *sledování*-*vláken* , který můžete použít během fáze vývoje, abyste mohli sledovat vlákno, které drží zámek v určitou dobu. Režim sledování vlákna je velmi užitečný pro ladění, ale doporučujeme, abyste ho ve verzi programu vypnuli, protože může zpomalit výkon. Další informace najdete v tématu [Postup: povolení režimu sledování vláken v struktuře SpinLock](../../../docs/standard/threading/how-to-enable-thread-tracking-mode-in-spinlock.md).  
  
## <a name="see-also"></a>Viz také:

- [Funkce a objekty dělení na vlákna](../../../docs/standard/threading/threading-objects-and-features.md)
