---
title: 'Postupy: povolení přístupu k datové službě (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 3d830bcd-32b4-4f26-9287-d58a071452c6
ms.openlocfilehash: 0ec9c9a730516b22b4eaa215e042e9393c01d752
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569108"
---
# <a name="how-to-enable-access-to-the-data-service-wcf-data-services"></a><span data-ttu-id="55abf-102">Postupy: povolení přístupu k datové službě (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="55abf-102">How to: Enable Access to the Data Service (WCF Data Services)</span></span>
<span data-ttu-id="55abf-103">V WCF Data Services musíte explicitně udělit přístup k prostředkům, které jsou zpřístupněny datovou službou.</span><span class="sxs-lookup"><span data-stu-id="55abf-103">In WCF Data Services, you must explicitly grant access to the resources that are exposed by a data service.</span></span> <span data-ttu-id="55abf-104">To znamená, že po vytvoření nové datové služby musíte explicitně poskytnout přístup k jednotlivým prostředkům jako sady entit.</span><span class="sxs-lookup"><span data-stu-id="55abf-104">This means that after you create a new data service, you must still explicitly provide access to individual resources as entity sets.</span></span> <span data-ttu-id="55abf-105">V tomto tématu se dozvíte, jak povolit přístup pro čtení a zápis do pěti sad entit v datové službě Northwind, která se vytvoří po dokončení [rychlého](quickstart-wcf-data-services.md)startu.</span><span class="sxs-lookup"><span data-stu-id="55abf-105">This topic shows how to enable read and write access to five of the entity sets in the Northwind data service that is created when you complete the [quickstart](quickstart-wcf-data-services.md).</span></span> <span data-ttu-id="55abf-106">Vzhledem k tomu, že je výčet <xref:System.Data.Services.EntitySetRights> definován pomocí <xref:System.FlagsAttribute>, lze pomocí logického operátoru OR zadat více oprávnění pro jednu sadu entit.</span><span class="sxs-lookup"><span data-stu-id="55abf-106">Because the <xref:System.Data.Services.EntitySetRights> enumeration is defined by using the <xref:System.FlagsAttribute>, you can use a logical OR operator to specify multiple permissions for a single entity set.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="55abf-107">Každý klient, který má přístup k aplikaci ASP.NET, může také přistupovat k prostředkům vystaveným datovou službou.</span><span class="sxs-lookup"><span data-stu-id="55abf-107">Any client that can access the ASP.NET application can also access the resources exposed by the data service.</span></span> <span data-ttu-id="55abf-108">Pokud chcete zabránit neoprávněnému přístupu k prostředkům, měli byste ve službě produkčních dat také zabezpečit samotnou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="55abf-108">In a production data service, to prevent unauthorized access to resources, you should also secure the application itself.</span></span> <span data-ttu-id="55abf-109">Další informace najdete v tématu [zabezpečení ASP.NET webů](https://docs.microsoft.com/previous-versions/aspnet/91f66yxt(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="55abf-109">For more information, see [Securing ASP.NET Web Sites](https://docs.microsoft.com/previous-versions/aspnet/91f66yxt(v=vs.100)).</span></span>  
  
### <a name="to-enable-access-to-the-data-service"></a><span data-ttu-id="55abf-110">Povolení přístupu k datové službě</span><span class="sxs-lookup"><span data-stu-id="55abf-110">To enable access to the data service</span></span>  
  
- <span data-ttu-id="55abf-111">V kódu pro datovou službu nahraďte zástupný kód ve funkci `InitializeService` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="55abf-111">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]  
  
     <span data-ttu-id="55abf-112">To umožňuje klientům mít přístup pro čtení a zápis do `Orders` a `Order_Details` sady entit a přístup jen pro čtení k sadám entit `Customers`.</span><span class="sxs-lookup"><span data-stu-id="55abf-112">This enables clients to have read and write access to the `Orders` and `Order_Details` entity sets and read-only access to the `Customers` entity sets.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55abf-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="55abf-113">See also</span></span>

- [<span data-ttu-id="55abf-114">Postupy: Vývoj datové služby WCF ve službě IIS</span><span class="sxs-lookup"><span data-stu-id="55abf-114">How to: Develop a WCF Data Service Running on IIS</span></span>](how-to-develop-a-wcf-data-service-running-on-iis.md)
- [<span data-ttu-id="55abf-115">Konfigurace datové služby</span><span class="sxs-lookup"><span data-stu-id="55abf-115">Configuring the Data Service</span></span>](configuring-the-data-service-wcf-data-services.md)
