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
ms.workload: dotnet
ms.openlocfilehash: e84bf7a94a6a6fa980e223daf0a6c7aaf489bb6e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-and-websockets"></a><span data-ttu-id="f9d8a-102">WCF a WebSockets</span><span class="sxs-lookup"><span data-stu-id="f9d8a-102">WCF and WebSockets</span></span>
<span data-ttu-id="f9d8a-103">Rozhraní .NET Framework 4.5 zavádí podporu pro objekty WebSockets ve službě Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="f9d8a-103">The .NET Framework 4.5 introduces support for WebSockets in Windows Communication Foundation.</span></span>  <span data-ttu-id="f9d8a-104">Technologie WebSockets je efektivní, založených na standardech technologie, která umožňuje obousměrnou komunikaci přes standardní HTTP porty 80 a 443.</span><span class="sxs-lookup"><span data-stu-id="f9d8a-104">WebSockets is an efficient, standards-based technology that enables bidirectional communication over the standard HTTP ports 80 and 443.</span></span> <span data-ttu-id="f9d8a-105">Použití standardní porty protokolu HTTP umožňuje objekty WebSockets ke komunikaci prostřednictvím webu prostřednictvím zprostředkovatelů.</span><span class="sxs-lookup"><span data-stu-id="f9d8a-105">The use of the standard HTTP ports allow WebSockets to communicate across the web through intermediaries.</span></span>  <span data-ttu-id="f9d8a-106">Aby mohly podporovat komunikaci pomocí přenosového protokolu WebSocket byly přidány dva nové standardní vazby.</span><span class="sxs-lookup"><span data-stu-id="f9d8a-106">Two new standard bindings have been added to support communication over a WebSocket transport.</span></span> <span data-ttu-id="f9d8a-107"><xref:System.ServiceModel.NetHttpBinding>a <xref:System.ServiceModel.NetHttpsBinding>.</span><span class="sxs-lookup"><span data-stu-id="f9d8a-107"><xref:System.ServiceModel.NetHttpBinding> and <xref:System.ServiceModel.NetHttpsBinding>.</span></span> <span data-ttu-id="f9d8a-108">Nastavení specifických pro objekty WebSockets lze nakonfigurovat podle <xref:System.ServiceModel.Channels.HttpTransportBindingElement> přímým přístupem <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f9d8a-108">WebSockets-specific settings can be configured on the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> by accessing the <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> property.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="f9d8a-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="f9d8a-109">In This Section</span></span>  
 [<span data-ttu-id="f9d8a-110">Používání NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="f9d8a-110">Using the NetHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/using-the-nethttpbinding.md)  
 <span data-ttu-id="f9d8a-111">Popisuje <xref:System.ServiceModel.NetHttpBinding> a jeho konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="f9d8a-111">Discusses the <xref:System.ServiceModel.NetHttpBinding> and how to configure it.</span></span>  
  
 [<span data-ttu-id="f9d8a-112">Postupy: Vytvoření služby WCF, která komunikuje přes WebSockets</span><span class="sxs-lookup"><span data-stu-id="f9d8a-112">How to: Create a WCF Service that Communicates over WebSockets</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-service-that-communicates-over-websockets.md)  
 <span data-ttu-id="f9d8a-113">Popisuje postup vytvoření služby WCF, který komunikuje přes objekty Websockets.</span><span class="sxs-lookup"><span data-stu-id="f9d8a-113">Describes how to create a WCF service that communicates over Websockets.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f9d8a-114">Odkaz</span><span class="sxs-lookup"><span data-stu-id="f9d8a-114">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f9d8a-115">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="f9d8a-115">Related Sections</span></span>
