---
title: WCF a WebSockets
ms.date: 03/30/2017
ms.assetid: 1e53b49e-022c-49c7-8984-4b21b53c05b3
ms.openlocfilehash: df4a251eb5a570c9fedf19d385a027e23481afed
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594943"
---
# <a name="wcf-and-websockets"></a>WCF a WebSockets
.NET Framework 4,5 zavádí podporu pro objekty WebSocket v Windows Communication Foundation.  WebSockets je efektivní technologie založená na standardech, která umožňuje obousměrnou komunikaci přes standardní porty HTTP 80 a 443. Použití standardních portů HTTP umožňuje protokolům WebSocket komunikovat přes web prostřednictvím zprostředkovatelů.  Pro podporu komunikace prostřednictvím přenosu protokolu WebSocket byly přidány dvě nové standardní vazby. <xref:System.ServiceModel.NetHttpBinding> a <xref:System.ServiceModel.NetHttpsBinding>. Nastavení specifická pro objekty WebSockets lze konfigurovat <xref:System.ServiceModel.Channels.HttpTransportBindingElement> pomocí přístupu k <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> Vlastnosti.
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Používání vazeb NetHttpBinding](using-the-nethttpbinding.md)  
 Popisuje <xref:System.ServiceModel.NetHttpBinding> a jak ji nakonfigurovat.  
  
 [Postupy: Vytvoření služby WCF, která komunikuje přes WebSockets](how-to-create-a-wcf-service-that-communicates-over-websockets.md)  
 Popisuje, jak vytvořit službu WCF, která komunikuje přes objekty WebSockets.  
  
## <a name="reference"></a>Referenční informace  
  
## <a name="related-sections"></a>Související oddíly
