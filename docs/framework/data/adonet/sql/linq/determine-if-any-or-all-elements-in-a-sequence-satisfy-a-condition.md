---
title: Určit, zda některé nebo všechny elementy v pořadí nesplňuje podmínku
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 339ec145-826c-46d2-8cf2-3acd252cd072
ms.openlocfilehash: cd910b35f82f816158cb686a283e44e3b8b6b33b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33359969"
---
# <a name="determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition"></a><span data-ttu-id="8a181-102">Určit, zda některé nebo všechny elementy v pořadí nesplňuje podmínku</span><span class="sxs-lookup"><span data-stu-id="8a181-102">Determine if Any or All Elements in a Sequence Satisfy a Condition</span></span>
<span data-ttu-id="8a181-103"><xref:System.Linq.Enumerable.All%2A> Vrátí operátor `true` Pokud všechny elementy v pořadí splňují podmínku.</span><span class="sxs-lookup"><span data-stu-id="8a181-103">The <xref:System.Linq.Enumerable.All%2A> operator returns `true` if all elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="8a181-104"><xref:System.Linq.Queryable.Any%2A> Vrátí operátor `true` Pokud libovolný prvek v pořadí splňuje podmínku.</span><span class="sxs-lookup"><span data-stu-id="8a181-104">The <xref:System.Linq.Queryable.Any%2A> operator returns `true` if any element in a sequence satisfies a condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a181-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="8a181-105">Example</span></span>  
 <span data-ttu-id="8a181-106">Následující příklad vrací posloupnost zákazníků, kteří mají alespoň jednu objednávku.</span><span class="sxs-lookup"><span data-stu-id="8a181-106">The following example returns a sequence of customers that have at least one order.</span></span> <span data-ttu-id="8a181-107">`Where` / `where` Klauzule se vyhodnocuje `true` Pokud v dané `Customer` obsahuje některý `Order`.</span><span class="sxs-lookup"><span data-stu-id="8a181-107">The `Where`/`where` clause evaluates to `true` if the given `Customer` has any `Order`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#37](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#37)]
 [!code-vb[DLinqQueryExamples#37](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37)]  
  
## <a name="example"></a><span data-ttu-id="8a181-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="8a181-108">Example</span></span>  
 <span data-ttu-id="8a181-109">Následující kód jazyka Visual Basic určuje seznamu zákazníků, kteří nejsou umístěny objednávky a zajišťuje, že pro každý zákazník v tomto seznamu, jméno kontaktní osoby je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="8a181-109">The following Visual Basic code determines the list of customers who have not placed orders, and ensures that for every customer in that list, a contact name is provided.</span></span>  
  
 [!code-vb[DLinqQueryExamples#37v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37v)]  
  
## <a name="example"></a><span data-ttu-id="8a181-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="8a181-110">Example</span></span>  
 <span data-ttu-id="8a181-111">Následující příklad jazyka C# vrací posloupnost zákazníků, jejichž objednávky mají `ShipCity` počínaje "C".</span><span class="sxs-lookup"><span data-stu-id="8a181-111">The following C# example returns a sequence of customers whose orders have a `ShipCity` beginning with "C".</span></span> <span data-ttu-id="8a181-112">Také součástí návratový jsou zákazníci, kteří nemají žádnou objednávku.</span><span class="sxs-lookup"><span data-stu-id="8a181-112">Also included in the return are customers who have no orders.</span></span> <span data-ttu-id="8a181-113">(Standardně <xref:System.Linq.Queryable.All%2A> vrátí operátor `true` pro prázdnou sekvencí.) Zákazníci bez objednávek se eliminovala ve výstupu konzoly pomocí `Count` operátor.</span><span class="sxs-lookup"><span data-stu-id="8a181-113">(By design, the <xref:System.Linq.Queryable.All%2A> operator returns `true` for an empty sequence.) Customers with no orders are eliminated in the console output by using the `Count` operator.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#38](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="8a181-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="8a181-114">See Also</span></span>  
 [<span data-ttu-id="8a181-115">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="8a181-115">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
