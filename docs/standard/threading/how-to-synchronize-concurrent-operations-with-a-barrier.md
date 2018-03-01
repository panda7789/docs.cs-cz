---
title: "Postupy: Synchronizace souběh operací pomocí bariéry"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Barrier, how to use
ms.assetid: e1a253ff-e0fb-4df8-95ff-d01a90d4cb19
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 616229abed93c6793b392724d038d8f9160cd6ae
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-synchronize-concurrent-operations-with-a-barrier"></a>Postupy: Synchronizace souběh operací pomocí bariéry
Následující příklad ukazuje, jak synchronizovat souběžné úlohy s <xref:System.Threading.Barrier>.  
  
## <a name="example"></a>Příklad  
 Účelem následující program je počítat se jak velký počet iterací (nebo fáze) vyžadovaných pro dvěma vlákny na každý najít jejich polovině řešení v fázi stejné pomocí randomizing algoritmus Chcete-li změnit pořadí slova. Po každé vlákno je na nesprávním místě jeho slova, porovná operaci po fáze bariéry oba výsledky, které chcete zobrazit, pokud bylo ve správném pořadí word vykresleno kompletní věta.  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 A <xref:System.Threading.Barrier> je objekt, který brání jednotlivé úkoly v rámci paralelní operace pokračovat, dokud všechny úlohy nezobrazí bariéry. Je užitečná při paralelní operace probíhá ve fázích a jednotlivé fáze vyžaduje synchronizaci mezi úkoly. V tomto příkladu jsou dvě fáze pro operaci. Každý úkol v první fázi doplní jeho části vyrovnávací paměti s daty. Když každý úkol dokončí naplnění jeho části, úloha signály bariéry, který je připraven k pokračovat a potom počká. Pokud všechny úlohy mají signalizovala bariéry, jsou odblokuje a spustí druhé fáze. Bariéry je nutné, protože druhé fáze vyžaduje, aby každý úkol měl přístup ke všem datům, která byla vygenerována k tomuto bodu. Bez bariéry může první na dokončení úloh pokusit číst z vyrovnávací paměti, které nebyly vyplněno ještě další věci. Můžete synchronizovat libovolný počet fáze tímto způsobem.  
  
## <a name="see-also"></a>Viz také  
 [Datové struktury pro paralelní programování](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)
