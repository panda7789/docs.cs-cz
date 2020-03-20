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
ms.openlocfilehash: d35278ab7feb42453b5a0adbc86c47b7ac3ff5ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047115"
---
# <a name="tcp-udp"></a>TCP-UDP
Aplikace mohou používat služby TCP (Transmission Control Protocol) a User <xref:System.Net.Sockets.TcpClient> <xref:System.Net.Sockets.TcpListener>Datagram <xref:System.Net.Sockets.UdpClient> Protocol (UDP) s třídami , a tříd. Tyto třídy protokolu jsou <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> postaveny na vrcholu třídy a starat se o podrobnosti přenosu dat.  
  
 Třídy protokolů používají synchronní metody třídy **Socket** k poskytování jednoduchého a jednoduchého přístupu k síťovým službám bez režie na údržbu informací o stavu nebo znalosti podrobností o nastavení soketů specifických pro protokol. Chcete-li použít asynchronní **Socket** metody, můžete použít asynchronní metody poskytované třídy. <xref:System.Net.Sockets.NetworkStream> Chcete-li získat přístup k funkcím **třídy Socket,** které nejsou vystaveny třídám protokolu, musíte použít třídu **Socket.**  
  
 **TcpClient** a **TcpListener** představují síť pomocí třídy **NetworkStream.** <xref:System.Net.Sockets.TcpClient.GetStream%2A> Pomocí metody vrátíte síťový proud a potom zavoláte <xref:System.Net.Sockets.NetworkStream.Read%2A> <xref:System.Net.Sockets.NetworkStream.Write%2A> datového proudu a metody. **NetworkStream** nevlastní základní soket třídprotokolu, takže jeho zavření nemá vliv na soket.  
  
 Třída **UdpClient** používá pole bajtů pro uložení datagramu UDP. Tuto metodu <xref:System.Net.Sockets.UdpClient.Send%2A> použijete k odeslání dat <xref:System.Net.Sockets.UdpClient.Receive%2A> do sítě a metodu pro příjem příchozího datagramu.  
  
## <a name="see-also"></a>Viz také

- [Použití služeb TCP](using-tcp-services.md)
- [Použití služeb UDP](using-udp-services.md)
- [Použití streamů v síti](using-streams-on-the-network.md)
- [Použití asynchronního serverového soketu](using-an-asynchronous-server-socket.md)
- [Použití asynchronního klientského soketu](using-an-asynchronous-client-socket.md)
- [Použití aplikačních protokolů](using-application-protocols.md)
