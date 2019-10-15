---
title: Ovládání automatického spouštění hostitele služeb WCF
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: 7f21cd7ea600277461146387b962a89ea0a8472b
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320630"
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a><span data-ttu-id="1ea65-102">Ovládání automatického spouštění hostitele služeb WCF</span><span class="sxs-lookup"><span data-stu-id="1ea65-102">Controlling Auto-launching of WCF Service Host</span></span>
<span data-ttu-id="1ea65-103">Můžete řídit schopnost automatického spouštění hostitele služby Windows Communication Foundation (WCF) pro projekt knihovny služby WCF (WcfSvcHost. exe), při ladění jiného projektu ve stejném řešení sady Visual Studio, které obsahuje více projektů.</span><span class="sxs-lookup"><span data-stu-id="1ea65-103">You can control the auto-launching capability of Windows Communication Foundation (WCF) Service Host (WcfSvcHost.exe) for a WCF Service Library project, when you debug another project in the same Visual Studio solution containing multiple projects.</span></span>  
  
 <span data-ttu-id="1ea65-104">Provedete to tak, že kliknete pravým tlačítkem na projekt služby WCF v **Průzkumník řešení**, zvolíte **vlastnosti**a kliknete na kartu **Možnosti WCF** . V případě, že je ve výchozím nastavení zaškrtnuté políčko **spustit hostitele služby WCF při ladění jiného projektu ve stejném řešení** , je povolené.</span><span class="sxs-lookup"><span data-stu-id="1ea65-104">To do so, right-click the WCF Service Project in **Solution Explorer**, choose **Properties**, and click **WCF Options** tab. The **Start WCF Service Host when debugging another project in the same solution** check box is enabled by default.</span></span> <span data-ttu-id="1ea65-105">Toto políčko můžete zrušit, aby se hostitel služby WCF pro tento konkrétní projekt nespustil při ladění jiného projektu ve stejném řešení.</span><span class="sxs-lookup"><span data-stu-id="1ea65-105">You can clear the box so that WCF Service Host for this specific project is not launched when another project is debugged in the same solution.</span></span>  
  
 <span data-ttu-id="1ea65-106">Toto chování nemá vliv na ladění F5 ani Přidat odkaz na službu funkce pro tento projekt.</span><span class="sxs-lookup"><span data-stu-id="1ea65-106">This behavior does not affect the F5 debugging, or Add Service Reference functionalities for this project.</span></span>  
  
 <span data-ttu-id="1ea65-107">Tato možnost je k dispozici pro následující projekty:</span><span class="sxs-lookup"><span data-stu-id="1ea65-107">This option is available to the following projects:</span></span>  
  
- <span data-ttu-id="1ea65-108">Projekt knihovny služby WCF.</span><span class="sxs-lookup"><span data-stu-id="1ea65-108">WCF Service Library Project.</span></span>  
  
- <span data-ttu-id="1ea65-109">Projekt knihovny služby sekvenčního pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="1ea65-109">Sequential Workflow Service Library Project.</span></span>  
  
- <span data-ttu-id="1ea65-110">Projekt knihovny služby pracovního postupu stavového stroje</span><span class="sxs-lookup"><span data-stu-id="1ea65-110">State Machine Workflow Service Library Project.</span></span>  
  
- <span data-ttu-id="1ea65-111">Projekt s knihovnou služby syndikace.</span><span class="sxs-lookup"><span data-stu-id="1ea65-111">Syndication Service Library Project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ea65-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1ea65-112">See also</span></span>

- [<span data-ttu-id="1ea65-113">Hostitel služby WCF (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="1ea65-113">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)
