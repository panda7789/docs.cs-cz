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
# <a name="wcf-and-websockets"></a><span data-ttu-id="ab504-102">WCF a WebSockets</span><span class="sxs-lookup"><span data-stu-id="ab504-102">WCF and WebSockets</span></span>
<span data-ttu-id="ab504-103">Rozhraní .NET Framework 4.5 zavádí podporu pro objekty Websocket ve Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="ab504-103">The .NET Framework 4.5 introduces support for WebSockets in Windows Communication Foundation.</span></span>  <span data-ttu-id="ab504-104">Protokoly Websocket je efektivní, založené na standardech technologie, které umožňuje obousměrnou komunikaci přes standardní HTTP porty 80 a 443.</span><span class="sxs-lookup"><span data-stu-id="ab504-104">WebSockets is an efficient, standards-based technology that enables bidirectional communication over the standard HTTP ports 80 and 443.</span></span> <span data-ttu-id="ab504-105">Použití standardní porty HTTP umožnit WebSockets komunikace prostřednictvím zprostředkovatelů na webu.</span><span class="sxs-lookup"><span data-stu-id="ab504-105">The use of the standard HTTP ports allow WebSockets to communicate across the web through intermediaries.</span></span>  <span data-ttu-id="ab504-106">Aby mohly podporovat komunikaci pomocí protokolu WebSocket přenosového byly přidány dva nové standardní vazby.</span><span class="sxs-lookup"><span data-stu-id="ab504-106">Two new standard bindings have been added to support communication over a WebSocket transport.</span></span> <span data-ttu-id="ab504-107"><xref:System.ServiceModel.NetHttpBinding> a <xref:System.ServiceModel.NetHttpsBinding>.</span><span class="sxs-lookup"><span data-stu-id="ab504-107"><xref:System.ServiceModel.NetHttpBinding> and <xref:System.ServiceModel.NetHttpsBinding>.</span></span> <span data-ttu-id="ab504-108">Nastavení pro konkrétní objekty Websocket lze nakonfigurovat podle <xref:System.ServiceModel.Channels.HttpTransportBindingElement> díky přístupu do <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ab504-108">WebSockets-specific settings can be configured on the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> by accessing the <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> property.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="ab504-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="ab504-109">In This Section</span></span>  
 [<span data-ttu-id="ab504-110">Používání NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="ab504-110">Using the NetHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/using-the-nethttpbinding.md)  
 <span data-ttu-id="ab504-111">Tento článek popisuje <xref:System.ServiceModel.NetHttpBinding> a jeho konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="ab504-111">Discusses the <xref:System.ServiceModel.NetHttpBinding> and how to configure it.</span></span>  
  
 [<span data-ttu-id="ab504-112">Postupy: Vytvoření služby WCF, který komunikuje přes WebSockets</span><span class="sxs-lookup"><span data-stu-id="ab504-112">How to: Create a WCF Service that Communicates over WebSockets</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-service-that-communicates-over-websockets.md)  
 <span data-ttu-id="ab504-113">Popisuje postup vytvoření služby WCF, který komunikuje přes Websockets.</span><span class="sxs-lookup"><span data-stu-id="ab504-113">Describes how to create a WCF service that communicates over Websockets.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ab504-114">Odkaz</span><span class="sxs-lookup"><span data-stu-id="ab504-114">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ab504-115">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="ab504-115">Related Sections</span></span>
