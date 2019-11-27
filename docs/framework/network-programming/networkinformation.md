---
title: Informace o síti
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: 31b44dd3-b903-4a48-8419-40419a3e4038
ms.openlocfilehash: bc0604fd33d06521727c9aa0302ed313d8a2305f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428228"
---
# <a name="networkinformation"></a><span data-ttu-id="590d5-102">Informace o síti</span><span class="sxs-lookup"><span data-stu-id="590d5-102">NetworkInformation</span></span>
<span data-ttu-id="590d5-103">Obor názvů <xref:System.Net.NetworkInformation> umožňuje shromažďovat informace o událostech, změnách, statistikách a vlastnostech sítě.</span><span class="sxs-lookup"><span data-stu-id="590d5-103">The <xref:System.Net.NetworkInformation> namespace enables you to gather information about network events, changes, statistics, and properties.</span></span> <span data-ttu-id="590d5-104">Můžete také určit, zda je vzdálený hostitel dosažitelný pomocí třídy <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="590d5-104">You can also determine whether a remote host is reachable by using the <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> class.</span></span>  
  
## <a name="network-availability-and-events"></a><span data-ttu-id="590d5-105">Dostupnost a události sítě</span><span class="sxs-lookup"><span data-stu-id="590d5-105">Network Availability and Events</span></span>  
 <span data-ttu-id="590d5-106">Třída <xref:System.Net.NetworkInformation.NetworkChange?displayProperty=nameWithType> umožňuje určit, zda se změnila síťová adresa nebo dostupnost.</span><span class="sxs-lookup"><span data-stu-id="590d5-106">The <xref:System.Net.NetworkInformation.NetworkChange?displayProperty=nameWithType> class enables you to determine whether the network address or availability has changed.</span></span> <span data-ttu-id="590d5-107">Chcete-li použít tuto třídu, vytvořte obslužnou rutinu události pro zpracování změny a přidružte ji k <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> nebo <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="590d5-107">To use this class, create an event handler to process the change, and associate it with a <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> or a <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler>.</span></span> <span data-ttu-id="590d5-108">Další informace najdete v tématu [Postupy: zjištění dostupnosti sítě a změny adres](how-to-detect-network-availability-and-address-changes.md).</span><span class="sxs-lookup"><span data-stu-id="590d5-108">For more information, see [How to: Detect Network Availability and Address Changes](how-to-detect-network-availability-and-address-changes.md).</span></span>  
  
## <a name="network-statistics-and-properties"></a><span data-ttu-id="590d5-109">Statistika sítě a vlastnosti</span><span class="sxs-lookup"><span data-stu-id="590d5-109">Network Statistics and Properties</span></span>  
 <span data-ttu-id="590d5-110">Statistiky sítě a vlastnosti můžete shromažďovat na základě rozhraní nebo protokolu.</span><span class="sxs-lookup"><span data-stu-id="590d5-110">You can gather network statistics and properties on an interface or protocol basis.</span></span> <span data-ttu-id="590d5-111">Třídy <xref:System.Net.NetworkInformation.NetworkInterface>, <xref:System.Net.NetworkInformation.NetworkInterfaceType>a <xref:System.Net.NetworkInformation.PhysicalAddress> poskytují informace o konkrétním síťovém rozhraní, zatímco třídy <xref:System.Net.NetworkInformation.IPInterfaceProperties>, <xref:System.Net.NetworkInformation.IPGlobalProperties>, <xref:System.Net.NetworkInformation.IPGlobalStatistics>, <xref:System.Net.NetworkInformation.TcpStatistics>a <xref:System.Net.NetworkInformation.UdpStatistics> poskytují informace o paketech vrstvy 3 a 4.</span><span class="sxs-lookup"><span data-stu-id="590d5-111">The <xref:System.Net.NetworkInformation.NetworkInterface>, <xref:System.Net.NetworkInformation.NetworkInterfaceType>, and <xref:System.Net.NetworkInformation.PhysicalAddress> classes give information about a particular network interface, while the <xref:System.Net.NetworkInformation.IPInterfaceProperties>, <xref:System.Net.NetworkInformation.IPGlobalProperties>, <xref:System.Net.NetworkInformation.IPGlobalStatistics>, <xref:System.Net.NetworkInformation.TcpStatistics>, and <xref:System.Net.NetworkInformation.UdpStatistics> classes give information about layer 3 and layer 4 packets.</span></span> <span data-ttu-id="590d5-112">Další informace najdete v tématu [Postupy: získání informací o rozhraní a protokolu](how-to-get-interface-and-protocol-information.md).</span><span class="sxs-lookup"><span data-stu-id="590d5-112">For more information, see [How to: Get Interface and Protocol Information](how-to-get-interface-and-protocol-information.md).</span></span>  
  
## <a name="determine-if-a-remote-host-is-reachable"></a><span data-ttu-id="590d5-113">Zjistit, jestli je vzdálený hostitel dosažitelný</span><span class="sxs-lookup"><span data-stu-id="590d5-113">Determine if a Remote Host is Reachable</span></span>  
 <span data-ttu-id="590d5-114">Třídu <xref:System.Net.NetworkInformation.Ping> můžete použít k určení, zda je vzdálený hostitel v síti a dostupný.</span><span class="sxs-lookup"><span data-stu-id="590d5-114">You can use the <xref:System.Net.NetworkInformation.Ping> class to determine whether a Remote Host is up, on the network, and reachable.</span></span> <span data-ttu-id="590d5-115">Další informace najdete v tématu [How to: příkaz příkazového testu na hostitele](how-to-ping-a-host.md).</span><span class="sxs-lookup"><span data-stu-id="590d5-115">For more information, see [How to: Ping a Host](how-to-ping-a-host.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="590d5-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="590d5-116">See also</span></span>

- [<span data-ttu-id="590d5-117">Ukázky programování sítě</span><span class="sxs-lookup"><span data-stu-id="590d5-117">Network Programming Samples</span></span>](network-programming-samples.md)

<!-- to-do: review sample links
- [Network Information Technology Sample](https://archive.msdn.microsoft.com/nclsamples/Wiki/View.aspx?title=Network%20Information)
- [NetStat Tool Technology Sample](https://archive.msdn.microsoft.com/nclsamples/Wiki/View.aspx?title=NetStat%20Tool)
- [Ping Client Technology Sample](https://archive.msdn.microsoft.com/nclsamples/Wiki/View.aspx?title=Ping%20Client)
-->
