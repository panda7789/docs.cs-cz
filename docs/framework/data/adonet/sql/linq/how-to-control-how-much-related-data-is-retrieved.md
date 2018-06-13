---
title: 'Postupy: řízení, kolik související Data načtena'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: efdc203e-3da9-4477-815e-54f10c3d7c6c
ms.openlocfilehash: 202e33f3130e8db7269af2b4669690cf5c6468cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33360854"
---
# <a name="how-to-control-how-much-related-data-is-retrieved"></a><span data-ttu-id="14896-102">Postupy: řízení, kolik související Data načtena</span><span class="sxs-lookup"><span data-stu-id="14896-102">How to: Control How Much Related Data Is Retrieved</span></span>
<span data-ttu-id="14896-103">Použití <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> metoda k určení, která data související s vaší hlavní cíl mají být načtena ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="14896-103">Use the <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> method to specify which data related to your main target should be retrieved at the same time.</span></span> <span data-ttu-id="14896-104">Například pokud jste si jisti, budete potřebovat informace o objednávek zákazníků, můžete použít <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> a ujistěte se, že je ve stejnou dobu jako informace o zákazníkovi načíst informace o objednávce.</span><span class="sxs-lookup"><span data-stu-id="14896-104">For example, if you know you will need information about customers' orders, you can use <xref:System.Data.Linq.DataLoadOptions.LoadWith%2A> to make sure that the order information is retrieved at the same time as the customer information.</span></span> <span data-ttu-id="14896-105">Tento přístup je výsledkem pouze jediná cesta k databázi pro obě sady informace.</span><span class="sxs-lookup"><span data-stu-id="14896-105">This approach results in only one trip to the database for both sets of information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14896-106">Můžete načíst data související s hlavním cílem tohoto dotazu načtením smíšený produkt jako jeden velký projekce, jako je například získávání objednávky po cíle zákazníků.</span><span class="sxs-lookup"><span data-stu-id="14896-106">You can retrieve data related to the main target of your query by retrieving a cross-product as one large projection, such as retrieving orders when you target customers.</span></span> <span data-ttu-id="14896-107">Ale tento přístup má často nevýhody.</span><span class="sxs-lookup"><span data-stu-id="14896-107">But this approach often has disadvantages.</span></span> <span data-ttu-id="14896-108">Například výsledky jsou právě projekce a není entit, které můžete změnit a ve uchováván [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="14896-108">For example, the results are just projections and not entities that can be changed and persisted by [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span></span> <span data-ttu-id="14896-109">A může být načítání velké množství dat, který není nutné.</span><span class="sxs-lookup"><span data-stu-id="14896-109">And you can be retrieving lots of data that you do not need.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14896-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="14896-110">Example</span></span>  
 <span data-ttu-id="14896-111">V následujícím příkladu všechny `Orders` pro všechny `Customers` kdo jsou umístěny v Londýně se načítají, když je proveden dotaz.</span><span class="sxs-lookup"><span data-stu-id="14896-111">In the following example, all the `Orders` for all the `Customers` who are located in London are retrieved when the query is executed.</span></span> <span data-ttu-id="14896-112">V důsledku toho následných přístup k `Orders` vlastnost `Customer` objekt neaktivuje nový databázový dotaz.</span><span class="sxs-lookup"><span data-stu-id="14896-112">As a result, successive access to the `Orders` property on a `Customer` object does not trigger a new database query.</span></span>  
  
 [!code-csharp[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.dataloadoptions/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.DataLoadOptions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.dataloadoptions/vb/module1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="14896-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="14896-113">See Also</span></span>  
 [<span data-ttu-id="14896-114">Dotazování na databázi</span><span class="sxs-lookup"><span data-stu-id="14896-114">Querying the Database</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)
