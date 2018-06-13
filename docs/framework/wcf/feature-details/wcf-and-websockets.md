---
title: WCF a WebSockets
ms.date: 03/30/2017
ms.assetid: 1e53b49e-022c-49c7-8984-4b21b53c05b3
ms.openlocfilehash: ac888db14ebd21c4aed2f717c1f71bed310b8388
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498524"
---
# <a name="wcf-and-websockets"></a><span data-ttu-id="0e188-102">WCF a WebSockets</span><span class="sxs-lookup"><span data-stu-id="0e188-102">WCF and WebSockets</span></span>
<span data-ttu-id="0e188-103">Rozhraní .NET Framework 4.5 zavádí podporu pro objekty WebSockets ve službě Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="0e188-103">The .NET Framework 4.5 introduces support for WebSockets in Windows Communication Foundation.</span></span>  <span data-ttu-id="0e188-104">Technologie WebSockets je efektivní, založených na standardech technologie, která umožňuje obousměrnou komunikaci přes standardní HTTP porty 80 a 443.</span><span class="sxs-lookup"><span data-stu-id="0e188-104">WebSockets is an efficient, standards-based technology that enables bidirectional communication over the standard HTTP ports 80 and 443.</span></span> <span data-ttu-id="0e188-105">Použití standardní porty protokolu HTTP umožňuje objekty WebSockets ke komunikaci prostřednictvím webu prostřednictvím zprostředkovatelů.</span><span class="sxs-lookup"><span data-stu-id="0e188-105">The use of the standard HTTP ports allow WebSockets to communicate across the web through intermediaries.</span></span>  <span data-ttu-id="0e188-106">Aby mohly podporovat komunikaci pomocí přenosového protokolu WebSocket byly přidány dva nové standardní vazby.</span><span class="sxs-lookup"><span data-stu-id="0e188-106">Two new standard bindings have been added to support communication over a WebSocket transport.</span></span> <span data-ttu-id="0e188-107"><xref:System.ServiceModel.NetHttpBinding> a <xref:System.ServiceModel.NetHttpsBinding>.</span><span class="sxs-lookup"><span data-stu-id="0e188-107"><xref:System.ServiceModel.NetHttpBinding> and <xref:System.ServiceModel.NetHttpsBinding>.</span></span> <span data-ttu-id="0e188-108">Nastavení specifických pro objekty WebSockets lze nakonfigurovat podle <xref:System.ServiceModel.Channels.HttpTransportBindingElement> přímým přístupem <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="0e188-108">WebSockets-specific settings can be configured on the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> by accessing the <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> property.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="0e188-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="0e188-109">In This Section</span></span>  
 [<span data-ttu-id="0e188-110">Používání NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="0e188-110">Using the NetHttpBinding</span></span>](../../../../docs/framework/wcf/feature-details/using-the-nethttpbinding.md)  
 <span data-ttu-id="0e188-111">Popisuje <xref:System.ServiceModel.NetHttpBinding> a jeho konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="0e188-111">Discusses the <xref:System.ServiceModel.NetHttpBinding> and how to configure it.</span></span>  
  
 [<span data-ttu-id="0e188-112">Postupy: Vytvoření služby WCF, která komunikuje přes WebSockets</span><span class="sxs-lookup"><span data-stu-id="0e188-112">How to: Create a WCF Service that Communicates over WebSockets</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-service-that-communicates-over-websockets.md)  
 <span data-ttu-id="0e188-113">Popisuje postup vytvoření služby WCF, který komunikuje přes objekty Websockets.</span><span class="sxs-lookup"><span data-stu-id="0e188-113">Describes how to create a WCF service that communicates over Websockets.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="0e188-114">Odkaz</span><span class="sxs-lookup"><span data-stu-id="0e188-114">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0e188-115">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="0e188-115">Related Sections</span></span>
