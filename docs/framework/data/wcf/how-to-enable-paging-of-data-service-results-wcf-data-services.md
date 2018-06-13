---
title: 'Postupy: povolení stránkování výsledků služby dat (služby WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- paging output [WCF Data Services]
ms.assetid: 9a316cbd-9612-4482-a541-a10bc78b2635
ms.openlocfilehash: 822184e3de3fd0cc628eb08619f93ba0734a464d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33360609"
---
# <a name="how-to-enable-paging-of-data-service-results-wcf-data-services"></a><span data-ttu-id="7ca15-102">Postupy: povolení stránkování výsledků služby dat (služby WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="7ca15-102">How to: Enable Paging of Data Service Results (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="7ca15-103"> umožňuje omezit počet vrácených dotazem služby data entity.</span><span class="sxs-lookup"><span data-stu-id="7ca15-103"> enables you to limit the number of entities returned by a data service query.</span></span> <span data-ttu-id="7ca15-104">Stránka omezení jsou definovány v metodu, která je volána, když služba je inicializován a můžete nastavit samostatně pro každou sadu entit.</span><span class="sxs-lookup"><span data-stu-id="7ca15-104">Page limits are defined in the method that is called when the service is initialized and can be set separately for each entity set.</span></span>  
  
 <span data-ttu-id="7ca15-105">Pokud je povoleno stránkování, poslední položku v informačním kanálu obsahuje odkaz na další stránku data.</span><span class="sxs-lookup"><span data-stu-id="7ca15-105">When paging is enabled, the final entry in the feed contains a link to the next page of data.</span></span> <span data-ttu-id="7ca15-106">Další informace najdete v tématu [konfigurace službu Data](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="7ca15-106">For more information, see [Configuring the Data Service](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="7ca15-107">Toto téma ukazuje, jak změnit datové služby pro povolení stránkování z vráceného `Customers` a `Orders` sady entit.</span><span class="sxs-lookup"><span data-stu-id="7ca15-107">This topic shows how to modify a data service to enable paging of returned `Customers` and `Orders` entity sets.</span></span> <span data-ttu-id="7ca15-108">Příklad v tomto tématu používá službu Northwind ukázková data.</span><span class="sxs-lookup"><span data-stu-id="7ca15-108">The example in this topic uses the Northwind sample data service.</span></span> <span data-ttu-id="7ca15-109">Tato služba se vytvoří při dokončení [rychlého startu služby WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="7ca15-109">This service is created when you complete the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span>  
  
### <a name="how-to-enable-paging-of-returned-customers-and-orders-entity-sets"></a><span data-ttu-id="7ca15-110">Postup povolení stránkování vrácený zákazníci a objednávky sad entit</span><span class="sxs-lookup"><span data-stu-id="7ca15-110">How to enable paging of returned Customers and Orders entity sets</span></span>  
  
-   <span data-ttu-id="7ca15-111">V kódu pro službu data, nahraďte zástupný symbol kód v `InitializeService` funkce následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="7ca15-111">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## <a name="see-also"></a><span data-ttu-id="7ca15-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="7ca15-112">See Also</span></span>  
 [<span data-ttu-id="7ca15-113">Načtení odloženého obsahu</span><span class="sxs-lookup"><span data-stu-id="7ca15-113">Loading Deferred Content</span></span>](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)  
 [<span data-ttu-id="7ca15-114">Postupy: Načtení stránkovaných výsledků</span><span class="sxs-lookup"><span data-stu-id="7ca15-114">How to: Load Paged Results</span></span>](../../../../docs/framework/data/wcf/how-to-load-paged-results-wcf-data-services.md)
