---
title: TCP-UDP
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
ms.openlocfilehash: e074a487c39dfaf1c4704f9dadf7ed8e430fb630
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59172546"
---
# <a name="tcp-udp"></a>TCP-UDP
Protokolu TCP (Transmission Control) a protokolu UDP (User Datagram) služby se může používat aplikace <xref:System.Net.Sockets.TcpClient>, <xref:System.Net.Sockets.TcpListener>, a <xref:System.Net.Sockets.UdpClient> třídy. Tyto třídy protokolu jsou zabudovány nad <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> třídy a aby se postaral o podrobnosti přenosu dat.  
  
 Protokol třídy použijte synchronní metody **soketu** třídy poskytují jednoduché a nekomplikované přístup k síťovým službám bez režie zachování informací o stavu nebo znát podrobnosti o nastavení konkrétní sokety. Použití asynchronního **soketu** metody, můžete použít asynchronní metody poskytnuté <xref:System.Net.Sockets.NetworkStream> třídy. Pro přístup k funkcím nástroje **soketu** tříd nejsou viditelné v rámci protokolu tříd je nutné použít **soketu** třídy.  
  
 **TcpClient** a **TcpListener** představují síť používání **NetworkStream** třídy. Můžete použít <xref:System.Net.Sockets.TcpClient.GetStream%2A> má metoda vrátit datový proud sítě a poté zavolejte datový proud <xref:System.Net.Sockets.NetworkStream.Read%2A> a <xref:System.Net.Sockets.NetworkStream.Write%2A> metody. **NetworkStream** není vlastníkem soketu základní třídy protokol, tak jeho uzavřením nemá vliv na soketu.  
  
 **UdpClient** třída používá pole bajtů pro uložení datagramů UDP. Můžete použít <xref:System.Net.Sockets.UdpClient.Send%2A> metoda k odesílání dat do sítě a <xref:System.Net.Sockets.UdpClient.Receive%2A> metoda přijímat příchozí datagram.  
  
## <a name="see-also"></a>Viz také:

- [Použití služeb TCP](../../../docs/framework/network-programming/using-tcp-services.md)
- [Použití služeb UDP](../../../docs/framework/network-programming/using-udp-services.md)
- [Použití streamů v síti](../../../docs/framework/network-programming/using-streams-on-the-network.md)
- [Použití asynchronního serverového soketu](../../../docs/framework/network-programming/using-an-asynchronous-server-socket.md)
- [Použití asynchronního klientského soketu](../../../docs/framework/network-programming/using-an-asynchronous-client-socket.md)
- [Použití aplikačních protokolů](../../../docs/framework/network-programming/using-application-protocols.md)
