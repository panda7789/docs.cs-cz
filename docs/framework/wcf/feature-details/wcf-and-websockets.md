---
title: WCF a WebSockets
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e53b49e-022c-49c7-8984-4b21b53c05b3
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 225bff20f514a653382f01becf133659dec4c5f0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-and-websockets"></a>WCF a WebSockets
Rozhraní .NET Framework 4.5 zavádí podporu pro objekty WebSockets ve službě Windows Communication Foundation.  Technologie WebSockets je efektivní, založených na standardech technologie, která umožňuje obousměrnou komunikaci přes standardní HTTP porty 80 a 443. Použití standardní porty protokolu HTTP umožňuje objekty WebSockets ke komunikaci prostřednictvím webu prostřednictvím zprostředkovatelů.  Aby mohly podporovat komunikaci pomocí přenosového protokolu WebSocket byly přidány dva nové standardní vazby. <xref:System.ServiceModel.NetHttpBinding>a <xref:System.ServiceModel.NetHttpsBinding>. Nastavení specifických pro objekty WebSockets lze nakonfigurovat podle <xref:System.ServiceModel.Channels.HttpTransportBindingElement> přímým přístupem <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> vlastnost.
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Používání vazeb NetHttpBinding](../../../../docs/framework/wcf/feature-details/using-the-nethttpbinding.md)  
 Popisuje <xref:System.ServiceModel.NetHttpBinding> a jeho konfiguraci.  
  
 [Postupy: vytvoření služby WCF, který komunikuje přes objekty WebSockets](../../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-service-that-communicates-over-websockets.md)  
 Popisuje postup vytvoření služby WCF, který komunikuje přes objekty Websockets.  
  
## <a name="reference"></a>Odkaz  
  
## <a name="related-sections"></a>Související oddíly
