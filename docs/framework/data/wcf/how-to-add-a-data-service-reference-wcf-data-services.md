---
title: 'Postupy: Přidání odkazu služby dat (služby WCF Data Services)'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
ms.openlocfilehash: a8dcc01fb7a564a363cabed6a22738cd520d317f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33356228"
---
# <a name="how-to-add-a-data-service-reference-wcf-data-services"></a><span data-ttu-id="71cf5-102">Postupy: Přidání odkazu služby dat (služby WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="71cf5-102">How to: Add a Data Service Reference (WCF Data Services)</span></span>
<span data-ttu-id="71cf5-103">Můžete použít **přidat odkaz na službu** dialogové okno v sadě Visual Studio se přidat odkaz na [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span><span class="sxs-lookup"><span data-stu-id="71cf5-103">You can use the **Add Service Reference** dialog in Visual Studio to add a reference to [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].</span></span> <span data-ttu-id="71cf5-104">To umožňuje snadno přístup ke službě data v aplikaci klienta, které vyvíjíte v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="71cf5-104">This enables you to more easily access a data service in a client application that you develop in Visual Studio.</span></span> <span data-ttu-id="71cf5-105">Po dokončení tohoto postupu se generují třídy dat na základě metadat, který byl získán z službu data.</span><span class="sxs-lookup"><span data-stu-id="71cf5-105">When you complete this procedure, data classes are generated based on metadata that is obtained from the data service.</span></span> <span data-ttu-id="71cf5-106">Další informace najdete v tématu [generování dat služby klientské knihovny](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="71cf5-106">For more information, see [Generating the Data Service Client Library](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md).</span></span>  
  
### <a name="to-add-a-data-service-reference"></a><span data-ttu-id="71cf5-107">Chcete-li přidat odkaz na službu data</span><span class="sxs-lookup"><span data-stu-id="71cf5-107">To add a data service reference</span></span>  
  
1.  <span data-ttu-id="71cf5-108">(Volitelné) Pokud službu data není součástí řešení a není spuštěná, spusťte službu data a poznamenejte si identifikátor URI služby data.</span><span class="sxs-lookup"><span data-stu-id="71cf5-108">(Optional) If the data service is not part of the solution and is not already running, start the data service and note the URI of the data service.</span></span>  
  
2.  <span data-ttu-id="71cf5-109">Klikněte pravým tlačítkem na projekt klienta a pak vyberte **přidat odkaz na službu**.</span><span class="sxs-lookup"><span data-stu-id="71cf5-109">Right-click the client project and then select **Add Service Reference**.</span></span>  
  
3.  <span data-ttu-id="71cf5-110">Pokud službu data je součástí aktuální řešení, klikněte na tlačítko **Discover**.</span><span class="sxs-lookup"><span data-stu-id="71cf5-110">If the data service is part of the current solution, click **Discover**.</span></span>  
  
     <span data-ttu-id="71cf5-111">-nebo-</span><span class="sxs-lookup"><span data-stu-id="71cf5-111">-or-</span></span>  
  
     <span data-ttu-id="71cf5-112">V **adresu** textového pole zadejte základní adresu URL služby data, jako třeba `http://localhost:1234/Northwind.svc`a potom klikněte na **přejděte**.</span><span class="sxs-lookup"><span data-stu-id="71cf5-112">In the **Address** text box, type the base URL of the data service, such as `http://localhost:1234/Northwind.svc`, and then click **Go**.</span></span>  
  
4.  <span data-ttu-id="71cf5-113">Click **OK**.</span><span class="sxs-lookup"><span data-stu-id="71cf5-113">Click **OK**.</span></span>  
  
     <span data-ttu-id="71cf5-114">Tento postup přidá nový soubor kód, který obsahuje datové třídy, které se používají pro přístup a pracovat s prostředky služby data jako objekty.</span><span class="sxs-lookup"><span data-stu-id="71cf5-114">This adds a new code file that contains the data classes that are used to access and interact with data service resources as objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71cf5-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="71cf5-115">See Also</span></span>  
 [<span data-ttu-id="71cf5-116">Rychlý start</span><span class="sxs-lookup"><span data-stu-id="71cf5-116">Quickstart</span></span>](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
