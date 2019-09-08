---
title: 'Postupy: Určení objemu načítaných souvisejících dat'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: efdc203e-3da9-4477-815e-54f10c3d7c6c
ms.openlocfilehash: 2112600dfcef65b1c85445b03806ce8e9cab6a27
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782063"
---
# <a name="how-to-control-how-much-related-data-is-retrieved"></a><span data-ttu-id="07880-102">Postupy: Určení objemu načítaných souvisejících dat</span><span class="sxs-lookup"><span data-stu-id="07880-102">How to: Control How Much Related Data Is Retrieved</span></span>
<span data-ttu-id="07880-103"><xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> Použijte metodu k určení, která data související s vaším hlavním cílem by měla být načtena ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="07880-103">Use the <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> method to specify which data related to your main target should be retrieved at the same time.</span></span> <span data-ttu-id="07880-104">Pokud například víte, že budete potřebovat informace o objednávkách zákazníků, můžete použít <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> k tomu, abyste se ujistili, že informace o objednávkách budou načteny ve stejnou dobu jako informace o zákaznících.</span><span class="sxs-lookup"><span data-stu-id="07880-104">For example, if you know you will need information about customers' orders, you can use <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> to make sure that the order information is retrieved at the same time as the customer information.</span></span> <span data-ttu-id="07880-105">Tento přístup má za následek pouze jednu cestu k databázi pro obě sady informací.</span><span class="sxs-lookup"><span data-stu-id="07880-105">This approach results in only one trip to the database for both sets of information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="07880-106">Data související s hlavním cílem dotazu můžete načíst načtením více produktů jako jedné velké projekce, jako je například načítání objednávek při cílení na zákazníky.</span><span class="sxs-lookup"><span data-stu-id="07880-106">You can retrieve data related to the main target of your query by retrieving a cross-product as one large projection, such as retrieving orders when you target customers.</span></span> <span data-ttu-id="07880-107">Ale tento přístup má často nevýhody.</span><span class="sxs-lookup"><span data-stu-id="07880-107">But this approach often has disadvantages.</span></span> <span data-ttu-id="07880-108">Například výsledky jsou pouze projekce, nikoli entity, které lze změnit a zachovat pomocí [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="07880-108">For example, the results are just projections and not entities that can be changed and persisted by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="07880-109">A můžete načíst spoustu dat, která nepotřebujete.</span><span class="sxs-lookup"><span data-stu-id="07880-109">And you can be retrieving lots of data that you do not need.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07880-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="07880-110">Example</span></span>  
 <span data-ttu-id="07880-111">V následujícím příkladu jsou při spuštění dotazu `Orders` načteny všechny `Customers` , které jsou umístěny v Londýně.</span><span class="sxs-lookup"><span data-stu-id="07880-111">In the following example, all the `Orders` for all the `Customers` who are located in London are retrieved when the query is executed.</span></span> <span data-ttu-id="07880-112">V důsledku toho se po úspěšném přístupu k `Orders` vlastnosti `Customer` objektu neaktivuje nový databázový dotaz.</span><span class="sxs-lookup"><span data-stu-id="07880-112">As a result, successive access to the `Orders` property on a `Customer` object does not trigger a new database query.</span></span>  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="07880-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="07880-113">See also</span></span>

- [<span data-ttu-id="07880-114">Dotazování na databázi</span><span class="sxs-lookup"><span data-stu-id="07880-114">Querying the Database</span></span>](querying-the-database.md)
