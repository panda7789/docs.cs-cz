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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138037"
---
# <a name="how-to-enable-thread-tracking-mode-in-spinlock"></a>Postupy: Povolení režimu sledování vláken ve struktuře SpinLock
<xref:System.Threading.SpinLock?displayProperty=nameWithType>je zámek vzájemného vyloučení nižší úrovně, který můžete použít pro scénáře, které mají velmi krátké čekací doby. <xref:System.Threading.SpinLock>není znovu účastníkem. Poté, co vlákno vstoupí do zámku, musí zámek před znovu zadat. Obvykle jakýkoli pokus o opětovné zadání zámku by způsobit zablokování a zablokování může být velmi obtížné ladit. Jako pomůcku pro vývoj podporuje režim sledování vláken, který způsobí, že výjimka má být vyvolána, když se vlákno pokusí znovu zadat zámek, <xref:System.Threading.SpinLock?displayProperty=nameWithType> který již obsahuje. To umožňuje snadněji vyhledat bod, ve kterém zámek nebyl ukončen správně. Můžete zapnout režim sledování vláken <xref:System.Threading.SpinLock> pomocí konstruktoru, který přebírá logický vstupní parametr `true`a předávání maješku argumentu . Po dokončení fáze vývoje a testování vypněte režim sledování vláken pro lepší výkon.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje režim sledování vláken. Řádky, které správně ukončit zámek jsou zakomentovány, aby simulovaly chybu kódování, která způsobuje jeden z následujících výsledků:  
  
- Výjimka je vyvolána, <xref:System.Threading.SpinLock> pokud byl vytvořen `true` `True` pomocí argumentu (v jazyce Visual Basic).  
  
- Zablokování, pokud <xref:System.Threading.SpinLock> byl vytvořen pomocí `false` argumentu (`False` v jazyce Visual Basic).  
  
 [!code-csharp[CDS_SpinLock#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#01)]
 [!code-vb[CDS_SpinLock#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_threadtracking.vb#01)]  
  
## <a name="see-also"></a>Viz také

- [SpinLock](../../../docs/standard/threading/spinlock.md)
