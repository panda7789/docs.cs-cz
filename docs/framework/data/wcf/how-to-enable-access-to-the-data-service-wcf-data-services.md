---
title: 'Postupy: Povolit přístup k datové službě (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 3d830bcd-32b4-4f26-9287-d58a071452c6
ms.openlocfilehash: 82b2ec9313c6e0d4b9fa05862209a3ea838f31fe
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918626"
---
# <a name="how-to-enable-access-to-the-data-service-wcf-data-services"></a><span data-ttu-id="99c4a-102">Postupy: Povolit přístup k datové službě (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="99c4a-102">How to: Enable Access to the Data Service (WCF Data Services)</span></span>
<span data-ttu-id="99c4a-103">V [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]nástroji musíte explicitně udělit přístup k prostředkům, které jsou zpřístupněny datovou službou.</span><span class="sxs-lookup"><span data-stu-id="99c4a-103">In [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], you must explicitly grant access to the resources that are exposed by a data service.</span></span> <span data-ttu-id="99c4a-104">To znamená, že po vytvoření nové datové služby musíte explicitně poskytnout přístup k jednotlivým prostředkům jako sady entit.</span><span class="sxs-lookup"><span data-stu-id="99c4a-104">This means that after you create a new data service, you must still explicitly provide access to individual resources as entity sets.</span></span> <span data-ttu-id="99c4a-105">V tomto tématu se dozvíte, jak povolit přístup pro čtení a zápis do pěti sad entit v datové službě Northwind, která se vytvoří po dokončení [rychlého](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)startu.</span><span class="sxs-lookup"><span data-stu-id="99c4a-105">This topic shows how to enable read and write access to five of the entity sets in the Northwind data service that is created when you complete the [quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span> <span data-ttu-id="99c4a-106">Vzhledem k tomu <xref:System.FlagsAttribute>, že je výčetdefinovánpomocí,lzepomocílogickéhooperátoruORzadatvíceoprávněníprojednusaduentit.<xref:System.Data.Services.EntitySetRights></span><span class="sxs-lookup"><span data-stu-id="99c4a-106">Because the <xref:System.Data.Services.EntitySetRights> enumeration is defined by using the <xref:System.FlagsAttribute>, you can use a logical OR operator to specify multiple permissions for a single entity set.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="99c4a-107">Každý klient, který má přístup k aplikaci ASP.NET, může také přistupovat k prostředkům vystaveným datovou službou.</span><span class="sxs-lookup"><span data-stu-id="99c4a-107">Any client that can access the ASP.NET application can also access the resources exposed by the data service.</span></span> <span data-ttu-id="99c4a-108">Pokud chcete zabránit neoprávněnému přístupu k prostředkům, měli byste ve službě produkčních dat také zabezpečit samotnou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="99c4a-108">In a production data service, to prevent unauthorized access to resources, you should also secure the application itself.</span></span> <span data-ttu-id="99c4a-109">Další informace najdete v tématu [zabezpečení ASP.NET webů](https://docs.microsoft.com/previous-versions/aspnet/91f66yxt(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="99c4a-109">For more information, see [Securing ASP.NET Web Sites](https://docs.microsoft.com/previous-versions/aspnet/91f66yxt(v=vs.100)).</span></span>  
  
### <a name="to-enable-access-to-the-data-service"></a><span data-ttu-id="99c4a-110">Povolení přístupu k datové službě</span><span class="sxs-lookup"><span data-stu-id="99c4a-110">To enable access to the data service</span></span>  
  
- <span data-ttu-id="99c4a-111">V kódu pro datovou službu nahraďte zástupný kód ve `InitializeService` funkci následujícím textem:</span><span class="sxs-lookup"><span data-stu-id="99c4a-111">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]  
  
     <span data-ttu-id="99c4a-112">Díky tomu mají klienti přístup pro čtení a zápis k `Orders` sadám entit a `Order_Details` a přístup k `Customers` sadám entit jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="99c4a-112">This enables clients to have read and write access to the `Orders` and `Order_Details` entity sets and read-only access to the `Customers` entity sets.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99c4a-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="99c4a-113">See also</span></span>

- [<span data-ttu-id="99c4a-114">Postupy: Vývoj datové služby WCF běžící ve službě IIS</span><span class="sxs-lookup"><span data-stu-id="99c4a-114">How to: Develop a WCF Data Service Running on IIS</span></span>](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)
- [<span data-ttu-id="99c4a-115">Konfigurace datové služby</span><span class="sxs-lookup"><span data-stu-id="99c4a-115">Configuring the Data Service</span></span>](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
