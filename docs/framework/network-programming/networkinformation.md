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
# <a name="networkinformation"></a>Informace o síti
Obor názvů <xref:System.Net.NetworkInformation> umožňuje shromažďovat informace o událostech, změnách, statistikách a vlastnostech sítě. Můžete také určit, zda je vzdálený hostitel dosažitelný pomocí třídy <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType>.  
  
## <a name="network-availability-and-events"></a>Dostupnost a události sítě  
 Třída <xref:System.Net.NetworkInformation.NetworkChange?displayProperty=nameWithType> umožňuje určit, zda se změnila síťová adresa nebo dostupnost. Chcete-li použít tuto třídu, vytvořte obslužnou rutinu události pro zpracování změny a přidružte ji k <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> nebo <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler>. Další informace najdete v tématu [Postupy: zjištění dostupnosti sítě a změny adres](how-to-detect-network-availability-and-address-changes.md).  
  
## <a name="network-statistics-and-properties"></a>Statistika sítě a vlastnosti  
 Statistiky sítě a vlastnosti můžete shromažďovat na základě rozhraní nebo protokolu. Třídy <xref:System.Net.NetworkInformation.NetworkInterface>, <xref:System.Net.NetworkInformation.NetworkInterfaceType>a <xref:System.Net.NetworkInformation.PhysicalAddress> poskytují informace o konkrétním síťovém rozhraní, zatímco třídy <xref:System.Net.NetworkInformation.IPInterfaceProperties>, <xref:System.Net.NetworkInformation.IPGlobalProperties>, <xref:System.Net.NetworkInformation.IPGlobalStatistics>, <xref:System.Net.NetworkInformation.TcpStatistics>a <xref:System.Net.NetworkInformation.UdpStatistics> poskytují informace o paketech vrstvy 3 a 4. Další informace najdete v tématu [Postupy: získání informací o rozhraní a protokolu](how-to-get-interface-and-protocol-information.md).  
  
## <a name="determine-if-a-remote-host-is-reachable"></a>Zjistit, jestli je vzdálený hostitel dosažitelný  
 Třídu <xref:System.Net.NetworkInformation.Ping> můžete použít k určení, zda je vzdálený hostitel v síti a dostupný. Další informace najdete v tématu [How to: příkaz příkazového testu na hostitele](how-to-ping-a-host.md).  
  
## <a name="see-also"></a>Viz také:

- [Ukázky programování sítě](network-programming-samples.md)

<!-- to-do: review sample links
- [Network Information Technology Sample](https://archive.msdn.microsoft.com/nclsamples/Wiki/View.aspx?title=Network%20Information)
- [NetStat Tool Technology Sample](https://archive.msdn.microsoft.com/nclsamples/Wiki/View.aspx?title=NetStat%20Tool)
- [Ping Client Technology Sample](https://archive.msdn.microsoft.com/nclsamples/Wiki/View.aspx?title=Ping%20Client)
-->
