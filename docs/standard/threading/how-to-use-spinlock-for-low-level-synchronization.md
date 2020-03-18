---
title: 'Postup: použití SpinLocku pro nízkoúrovňovou synchronizaci'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinLock, how to use
ms.assetid: a9ed3e4e-4f29-4207-b730-ed0a51ecbc19
ms.openlocfilehash: ad254cb6208bff868e5fc689c502b7ddcc175ad5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73137958"
---
# <a name="how-to-use-spinlock-for-low-level-synchronization"></a>Postup: použití SpinLocku pro nízkoúrovňovou synchronizaci

Následující příklad ukazuje, jak <xref:System.Threading.SpinLock>používat . V tomto příkladu kritické části provádí minimální množství práce, což <xref:System.Threading.SpinLock>je dobrým kandidátem pro . Zvýšení práce malé množství zvyšuje výkon <xref:System.Threading.SpinLock> ve srovnání se standardní zámek. Existuje však bod, ve kterém SpinLock stane dražší než standardní zámek. Můžete použít funkce profilování souběžnosti v nástrojích profilování, abyste zjistili, který typ zámku poskytuje lepší výkon v programu. Další informace naleznete v tématu [Vizualizér souběžnosti](/visualstudio/profiling/concurrency-visualizer).  
  
 [!code-csharp[CDS_SpinLock#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#02)]
 [!code-vb[CDS_SpinLock#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_vb.vb#02)]  
  
 <xref:System.Threading.SpinLock>může být užitečné, pokud zámek sdíleného prostředku nebude uchováván příliš dlouho. V takových případech může být v počítačích s více jádry efektivní, aby se blokované vlákno otáčelo několik cyklů, dokud není zámek uvolněn. Odstřeďováním vlákno není blokováno, což je proces náročný na procesor. <xref:System.Threading.SpinLock>za určitých podmínek přestane točit, aby se zabránilo hladovění logických procesorů nebo prioritní inverzi v systémech s hyper-threadingem.  
  
 Tento příklad <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> používá třídu, která vyžaduje synchronizaci uživatelů pro přístup s více vlákny. V aplikacích, které cílí na rozhraní .NET <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>Framework verze 4, je další možností použití rozhraní , které nevyžaduje žádné zámky uživatelů.  
  
 Všimněte si `false` `False` použití ( v jazyce <xref:System.Threading.SpinLock.Exit%2A?displayProperty=nameWithType>Visual Basic) ve volání . To poskytuje nejlepší výkon. `true` Zadejte`True` ( v jazyce Visual Basic) na architektury IA64 použít plot paměti, která vyprázdní vyrovnávací paměti pro zápis zajistit, že zámek je nyní k dispozici pro ostatní vlákna k ukončení.  
  
## <a name="see-also"></a>Viz také

- [Dělení objektů a funkcí na vlákna](threading-objects-and-features.md)
- [příkaz lock (C#)](../../csharp/language-reference/keywords/lock-statement.md)
- [SyncLock, příkaz (Visual Basic)](../../visual-basic/language-reference/statements/synclock-statement.md)
