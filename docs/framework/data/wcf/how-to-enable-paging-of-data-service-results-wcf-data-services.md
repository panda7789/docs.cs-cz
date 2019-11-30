---
title: 'Postupy: povolení stránkování výsledků datové služby (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- paging output [WCF Data Services]
ms.assetid: 9a316cbd-9612-4482-a541-a10bc78b2635
ms.openlocfilehash: 6b7cea2475a5c11091a04ef3044bbc958e55fc5d
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569093"
---
# <a name="how-to-enable-paging-of-data-service-results-wcf-data-services"></a><span data-ttu-id="47266-102">Postupy: povolení stránkování výsledků datové služby (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="47266-102">How to: Enable Paging of Data Service Results (WCF Data Services)</span></span>
<span data-ttu-id="47266-103">WCF Data Services umožňuje omezit počet entit vrácených dotazem datové služby.</span><span class="sxs-lookup"><span data-stu-id="47266-103">WCF Data Services enables you to limit the number of entities returned by a data service query.</span></span> <span data-ttu-id="47266-104">Omezení stránky jsou definována v metodě, která je volána při inicializaci služby a lze ji nastavit samostatně pro každou sadu entit.</span><span class="sxs-lookup"><span data-stu-id="47266-104">Page limits are defined in the method that is called when the service is initialized and can be set separately for each entity set.</span></span>  
  
 <span data-ttu-id="47266-105">Pokud je povoleno stránkování, obsahuje konečná položka v informačním kanálu odkaz na další stránku dat.</span><span class="sxs-lookup"><span data-stu-id="47266-105">When paging is enabled, the final entry in the feed contains a link to the next page of data.</span></span> <span data-ttu-id="47266-106">Další informace najdete v tématu [konfigurace datové služby](configuring-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="47266-106">For more information, see [Configuring the Data Service](configuring-the-data-service-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="47266-107">V tomto tématu se dozvíte, jak upravit datovou službu a povolit stránkování vrácených `Customers` a `Orders` sad entit.</span><span class="sxs-lookup"><span data-stu-id="47266-107">This topic shows how to modify a data service to enable paging of returned `Customers` and `Orders` entity sets.</span></span> <span data-ttu-id="47266-108">Příklad v tomto tématu používá ukázkovou datovou službu Northwind.</span><span class="sxs-lookup"><span data-stu-id="47266-108">The example in this topic uses the Northwind sample data service.</span></span> <span data-ttu-id="47266-109">Tato služba se vytvoří po dokončení [WCF Data Services rychlý Start](quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="47266-109">This service is created when you complete the [WCF Data Services quickstart](quickstart-wcf-data-services.md).</span></span>  
  
### <a name="how-to-enable-paging-of-returned-customers-and-orders-entity-sets"></a><span data-ttu-id="47266-110">Jak povolit stránkování vrácených zákazníků a objednávek sady entit</span><span class="sxs-lookup"><span data-stu-id="47266-110">How to enable paging of returned Customers and Orders entity sets</span></span>  
  
- <span data-ttu-id="47266-111">V kódu pro datovou službu nahraďte zástupný kód ve funkci `InitializeService` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="47266-111">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## <a name="see-also"></a><span data-ttu-id="47266-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="47266-112">See also</span></span>

- [<span data-ttu-id="47266-113">Načtení odloženého obsahu</span><span class="sxs-lookup"><span data-stu-id="47266-113">Loading Deferred Content</span></span>](loading-deferred-content-wcf-data-services.md)
- [<span data-ttu-id="47266-114">Postupy: Načtení stránkovaných výsledků</span><span class="sxs-lookup"><span data-stu-id="47266-114">How to: Load Paged Results</span></span>](how-to-load-paged-results-wcf-data-services.md)
