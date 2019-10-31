---
title: 'Postupy: použití struktuře SpinLock pro synchronizaci nízké úrovně'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinLock, how to use
ms.assetid: a9ed3e4e-4f29-4207-b730-ed0a51ecbc19
ms.openlocfilehash: ad254cb6208bff868e5fc689c502b7ddcc175ad5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137958"
---
# <a name="how-to-use-spinlock-for-low-level-synchronization"></a>Postupy: použití struktuře SpinLock pro synchronizaci nízké úrovně

Následující příklad ukazuje, jak použít <xref:System.Threading.SpinLock>. V tomto příkladu kritická část provádí minimální množství práce, což je dobrým kandidátem na <xref:System.Threading.SpinLock>. Zvýšení práce: malá hodnota zvyšuje výkon <xref:System.Threading.SpinLock> v porovnání se standardním zámkem. Existuje však bod, ve kterém se struktuře SpinLock stala dražší než standardní zámek. Pomocí funkce profilace souběžného zpracování v nástrojích pro profilaci můžete zjistit, který typ zámku poskytuje lepší výkon v programu. Další informace najdete v tématu [Vizualizátor souběžnosti](/visualstudio/profiling/concurrency-visualizer).  
  
 [!code-csharp[CDS_SpinLock#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#02)]
 [!code-vb[CDS_SpinLock#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_vb.vb#02)]  
  
 <xref:System.Threading.SpinLock> může být užitečné, když se zámek sdíleného prostředku nebude uchovávat moc dlouho. V takových případech může být pro počítače s více jádry efektivní, aby se blokované vlákno rozmíchoval na několik cyklů, dokud se zámek neuvolní. Po odstřeďování se vlákno neblokuje, což je proces náročný na procesor. <xref:System.Threading.SpinLock> zastaví za určitých podmínek, aby nedocházelo k vyčerpáníí logických procesorů nebo prioritních inverze v systémech pomocí technologie Hyper-Threading.  
  
 V tomto příkladu se používá třída <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>, která vyžaduje synchronizaci uživatelů při přístupu s více vlákny. V aplikacích, které cílí na .NET Framework verze 4, je další možností použití <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>, která nevyžaduje žádné zámky uživatelů.  
  
 Všimněte si použití `false` (`False` v Visual Basic) ve volání <xref:System.Threading.SpinLock.Exit%2A?displayProperty=nameWithType>. Tím se dosáhne nejlepšího výkonu. Určete `true` (`True` v Visual Basic) na architektuřeech IA64 pro použití vyrovnávací paměti, která vyprázdní vyrovnávací paměti pro zápis, aby se zajistilo, že je zámek k dispozici pro ukončení jiných vláken.  
  
## <a name="see-also"></a>Viz také:

- [Dělení objektů a funkcí](threading-objects-and-features.md)
- [Lock – příkazC#()](../../csharp/language-reference/keywords/lock-statement.md)
- [Příkaz SyncLock (Visual Basic)](../../visual-basic/language-reference/statements/synclock-statement.md)
