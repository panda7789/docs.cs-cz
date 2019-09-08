---
title: 'Postupy: Přidání odkazu na datovou službu (WCF Data Services)'
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
ms.openlocfilehash: 42d89cf87b5fe9bbdb229f10cd6a0e340d4c08fd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790748"
---
# <a name="how-to-add-a-data-service-reference-wcf-data-services"></a><span data-ttu-id="3af74-102">Postupy: Přidání odkazu na datovou službu (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="3af74-102">How to: Add a data service reference (WCF Data Services)</span></span>

<span data-ttu-id="3af74-103">Pomocí dialogového okna **Přidat odkaz na službu** v aplikaci Visual Studio můžete přidat odkaz na WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="3af74-103">You can use the **Add Service Reference** dialog in Visual Studio to add a reference to WCF Data Services.</span></span> <span data-ttu-id="3af74-104">To umožňuje snazší přístup k datové službě v klientské aplikaci, kterou vyvíjíte v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3af74-104">This enables you to more easily access a data service in a client application that you develop in Visual Studio.</span></span> <span data-ttu-id="3af74-105">Po dokončení tohoto postupu se datové třídy generují na základě metadat získaných z datové služby.</span><span class="sxs-lookup"><span data-stu-id="3af74-105">When you complete this procedure, data classes are generated based on metadata that is obtained from the data service.</span></span> <span data-ttu-id="3af74-106">Další informace najdete v tématu [generování klientské knihovny datové služby](generating-the-data-service-client-library-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="3af74-106">For more information, see [Generating the Data Service Client Library](generating-the-data-service-client-library-wcf-data-services.md).</span></span>

## <a name="add-a-data-service-reference"></a><span data-ttu-id="3af74-107">Přidat odkaz na datovou službu</span><span class="sxs-lookup"><span data-stu-id="3af74-107">Add a data service reference</span></span>

1. <span data-ttu-id="3af74-108">Volitelné Pokud datová služba není součástí řešení a ještě není spuštěná, spusťte datovou službu a poznamenejte si identifikátor URI datové služby.</span><span class="sxs-lookup"><span data-stu-id="3af74-108">(Optional) If the data service is not part of the solution and is not already running, start the data service and note the URI of the data service.</span></span>

2. <span data-ttu-id="3af74-109">V aplikaci Visual Studio klikněte v **Průzkumník řešení**pravým tlačítkem myši na projekt klienta a vyberte možnost **Přidat** > odkaz na**službu**.</span><span class="sxs-lookup"><span data-stu-id="3af74-109">In Visual Studio, in **Solution Explorer**, right-click the client project and then select **Add** > **Service Reference**.</span></span>

3. <span data-ttu-id="3af74-110">Pokud je datová služba součástí aktuálního řešení, klikněte na tlačítko **zjistit**.</span><span class="sxs-lookup"><span data-stu-id="3af74-110">If the data service is part of the current solution, click **Discover**.</span></span>

     <span data-ttu-id="3af74-111">-nebo-</span><span class="sxs-lookup"><span data-stu-id="3af74-111">-or-</span></span>

     <span data-ttu-id="3af74-112">Do textového pole **adresa** zadejte základní adresu URL datové služby, například `http://localhost:1234/Northwind.svc`a potom klikněte na tlačítko **Přejít**.</span><span class="sxs-lookup"><span data-stu-id="3af74-112">In the **Address** text box, type the base URL of the data service, such as `http://localhost:1234/Northwind.svc`, and then click **Go**.</span></span>

4. <span data-ttu-id="3af74-113">Vyberte **OK**.</span><span class="sxs-lookup"><span data-stu-id="3af74-113">Select **OK**.</span></span>

     <span data-ttu-id="3af74-114">Do projektu se přidá nový soubor kódu, který obsahuje datové třídy, které mají přístup k prostředkům datové služby a budou s nimi pracovat.</span><span class="sxs-lookup"><span data-stu-id="3af74-114">A new code file that contains the data classes that can access and interact with data service resources is added to the project.</span></span>

## <a name="see-also"></a><span data-ttu-id="3af74-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3af74-115">See also</span></span>

- [<span data-ttu-id="3af74-116">Rychlý start</span><span class="sxs-lookup"><span data-stu-id="3af74-116">Quickstart</span></span>](quickstart-wcf-data-services.md)
