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
ms.openlocfilehash: 54706293784d77e535cac582c99b1dd21a12e380
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048385"
---
# <a name="how-to-create-a-socket"></a>Postupy: Vytvoření soketu
Předtím, než budete moci použít soket ke komunikaci se vzdálenými zařízeními, je nutné soket inicializovat pomocí informací o protokolu a síťové adrese. Konstruktor <xref:System.Net.Sockets.Socket> třídy má parametry, které určují rodinu adres, typ soketu a typ protokolu, který soket používá k vytváření připojení.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří soket, který lze použít ke komunikaci v síti založené na protokolu TCP/IP, jako je například Internet.  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Stream, ProtocolType.Tcp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Stream, ProtocolType.Tcp)  
```  
  
 Pokud chcete místo TCP používat protokol UDP, změňte typ protokolu tak, jak je uvedeno v následujícím příkladu:  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Dgram, ProtocolType.Udp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Dgram, ProtocolType.Udp)  
```  
  
 Výčet Určuje standardní skupiny adres používané třídou Socket k překladu síťových adres (například člen **parametr AddressFamily. Internetwork** Určuje rodinu adres IP verze 4). <xref:System.Net.Sockets.AddressFamily>  
  
 Výčet Určuje typ soketu (například člen **SocketType. Stream** indikuje standardní soket pro odesílání a příjem dat pomocí řízení toku). <xref:System.Net.Sockets.SocketType>  
  
 Výčet Určuje síťový protokol, který se má použít při komunikaci na **soketu** (například **typprotokolu. TCP** znamená, že soket používá protokol TCP; <xref:System.Net.Sockets.ProtocolType> **Typprotokolu. UDP** označuje, že SOKET používá UDP).  
  
 Po vytvoření **soketu** může buď iniciovat připojení ke vzdálenému koncovému bodu, nebo přijímat připojení ze vzdálených zařízení.  
  
## <a name="see-also"></a>Viz také:

- [Použití klientských soketů](using-client-sockets.md)
- [Naslouchání pomocí soketů](listening-with-sockets.md)
