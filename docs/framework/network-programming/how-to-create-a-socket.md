---
title: "Postupy: vytvoření soket"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "7"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 24ec39798f5f31cf20cc5c84714efaae6ccbed52
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
