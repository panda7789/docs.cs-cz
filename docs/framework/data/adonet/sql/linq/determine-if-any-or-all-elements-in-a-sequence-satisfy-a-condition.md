---
title: Určení, jestli některé nebo všechny prvky v posloupnosti vyhovují podmínce
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 339ec145-826c-46d2-8cf2-3acd252cd072
ms.openlocfilehash: c1bc8e18f2e3b0c67b98713e67fc261649a6a0e2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59128333"
---
# <a name="determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition"></a>Určení, jestli některé nebo všechny prvky v posloupnosti vyhovují podmínce
<xref:System.Linq.Enumerable.All%2A> Operátor vrátí `true` Pokud všechny prvky v sekvenci splňují podmínku.  
  
 <xref:System.Linq.Queryable.Any%2A> Operátor vrátí `true` Pokud libovolný prvek v sekvenci splňuje podmínku.  
  
## <a name="example"></a>Příklad  
 Následující příklad vrátí sekvenci zákazníky, kteří mají alespoň jednu objednávku. `Where` / `where` Vyhodnotí jako klauzuli `true` -li daného `Customer` obsahuje některý `Order`.  
  
 [!code-csharp[DLinqQueryExamples#37](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#37)]
 [!code-vb[DLinqQueryExamples#37](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37)]  
  
## <a name="example"></a>Příklad  
 Následující kód jazyka Visual Basic určuje seznam zákazníků, kteří nejsou umístěny objednávky a zajistí, že pro každý zákazník v tomto seznamu jméno kontaktní osoby je k dispozici.  
  
 [!code-vb[DLinqQueryExamples#37v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37v)]  
  
## <a name="example"></a>Příklad  
 Následující C# příkladu vrátí sekvenci zákazníků, jejichž objednávky `ShipCity` počínaje "C". Obsahuje taky návratový jsou zákazníci, kteří mají žádné objednávky. (Podle návrhu, <xref:System.Linq.Queryable.All%2A> operátor vrátí `true` pro prázdnou sekvencí.) Zákazníci s žádné objednávky se eliminovala ve výstupu konzoly pomocí `Count` operátor.  
  
 [!code-csharp[DLinqQueryExamples#38](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#38)]  
  
## <a name="see-also"></a>Viz také:

- [Příklady dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
