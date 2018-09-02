---
title: 'Postupy: Přidání odkazu na datovou službu (WCF Data Services)'
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
ms.openlocfilehash: fc1786e1c6102c702374989253cd3ce23e3f7b54
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43404420"
---
# <a name="how-to-add-a-data-service-reference-wcf-data-services"></a><span data-ttu-id="19959-102">Postupy: Přidání odkazu na datovou službu (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="19959-102">How to: Add a data service reference (WCF Data Services)</span></span>

<span data-ttu-id="19959-103">Můžete použít **přidat odkaz na službu** dialogového okna v sadě Visual Studio se přidat odkaz na služeb WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="19959-103">You can use the **Add Service Reference** dialog in Visual Studio to add a reference to WCF Data Services.</span></span> <span data-ttu-id="19959-104">To umožňuje jednodušší přístup ke službě data v klientské aplikaci, která při vývoji v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="19959-104">This enables you to more easily access a data service in a client application that you develop in Visual Studio.</span></span> <span data-ttu-id="19959-105">Po dokončení tohoto postupu datových tříd jsou generovány na základě metadat, která se získá z datové služby.</span><span class="sxs-lookup"><span data-stu-id="19959-105">When you complete this procedure, data classes are generated based on metadata that is obtained from the data service.</span></span> <span data-ttu-id="19959-106">Další informace najdete v tématu [generování klientské knihovny datové služby](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="19959-106">For more information, see [Generating the Data Service Client Library](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md).</span></span>

## <a name="add-a-data-service-reference"></a><span data-ttu-id="19959-107">Přidání odkazu na datovou službu</span><span class="sxs-lookup"><span data-stu-id="19959-107">Add a data service reference</span></span>

1. <span data-ttu-id="19959-108">(Volitelné) Pokud datové služby není součástí řešení a není spuštěná, spusťte službu data a poznamenejte si URI datové služby.</span><span class="sxs-lookup"><span data-stu-id="19959-108">(Optional) If the data service is not part of the solution and is not already running, start the data service and note the URI of the data service.</span></span>

2. <span data-ttu-id="19959-109">V sadě Visual Studio v **Průzkumníka řešení**, klikněte pravým tlačítkem na klientský projekt a pak vyberte **přidat** > **odkaz na službu**.</span><span class="sxs-lookup"><span data-stu-id="19959-109">In Visual Studio, in **Solution Explorer**, right-click the client project and then select **Add** > **Service Reference**.</span></span>

3. <span data-ttu-id="19959-110">Pokud datové služby je součástí aktuálního řešení, klikněte na tlačítko **Discover**.</span><span class="sxs-lookup"><span data-stu-id="19959-110">If the data service is part of the current solution, click **Discover**.</span></span>

     <span data-ttu-id="19959-111">-nebo-</span><span class="sxs-lookup"><span data-stu-id="19959-111">-or-</span></span>

     <span data-ttu-id="19959-112">V **adresu** textového pole zadejte základní adresu URL datové služby, jako například `http://localhost:1234/Northwind.svc`a potom klikněte na tlačítko **Přejít**.</span><span class="sxs-lookup"><span data-stu-id="19959-112">In the **Address** text box, type the base URL of the data service, such as `http://localhost:1234/Northwind.svc`, and then click **Go**.</span></span>

4. <span data-ttu-id="19959-113">Vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="19959-113">Select **OK**.</span></span>

     <span data-ttu-id="19959-114">Do projektu se přidá nový soubor kódu, který obsahuje datových tříd, které můžete používat a komunikovat s prostředkům datové služby.</span><span class="sxs-lookup"><span data-stu-id="19959-114">A new code file that contains the data classes that can access and interact with data service resources is added to the project.</span></span>

## <a name="see-also"></a><span data-ttu-id="19959-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="19959-115">See also</span></span>

- [<span data-ttu-id="19959-116">Rychlý start</span><span class="sxs-lookup"><span data-stu-id="19959-116">Quickstart</span></span>](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)