---
title: 'Postupy: Synchronizace souběh operací pomocí bariéry'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Barrier, how to use
ms.assetid: e1a253ff-e0fb-4df8-95ff-d01a90d4cb19
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 16dc60fa9cd8782efbe1b6028413138b5991839e
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44078805"
---
# <a name="how-to-synchronize-concurrent-operations-with-a-barrier"></a>Postupy: Synchronizace souběh operací pomocí bariéry
Následující příklad ukazuje, jak synchronizovat souběžné úkoly se <xref:System.Threading.Barrier>.  
  
## <a name="example"></a>Příklad  
 Účelem následující program se mají spočítat, kolik iterací (nebo fáze) jsou vyžadovaných pro dvěma vlákny na každé hledání své polovině řešení v stejné fázi pomocí algoritmu randomizing změnit pořadí slova. Po každé vlákno má které se náhodně pomíchají jeho slova, porovnává operaci po fázi barrier dva výsledky zobrazíte, pokud bylo ve správném pořadí slov vykresleno kompletní věta.  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 A <xref:System.Threading.Barrier> je objekt, který brání jednotlivé úkoly v rámci paralelní operace pokračovat, dokud všechny úkoly nezobrazí odbourejte překážky bránící. To je užitečné, když paralelní operace probíhá ve fázích a jednotlivé fáze vyžaduje synchronizaci mezi úkoly. V tomto příkladu existují dvě fáze operace. Každý úkol v první fázi, vyplní její části vyrovnávací paměti s daty. Když každý úkol dokončí, naplnění jeho části, úloha signály barrier, která bude chtít pokračovat a potom počká. Když všechny úlohy mají signalizován bariéry, se odblokuje a spustí druhé fáze. Odbourejte překážky bránící je nezbytné, protože druhé fáze vyžaduje, aby každý úkol mají přístup ke všem datům generovaný do tohoto bodu. Bez bariéry může první úkoly k dokončení pokusí číst z vyrovnávací paměti, které nebyly byl vyplněn ještě další úkoly. Libovolný počet fází tímto způsobem můžete synchronizovat.  
  
## <a name="see-also"></a>Viz také:

- [Datové struktury pro paralelní programování](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)
