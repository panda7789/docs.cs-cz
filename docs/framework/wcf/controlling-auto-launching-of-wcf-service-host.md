---
title: Ovládání automatického spouštění hostitele služeb WCF
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: f7f58a684449819fe945ad1ba5bff12f425c8294
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54712389"
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a><span data-ttu-id="13ecb-102">Ovládání automatického spouštění hostitele služeb WCF</span><span class="sxs-lookup"><span data-stu-id="13ecb-102">Controlling Auto-launching of WCF Service Host</span></span>
<span data-ttu-id="13ecb-103">Můžete řídit funkce automatického spouštění hostitele služeb Windows Communication Foundation (WCF) (WcfSvcHost.exe) pro projekt knihovny služby WCF při ladění jiného projektu ve stejném řešení sady Visual Studio obsahuje více projektů.</span><span class="sxs-lookup"><span data-stu-id="13ecb-103">You can control the auto-launching capability of Windows Communication Foundation (WCF) Service Host (WcfSvcHost.exe) for a WCF Service Library project, when you debug another project in the same Visual Studio solution containing multiple projects.</span></span>  
  
 <span data-ttu-id="13ecb-104">Uděláte to tak, klikněte pravým tlačítkem na projekt služby WCF v **Průzkumníka řešení**, zvolte **vlastnosti**a klikněte na tlačítko **možnosti WCF** kartu. **Spuštění hostitele služby WCF při ladění jiného projektu ve stejném řešení** zaškrtávací políčko je dostupné ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="13ecb-104">To do so, right-click the WCF Service Project in **Solution Explorer**, choose **Properties**, and click **WCF Options** tab. The **Start WCF Service Host when debugging another project in the same solution** check box is enabled by default.</span></span> <span data-ttu-id="13ecb-105">Do pole můžete vymazat tak, aby hostitel služby WCF pro tento konkrétní projekt není spuštěn při ladění jiného projektu ve stejném řešení.</span><span class="sxs-lookup"><span data-stu-id="13ecb-105">You can clear the box so that WCF Service Host for this specific project is not launched when another project is debugged in the same solution.</span></span>  
  
 <span data-ttu-id="13ecb-106">Toto chování neovlivňuje ladění F5 nebo přidat odkaz na službu funkcích pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="13ecb-106">This behavior does not affect the F5 debugging, or Add Service Reference functionalities for this project.</span></span>  
  
 <span data-ttu-id="13ecb-107">Tato možnost je k dispozici pro následující projekty:</span><span class="sxs-lookup"><span data-stu-id="13ecb-107">This option is available to the following projects:</span></span>  
  
-   <span data-ttu-id="13ecb-108">Projekt knihovny služby WCF.</span><span class="sxs-lookup"><span data-stu-id="13ecb-108">WCF Service Library Project.</span></span>  
  
-   <span data-ttu-id="13ecb-109">Projekt knihovna služby sekvenčního pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="13ecb-109">Sequential Workflow Service Library Project.</span></span>  
  
-   <span data-ttu-id="13ecb-110">Projekt knihovny služby pracovního postupu stavového stroje.</span><span class="sxs-lookup"><span data-stu-id="13ecb-110">State Machine Workflow Service Library Project.</span></span>  
  
-   <span data-ttu-id="13ecb-111">Projekt knihovna služby syndikace.</span><span class="sxs-lookup"><span data-stu-id="13ecb-111">Syndication Service Library Project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13ecb-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="13ecb-112">See also</span></span>
- [<span data-ttu-id="13ecb-113">Hostitel služby WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="13ecb-113">WCF Service Host (WcfSvcHost.exe)</span></span>](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
