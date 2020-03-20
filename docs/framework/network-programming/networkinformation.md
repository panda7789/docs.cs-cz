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
# <a name="networkinformation"></a>Informace o síti
Obor <xref:System.Net.NetworkInformation> názvů umožňuje shromažďovat informace o síťových událostech, změnách, statistikách a vlastnostech. Můžete také určit, zda vzdálený hostitel je <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> dosažitelný pomocí třídy.  
  
## <a name="network-availability-and-events"></a>Dostupnost a události sítě  
 Třída <xref:System.Net.NetworkInformation.NetworkChange?displayProperty=nameWithType> umožňuje určit, zda došlo ke změně síťové adresy nebo dostupnosti. Chcete-li použít tuto třídu, vytvořte obslužnou rutinu události ke zpracování změny a přidružte ji <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> k nebo <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler>. Další informace naleznete v [tématu How to: Detect network Availability and Address Changes](how-to-detect-network-availability-and-address-changes.md).  
  
## <a name="network-statistics-and-properties"></a>Statistika sítě a vlastnosti  
 Můžete shromažďovat síťové statistiky a vlastnosti na základě rozhraní nebo protokolu. <xref:System.Net.NetworkInformation.NetworkInterface>Třídy <xref:System.Net.NetworkInformation.NetworkInterfaceType>, <xref:System.Net.NetworkInformation.PhysicalAddress> a poskytují informace o určitém <xref:System.Net.NetworkInformation.IPInterfaceProperties>síťovém rozhraní, zatímco <xref:System.Net.NetworkInformation.IPGlobalProperties>, <xref:System.Net.NetworkInformation.IPGlobalStatistics>, <xref:System.Net.NetworkInformation.TcpStatistics>, a <xref:System.Net.NetworkInformation.UdpStatistics> třídy poskytují informace o paketech vrstvy 3 a vrstvy 4. Další informace naleznete v [tématu How to: Get Interface and Protocol Information](how-to-get-interface-and-protocol-information.md).  
  
## <a name="determine-if-a-remote-host-is-reachable"></a>Zjištění, zda je vzdálený hostitel dostupný  
 Třídu <xref:System.Net.NetworkInformation.Ping> můžete použít k určení, zda je vzdálený hostitel v síti zapnutý a dostupný. Další informace naleznete v [tématu How to: Ping a Host](how-to-ping-a-host.md).  
  
## <a name="see-also"></a>Viz také

- [Ukázky programování sítě](network-programming-samples.md)

<!-- to-do: review sample links
- [Network Information Technology Sample](https://archive.msdn.microsoft.com/nclsamples/Wiki/View.aspx?title=Network%20Information)
- [NetStat Tool Technology Sample](https://archive.msdn.microsoft.com/nclsamples/Wiki/View.aspx?title=NetStat%20Tool)
- [Ping Client Technology Sample](https://archive.msdn.microsoft.com/nclsamples/Wiki/View.aspx?title=Ping%20Client)
-->
