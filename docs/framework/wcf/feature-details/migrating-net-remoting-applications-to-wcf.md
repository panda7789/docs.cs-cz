---
title: Migrace aplikací vzdálené komunikace .NET do WCF
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: 96018b775b858e8ac0d0221135cb5109b0cd81d3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54509997"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a><span data-ttu-id="86326-102">Migrace aplikací vzdálené komunikace .NET do WCF</span><span class="sxs-lookup"><span data-stu-id="86326-102">Migrating .NET Remoting Applications to WCF</span></span>
<span data-ttu-id="86326-103">**Toto téma se věnuje starší technologie, která se zachovává kvůli zpětné kompatibilitě se stávajícími aplikacemi a nedoporučuje se používat pro vývoj nových projektů. Distribuované aplikace by měla nyní být vyvinuto s použitím WCF.**</span><span class="sxs-lookup"><span data-stu-id="86326-103">**This topic is specific to a legacy technology that is retained for backward compatibility with existing applications and is not recommended for new development. Distributed applications should now be developed using WCF.**</span></span>  
  
 <span data-ttu-id="86326-104">Existují dva způsoby, jak využít výhod WCF se stávajícími aplikacemi .NET Remoting: integrace a migrace.</span><span class="sxs-lookup"><span data-stu-id="86326-104">There are two ways to take advantage of WCF with existing .NET Remoting applications: integration and migration.</span></span> <span data-ttu-id="86326-105">Integrace umožňuje mít .net Remoting 2.0 a WCF s kódem na straně sebe, umožňuje vystavit stejné objekty obchodní přes obě technologie současně bez nutnosti upravovat vaše existující rozhraní .net 2.0 vzdálené komunikace.</span><span class="sxs-lookup"><span data-stu-id="86326-105">Integration allows you to have .Net Remoting 2.0 and WCF running side by side, letting you expose the same business objects over both technologies simultaneously without having to modify your existing .Net Remoting 2.0 code.</span></span> <span data-ttu-id="86326-106">Integrace vyžaduje, zda jsou spuštěny [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="86326-106">Integration requires that you are running on [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 or greater.</span></span> <span data-ttu-id="86326-107">Pokud chcete využít výhod funkcí WCF a není nutné kompatibility při přenosu pomocí vzdálené komunikace 2.0 systémů, můžete migrovat celou službu do WCF.</span><span class="sxs-lookup"><span data-stu-id="86326-107">If you want to take advantage of WCF features and do not need wire compatibility with Remoting 2.0 systems, you can migrate your entire service to WCF.</span></span> <span data-ttu-id="86326-108">Migrace z verze 2.0 vzdálené komunikace .NET na WCF vyžaduje změny v rozhraní vzdáleného objektu a jeho nastavení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="86326-108">Migration from .NET Remoting 2.0 to WCF requires changes to the remote object's interface and its configuration settings.</span></span> <span data-ttu-id="86326-109">Obě tato témata se věnují [ze vzdálené komunikace Windows Communication Foundation](https://go.microsoft.com/fwlink/?LinkId=74403).</span><span class="sxs-lookup"><span data-stu-id="86326-109">Both of these topics are covered in [From Remoting to the Windows Communication Foundation](https://go.microsoft.com/fwlink/?LinkId=74403).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86326-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="86326-110">See also</span></span>
- [<span data-ttu-id="86326-111">Koncepční přehled</span><span class="sxs-lookup"><span data-stu-id="86326-111">Conceptual Overview</span></span>](../../../../docs/framework/wcf/conceptual-overview.md)
