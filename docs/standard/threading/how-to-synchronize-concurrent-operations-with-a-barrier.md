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
ms.openlocfilehash: 2e13dfb277807eb0a9f256f74c2845f5a4d2a047
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279294"
---
# <a name="how-to-synchronize-concurrent-operations-with-a-barrier"></a>Postupy: Synchronizace souběh operací pomocí bariéry
Následující příklad ukazuje, jak synchronizovat souběžné úlohy s <xref:System.Threading.Barrier> .  
  
## <a name="example"></a>Příklad  
 Účelem následujícího programu je zjistit, kolik iterací (nebo fází) se vyžaduje pro dvě vlákna při hledání jejich poloviny řešení ve stejné fázi pomocí náhodného algoritmu k opakovanému rozmísení slov. Poté, co každé vlákno přeruší svá slova, porovná operace po fázi povýšení těchto dvou výsledků, aby bylo možné zjistit, zda byla úplná věta vykreslena ve správném textovém pořadí.  
  
 [!code-csharp[CDS_Barrier#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_barrier/cs/barrier.cs#01)]
 [!code-vb[CDS_Barrier#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_barrier/vb/barrier_vb.vb#01)]  
  
 A <xref:System.Threading.Barrier> je objekt, který brání jednotlivým úlohám v paralelní operaci pokračovat, dokud všechny úlohy nedosáhnou bariéry. Je užitečné v případě, že dojde k paralelní operaci ve fázích a každá fáze vyžaduje synchronizaci mezi úlohami. V tomto příkladu existují dvě fáze operace. V první fázi každý úkol vyplní svou část vyrovnávací paměti daty. Když každý úkol dokončí vyplňování oddílu, úloha signalizuje bariéru, že je připravená k pokračování, a potom počká. Když všechny úlohy signalizují bariéru, odblokuje se a druhá fáze se spustí. Bariéra je nezbytná, protože druhá fáze vyžaduje, aby každý úkol měl přístup ke všem datům, která byla vygenerována do tohoto bodu. Bez bariéry se může první dokončený úkol pokusit přečíst z vyrovnávacích pamětí, které ještě nejsou vyplněné jinými úkoly. Tímto způsobem můžete synchronizovat libovolný počet fází.  
  
## <a name="see-also"></a>Viz také

- [Datové struktury pro paralelní programování](../parallel-programming/data-structures-for-parallel-programming.md)
