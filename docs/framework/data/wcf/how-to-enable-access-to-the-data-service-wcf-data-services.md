---
title: "Postupy: povolení přístupu ke službě Data (služby WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: WCF Data Services, configuring
ms.assetid: 3d830bcd-32b4-4f26-9287-d58a071452c6
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f481a3a918282bf598277dcd4e1bf29d63edddc1
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-enable-access-to-the-data-service-wcf-data-services"></a><span data-ttu-id="705b1-102">Postupy: povolení přístupu ke službě Data (služby WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="705b1-102">How to: Enable Access to the Data Service (WCF Data Services)</span></span>
<span data-ttu-id="705b1-103">V [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], je nutné explicitně udělit přístup k prostředkům, které jsou vystavené datové služby.</span><span class="sxs-lookup"><span data-stu-id="705b1-103">In [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], you must explicitly grant access to the resources that are exposed by a data service.</span></span> <span data-ttu-id="705b1-104">To znamená, že po vytvoření nové datové služby, je nutné stále explicitně zadat přístup k jednotlivým prostředkům jako sady entit.</span><span class="sxs-lookup"><span data-stu-id="705b1-104">This means that after you create a new data service, you must still explicitly provide access to individual resources as entity sets.</span></span> <span data-ttu-id="705b1-105">Toto téma ukazuje, jak povolit čtení a zápis do pěti entity nastaví ve službě Northwind data, která se vytvoří při dokončení [rychlý Start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="705b1-105">This topic shows how to enable read and write access to five of the entity sets in the Northwind data service that is created when you complete the [quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span> <span data-ttu-id="705b1-106">Protože <xref:System.Data.Services.EntitySetRights> je výčet definován pomocí <xref:System.FlagsAttribute>, můžete použít logickou nebo nastavit operátor zadat více oprávnění pro jednu entitu.</span><span class="sxs-lookup"><span data-stu-id="705b1-106">Because the <xref:System.Data.Services.EntitySetRights> enumeration is defined by using the <xref:System.FlagsAttribute>, you can use a logical OR operator to specify multiple permissions for a single entity set.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="705b1-107">Libovolného klienta, který můžete přístup k aplikaci ASP.NET můžete také přístup k prostředkům vystavené službu data.</span><span class="sxs-lookup"><span data-stu-id="705b1-107">Any client that can access the ASP.NET application can also access the resources exposed by the data service.</span></span> <span data-ttu-id="705b1-108">V produkčním datové služby aby se zabránilo neoprávněnému přístupu k prostředkům, je nutné také zabezpečit vlastní aplikace.</span><span class="sxs-lookup"><span data-stu-id="705b1-108">In a production data service, to prevent unauthorized access to resources, you should also secure the application itself.</span></span> <span data-ttu-id="705b1-109">Další informace najdete v tématu [NIB: zabezpečení ASP.NET](http://msdn.microsoft.com/library/04b37532-18d9-40b4-8e5f-ee09a70b311d).</span><span class="sxs-lookup"><span data-stu-id="705b1-109">For more information, see [NIB: ASP.NET Security](http://msdn.microsoft.com/library/04b37532-18d9-40b4-8e5f-ee09a70b311d).</span></span>  
  
### <a name="to-enable-access-to-the-data-service"></a><span data-ttu-id="705b1-110">Chcete-li povolit přístup ke službě data</span><span class="sxs-lookup"><span data-stu-id="705b1-110">To enable access to the data service</span></span>  
  
-   <span data-ttu-id="705b1-111">V kódu pro službu data, nahraďte zástupný symbol kód v `InitializeService` funkce následujícím kódem:</span><span class="sxs-lookup"><span data-stu-id="705b1-111">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#allreadconfig)]  
  
     <span data-ttu-id="705b1-112">To umožňuje klientům ke čtení a zápis `Orders` a `Order_Details` sad entit a přístup jen pro čtení k `Customers` sady entit.</span><span class="sxs-lookup"><span data-stu-id="705b1-112">This enables clients to have read and write access to the `Orders` and `Order_Details` entity sets and read-only access to the `Customers` entity sets.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="705b1-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="705b1-113">See Also</span></span>  
 [<span data-ttu-id="705b1-114">Postupy: Vývoj datové služby WCF ve službě IIS</span><span class="sxs-lookup"><span data-stu-id="705b1-114">How to: Develop a WCF Data Service Running on IIS</span></span>](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)  
 [<span data-ttu-id="705b1-115">Konfigurace datové služby</span><span class="sxs-lookup"><span data-stu-id="705b1-115">Configuring the Data Service</span></span>](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
