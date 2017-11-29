---
title: SpinLock
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: synchronization primitives, SpinLock
ms.assetid: f9af93bb-7a0d-4ba5-afe8-74f48b6b6958
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: efe9b3126b3c952ab156f9ca40752ad8d3fddcd1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="spinlock"></a>SpinLock
<xref:System.Threading.SpinLock> Struktura je nízké úrovně, vzájemné vyloučení synchronizaci primitivní, otáčí během čekání na získání zámku. Na počítači, vícejádrovými, když se očekává, dobu čekání být krátké a pokud je minimální, kolizí <xref:System.Threading.SpinLock> můžete provádět lépe než jiné druhy zámky. Doporučujeme však používat <xref:System.Threading.SpinLock> pouze, když určíte profilace, který <xref:System.Threading.Monitor?displayProperty=nameWithType> metoda nebo <xref:System.Threading.Interlocked> metody jsou výrazně zpomalení výkonu vašeho programu.  
  
 <xref:System.Threading.SpinLock>může yield časového intervalu vlákna, i když ho ještě nebyla získat zámek. Dělá to předejdete prioritu podprocesu inverzi a umožňuje uvolňování pokračovat. Při použití <xref:System.Threading.SpinLock>, ujistěte se, že žádný přístup z více vláken může obsahovat zámek pro více než velmi krátké časové období a že žádný přístup z více vláken můžete blokovat, když drží zámek.  
  
 Protože SpinLock je typ hodnoty, je nutné explicitně předat ji odkazem Pokud máte v úmyslu dvě kopie odkazovat na stejné zámek.  
  
 Další informace o tom, jak pomocí tohoto typu najdete v tématu <xref:System.Threading.SpinLock?displayProperty=nameWithType>. Příklad, naleznete v části [postupy: použití SpinLock pro synchronizaci nižší úrovně](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md).  
  
 <xref:System.Threading.SpinLock>podporuje *vlákno*-*sledování* režim, který můžete použít během fáze vývoje k usnadnění sledování vláken, která nastavila zámek v určitém čase. Režimu sledování vláken je velmi užitečná pro ladění, ale doporučujeme vypnout ho ve verzi vašeho programu vzhledem k tomu může zpomalit výkon. Další informace najdete v tématu [postupy: povolení vlákna sledování režimu ve struktuře SpinLock](../../../docs/standard/threading/how-to-enable-thread-tracking-mode-in-spinlock.md).  
  
## <a name="see-also"></a>Viz také  
 [Dělení na vlákna objektů a funkcí](../../../docs/standard/threading/threading-objects-and-features.md)
