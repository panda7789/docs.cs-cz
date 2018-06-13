---
title: NetworkInformation
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: 31b44dd3-b903-4a48-8419-40419a3e4038
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 964e76a008e1c18fe9f609f1dd63bce565e95d44
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33396316"
---
# <a name="networkinformation"></a>NetworkInformation
<xref:System.Net.NetworkInformation> Obor názvů umožňuje shromažďovat informace o události sítě, změny, statistiky a vlastnosti. Můžete také určit, zda je vzdálený hostitel dosažitelný pomocí <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> třídy.  
  
## <a name="network-availability-and-events"></a>Dostupnost sítě a události  
 <xref:System.Net.NetworkInformation.NetworkChange?displayProperty=nameWithType> Třída umožňuje určit, zda došlo ke změně adresy sítě nebo dostupnost. Pokud chcete používat tuto třídu, vytvořte obslužnou rutinu události ke zpracování změn a přidružte ji s <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> nebo <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler>. Další informace najdete v tématu [postupy: zjištění dostupnosti sítě a změny adresy](../../../docs/framework/network-programming/how-to-detect-network-availability-and-address-changes.md).  
  
## <a name="network-statistics-and-properties"></a>Vlastnosti a statistiku sítě  
 Můžete shromáždit statistiku sítě a vlastností na základě rozhraní nebo protokolu. <xref:System.Net.NetworkInformation.NetworkInterface>, <xref:System.Net.NetworkInformation.NetworkInterfaceType>, A <xref:System.Net.NetworkInformation.PhysicalAddress> třídy poskytnout informace o konkrétní síťové rozhraní, zatímco <xref:System.Net.NetworkInformation.IPInterfaceProperties>, <xref:System.Net.NetworkInformation.IPGlobalProperties>, <xref:System.Net.NetworkInformation.IPGlobalStatistics>, <xref:System.Net.NetworkInformation.TcpStatistics>, a <xref:System.Net.NetworkInformation.UdpStatistics> třídy poskytnout informace o vrstvy 3 a 4 pakety vrstvy. Další informace najdete v tématu [postupy: získání rozhraní a informace o protokolu](../../../docs/framework/network-programming/how-to-get-interface-and-protocol-information.md).  
  
## <a name="determine-if-a-remote-host-is-reachable"></a>Určí, zda vzdáleného hostitele dostupné  
 Můžete použít <xref:System.Net.NetworkInformation.Ping> třídu k určení, zda je vzdálený hostitel nahoru, v síti a dostupný. Další informace najdete v tématu [postup: příkaz Ping hostitele](../../../docs/framework/network-programming/how-to-ping-a-host.md).  
  
## <a name="see-also"></a>Viz také  
 [Ukázky programování sítě](../../../docs/framework/network-programming/network-programming-samples.md)  
 [Ukázka technologie informace o síti](http://go.microsoft.com/fwlink/?LinkID=179564)  
 [Ukázkový nástroj NetStat technologie](http://go.microsoft.com/fwlink/?LinkID=179562)  
 [Ukázka technologie ping klienta](http://go.microsoft.com/fwlink/?LinkID=179565)
