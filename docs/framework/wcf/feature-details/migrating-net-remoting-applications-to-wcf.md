---
title: "Migrace aplikací vzdálené komunikace .NET do WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ',NET remoting [WCF]'
ms.assetid: 24793465-65ae-4308-8c12-dce4fd12a583
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dff06fbc52c0f4371abf0bcc465fd6a6d8be5859
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="migrating-net-remoting-applications-to-wcf"></a><span data-ttu-id="4b884-102">Migrace aplikací vzdálené komunikace .NET do WCF</span><span class="sxs-lookup"><span data-stu-id="4b884-102">Migrating .NET Remoting Applications to WCF</span></span>
<span data-ttu-id="4b884-103">**Toto téma je specifické pro starší verze technologie, která se zachovává kvůli zpětné kompatibilitě se stávajícími aplikacemi a nedoporučuje se používat pro vývoj. Distribuované aplikace by měla vyvinuté teď pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].**</span><span class="sxs-lookup"><span data-stu-id="4b884-103">**This topic is specific to a legacy technology that is retained for backward compatibility with existing applications and is not recommended for new development. Distributed applications should now be developed using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].**</span></span>  
  
 <span data-ttu-id="4b884-104">Existují dva způsoby, jak využít výhod [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] se stávajícími aplikacemi .NET Remoting: integrace a migrace.</span><span class="sxs-lookup"><span data-stu-id="4b884-104">There are two ways to take advantage of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] with existing .NET Remoting applications: integration and migration.</span></span> <span data-ttu-id="4b884-105">Integrace umožňuje, abyste měli rozhraní .net 2.0 vzdálenou komunikaci a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] spuštění vedle sebe, když necháte vystavit stejné objekty obchodní přes obě technologie současně bez nutnosti upravovat vaše stávající rozhraní .net 2.0 vzdálenou komunikaci kódu.</span><span class="sxs-lookup"><span data-stu-id="4b884-105">Integration allows you to have .Net Remoting 2.0 and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] running side by side, letting you expose the same business objects over both technologies simultaneously without having to modify your existing .Net Remoting 2.0 code.</span></span> <span data-ttu-id="4b884-106">Integrace vyžaduje, že používáte [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="4b884-106">Integration requires that you are running on [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 or greater.</span></span> <span data-ttu-id="4b884-107">Pokud chcete využít výhod [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] funkce a nechcete nemusí propojit kompatibilitu s systémy 2.0 vzdálenou komunikaci, můžete migrovat celou služby [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4b884-107">If you want to take advantage of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] features and do not need wire compatibility with Remoting 2.0 systems, you can migrate your entire service to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="4b884-108">Migrace z .NET Remoting 2.0 k [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vyžaduje změny ke vzdálenému objektu rozhraní a jeho nastavení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="4b884-108">Migration from .NET Remoting 2.0 to [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] requires changes to the remote object's interface and its configuration settings.</span></span> <span data-ttu-id="4b884-109">Obě tato témata jsou popsané v [ze vzdálené komunikace do služby Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkId=74403).</span><span class="sxs-lookup"><span data-stu-id="4b884-109">Both of these topics are covered in [From Remoting to the Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkId=74403).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b884-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="4b884-110">See Also</span></span>  
 [<span data-ttu-id="4b884-111">Koncepční přehled</span><span class="sxs-lookup"><span data-stu-id="4b884-111">Conceptual Overview</span></span>](../../../../docs/framework/wcf/conceptual-overview.md)
