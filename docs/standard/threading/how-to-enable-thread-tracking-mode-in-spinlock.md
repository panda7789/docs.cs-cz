---
title: 'Postupy: Povolení režimu sledování vláken ve struktuře SpinLock'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinLock, how to enable thread-tracking
ms.assetid: 62ee2e68-0bdd-4869-afc9-f0a57a11ae01
ms.openlocfilehash: f52a844284cf46bcace3f54f8b320d336050a64e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138037"
---
# <a name="how-to-enable-thread-tracking-mode-in-spinlock"></a>Postupy: Povolení režimu sledování vláken ve struktuře SpinLock
<xref:System.Threading.SpinLock?displayProperty=nameWithType> je vzájemný zámek pro vzájemné vyloučení, který můžete použít pro scénáře s velmi krátkými čekacími časy. <xref:System.Threading.SpinLock> není znovu vstupující. Po vložení vlákna do zámku musí být zámek správně ukončen, než bude možné ho znovu zadat. Každý pokus o opětovné zadání zámku by obvykle způsobil zablokování a zablokování může být pro ladění velmi obtížné. Jako pomůcka pro vývoj <xref:System.Threading.SpinLock?displayProperty=nameWithType> podporuje režim sledování vláken, který způsobí vyvolání výjimky, když se vlákno pokusí znovu zadat zámek, který už je uložený. To vám umožní snadněji najít bod, ve kterém se zámek neukončil správně. Režim sledování vláken lze zapnout pomocí <xref:System.Threading.SpinLock> konstruktoru, který přebírá logický vstupní parametr a je v argumentu `true`. Po dokončení fází vývoje a testování vypněte režim sledování vláken pro lepší výkon.  
  
## <a name="example"></a>Příklad  
 Následující příklad znázorňuje režim sledování vláken. Řádky, které správně ukončí zámek, jsou zakomentovány, aby se simulovala Chyba kódování, která způsobuje jednu z následujících výsledků:  
  
- Pokud byl <xref:System.Threading.SpinLock> vytvořen pomocí argumentu `true` (`True` v Visual Basic), je vyvolána výjimka.  
  
- Zablokování, pokud byl <xref:System.Threading.SpinLock> vytvořen pomocí argumentu `false` (`False` v Visual Basic).  
  
 [!code-csharp[CDS_SpinLock#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#01)]
 [!code-vb[CDS_SpinLock#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_threadtracking.vb#01)]  
  
## <a name="see-also"></a>Viz také:

- [SpinLock](../../../docs/standard/threading/spinlock.md)
