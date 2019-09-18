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
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047115"
---
# <a name="tcp-udp"></a>TCP-UDP
Aplikace mohou používat služby protokolu TCP (Transmission Control Protocol) a UDP (User Datagram Protocol) s <xref:System.Net.Sockets.TcpClient>třídami, <xref:System.Net.Sockets.UdpClient> <xref:System.Net.Sockets.TcpListener>a. Tyto třídy protokolu jsou postaveny nad <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> třídou a postarou se o podrobnosti přenosu dat.  
  
 Třídy protokolu používají synchronní metody třídy **Socket** k poskytování jednoduchého a jednoduššího přístupu k síťovým službám bez režie údržby stavových informací nebo zjištění podrobností o nastavení soketů specifických pro protokol. Chcete-li použít metody asynchronního **soketu** , můžete použít asynchronní metody poskytované <xref:System.Net.Sockets.NetworkStream> třídou. Chcete-li získat přístup k funkcím třídy **Socket** , která není vystavena třídami protokolu, je nutné použít třídu **Socket** .  
  
 **TcpClient** a **Třída TcpListener nesmí** reprezentují síť pomocí třídy **NetworkStream** . Použijte <xref:System.Net.Sockets.TcpClient.GetStream%2A> metodu k vrácení síťového datového proudu a pak zavolejte <xref:System.Net.Sockets.NetworkStream.Read%2A> metody a <xref:System.Net.Sockets.NetworkStream.Write%2A> . **NetworkStream** nevlastní základní soket tříd protokolů, takže jeho zavření nemá vliv na soket.  
  
 Třída **UdpClient** používá pole bajtů k uložení datagramu UDP. Použijte <xref:System.Net.Sockets.UdpClient.Send%2A> metodu k odeslání dat do sítě <xref:System.Net.Sockets.UdpClient.Receive%2A> a metody pro příjem příchozího datagramu.  
  
## <a name="see-also"></a>Viz také:

- [Použití služeb TCP](using-tcp-services.md)
- [Použití služeb UDP](using-udp-services.md)
- [Použití streamů v síti](using-streams-on-the-network.md)
- [Použití asynchronního serverového soketu](using-an-asynchronous-server-socket.md)
- [Použití asynchronního klientského soketu](using-an-asynchronous-client-socket.md)
- [Použití aplikačních protokolů](using-application-protocols.md)
