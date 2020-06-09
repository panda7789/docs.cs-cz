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
# <a name="wcf-and-websockets"></a><span data-ttu-id="52ae4-102">WCF a WebSockets</span><span class="sxs-lookup"><span data-stu-id="52ae4-102">WCF and WebSockets</span></span>
<span data-ttu-id="52ae4-103">.NET Framework 4,5 zavádí podporu pro objekty WebSocket v Windows Communication Foundation.</span><span class="sxs-lookup"><span data-stu-id="52ae4-103">The .NET Framework 4.5 introduces support for WebSockets in Windows Communication Foundation.</span></span>  <span data-ttu-id="52ae4-104">WebSockets je efektivní technologie založená na standardech, která umožňuje obousměrnou komunikaci přes standardní porty HTTP 80 a 443.</span><span class="sxs-lookup"><span data-stu-id="52ae4-104">WebSockets is an efficient, standards-based technology that enables bidirectional communication over the standard HTTP ports 80 and 443.</span></span> <span data-ttu-id="52ae4-105">Použití standardních portů HTTP umožňuje protokolům WebSocket komunikovat přes web prostřednictvím zprostředkovatelů.</span><span class="sxs-lookup"><span data-stu-id="52ae4-105">The use of the standard HTTP ports allow WebSockets to communicate across the web through intermediaries.</span></span>  <span data-ttu-id="52ae4-106">Pro podporu komunikace prostřednictvím přenosu protokolu WebSocket byly přidány dvě nové standardní vazby.</span><span class="sxs-lookup"><span data-stu-id="52ae4-106">Two new standard bindings have been added to support communication over a WebSocket transport.</span></span> <span data-ttu-id="52ae4-107"><xref:System.ServiceModel.NetHttpBinding> a <xref:System.ServiceModel.NetHttpsBinding>.</span><span class="sxs-lookup"><span data-stu-id="52ae4-107"><xref:System.ServiceModel.NetHttpBinding> and <xref:System.ServiceModel.NetHttpsBinding>.</span></span> <span data-ttu-id="52ae4-108">Nastavení specifická pro objekty WebSockets lze konfigurovat <xref:System.ServiceModel.Channels.HttpTransportBindingElement> pomocí přístupu k <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="52ae4-108">WebSockets-specific settings can be configured on the <xref:System.ServiceModel.Channels.HttpTransportBindingElement> by accessing the <xref:System.ServiceModel.Channels.HttpTransportBindingElement.WebSocketSettings%2A> property.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="52ae4-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="52ae4-109">In This Section</span></span>  
 [<span data-ttu-id="52ae4-110">Používání vazeb NetHttpBinding</span><span class="sxs-lookup"><span data-stu-id="52ae4-110">Using the NetHttpBinding</span></span>](using-the-nethttpbinding.md)  
 <span data-ttu-id="52ae4-111">Popisuje <xref:System.ServiceModel.NetHttpBinding> a jak ji nakonfigurovat.</span><span class="sxs-lookup"><span data-stu-id="52ae4-111">Discusses the <xref:System.ServiceModel.NetHttpBinding> and how to configure it.</span></span>  
  
 [<span data-ttu-id="52ae4-112">Postupy: Vytvoření služby WCF, která komunikuje přes WebSockets</span><span class="sxs-lookup"><span data-stu-id="52ae4-112">How to: Create a WCF Service that Communicates over WebSockets</span></span>](how-to-create-a-wcf-service-that-communicates-over-websockets.md)  
 <span data-ttu-id="52ae4-113">Popisuje, jak vytvořit službu WCF, která komunikuje přes objekty WebSockets.</span><span class="sxs-lookup"><span data-stu-id="52ae4-113">Describes how to create a WCF service that communicates over Websockets.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="52ae4-114">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="52ae4-114">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="52ae4-115">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="52ae4-115">Related Sections</span></span>
