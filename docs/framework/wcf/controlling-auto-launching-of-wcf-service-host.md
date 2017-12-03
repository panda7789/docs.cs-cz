---
title: "Ovládání automatického spouštění hostitele služeb WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 60c7e2ddd4d4d57b675f2c12f8c5f567e8d23020
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a><span data-ttu-id="e09d5-102">Ovládání automatického spouštění hostitele služeb WCF</span><span class="sxs-lookup"><span data-stu-id="e09d5-102">Controlling Auto-launching of WCF Service Host</span></span>
<span data-ttu-id="e09d5-103">Můžete řídit funkci automatického spouštění systému [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] hostitel služby (WcfSvcHost.exe) pro [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] projektu knihovny služby, při ladění projektu pro jiné ve stejné [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] řešení obsahující více projektů.</span><span class="sxs-lookup"><span data-stu-id="e09d5-103">You can control the auto-launching capability of [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] Service Host (WcfSvcHost.exe) for a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Library project, when you debug another project in the same [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] solution containing multiple projects.</span></span>  
  
 <span data-ttu-id="e09d5-104">To pokud chcete udělat, klikněte pravým tlačítkem myši [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] projektu služby v **Průzkumníku řešení**, zvolte **vlastnosti**a klikněte na tlačítko **WCF možnosti** kartě. **Spustit hostitel služby WCF při ladění jiného projektu ve stejném řešení** zaškrtávací políčko je dostupné ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="e09d5-104">To do so, right-click the [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Project in **Solution Explorer**, choose **Properties**, and click **WCF Options** tab. The **Start WCF Service Host when debugging another project in the same solution** check box is enabled by default.</span></span> <span data-ttu-id="e09d5-105">Můžete vymazat pole tak, aby [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] hostitele služby pro tento konkrétní projekt není spustí, když je ve stejném řešení ladit jiného projektu.</span><span class="sxs-lookup"><span data-stu-id="e09d5-105">You can clear the box so that [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] Service Host for this specific project is not launched when another project is debugged in the same solution.</span></span>  
  
 <span data-ttu-id="e09d5-106">Toto chování neovlivňuje ladění F5 nebo funkce Přidat odkaz na službu pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="e09d5-106">This behavior does not affect the F5 debugging, or Add Service Reference functionalities for this project.</span></span>  
  
 <span data-ttu-id="e09d5-107">Tato možnost je dostupná na následujících projektech:</span><span class="sxs-lookup"><span data-stu-id="e09d5-107">This option is available to the following projects:</span></span>  
  
-   [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]<span data-ttu-id="e09d5-108">Projekt knihovny služby.</span><span class="sxs-lookup"><span data-stu-id="e09d5-108"> Service Library Project.</span></span>  
  
-   <span data-ttu-id="e09d5-109">Projekt knihovny služby sekvenční pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="e09d5-109">Sequential Workflow Service Library Project.</span></span>  
  
-   <span data-ttu-id="e09d5-110">Projekt knihovny služby stavu počítače pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="e09d5-110">State Machine Workflow Service Library Project.</span></span>  
  
-   <span data-ttu-id="e09d5-111">Syndikace projektu knihovny služby.</span><span class="sxs-lookup"><span data-stu-id="e09d5-111">Syndication Service Library Project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e09d5-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="e09d5-112">See Also</span></span>  
 [<span data-ttu-id="e09d5-113">Hostitel služby WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="e09d5-113">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
