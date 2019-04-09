---
title: Migrace aplikací vzdálené komunikace .NET do WCF
ms.date: 03/30/2017
helpviewer_keywords:
- ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
ms.openlocfilehash: 4040fb0ac223f91705a49b733f6a1f42d144068e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091110"
---
# <a name="migrating-net-remoting-applications-to-wcf"></a><span data-ttu-id="a33da-102">Migrace aplikací vzdálené komunikace .NET do WCF</span><span class="sxs-lookup"><span data-stu-id="a33da-102">Migrating .NET Remoting Applications to WCF</span></span>
**<span data-ttu-id="a33da-103">Toto téma se věnuje starší technologie, která se zachovává kvůli zpětné kompatibilitě se stávajícími aplikacemi a nedoporučuje se používat pro vývoj nových projektů.</span><span class="sxs-lookup"><span data-stu-id="a33da-103">This topic is specific to a legacy technology that is retained for backward compatibility with existing applications and is not recommended for new development.</span></span> <span data-ttu-id="a33da-104">Distribuované aplikace by měla nyní být vyvinuto s použitím WCF.</span><span class="sxs-lookup"><span data-stu-id="a33da-104">Distributed applications should now be developed using WCF.</span></span>**  
  
 <span data-ttu-id="a33da-105">Existují dva způsoby, jak využít výhod WCF se stávajícími aplikacemi .NET Remoting: integrace a migrace.</span><span class="sxs-lookup"><span data-stu-id="a33da-105">There are two ways to take advantage of WCF with existing .NET Remoting applications: integration and migration.</span></span> <span data-ttu-id="a33da-106">Integrace umožňuje mít 2.0 vzdálené komunikace .NET a WCF souběžné spuštění, umožňuje vystavit stejné objekty obchodní přes obou technologií současně, aniž byste museli změnit váš stávající kód 2.0 vzdálené komunikace .NET.</span><span class="sxs-lookup"><span data-stu-id="a33da-106">Integration allows you to have .NET Remoting 2.0 and WCF running side by side, letting you expose the same business objects over both technologies simultaneously without having to modify your existing .NET Remoting 2.0 code.</span></span> <span data-ttu-id="a33da-107">Integrace vyžaduje, zda jsou spuštěny [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="a33da-107">Integration requires that you are running on [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 or greater.</span></span> <span data-ttu-id="a33da-108">Pokud chcete využít výhod funkcí WCF a není nutné kompatibility při přenosu pomocí vzdálené komunikace 2.0 systémů, můžete migrovat celou službu do WCF.</span><span class="sxs-lookup"><span data-stu-id="a33da-108">If you want to take advantage of WCF features and do not need wire compatibility with Remoting 2.0 systems, you can migrate your entire service to WCF.</span></span> <span data-ttu-id="a33da-109">Migrace z verze 2.0 vzdálené komunikace .NET na WCF vyžaduje změny v rozhraní vzdáleného objektu a jeho nastavení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="a33da-109">Migration from .NET Remoting 2.0 to WCF requires changes to the remote object's interface and its configuration settings.</span></span> <span data-ttu-id="a33da-110">Obě tato témata se věnují [ze vzdálené komunikace Windows Communication Foundation](https://go.microsoft.com/fwlink/?LinkId=74403).</span><span class="sxs-lookup"><span data-stu-id="a33da-110">Both of these topics are covered in [From Remoting to the Windows Communication Foundation](https://go.microsoft.com/fwlink/?LinkId=74403).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a33da-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a33da-111">See also</span></span>

- [<span data-ttu-id="a33da-112">Koncepční přehled</span><span class="sxs-lookup"><span data-stu-id="a33da-112">Conceptual Overview</span></span>](../../../../docs/framework/wcf/conceptual-overview.md)
