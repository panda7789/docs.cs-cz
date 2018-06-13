---
title: Migrace aplikací vzdálené komunikace .NET do WCF
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: 53f63352503a48ee849580e676b5fe98f3dcf2cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492493"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a><span data-ttu-id="d9066-102">Migrace aplikací vzdálené komunikace .NET do WCF</span><span class="sxs-lookup"><span data-stu-id="d9066-102">Migrating .NET Remoting Applications to WCF</span></span>
<span data-ttu-id="d9066-103">**Toto téma je specifické pro starší verze technologie, která se zachovává kvůli zpětné kompatibilitě se stávajícími aplikacemi a nedoporučuje se používat pro vývoj. Distribuované aplikace by měla být nyní vyvinuté pomocí WCF.**</span><span class="sxs-lookup"><span data-stu-id="d9066-103">**This topic is specific to a legacy technology that is retained for backward compatibility with existing applications and is not recommended for new development. Distributed applications should now be developed using WCF.**</span></span>  
  
 <span data-ttu-id="d9066-104">Existují dva způsoby, jak využít výhod WCF se stávajícími aplikacemi .NET Remoting: integrace a migrace.</span><span class="sxs-lookup"><span data-stu-id="d9066-104">There are two ways to take advantage of WCF with existing .NET Remoting applications: integration and migration.</span></span> <span data-ttu-id="d9066-105">Integrace umožňuje, abyste měli .net Remoting 2.0 a WCF s kódem na straně stranou, umožňuje vystavit stejné objekty obchodní přes obě technologie současně, bez nutnosti upravovat vaše stávající rozhraní .net 2.0 vzdálenou komunikaci.</span><span class="sxs-lookup"><span data-stu-id="d9066-105">Integration allows you to have .Net Remoting 2.0 and WCF running side by side, letting you expose the same business objects over both technologies simultaneously without having to modify your existing .Net Remoting 2.0 code.</span></span> <span data-ttu-id="d9066-106">Integrace vyžaduje, že používáte [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="d9066-106">Integration requires that you are running on [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 or greater.</span></span> <span data-ttu-id="d9066-107">Pokud chcete využít výhod funkce WCF a není nutné přenosová kompatibilitu s systémy 2.0 vzdálenou komunikaci, můžete migrovat celou službou WCF.</span><span class="sxs-lookup"><span data-stu-id="d9066-107">If you want to take advantage of WCF features and do not need wire compatibility with Remoting 2.0 systems, you can migrate your entire service to WCF.</span></span> <span data-ttu-id="d9066-108">Migrace z .NET Remoting 2.0 do WCF vyžaduje změny ke vzdálenému objektu rozhraní a jeho nastavení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="d9066-108">Migration from .NET Remoting 2.0 to WCF requires changes to the remote object's interface and its configuration settings.</span></span> <span data-ttu-id="d9066-109">Obě tato témata jsou popsané v [ze vzdálené komunikace do služby Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkId=74403).</span><span class="sxs-lookup"><span data-stu-id="d9066-109">Both of these topics are covered in [From Remoting to the Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkId=74403).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9066-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="d9066-110">See Also</span></span>  
 [<span data-ttu-id="d9066-111">Koncepční přehled</span><span class="sxs-lookup"><span data-stu-id="d9066-111">Conceptual Overview</span></span>](../../../../docs/framework/wcf/conceptual-overview.md)
