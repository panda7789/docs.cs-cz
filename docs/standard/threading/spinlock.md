---
title: SpinLock
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization primitives, SpinLock
ms.assetid: f9af93bb-7a0d-4ba5-afe8-74f48b6b6958
ms.openlocfilehash: eac9a1be38ea81e8ccee1d05d9061ceeb597627f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73106173"
---
# <a name="spinlock"></a>SpinLock
<xref:System.Threading.SpinLock> Struktura je základní synchronizace synchronizace nízké úrovně, vzájemné vyloučení, která se otáčí, zatímco čeká na získání zámku. V počítačích s více jádry, pokud se očekává, <xref:System.Threading.SpinLock> že čekací doby budou krátké a pokud je tvrzení minimální, může fungovat lépe než jiné druhy zámků. Doporučujeme však použít <xref:System.Threading.SpinLock> pouze v případě, že <xref:System.Threading.Monitor?displayProperty=nameWithType> určíte <xref:System.Threading.Interlocked> profilování, že metoda nebo metody výrazně zpomalují výkon programu.  
  
 <xref:System.Threading.SpinLock>může přinést časový úsek nitě, i když ještě nezískal zámek. Je to tak, aby se zabránilo inverze priority vlákna a povolit uvolňování systému k pokroku. Při použití <xref:System.Threading.SpinLock>, ujistěte se, že žádné vlákno může držet zámek pro více než velmi krátké časové rozpětí a že žádné vlákno může blokovat, zatímco drží zámek.  
  
 Protože SpinLock je typ hodnoty, musíte explicitně předat odkazem, pokud máte v úmyslu dvě kopie odkazovat na stejný zámek.  
  
 Další informace o použití tohoto typu <xref:System.Threading.SpinLock?displayProperty=nameWithType>naleznete v tématu . Příklad najdete v [tématu How to: Use SpinLock for Low-Level Sync](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md).  
  
 <xref:System.Threading.SpinLock>podporuje režim*sledování* *vláken,*-který můžete použít během fáze vývoje ke sledování podprocesu, který drží zámek v určitém čase. Režim sledování vláken je velmi užitečné pro ladění, ale doporučujeme jej vypnout ve verzi programu, protože může zpomalit výkon. Další informace naleznete v [tématu How to: Enable Thread-Tracking Mode in SpinLock](../../../docs/standard/threading/how-to-enable-thread-tracking-mode-in-spinlock.md).  
  
## <a name="see-also"></a>Viz také

- [Objekty a prvky zřetězení](../../../docs/standard/threading/threading-objects-and-features.md)
