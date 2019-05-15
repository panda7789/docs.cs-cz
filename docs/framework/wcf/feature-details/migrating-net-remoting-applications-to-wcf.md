---
title: Migrace aplikací vzdálené komunikace .NET do WCF
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: c0ce7c9badc8bad6eedc58827b6efe2595ab2cf8
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592863"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a><span data-ttu-id="f216d-102">Migrace aplikací vzdálené komunikace .NET do WCF</span><span class="sxs-lookup"><span data-stu-id="f216d-102">Migrating .NET Remoting Applications to WCF</span></span>
<span data-ttu-id="f216d-103">**Toto téma se věnuje starší technologie, která se zachovává kvůli zpětné kompatibilitě se stávajícími aplikacemi a nedoporučuje se používat pro vývoj nových projektů. Distribuované aplikace by měla nyní být vyvinuto s použitím WCF.**</span><span class="sxs-lookup"><span data-stu-id="f216d-103">**This topic is specific to a legacy technology that is retained for backward compatibility with existing applications and is not recommended for new development. Distributed applications should now be developed using WCF.**</span></span>  
  
 <span data-ttu-id="f216d-104">Existují dva způsoby, jak využít výhod WCF se stávajícími aplikacemi .NET Remoting: integrace a migrace.</span><span class="sxs-lookup"><span data-stu-id="f216d-104">There are two ways to take advantage of WCF with existing .NET Remoting applications: integration and migration.</span></span> <span data-ttu-id="f216d-105">Integrace umožňuje mít 2.0 vzdálené komunikace .NET a WCF souběžné spuštění, umožňuje vystavit stejné objekty obchodní přes obou technologií současně, aniž byste museli změnit váš stávající kód 2.0 vzdálené komunikace .NET.</span><span class="sxs-lookup"><span data-stu-id="f216d-105">Integration allows you to have .NET Remoting 2.0 and WCF running side by side, letting you expose the same business objects over both technologies simultaneously without having to modify your existing .NET Remoting 2.0 code.</span></span> <span data-ttu-id="f216d-106">Integrace vyžaduje také, že používáte v rozhraní .NET Framework 2.0 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="f216d-106">Integration requires that you are running on .NET Framework 2.0 or greater.</span></span> <span data-ttu-id="f216d-107">Pokud chcete využít výhod funkcí WCF a není nutné kompatibility při přenosu pomocí vzdálené komunikace 2.0 systémů, můžete migrovat celou službu do WCF.</span><span class="sxs-lookup"><span data-stu-id="f216d-107">If you want to take advantage of WCF features and do not need wire compatibility with Remoting 2.0 systems, you can migrate your entire service to WCF.</span></span> <span data-ttu-id="f216d-108">Migrace z verze 2.0 vzdálené komunikace .NET na WCF vyžaduje změny v rozhraní vzdáleného objektu a jeho nastavení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="f216d-108">Migration from .NET Remoting 2.0 to WCF requires changes to the remote object's interface and its configuration settings.</span></span> <span data-ttu-id="f216d-109">Obě tato témata se věnují [ze vzdálené komunikace Windows Communication Foundation](https://go.microsoft.com/fwlink/?LinkId=74403).</span><span class="sxs-lookup"><span data-stu-id="f216d-109">Both of these topics are covered in [From Remoting to the Windows Communication Foundation](https://go.microsoft.com/fwlink/?LinkId=74403).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f216d-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f216d-110">See also</span></span>

- [<span data-ttu-id="f216d-111">Koncepční přehled</span><span class="sxs-lookup"><span data-stu-id="f216d-111">Conceptual Overview</span></span>](../../../../docs/framework/wcf/conceptual-overview.md)
