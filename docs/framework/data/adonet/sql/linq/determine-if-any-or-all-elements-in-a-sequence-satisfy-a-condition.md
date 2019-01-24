---
title: Pokud některé nebo všechny elementy v sekvenci vyhovují podmínce
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 339ec145-826c-46d2-8cf2-3acd252cd072
ms.openlocfilehash: d3c343d3cf5068e473efbd62de019a25cf19dc10
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54702571"
---
# <a name="determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition"></a>Pokud některé nebo všechny elementy v sekvenci vyhovují podmínce
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
