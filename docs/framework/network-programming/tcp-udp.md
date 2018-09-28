---
title: UDP PROTOKOLU TCP
ms.date: 03/30/2017
helpviewer_keywords:
- protocols, TCP/UDP
- network resources, TCP/UDP
- sending data, TCP/UDP
- TCP/UDP
- TcpClient class, about TcpClient class
- application protocols, TCP/UDP
- receiving data, TCP/UDP
- TcpListener class, about TcpListener class
- Socket class, about Socket class
- UDP
- data requests, TCP/UDP
- requesting data from Internet, TCP/UDP
- Internet, TCP/UDP
ms.assetid: df29b4b0-49e8-4923-82b9-13150dfc40f5
author: mcleblanc
ms.author: markl
ms.openlocfilehash: b3e39b952b37f70513b3a84ce6b6059b85e01c28
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/28/2018
ms.locfileid: "47421583"
---
# <a name="tcp-udp"></a>UDP PROTOKOLU TCP
Protokolu TCP (Transmission Control) a protokolu UDP (User Datagram) služby se může používat aplikace <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, a <xref:System.Net.Sockets.UdpClient> třídy. Tyto třídy protokolu jsou zabudovány nad <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> třídy a aby se postaral o podrobnosti přenosu dat.  
  
 Protokol třídy použijte synchronní metody **soketu** třídy poskytují jednoduché a nekomplikované přístup k síťovým službám bez režie zachování informací o stavu nebo znát podrobnosti o nastavení konkrétní sokety. Použití asynchronního **soketu** metody, můžete použít asynchronní metody poskytnuté <xref:System.Net.Sockets.NetworkStream> třídy. Pro přístup k funkcím nástroje **soketu** tříd nejsou viditelné v rámci protokolu tříd je nutné použít **soketu** třídy.  
  
 **TcpClient** a **TcpListener** představují síť používání **NetworkStream** třídy. Můžete použít <xref:System.Net.Sockets.TcpClient.GetStream%2A> má metoda vrátit datový proud sítě a poté zavolejte datový proud <xref:System.Net.Sockets.NetworkStream.Read%2A> a <xref:System.Net.Sockets.NetworkStream.Write%2A> metody. **NetworkStream** není vlastníkem soketu základní třídy protokol, tak jeho uzavřením nemá vliv na soketu.  
  
 **UdpClient** třída používá pole bajtů pro uložení datagramů UDP. Můžete použít <xref:System.Net.Sockets.UdpClient.Send%2A> metoda k odesílání dat do sítě a <xref:System.Net.Sockets.UdpClient.Receive%2A> metoda přijímat příchozí datagram.  
  
## <a name="see-also"></a>Viz také  
 [Použití služeb TCP](../../../docs/framework/network-programming/using-tcp-services.md)  
 [Použití služeb UDP](../../../docs/framework/network-programming/using-udp-services.md)  
 [Použití streamů v síti](../../../docs/framework/network-programming/using-streams-on-the-network.md)  
 [Použití asynchronního serverového soketu](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)  
 [Použití asynchronního klientského soketu](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)  
 [Použití aplikačních protokolů](../../../docs/framework/network-programming/using-application-protocols.md)
