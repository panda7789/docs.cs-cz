---
title: 'Postupy: Určení objemu načítaných souvisejících dat'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: efdc203e-3da9-4477-815e-54f10c3d7c6c
ms.openlocfilehash: dd59c09185eab003274614dcc30393b060e6b7c0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215440"
---
# <a name="how-to-control-how-much-related-data-is-retrieved"></a><span data-ttu-id="88191-102">Postupy: Určení objemu načítaných souvisejících dat</span><span class="sxs-lookup"><span data-stu-id="88191-102">How to: Control How Much Related Data Is Retrieved</span></span>
<span data-ttu-id="88191-103">Použití <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> metody k určení, která data související s vaší hlavní cíl by měly být načteny současně.</span><span class="sxs-lookup"><span data-stu-id="88191-103">Use the <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> method to specify which data related to your main target should be retrieved at the same time.</span></span> <span data-ttu-id="88191-104">Například pokud víte, budete potřebovat informace o objednávek zákazníků, můžete použít <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> abyste měli jistotu, že je ve stejnou dobu jako informace o zákaznících načíst informace o objednávce.</span><span class="sxs-lookup"><span data-stu-id="88191-104">For example, if you know you will need information about customers' orders, you can use <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> to make sure that the order information is retrieved at the same time as the customer information.</span></span> <span data-ttu-id="88191-105">Tento přístup za následek jenom jednu cestu k databázi pro obě sady informace.</span><span class="sxs-lookup"><span data-stu-id="88191-105">This approach results in only one trip to the database for both sets of information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="88191-106">Můžete načíst data související s hlavním cílem dotazu načtením mezi produkty jako jeden velký projekce, třeba načítání objednávek, při použití prostředí zákazníků.</span><span class="sxs-lookup"><span data-stu-id="88191-106">You can retrieve data related to the main target of your query by retrieving a cross-product as one large projection, such as retrieving orders when you target customers.</span></span> <span data-ttu-id="88191-107">Ale tento přístup má často nevýhody.</span><span class="sxs-lookup"><span data-stu-id="88191-107">But this approach often has disadvantages.</span></span> <span data-ttu-id="88191-108">Například výsledky jsou pouze projekce a není entity, které je možné změnit a určen na základě [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="88191-108">For example, the results are just projections and not entities that can be changed and persisted by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="88191-109">A můžete načítají velké množství dat, která není nutné.</span><span class="sxs-lookup"><span data-stu-id="88191-109">And you can be retrieving lots of data that you do not need.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88191-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="88191-110">Example</span></span>  
 <span data-ttu-id="88191-111">V následujícím příkladu všechny `Orders` pro všechny `Customers` kdo jsou umístěny v Londýně jsou načteny při spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="88191-111">In the following example, all the `Orders` for all the `Customers` who are located in London are retrieved when the query is executed.</span></span> <span data-ttu-id="88191-112">V důsledku toho po sobě jdoucích přístup k `Orders` vlastnosti `Customer` objekt neaktivuje nový databázový dotaz.</span><span class="sxs-lookup"><span data-stu-id="88191-112">As a result, successive access to the `Orders` property on a `Customer` object does not trigger a new database query.</span></span>  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="88191-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="88191-113">See also</span></span>

- [<span data-ttu-id="88191-114">Dotazy do databáze</span><span class="sxs-lookup"><span data-stu-id="88191-114">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
