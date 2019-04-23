---
title: 'Postupy: Povolit stránkování výsledků datové služby (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- paging output [WCF Data Services]
ms.assetid: 9a316cbd-9612-4482-a541-a10bc78b2635
ms.openlocfilehash: edc150d118153849dd84eb40f1443d842c7d346d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59517817"
---
# <a name="how-to-enable-paging-of-data-service-results-wcf-data-services"></a><span data-ttu-id="936f3-102">Postupy: Povolit stránkování výsledků datové služby (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="936f3-102">How to: Enable Paging of Data Service Results (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] <span data-ttu-id="936f3-103">umožňuje omezit počet entit vrácených dotazem dat služby.</span><span class="sxs-lookup"><span data-stu-id="936f3-103">enables you to limit the number of entities returned by a data service query.</span></span> <span data-ttu-id="936f3-104">Stránky omezení jsou definovány v metodě, která je volána, když služba je inicializována a je možné nastavit zvlášť pro každou sadu entit.</span><span class="sxs-lookup"><span data-stu-id="936f3-104">Page limits are defined in the method that is called when the service is initialized and can be set separately for each entity set.</span></span>  
  
 <span data-ttu-id="936f3-105">Když je povoleno stránkování, poslední položku v informačním kanálu obsahuje odkaz na další stránku data.</span><span class="sxs-lookup"><span data-stu-id="936f3-105">When paging is enabled, the final entry in the feed contains a link to the next page of data.</span></span> <span data-ttu-id="936f3-106">Další informace najdete v tématu [konfigurace datové služby](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="936f3-106">For more information, see [Configuring the Data Service](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="936f3-107">Toto téma ukazuje, jak změnit datové služby umožňující stránkování vrácené `Customers` a `Orders` sady entit.</span><span class="sxs-lookup"><span data-stu-id="936f3-107">This topic shows how to modify a data service to enable paging of returned `Customers` and `Orders` entity sets.</span></span> <span data-ttu-id="936f3-108">V příkladu v tomto tématu se používá ukázková datová služba Northwind.</span><span class="sxs-lookup"><span data-stu-id="936f3-108">The example in this topic uses the Northwind sample data service.</span></span> <span data-ttu-id="936f3-109">Tato služba se vytvoří při dokončení [rychlý start služeb WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="936f3-109">This service is created when you complete the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span>  
  
### <a name="how-to-enable-paging-of-returned-customers-and-orders-entity-sets"></a><span data-ttu-id="936f3-110">Jak povolit stránkování vrácené zákazníci a objednávky sady entit</span><span class="sxs-lookup"><span data-stu-id="936f3-110">How to enable paging of returned Customers and Orders entity sets</span></span>  
  
-   <span data-ttu-id="936f3-111">V kódu pro datovou službu, nahraďte zástupný symbol kód v `InitializeService` funkce následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="936f3-111">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## <a name="see-also"></a><span data-ttu-id="936f3-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="936f3-112">See also</span></span>

- [<span data-ttu-id="936f3-113">Načtení odloženého obsahu</span><span class="sxs-lookup"><span data-stu-id="936f3-113">Loading Deferred Content</span></span>](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)
- [<span data-ttu-id="936f3-114">Postupy: Načtení stránkovaných výsledků</span><span class="sxs-lookup"><span data-stu-id="936f3-114">How to: Load Paged Results</span></span>](../../../../docs/framework/data/wcf/how-to-load-paged-results-wcf-data-services.md)
