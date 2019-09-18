---
title: NetworkInformation
ms.date: 03/30/2017
helpviewer_keywords:
- Network
ms.assetid: 31b44dd3-b903-4a48-8419-40419a3e4038
ms.openlocfilehash: 65b15e61acaa39c9bfc4e0bd81b26f5a211bd1f1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047553"
---
# <a name="networkinformation"></a>NetworkInformation
<xref:System.Net.NetworkInformation> Obor názvů umožňuje shromažďovat informace o událostech, změnách, statistikách a vlastnostech sítě. Můžete také určit, zda je vzdálený hostitel dosažitelný pomocí <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> třídy.  
  
## <a name="network-availability-and-events"></a>Dostupnost a události sítě  
 <xref:System.Net.NetworkInformation.NetworkChange?displayProperty=nameWithType> Třída umožňuje určit, zda se změnila síťová adresa nebo dostupnost. Chcete-li použít tuto třídu, vytvořte obslužnou rutinu události pro zpracování změny a přidružte ji <xref:System.Net.NetworkInformation.NetworkAddressChangedEventHandler> k <xref:System.Net.NetworkInformation.NetworkAvailabilityChangedEventHandler>nebo. Další informace najdete v tématu [jak: Zjišťuje dostupnost sítě a změny](how-to-detect-network-availability-and-address-changes.md)adres.  
  
## <a name="network-statistics-and-properties"></a>Statistika sítě a vlastnosti  
 Statistiky sítě a vlastnosti můžete shromažďovat na základě rozhraní nebo protokolu. <xref:System.Net.NetworkInformation.IPGlobalProperties> <xref:System.Net.NetworkInformation.UdpStatistics> Třídy <xref:System.Net.NetworkInformation.NetworkInterface>, <xref:System.Net.NetworkInformation.NetworkInterfaceType>a poskytujíinformace<xref:System.Net.NetworkInformation.IPInterfaceProperties> o<xref:System.Net.NetworkInformation.IPGlobalStatistics> konkrétním<xref:System.Net.NetworkInformation.TcpStatistics>síťovém rozhraní, zatímco třídy,,, a poskytují informace <xref:System.Net.NetworkInformation.PhysicalAddress> o paketech vrstvy 3 a 4. Další informace najdete v tématu [jak: Získat informace o](how-to-get-interface-and-protocol-information.md)rozhraní a protokolu.  
  
## <a name="determine-if-a-remote-host-is-reachable"></a>Zjistit, jestli je vzdálený hostitel dosažitelný  
 <xref:System.Net.NetworkInformation.Ping> Třídu můžete použít k určení, zda je vzdálený hostitel v síti a dostupný. Další informace najdete v tématu [jak: Proveďte test hostitele](how-to-ping-a-host.md)na hostiteli.  
  
## <a name="see-also"></a>Viz také:

- [Ukázky programování sítě](network-programming-samples.md)
- [Ukázka technologie síťové informace](https://go.microsoft.com/fwlink/?LinkID=179564)
- [Ukázka technologie nástroje NetStat](https://go.microsoft.com/fwlink/?LinkID=179562)
- [Ukázka technologie klientského testu klienta](https://go.microsoft.com/fwlink/?LinkID=179565)
