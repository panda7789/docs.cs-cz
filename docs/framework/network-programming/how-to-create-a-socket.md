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
ms.openlocfilehash: 0bbdab11201171bf8d730276c7f94cbc5317acdd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642682"
---
# <a name="how-to-create-a-socket"></a>Postupy: Vytvoření soketu
Než použijete soket pro komunikaci se vzdálenými zařízeními soketu. je nutné inicializovat s informace o protokolu a síťové adrese. Konstruktor pro <xref:System.Net.Sockets.Socket> třída obsahuje parametry, které určují rodina adres, typ soketu a typ protokolu, který využívá soket, aby připojení.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří soket, který slouží ke komunikaci v síti založené na TCP/IP, jako je Internet.  
  
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
  
 <xref:System.Net.Sockets.AddressFamily> Výčet určuje rodiny standardní adres používané **soketu** třídy vyřešit síťových adres (například **AddressFamily.InterNetwork** člen Určuje IP adresu Rodina adres verze 4).  
  
 <xref:System.Net.Sockets.SocketType> Výčet Určuje typ soketu (například **SocketType.Stream** člen označuje standardní soket pro odesílání a přijímání dat pomocí toku řízení).  
  
 <xref:System.Net.Sockets.ProtocolType> Výčet Určuje protokol sítě při komunikaci na **soketu** (například **ProtocolType.Tcp** označuje, že používá soket TCP; **ProtocolType.Udp** označuje, že soketu používá UDP).  
  
 Po **soketu** je vytvořen, ho můžete inicializovat připojení a vzdálený koncový bod nebo přijímat připojení ze vzdálených zařízeních.  
  
## <a name="see-also"></a>Viz také:

- [Použití klientských soketů](../../../docs/framework/network-programming/using-client-sockets.md)
- [Naslouchání pomocí soketů](../../../docs/framework/network-programming/listening-with-sockets.md)
