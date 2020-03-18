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
ms.openlocfilehash: 33098878764c2f8a8c1f83a122028da40b984243
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73137965"
---
# <a name="how-to-synchronize-concurrent-operations-with-a-barrier"></a>Postupy: Synchronizace souběh operací pomocí bariéry
Následující příklad ukazuje, jak synchronizovat <xref:System.Threading.Barrier>souběžné úkoly s aplikací .  
  
## <a name="example"></a>Příklad  
 Účelem následujícího programu je spočítat, kolik iterací (nebo fází) je vyžadováno pro dvě vlákna, aby každá z nich našla svou polovinu řešení ve stejné fázi pomocí randomizačního algoritmu pro opětovné uspořádání slov. Poté, co každé vlákno zamíchá svá slova, bariéra po fázové operaci porovná dva výsledky, aby zjistila, zda byla celá věta vykreslena ve správném pořadí slov.  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 A <xref:System.Threading.Barrier> je objekt, který zabraňuje pokračování jednotlivých úloh v paralelní operaci, dokud všechny úkoly nedosáhnou bariéry. Je užitečné, když paralelní operace probíhá ve fázích a každá fáze vyžaduje synchronizaci mezi úkoly. V tomto příkladu existují dvě fáze operace. V první fázi každý úkol vyplní svou část vyrovnávací paměti daty. Po dokončení plnění každého úkolu úloha signalizuje bariéru, že je připravena pokračovat, a poté čeká. Když všechny úkoly signalizovaly bariéru, jsou odblokovány a druhá fáze začíná. Bariéra je nezbytná, protože druhá fáze vyžaduje, aby každý úkol měl přístup ke všem datům, která byla do tohoto okamžiku vygenerována. Bez bariéry první úkoly k dokončení může pokusit číst z vyrovnávacích pamětí, které nebyly vyplněny ještě jiné úkoly. Tímto způsobem můžete synchronizovat libovolný počet fází.  
  
## <a name="see-also"></a>Viz také

- [Datové struktury pro paralelní programování](../../../docs/standard/parallel-programming/data-structures-for-parallel-programming.md)
