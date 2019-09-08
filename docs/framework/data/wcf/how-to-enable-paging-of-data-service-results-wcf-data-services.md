---
title: 'Postupy: Povolit stránkování výsledků datové služby (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- paging output [WCF Data Services]
ms.assetid: 9a316cbd-9612-4482-a541-a10bc78b2635
ms.openlocfilehash: 82b4d0fd3531778ab494d6526a56b092edf9481a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780049"
---
# <a name="how-to-enable-paging-of-data-service-results-wcf-data-services"></a><span data-ttu-id="63b8a-102">Postupy: Povolit stránkování výsledků datové služby (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="63b8a-102">How to: Enable Paging of Data Service Results (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="63b8a-103">umožňuje omezit počet entit vrácených dotazem datové služby.</span><span class="sxs-lookup"><span data-stu-id="63b8a-103">enables you to limit the number of entities returned by a data service query.</span></span> <span data-ttu-id="63b8a-104">Omezení stránky jsou definována v metodě, která je volána při inicializaci služby a lze ji nastavit samostatně pro každou sadu entit.</span><span class="sxs-lookup"><span data-stu-id="63b8a-104">Page limits are defined in the method that is called when the service is initialized and can be set separately for each entity set.</span></span>  
  
 <span data-ttu-id="63b8a-105">Pokud je povoleno stránkování, obsahuje konečná položka v informačním kanálu odkaz na další stránku dat.</span><span class="sxs-lookup"><span data-stu-id="63b8a-105">When paging is enabled, the final entry in the feed contains a link to the next page of data.</span></span> <span data-ttu-id="63b8a-106">Další informace najdete v tématu [konfigurace datové služby](configuring-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="63b8a-106">For more information, see [Configuring the Data Service](configuring-the-data-service-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="63b8a-107">V tomto tématu se dozvíte, jak upravit datovou službu a povolit `Customers` stránkování `Orders` vrácených a sad entit.</span><span class="sxs-lookup"><span data-stu-id="63b8a-107">This topic shows how to modify a data service to enable paging of returned `Customers` and `Orders` entity sets.</span></span> <span data-ttu-id="63b8a-108">Příklad v tomto tématu používá ukázkovou datovou službu Northwind.</span><span class="sxs-lookup"><span data-stu-id="63b8a-108">The example in this topic uses the Northwind sample data service.</span></span> <span data-ttu-id="63b8a-109">Tato služba se vytvoří po dokončení [WCF Data Services rychlý Start](quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="63b8a-109">This service is created when you complete the [WCF Data Services quickstart](quickstart-wcf-data-services.md).</span></span>  
  
### <a name="how-to-enable-paging-of-returned-customers-and-orders-entity-sets"></a><span data-ttu-id="63b8a-110">Jak povolit stránkování vrácených zákazníků a objednávek sady entit</span><span class="sxs-lookup"><span data-stu-id="63b8a-110">How to enable paging of returned Customers and Orders entity sets</span></span>  
  
- <span data-ttu-id="63b8a-111">V kódu pro datovou službu nahraďte zástupný kód ve `InitializeService` funkci následujícím textem:</span><span class="sxs-lookup"><span data-stu-id="63b8a-111">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## <a name="see-also"></a><span data-ttu-id="63b8a-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="63b8a-112">See also</span></span>

- [<span data-ttu-id="63b8a-113">Načtení odloženého obsahu</span><span class="sxs-lookup"><span data-stu-id="63b8a-113">Loading Deferred Content</span></span>](loading-deferred-content-wcf-data-services.md)
- [<span data-ttu-id="63b8a-114">Postupy: Načíst stránkované výsledky</span><span class="sxs-lookup"><span data-stu-id="63b8a-114">How to: Load Paged Results</span></span>](how-to-load-paged-results-wcf-data-services.md)
