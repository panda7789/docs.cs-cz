---
title: SpinLock
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization primitives, SpinLock
ms.assetid: f9af93bb-7a0d-4ba5-afe8-74f48b6b6958
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5bd2468c7b68a9c79e7418a32294676fb468e1a9
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44042631"
---
# <a name="spinlock"></a>SpinLock
<xref:System.Threading.SpinLock> Struktury je nižší úrovně, vyloučeného primitiv synchronizace, který otáčí během čekání na získání zámku. Na vícejádrových počítačích po očekávané době čekání bude krátký a pokud je minimální, kolize <xref:System.Threading.SpinLock> může mít lepší výkon než jiné druhy zámků. Doporučujeme však, že používáte <xref:System.Threading.SpinLock> pouze při zjišťování pomocí Profilování, která <xref:System.Threading.Monitor?displayProperty=nameWithType> metoda nebo <xref:System.Threading.Interlocked> metody jsou výrazně zpomalení výkonu aplikace.  
  
 <xref:System.Threading.SpinLock> může přinést časovém intervalu vlákna, i v případě, že nezískal ještě zámek. Dělá to aby se zabránilo inverzi priorita vlákna a umožňuje systému uvolňování paměti pokroku. Při použití <xref:System.Threading.SpinLock>, ujistěte se, že žádné vlákno může obsahovat zámek pro více než velmi krátké časové období, a že žádné vlákno může blokovat, když drží zámek.  
  
 Protože SpinLock je typ hodnoty, musí explicitně předání odkazem. Pokud máte v úmyslu dvě kopie odkazovat na stejnou zámku.  
  
 Další informace o tom, jak pomocí tohoto typu, najdete v části <xref:System.Threading.SpinLock?displayProperty=nameWithType>. Příklad najdete v tématu [postupy: použití SpinLock nižší úrovně synchronizace](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md).  
  
 <xref:System.Threading.SpinLock> podporuje *vlákno*-*sledování* režimu, můžete ve fázi vývoje, chcete-li sledovat vlákna, které drží zámek v určitém čase. Režimu sledování vláken je velmi užitečné pro ladění, ale doporučujeme vám, že vy ji vypnete ve vydané verzi programu protože to může snížit výkon. Další informace najdete v tématu [postupy: povolení vlákno sledování režimu ve struktuře SpinLock](../../../docs/standard/threading/how-to-enable-thread-tracking-mode-in-spinlock.md).  
  
## <a name="see-also"></a>Viz také:

- [Funkce a objekty dělení na vlákna](../../../docs/standard/threading/threading-objects-and-features.md)
