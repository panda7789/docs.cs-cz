---
title: Informace o síti
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: 31b44dd3-b903-4a48-8419-40419a3e4038
ms.openlocfilehash: bc0604fd33d06521727c9aa0302ed313d8a2305f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74428228"
---
# <a name="networkinformation"></a><span data-ttu-id="d30ca-102">Informace o síti</span><span class="sxs-lookup"><span data-stu-id="d30ca-102">NetworkInformation</span></span>
<span data-ttu-id="d30ca-103">Obor <xref:System.Net.NetworkInformation> názvů umožňuje shromažďovat informace o síťových událostech, změnách, statistikách a vlastnostech.</span><span class="sxs-lookup"><span data-stu-id="d30ca-103">The <xref:System.Net.NetworkInformation> namespace enables you to gather information about network events, changes, statistics, and properties.</span></span> <span data-ttu-id="d30ca-104">Můžete také určit, zda vzdálený hostitel je <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> dosažitelný pomocí třídy.</span><span class="sxs-lookup"><span data-stu-id="d30ca-104">You can also determine whether a remote host is reachable by using the <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> class.</span></span>  
  
## <a name="network-availability-and-events"></a><span data-ttu-id="d30ca-105">Dostupnost a události sítě</span><span class="sxs-lookup"><span data-stu-id="d30ca-105">Network Availability and Events</span></span>  
 <span data-ttu-id="d30ca-106">Třída <xref:System.Net.NetworkInformation.NetworkChange?displayProperty=nameWithType> umožňuje určit, zda došlo ke změně síťové adresy nebo dostupnosti.</span><span class="sxs-lookup"><span data-stu-id="d30ca-106">The <xref:System.Net.NetworkInformation.NetworkChange?displayProperty=nameWithType> class enables you to determine whether the network address or availability has changed.</span></span> <span data-ttu-id="d30ca-107">Chcete-li použít tuto třídu, vytvořte obslužnou rutinu události ke zpracování změny a přidružte ji <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> k nebo <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="d30ca-107">To use this class, create an event handler to process the change, and associate it with a <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> or a <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler>.</span></span> <span data-ttu-id="d30ca-108">Další informace naleznete v [tématu How to: Detect network Availability and Address Changes](how-to-detect-network-availability-and-address-changes.md).</span><span class="sxs-lookup"><span data-stu-id="d30ca-108">For more information, see [How to: Detect Network Availability and Address Changes](how-to-detect-network-availability-and-address-changes.md).</span></span>  
  
## <a name="network-statistics-and-properties"></a><span data-ttu-id="d30ca-109">Statistika sítě a vlastnosti</span><span class="sxs-lookup"><span data-stu-id="d30ca-109">Network Statistics and Properties</span></span>  
 <span data-ttu-id="d30ca-110">Můžete shromažďovat síťové statistiky a vlastnosti na základě rozhraní nebo protokolu.</span><span class="sxs-lookup"><span data-stu-id="d30ca-110">You can gather network statistics and properties on an interface or protocol basis.</span></span> <span data-ttu-id="d30ca-111"><xref:System.Net.NetworkInformation.NetworkInterface>Třídy <xref:System.Net.NetworkInformation.NetworkInterfaceType>, <xref:System.Net.NetworkInformation.PhysicalAddress> a poskytují informace o určitém <xref:System.Net.NetworkInformation.IPInterfaceProperties>síťovém rozhraní, zatímco <xref:System.Net.NetworkInformation.IPGlobalProperties>, <xref:System.Net.NetworkInformation.IPGlobalStatistics>, <xref:System.Net.NetworkInformation.TcpStatistics>, a <xref:System.Net.NetworkInformation.UdpStatistics> třídy poskytují informace o paketech vrstvy 3 a vrstvy 4.</span><span class="sxs-lookup"><span data-stu-id="d30ca-111">The <xref:System.Net.NetworkInformation.NetworkInterface>, <xref:System.Net.NetworkInformation.NetworkInterfaceType>, and <xref:System.Net.NetworkInformation.PhysicalAddress> classes give information about a particular network interface, while the <xref:System.Net.NetworkInformation.IPInterfaceProperties>, <xref:System.Net.NetworkInformation.IPGlobalProperties>, <xref:System.Net.NetworkInformation.IPGlobalStatistics>, <xref:System.Net.NetworkInformation.TcpStatistics>, and <xref:System.Net.NetworkInformation.UdpStatistics> classes give information about layer 3 and layer 4 packets.</span></span> <span data-ttu-id="d30ca-112">Další informace naleznete v [tématu How to: Get Interface and Protocol Information](how-to-get-interface-and-protocol-information.md).</span><span class="sxs-lookup"><span data-stu-id="d30ca-112">For more information, see [How to: Get Interface and Protocol Information](how-to-get-interface-and-protocol-information.md).</span></span>  
  
## <a name="determine-if-a-remote-host-is-reachable"></a><span data-ttu-id="d30ca-113">Zjištění, zda je vzdálený hostitel dostupný</span><span class="sxs-lookup"><span data-stu-id="d30ca-113">Determine if a Remote Host is Reachable</span></span>  
 <span data-ttu-id="d30ca-114">Třídu <xref:System.Net.NetworkInformation.Ping> můžete použít k určení, zda je vzdálený hostitel v síti zapnutý a dostupný.</span><span class="sxs-lookup"><span data-stu-id="d30ca-114">You can use the <xref:System.Net.NetworkInformation.Ping> class to determine whether a Remote Host is up, on the network, and reachable.</span></span> <span data-ttu-id="d30ca-115">Další informace naleznete v [tématu How to: Ping a Host](how-to-ping-a-host.md).</span><span class="sxs-lookup"><span data-stu-id="d30ca-115">For more information, see [How to: Ping a Host](how-to-ping-a-host.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d30ca-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="d30ca-116">See also</span></span>

- [<span data-ttu-id="d30ca-117">Ukázky programování sítě</span><span class="sxs-lookup"><span data-stu-id="d30ca-117">Network Programming Samples</span></span>](network-programming-samples.md)

<!-- to-do: review sample links
- [Network Information Technology Sample](https://archive.msdn.microsoft.com/nclsamples/Wiki/View.aspx?title=Network%20Information)
- [NetStat Tool Technology Sample](https://archive.msdn.microsoft.com/nclsamples/Wiki/View.aspx?title=NetStat%20Tool)
- [Ping Client Technology Sample](https://archive.msdn.microsoft.com/nclsamples/Wiki/View.aspx?title=Ping%20Client)
-->
