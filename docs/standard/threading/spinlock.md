---
title: SpinLock
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization primitives, SpinLock
ms.assetid: f9af93bb-7a0d-4ba5-afe8-74f48b6b6958
ms.openlocfilehash: a5202be5e3055702954ad7a1565999ad2496eaea
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291120"
---
# <a name="spinlock"></a>SpinLock
<xref:System.Threading.SpinLock>Struktura je základní a vzájemně vyloučená synchronizační operace, která se při čekání na získání zámku. U vícejádrových počítačů, pokud se očekává, že čekací časy budou krátké a když je spory minimální, může docházet k <xref:System.Threading.SpinLock> lepšímu výkonu než jiné druhy zámků. Nicméně doporučujeme, abyste používali <xref:System.Threading.SpinLock> pouze v případě, že určíte profilování, že <xref:System.Threading.Monitor?displayProperty=nameWithType> Metoda nebo <xref:System.Threading.Interlocked> metody výrazně zpomalují výkon programu.  
  
 <xref:System.Threading.SpinLock>může vracet časový úsek vlákna i v případě, že ještě zámek nezískal. Dělá to tak, aby nedocházelo k inverze priority vlákna, a aby systém uvolňování paměti mohl provádět. Když použijete <xref:System.Threading.SpinLock> , zajistěte, aby žádné vlákno nemohlo uchovávat zámek více než velmi krátkého časového rozsahu a že se žádné vlákno nemůže blokovat, pokud zámek drží.  
  
 Vzhledem k tomu, že struktuře SpinLock je hodnotový typ, je nutné explicitně předat odkaz, pokud chcete, aby tyto dvě kopie odkazovaly na stejný zámek.  
  
 Další informace o tom, jak tento typ použít, naleznete v tématu <xref:System.Threading.SpinLock?displayProperty=nameWithType> . Příklad naleznete v tématu [How to: use struktuře SpinLock for the low-level Synchronization](how-to-use-spinlock-for-low-level-synchronization.md).  
  
 <xref:System.Threading.SpinLock>podporuje režim *thread* - *sledování* vláken, který můžete použít během fáze vývoje, abyste mohli sledovat vlákno, které drží zámek v určitou dobu. Režim sledování vlákna je velmi užitečný pro ladění, ale doporučujeme, abyste ho ve verzi programu vypnuli, protože může zpomalit výkon. Další informace najdete v tématu [Postup: povolení režimu sledování vláken v struktuře SpinLock](how-to-enable-thread-tracking-mode-in-spinlock.md).  
  
## <a name="see-also"></a>Viz také

- [Dělení objektů a funkcí](threading-objects-and-features.md)
