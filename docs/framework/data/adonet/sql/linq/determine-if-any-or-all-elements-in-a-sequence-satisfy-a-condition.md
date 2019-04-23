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
# <a name="determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition"></a><span data-ttu-id="d6215-102">Určení, jestli některé nebo všechny prvky v posloupnosti vyhovují podmínce</span><span class="sxs-lookup"><span data-stu-id="d6215-102">Determine if Any or All Elements in a Sequence Satisfy a Condition</span></span>
<span data-ttu-id="d6215-103"><xref:System.Linq.Enumerable.All%2A> Operátor vrátí `true` Pokud všechny prvky v sekvenci splňují podmínku.</span><span class="sxs-lookup"><span data-stu-id="d6215-103">The <xref:System.Linq.Enumerable.All%2A> operator returns `true` if all elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="d6215-104"><xref:System.Linq.Queryable.Any%2A> Operátor vrátí `true` Pokud libovolný prvek v sekvenci splňuje podmínku.</span><span class="sxs-lookup"><span data-stu-id="d6215-104">The <xref:System.Linq.Queryable.Any%2A> operator returns `true` if any element in a sequence satisfies a condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6215-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="d6215-105">Example</span></span>  
 <span data-ttu-id="d6215-106">Následující příklad vrátí sekvenci zákazníky, kteří mají alespoň jednu objednávku.</span><span class="sxs-lookup"><span data-stu-id="d6215-106">The following example returns a sequence of customers that have at least one order.</span></span> <span data-ttu-id="d6215-107">`Where` / `where` Vyhodnotí jako klauzuli `true` -li daného `Customer` obsahuje některý `Order`.</span><span class="sxs-lookup"><span data-stu-id="d6215-107">The `Where`/`where` clause evaluates to `true` if the given `Customer` has any `Order`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#37](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#37)]
 [!code-vb[DLinqQueryExamples#37](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37)]  
  
## <a name="example"></a><span data-ttu-id="d6215-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="d6215-108">Example</span></span>  
 <span data-ttu-id="d6215-109">Následující kód jazyka Visual Basic určuje seznam zákazníků, kteří nejsou umístěny objednávky a zajistí, že pro každý zákazník v tomto seznamu jméno kontaktní osoby je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="d6215-109">The following Visual Basic code determines the list of customers who have not placed orders, and ensures that for every customer in that list, a contact name is provided.</span></span>  
  
 [!code-vb[DLinqQueryExamples#37v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37v)]  
  
## <a name="example"></a><span data-ttu-id="d6215-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="d6215-110">Example</span></span>  
 <span data-ttu-id="d6215-111">Následující C# příkladu vrátí sekvenci zákazníků, jejichž objednávky `ShipCity` počínaje "C".</span><span class="sxs-lookup"><span data-stu-id="d6215-111">The following C# example returns a sequence of customers whose orders have a `ShipCity` beginning with "C".</span></span> <span data-ttu-id="d6215-112">Obsahuje taky návratový jsou zákazníci, kteří mají žádné objednávky.</span><span class="sxs-lookup"><span data-stu-id="d6215-112">Also included in the return are customers who have no orders.</span></span> <span data-ttu-id="d6215-113">(Podle návrhu, <xref:System.Linq.Queryable.All%2A> operátor vrátí `true` pro prázdnou sekvencí.) Zákazníci s žádné objednávky se eliminovala ve výstupu konzoly pomocí `Count` operátor.</span><span class="sxs-lookup"><span data-stu-id="d6215-113">(By design, the <xref:System.Linq.Queryable.All%2A> operator returns `true` for an empty sequence.) Customers with no orders are eliminated in the console output by using the `Count` operator.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#38](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="d6215-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d6215-114">See also</span></span>

- [<span data-ttu-id="d6215-115">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="d6215-115">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
