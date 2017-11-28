---
title: "Přidání odkazu na službu do řešení pracovního postupu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83574cf3-9803-49bc-837f-432936dc9c76
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 511ff8fa982e9a9ca29faf714725626f7925f659
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="adding-a-service-reference-in-a-workflow-solution"></a><span data-ttu-id="a4d0c-102">Přidání odkazu na službu do řešení pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="a4d0c-102">Adding a Service Reference in a Workflow Solution</span></span>
<span data-ttu-id="a4d0c-103">Přidání odkazu na službu do pracovního postupu aplikace funguje trochu jinak, než regulární aplikace WCF.</span><span class="sxs-lookup"><span data-stu-id="a4d0c-103">Adding a service reference in a workflow application works a little differently than a regular WCF application.</span></span> <span data-ttu-id="a4d0c-104">Když vyberete Přidat odkaz na službu a zadejte adresu URL služby stáhne metadata a jsou generovány vlastních aktivit, které vám umožní volání služby WCF nebo pracovního postupu služby WCF přidat odkaz na.</span><span class="sxs-lookup"><span data-stu-id="a4d0c-104">When you select Add Service Reference and specify the URL to the service the metadata is downloaded and custom activities are generated that allow you to call the WCF service or WCF workflow service you added a reference to.</span></span> <span data-ttu-id="a4d0c-105">Po přidání odkazu na službu, znovu sestavte řešení, tak generovaného aktivity jsou vytvořeny.</span><span class="sxs-lookup"><span data-stu-id="a4d0c-105">After adding a service reference, rebuild the solution so the generated activities are built.</span></span> <span data-ttu-id="a4d0c-106">Se potom zobrazí v panelu nástrojů Návrháře pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="a4d0c-106">They will then appear in the workflow designer toolbox.</span></span> <span data-ttu-id="a4d0c-107">Všimněte si však, že bude fungovat pouze pokud přidáváte odkazu na službu v rámci řešení pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="a4d0c-107">Note however, that this will only work if you are adding a service reference within a workflow solution.</span></span> <span data-ttu-id="a4d0c-108">Následující webové přetypování ukazuje, jak přidat odkaz na službu v jiné typy projektů: [volání z pracovního postupu v projektu webové služby WCF](http://go.microsoft.com/fwlink/?LinkId=207725).</span><span class="sxs-lookup"><span data-stu-id="a4d0c-108">The following web cast shows how to add a service reference in other types of projects: [Calling a WCF Service from a Workflow in a Web Project](http://go.microsoft.com/fwlink/?LinkId=207725).</span></span>  
  
 <span data-ttu-id="a4d0c-109">Přidání dvou nebo více odkazů na služby pro služby, které obsahují stejný název operace způsobí, že problém.</span><span class="sxs-lookup"><span data-stu-id="a4d0c-109">Adding two or more service references to services that contain the same operation name will cause a problem.</span></span> <span data-ttu-id="a4d0c-110">Vygenerovaný aktivity bude volat pouze první operaci služby.</span><span class="sxs-lookup"><span data-stu-id="a4d0c-110">The generated activities will call only the first service operation.</span></span> <span data-ttu-id="a4d0c-111">Chcete-li vyřešit tento problém přejmenování operací služby tak, aby se liší nebo změňte název konfigurace koncového bodu uvnitř generovaného aktivity.</span><span class="sxs-lookup"><span data-stu-id="a4d0c-111">To work around this issue rename the service operations so they are different or change the endpoint configuration name within each generated activity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4d0c-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="a4d0c-112">See Also</span></span>  
 [<span data-ttu-id="a4d0c-113">Služby pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="a4d0c-113">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="a4d0c-114">Postupy: vytvoření služby pracovního postupu, který volá jinou službu pracovních postupů</span><span class="sxs-lookup"><span data-stu-id="a4d0c-114">How to: Create a Workflow Service That Calls Another Workflow Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-that-calls-another-workflow-service.md)  
 [<span data-ttu-id="a4d0c-115">Volání z pracovního postupu v projektu webové služby WCF</span><span class="sxs-lookup"><span data-stu-id="a4d0c-115">Calling a WCF Service from a Workflow in a Web Project</span></span>](http://go.microsoft.com/fwlink/?LinkId=207725)
