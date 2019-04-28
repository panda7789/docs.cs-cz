---
title: WCF a WebSockets
ms.date: 03/30/2017
ms.assetid: 1e53b49e-022c-49c7-8984-4b21b53c05b3
ms.openlocfilehash: ac888db14ebd21c4aed2f717c1f71bed310b8388
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768729"
---
# <a name="wcf-and-websockets"></a>WCF a WebSockets
Rozhraní .NET Framework 4.5 zavádí podporu pro objekty Websocket ve Windows Communication Foundation.  Protokoly Websocket je efektivní, založené na standardech technologie, které umožňuje obousměrnou komunikaci přes standardní HTTP porty 80 a 443. Použití standardní porty HTTP umožnit WebSockets komunikace prostřednictvím zprostředkovatelů na webu.  Aby mohly podporovat komunikaci pomocí protokolu WebSocket přenosového byly přidány dva nové standardní vazby. <xref:System.ServiceModel.NetHttpBinding> a <xref:System.ServiceModel.NetHttpsBinding>. Nastavení pro konkrétní objekty Websocket lze nakonfigurovat podle <xref:System.ServiceModel.Channels.HttpTransportBindingElement> díky přístupu do <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> vlastnost.
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Používání NetHttpBinding](../../../../docs/framework/wcf/feature-details/using-the-nethttpbinding.md)  
 Tento článek popisuje <xref:System.ServiceModel.NetHttpBinding> a jeho konfiguraci.  
  
 [Postupy: Vytvoření služby WCF, který komunikuje přes WebSockets](../../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-service-that-communicates-over-websockets.md)  
 Popisuje postup vytvoření služby WCF, který komunikuje přes Websockets.  
  
## <a name="reference"></a>Odkaz  
  
## <a name="related-sections"></a>Související oddíly
