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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f3b9671c10889287bc22d64df1fb5c3a2984bd55
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44195277"
---
# <a name="how-to-enable-thread-tracking-mode-in-spinlock"></a>Postupy: Povolení režimu sledování vláken ve struktuře SpinLock
<xref:System.Threading.SpinLock?displayProperty=nameWithType> je nízké úrovně vzájemné vyloučení zámek, který můžete použít pro scénáře, které mají velmi krátké čekací dobu. <xref:System.Threading.SpinLock> není vícenásobně. Poté, co vlákno zadá zámek, ho ukončíte zámek správně předtím, než můžete znovu zadat. Obvykle jakékoli pokusy o potvrzení zámek by způsobila zablokování a zablokování může být velmi obtížné ladit. Jako vodítko k vývoji <xref:System.Threading.SpinLock?displayProperty=nameWithType> podporuje režimu sledování vláken, která způsobí výjimku, která je vyvolána, když vlákno se pokusí znovu zadejte zámek, který již obsahuje. To umožňuje více snadno najít bod, ve kterém zámek nebyl ukončen správně. Můžete zapnout režimu sledování vláken pomocí <xref:System.Threading.SpinLock> konstruktor, který přebírá logickou hodnotu vstupní parametr a předávání argument `true`. Po dokončení vývojové a testovací fázi se vypněte režimu sledování vláken pro zajištění lepšího výkonu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje režimu sledování vláken. Řádky, které správně ukončení uzamčení jsou označené jako komentář pro simulaci chyby kódu, který způsobí, že jeden z následujících výsledků:  
  
-   Pokud je vyvolána výjimka <xref:System.Threading.SpinLock> bylo vytvořeno s použitím argument `true` (`True` v jazyce Visual Basic).  
  
-   Vzájemné zablokování, pokud <xref:System.Threading.SpinLock> bylo vytvořeno s použitím argument `false` (`False` v jazyce Visual Basic).  
  
 [!code-csharp[CDS_SpinLock#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#01)]
 [!code-vb[CDS_SpinLock#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_threadtracking.vb#01)]  
  
## <a name="see-also"></a>Viz také:

- [SpinLock](../../../docs/standard/threading/spinlock.md)
