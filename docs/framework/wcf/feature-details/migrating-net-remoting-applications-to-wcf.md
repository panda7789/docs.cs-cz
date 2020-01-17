---
title: Migrace aplikací vzdálené komunikace .NET do WCF
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: 1d7edab8ad89660f3384d0ccf556384175c4d5db
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76212165"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a><span data-ttu-id="1566b-102">Migrace aplikací vzdálené komunikace .NET do WCF</span><span class="sxs-lookup"><span data-stu-id="1566b-102">Migrating .NET Remoting Applications to WCF</span></span>
<span data-ttu-id="1566b-103">**Toto téma je specifické pro starší verze technologie, která se zachovává kvůli zpětné kompatibilitě se stávajícími aplikacemi a nedoporučuje se pro nový vývoj. Distribuované aplikace by se teď měly vyvíjet pomocí WCF.**</span><span class="sxs-lookup"><span data-stu-id="1566b-103">**This topic is specific to a legacy technology that is retained for backward compatibility with existing applications and is not recommended for new development. Distributed applications should now be developed using WCF.**</span></span>  
  
 <span data-ttu-id="1566b-104">Existují dva způsoby, jak využít WCF se stávajícími aplikacemi vzdálené komunikace .NET: integrace a migrace.</span><span class="sxs-lookup"><span data-stu-id="1566b-104">There are two ways to take advantage of WCF with existing .NET Remoting applications: integration and migration.</span></span> <span data-ttu-id="1566b-105">Integrace umožňuje, aby se Vzdálená komunikace .NET 2,0 a WCF běžely souběžně, což vám umožní vystavit stejné obchodní objekty i přes obě technologie, aniž by bylo nutné měnit stávající kód vzdálené 2,0 komunikace v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="1566b-105">Integration allows you to have .NET Remoting 2.0 and WCF running side by side, letting you expose the same business objects over both technologies simultaneously without having to modify your existing .NET Remoting 2.0 code.</span></span> <span data-ttu-id="1566b-106">Integrace vyžaduje, abyste spustili .NET Framework 2,0 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="1566b-106">Integration requires that you are running on .NET Framework 2.0 or greater.</span></span> <span data-ttu-id="1566b-107">Pokud chcete využít výhod funkcí WCF a nepotřebujete kompatibilitu s komunikací se systémy vzdálené komunikace 2,0, můžete migrovat celou službu na WCF.</span><span class="sxs-lookup"><span data-stu-id="1566b-107">If you want to take advantage of WCF features and do not need wire compatibility with Remoting 2.0 systems, you can migrate your entire service to WCF.</span></span> <span data-ttu-id="1566b-108">Migrace z technologie vzdálené komunikace .NET 2,0 na WCF vyžaduje změny rozhraní vzdáleného objektu a jeho nastavení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="1566b-108">Migration from .NET Remoting 2.0 to WCF requires changes to the remote object's interface and its configuration settings.</span></span> <span data-ttu-id="1566b-109">Obě tato témata jsou popsaná v tématu [Vzdálená komunikace s Windows Communication Foundation](https://docs.microsoft.com/previous-versions/aa730857(v=vs.80)).</span><span class="sxs-lookup"><span data-stu-id="1566b-109">Both of these topics are covered in [From Remoting to the Windows Communication Foundation](https://docs.microsoft.com/previous-versions/aa730857(v=vs.80)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1566b-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1566b-110">See also</span></span>

- [<span data-ttu-id="1566b-111">Koncepční přehled</span><span class="sxs-lookup"><span data-stu-id="1566b-111">Conceptual Overview</span></span>](../../../../docs/framework/wcf/conceptual-overview.md)
