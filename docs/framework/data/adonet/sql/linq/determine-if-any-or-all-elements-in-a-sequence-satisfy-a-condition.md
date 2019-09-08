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
# <a name="determine-if-any-or-all-elements-in-a-sequence-satisfy-a-condition"></a><span data-ttu-id="40a14-102">Určení, jestli některé nebo všechny prvky v posloupnosti vyhovují podmínce</span><span class="sxs-lookup"><span data-stu-id="40a14-102">Determine if Any or All Elements in a Sequence Satisfy a Condition</span></span>
<span data-ttu-id="40a14-103"><xref:System.Linq.Enumerable.All%2A> Operátor vrátí`true` , pokud všechny prvky v sekvenci splní podmínku.</span><span class="sxs-lookup"><span data-stu-id="40a14-103">The <xref:System.Linq.Enumerable.All%2A> operator returns `true` if all elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="40a14-104"><xref:System.Linq.Queryable.Any%2A> Operátor vrátí`true` , pokud kterýkoli prvek v sekvenci splňuje podmínku.</span><span class="sxs-lookup"><span data-stu-id="40a14-104">The <xref:System.Linq.Queryable.Any%2A> operator returns `true` if any element in a sequence satisfies a condition.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40a14-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="40a14-105">Example</span></span>  
 <span data-ttu-id="40a14-106">Následující příklad vrátí posloupnost zákazníků, které mají alespoň jednu objednávku.</span><span class="sxs-lookup"><span data-stu-id="40a14-106">The following example returns a sequence of customers that have at least one order.</span></span> <span data-ttu-id="40a14-107">`Where` `Customer` `Order`Klauzule je vyhodnocena ,`true` Pokud má daný výsledek nějaký. / `where`</span><span class="sxs-lookup"><span data-stu-id="40a14-107">The `Where`/`where` clause evaluates to `true` if the given `Customer` has any `Order`.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#37](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#37)]
 [!code-vb[DLinqQueryExamples#37](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37)]  
  
## <a name="example"></a><span data-ttu-id="40a14-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="40a14-108">Example</span></span>  
 <span data-ttu-id="40a14-109">Následující kód Visual Basic určuje seznam zákazníků, kteří si neumístili objednávky, a zajišťují, že pro každého zákazníka v tomto seznamu je zadáno jméno kontaktu.</span><span class="sxs-lookup"><span data-stu-id="40a14-109">The following Visual Basic code determines the list of customers who have not placed orders, and ensures that for every customer in that list, a contact name is provided.</span></span>  
  
 [!code-vb[DLinqQueryExamples#37v](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#37v)]  
  
## <a name="example"></a><span data-ttu-id="40a14-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="40a14-110">Example</span></span>  
 <span data-ttu-id="40a14-111">Následující C# příklad vrací sekvenci zákazníků, jejichž objednávky začínají na `ShipCity` "C".</span><span class="sxs-lookup"><span data-stu-id="40a14-111">The following C# example returns a sequence of customers whose orders have a `ShipCity` beginning with "C".</span></span> <span data-ttu-id="40a14-112">Také zahrnuté v návratu jsou zákazníci, kteří nemají žádné objednávky.</span><span class="sxs-lookup"><span data-stu-id="40a14-112">Also included in the return are customers who have no orders.</span></span> <span data-ttu-id="40a14-113">(Podle návrhu <xref:System.Linq.Queryable.All%2A> operátor vrátí `true` prázdnou sekvenci.) Zákazníci bez objednávek se v výstupu konzoly eliminují pomocí `Count` operátoru.</span><span class="sxs-lookup"><span data-stu-id="40a14-113">(By design, the <xref:System.Linq.Queryable.All%2A> operator returns `true` for an empty sequence.) Customers with no orders are eliminated in the console output by using the `Count` operator.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#38](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="40a14-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="40a14-114">See also</span></span>

- [<span data-ttu-id="40a14-115">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="40a14-115">Query Examples</span></span>](query-examples.md)
