---
title: Určení, jestli některé nebo všechny prvky v posloupnosti vyhovují podmínce
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 339ec145-826c-46d2-8cf2-3acd252cd072
ms.openlocfilehash: 7de65579cb41641aded0b9a320fac59804959ff5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782228"
---
# <a name="determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition"></a>Určení, jestli některé nebo všechny prvky v posloupnosti vyhovují podmínce
<xref:System.Linq.Enumerable.All%2A> Operátor vrátí`true` , pokud všechny prvky v sekvenci splní podmínku.  
  
 <xref:System.Linq.Queryable.Any%2A> Operátor vrátí`true` , pokud kterýkoli prvek v sekvenci splňuje podmínku.  
  
## <a name="example"></a>Příklad  
 Následující příklad vrátí posloupnost zákazníků, které mají alespoň jednu objednávku. `Where` `Customer` `Order`Klauzule je vyhodnocena ,`true` Pokud má daný výsledek nějaký. / `where`  
  
 [!code-csharp[DLinqQueryExamples#37](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#37)]
 [!code-vb[DLinqQueryExamples#37](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37)]  
  
## <a name="example"></a>Příklad  
 Následující kód Visual Basic určuje seznam zákazníků, kteří si neumístili objednávky, a zajišťují, že pro každého zákazníka v tomto seznamu je zadáno jméno kontaktu.  
  
 [!code-vb[DLinqQueryExamples#37v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37v)]  
  
## <a name="example"></a>Příklad  
 Následující C# příklad vrací sekvenci zákazníků, jejichž objednávky začínají na `ShipCity` "C". Také zahrnuté v návratu jsou zákazníci, kteří nemají žádné objednávky. (Podle návrhu <xref:System.Linq.Queryable.All%2A> operátor vrátí `true` prázdnou sekvenci.) Zákazníci bez objednávek se v výstupu konzoly eliminují pomocí `Count` operátoru.  
  
 [!code-csharp[DLinqQueryExamples#38](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#38)]  
  
## <a name="see-also"></a>Viz také:

- [Příklady dotazů](query-examples.md)
