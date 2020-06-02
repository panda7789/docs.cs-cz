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
ms.openlocfilehash: 1a46655530948bb8732362dbd6d86ead495b0998
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279527"
---
# <a name="how-to-enable-thread-tracking-mode-in-spinlock"></a>Postupy: Povolení režimu sledování vláken ve struktuře SpinLock
<xref:System.Threading.SpinLock?displayProperty=nameWithType>je vzájemný zámek vzájemného vyloučení, který můžete použít pro scénáře s velmi krátkými čekacími časy. <xref:System.Threading.SpinLock>není znovu vstupující. Po vložení vlákna do zámku musí být zámek správně ukončen, než bude možné ho znovu zadat. Každý pokus o opětovné zadání zámku by obvykle způsobil zablokování a zablokování může být pro ladění velmi obtížné. Jako pomůcka pro vývoj <xref:System.Threading.SpinLock?displayProperty=nameWithType> podporuje režim sledování vláken, který způsobí, že výjimka bude vyvolána, když se vlákno pokusí znovu zadat zámek, který už je uložený. To vám umožní snadněji najít bod, ve kterém se zámek neukončil správně. Režim sledování vláken lze zapnout pomocí <xref:System.Threading.SpinLock> konstruktoru, který přebírá logický vstupní parametr, a předáním argumentu `true` . Po dokončení fází vývoje a testování vypněte režim sledování vláken pro lepší výkon.  
  
## <a name="example"></a>Příklad  
 Následující příklad znázorňuje režim sledování vláken. Řádky, které správně ukončí zámek, jsou zakomentovány, aby se simulovala Chyba kódování, která způsobuje jednu z následujících výsledků:  
  
- Pokud <xref:System.Threading.SpinLock> byl vytvořen pomocí argumentu `true` ( `True` v Visual Basic), je vyvolána výjimka.  
  
- Zablokování, pokud <xref:System.Threading.SpinLock> byl vytvořen pomocí argumentu `false` ( `False` v Visual Basic).  
  
 [!code-csharp[CDS_SpinLock#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#01)]
 [!code-vb[CDS_SpinLock#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_threadtracking.vb#01)]  
  
## <a name="see-also"></a>Viz také

- [SpinLock](spinlock.md)
