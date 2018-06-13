---
title: 'Postupy: vytvoření soket'
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 600ea82965c332c8620db689abb50965f15f0067
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33396945"
---
# <a name="how-to-create-a-socket"></a>Postupy: vytvoření soket
Než použijete soket pro komunikaci se vzdáleným zařízením soket musí být inicializován s informace o protokolu a síťových adres. V konstruktoru pro <xref:System.Net.Sockets.Socket> třída má parametrů, které určují rodina adres, typ soketu a typ protokolu, který soketu používá k vytvoření připojení.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří soketu, který lze použít pro komunikaci v síti založené na protokolu TCP, jako je Internet.  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Stream, ProtocolType.Tcp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Stream, ProtocolType.Tcp)  
```  
  
 Místo TCP použít UDP, změňte typ protokolu, jako v následujícím příkladu:  
  
```csharp  
Socket s = new Socket(AddressFamily.InterNetwork,   
   SocketType.Dgram, ProtocolType.Udp);  
```  
  
```vb  
Dim s as New Socket(AddressFamily.InterNetwork, _  
   SocketType.Dgram, ProtocolType.Udp)  
```  
  
 <xref:System.Net.Sockets.AddressFamily> Výčet určuje rodiny standardní adres používané **soketu** třída přeložit síťových adres (například **AddressFamily.InterNetwork** člen Určuje IP adresu Rodina adres verze 4).  
  
 <xref:System.Net.Sockets.SocketType> Výčet Určuje typ soketu (například **SocketType.Stream** člen označuje standardní soket pro odesílání a příjmu dat pomocí řízení toku).  
  
 <xref:System.Net.Sockets.ProtocolType> Výčet Určuje protokol sítě použít při komunikaci na **soketu** (například **ProtocolType.Tcp** označuje, že soketem používá TCP; **ProtocolType.Udp** označuje, že soketem používá UDP).  
  
 Po **soketu** je vytvořen, ho můžete iniciovat připojení k vzdálený koncový bod nebo přijímat připojení ze vzdálených zařízení.  
  
## <a name="see-also"></a>Viz také  
 [Použití klientských soketů](../../../docs/framework/network-programming/using-client-sockets.md)  
 [Naslouchání pomocí soketů](../../../docs/framework/network-programming/listening-with-sockets.md)
