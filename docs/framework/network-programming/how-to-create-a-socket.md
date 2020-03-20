---
title: 'Postupy: Vytvoření soketu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application protocols, sockets
- Networking
- sending data, sockets
- data requests, sockets
- requesting data from Internet, sockets
- Socket class, creating sockets
- Network Resources
- receiving data, sockets
- protocols, sockets
- Internet, sockets
- sockets, creating
ms.assetid: c64a049c-5981-43bc-a2dc-1851473589c7
ms.openlocfilehash: e71e7e235048361580c65bdb551919fe3038130b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180826"
---
# <a name="how-to-create-a-socket"></a>Postupy: Vytvoření soketu
Před použitím soketu ke komunikaci se vzdálenými zařízeními musí být soket inicializován s informacemi o protokolu a síťové adrese. Konstruktor pro <xref:System.Net.Sockets.Socket> třídu má parametry, které určují rodinu adres, typ soketu a typ protokolu, který soket používá k připojení.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří Socket, který lze použít ke komunikaci v síti založené na protokolu TCP/IP, jako je například Internet.  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,
   SocketType.Stream, ProtocolType.Tcp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Stream, ProtocolType.Tcp)  
```  
  
 Chcete-li místo protokolu TCP použít protokol UDP, změňte typ protokolu, jako v následujícím příkladu:  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,
   SocketType.Dgram, ProtocolType.Udp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Dgram, ProtocolType.Udp)  
```  
  
 Výčet <xref:System.Net.Sockets.AddressFamily> určuje standardní rodiny adres používané třídou **Socket** k překladu síťových adres (například člen **AddressFamily.InterNetwork** určuje rodinu adres IP verze 4).  
  
 Výčet <xref:System.Net.Sockets.SocketType> určuje typ soketu (například člen **SocketType.Stream** označuje standardní soket pro odesílání a přijímání dat s řízením toku).  
  
 Výčet <xref:System.Net.Sockets.ProtocolType> určuje síťový protokol, který se má použít při komunikaci v **Socketu** (například **ProtocolType.Tcp** označuje, že soket používá protokol TCP; **ProtocolType.Udp** označuje, že soket používá UDP).  
  
 Po vytvoření **Socket** může buď zahájit připojení ke vzdálenému koncovému bodu nebo přijímat připojení ze vzdálených zařízení.  
  
## <a name="see-also"></a>Viz také

- [Použití klientských soketů](using-client-sockets.md)
- [Naslouchání pomocí soketů](listening-with-sockets.md)
