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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 240901f4fa04a2468d5964821680506ea117bf7f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="migrating-net-remoting-applications-to-wcf"></a>Migrace aplikací vzdálené komunikace .NET do WCF
**Toto téma je specifické pro starší verze technologie, která se zachovává kvůli zpětné kompatibilitě se stávajícími aplikacemi a nedoporučuje se používat pro vývoj. Distribuované aplikace by měla vyvinuté teď pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].**  
  
 Existují dva způsoby, jak využít výhod [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] se stávajícími aplikacemi .NET Remoting: integrace a migrace. Integrace umožňuje, abyste měli rozhraní .net 2.0 vzdálenou komunikaci a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] spuštění vedle sebe, když necháte vystavit stejné objekty obchodní přes obě technologie současně bez nutnosti upravovat vaše stávající rozhraní .net 2.0 vzdálenou komunikaci kódu. Integrace vyžaduje, že používáte [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 2.0 nebo vyšší. Pokud chcete využít výhod [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] funkce a nechcete nemusí propojit kompatibilitu s systémy 2.0 vzdálenou komunikaci, můžete migrovat celou služby [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Migrace z .NET Remoting 2.0 k [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vyžaduje změny ke vzdálenému objektu rozhraní a jeho nastavení konfigurace. Obě tato témata jsou popsané v [ze vzdálené komunikace do služby Windows Communication Foundation](http://go.microsoft.com/fwlink/?LinkId=74403).  
  
## <a name="see-also"></a>Viz také  
 [Koncepční přehled](../../../../docs/framework/wcf/conceptual-overview.md)
