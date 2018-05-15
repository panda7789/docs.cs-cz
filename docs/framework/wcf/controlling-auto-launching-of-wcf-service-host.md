---
title: Ovládání automatického spouštění hostitele služeb WCF
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: 63c3ca00c0cdc0b28de0fe245b616acd04ca50fe
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a><span data-ttu-id="cf5a8-102">Ovládání automatického spouštění hostitele služeb WCF</span><span class="sxs-lookup"><span data-stu-id="cf5a8-102">Controlling Auto-launching of WCF Service Host</span></span>
<span data-ttu-id="cf5a8-103">Můžete ovládat funkce automatického spouštění hostitele služeb Windows Communication Foundation (WCF) (WcfSvcHost.exe) pro projekt knihovny služby WCF, při ladění projektu pro jiné ve stejném řešení sady Visual Studio obsahující více projektů.</span><span class="sxs-lookup"><span data-stu-id="cf5a8-103">You can control the auto-launching capability of Windows Communication Foundation (WCF) Service Host (WcfSvcHost.exe) for a WCF Service Library project, when you debug another project in the same Visual Studio solution containing multiple projects.</span></span>  
  
 <span data-ttu-id="cf5a8-104">Uděláte to tak, klikněte pravým tlačítkem na projekt služby WCF v **Průzkumníku řešení**, zvolte **vlastnosti**a klikněte na tlačítko **WCF možnosti** kartě. **Spustit hostitel služby WCF při ladění jiného projektu ve stejném řešení** zaškrtávací políčko je dostupné ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="cf5a8-104">To do so, right-click the WCF Service Project in **Solution Explorer**, choose **Properties**, and click **WCF Options** tab. The **Start WCF Service Host when debugging another project in the same solution** check box is enabled by default.</span></span> <span data-ttu-id="cf5a8-105">Pole můžete vymazat tak, aby hostitel služby WCF pro tento konkrétní projekt není spustí, když je ve stejném řešení ladit jiného projektu.</span><span class="sxs-lookup"><span data-stu-id="cf5a8-105">You can clear the box so that WCF Service Host for this specific project is not launched when another project is debugged in the same solution.</span></span>  
  
 <span data-ttu-id="cf5a8-106">Toto chování neovlivňuje ladění F5 nebo funkce Přidat odkaz na službu pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="cf5a8-106">This behavior does not affect the F5 debugging, or Add Service Reference functionalities for this project.</span></span>  
  
 <span data-ttu-id="cf5a8-107">Tato možnost je dostupná na následujících projektech:</span><span class="sxs-lookup"><span data-stu-id="cf5a8-107">This option is available to the following projects:</span></span>  
  
-   <span data-ttu-id="cf5a8-108">Projekt knihovny služby WCF.</span><span class="sxs-lookup"><span data-stu-id="cf5a8-108">WCF Service Library Project.</span></span>  
  
-   <span data-ttu-id="cf5a8-109">Projekt knihovny služby sekvenční pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="cf5a8-109">Sequential Workflow Service Library Project.</span></span>  
  
-   <span data-ttu-id="cf5a8-110">Projekt knihovny služby stavu počítače pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="cf5a8-110">State Machine Workflow Service Library Project.</span></span>  
  
-   <span data-ttu-id="cf5a8-111">Syndikace projektu knihovny služby.</span><span class="sxs-lookup"><span data-stu-id="cf5a8-111">Syndication Service Library Project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf5a8-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="cf5a8-112">See Also</span></span>  
 [<span data-ttu-id="cf5a8-113">Hostitel služby WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="cf5a8-113">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
