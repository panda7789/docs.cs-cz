---
title: 'Klient: Objekty pro vytváření kanálů a kanály'
ms.date: 03/30/2017
ms.assetid: ef245191-fdab-4468-a0da-7c6f25d2110f
ms.openlocfilehash: bfa5d2478d5c12f16c2d9531de02e1c868eab560
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61858404"
---
# <a name="client-channel-factories-and-channels"></a>Klient: Objekty pro vytváření kanálů a kanály
Toto téma popisuje vytvoření vytvoření objektů pro vytváření kanálů a kanály.  
  
## <a name="channel-factories-and-channels"></a>Objekty pro vytváření kanálů a kanály  
 Objekty pro vytváření kanálů zodpovídají za vytváření kanálů. Kanály vytvořené objekty pro vytváření kanálů se používají pro zasílání zpráv. Tyto kanály jsou zodpovědné za z vrstvy výše se zobrazuje zpráva, provádění jakékoli zpracování je nezbytné pak posílání zprávy na vrstvě níže. Tento proces je znázorněný následujícím obrázku.  
  
 ![Klientské objekty pro vytváření a kanály](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")  
Vytvoří objekt pro vytváření kanálů kanály.  
  
 Při zavření, objekty pro vytváření kanálů zodpovídají za zavření všechny kanály, které vytvořili, které ještě nebyly uzavřeny. Upozorňujeme, že model asymetrického zde protože při zavření kanálu naslouchacího procesu se jenom zastaví přijímání nových kanálů, ale ponechá stávajících prodejních kanálů otevřít tak, aby může i dál příjem zpráv.  
  
 WCF poskytuje pomocné rutiny základní třídy pro tento proces. (Diagram tříd pomocných rutin kanál popsané v tomto tématu, naleznete v tématu [přehled modelu kanálu](../../../../docs/framework/wcf/extending/channel-model-overview.md).)  
  
- <xref:System.ServiceModel.Channels.CommunicationObject> Implementuje třída <xref:System.ServiceModel.ICommunicationObject> a vynucuje stavového stroje popsaný v kroku 2 z [vývoj kanálů](../../../../docs/framework/wcf/extending/developing-channels.md).  
  
- <xref:System.ServiceModel.Channels.ChannelManagerBase> Implementuje třída <xref:System.ServiceModel.Channels.CommunicationObject> a poskytuje jednotné základní třídu pro <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> a <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>. <xref:System.ServiceModel.Channels.ChannelManagerBase> Třídy funguje ve spojení s <xref:System.ServiceModel.Channels.ChannelBase>, což je základní třídy, která implementuje <xref:System.ServiceModel.Channels.IChannel>.
  
- <xref:System.ServiceModel.Channels.ChannelFactoryBase> Implementuje třída <xref:System.ServiceModel.Channels.ChannelManagerBase> a <xref:System.ServiceModel.Channels.IChannelFactory> a slučuje `CreateChannel` přetížení do jedné `OnCreateChannel` abstraktní metody.
  
- <xref:System.ServiceModel.Channels.ChannelListenerBase> Implementuje třída <xref:System.ServiceModel.Channels.IChannelListener>. Postará se o správu základního stavu. 
  
 Podle následující diskuse [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) vzorku.  
  
### <a name="creating-a-channel-factory"></a>Vytvoření objektu pro vytváření kanálů  
 `UdpChannelFactory` Je odvozena z <xref:System.ServiceModel.Channels.ChannelFactoryBase>. Ukázka přepíše <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> pro poskytnutí přístupu k verze kodér zprávy. Ukázka také přepisuje <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> k dovolí naše instanci <xref:System.ServiceModel.Channels.BufferManager> když změní stav stavového stroje.  
  
#### <a name="the-udp-output-channel"></a>Výstupní kanál UDP  
 `UdpOutputChannel` Implementuje <xref:System.ServiceModel.Channels.IOutputChannel>. Konstruktor ověří argumenty a vytvoří cíl <xref:System.Net.EndPoint> objektu na základě <xref:System.ServiceModel.EndpointAddress> , který je předán.  
  
 Přepsané <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> vytvoří soket, který se používá k odesílání zpráv do to <xref:System.Net.EndPoint>.  
  
 ```csharp 
this.socket = new Socket(  
this.remoteEndPoint.AddressFamily,
   SocketType.Dgram,
   ProtocolType.Udp
);  
```  

 Kanál můžete zavřít, bez výpadku nebo ungracefully. Pokud kanál je uzavřen řádně soketu se zavře a základní třídy je provedeno volání `OnClose` metoda. Pokud to vyvolá výjimku, zavolá infrastruktury `Abort` zajistit kanál je vyčištěn.  
  
```csharp  
this.socket.Close();  
base.OnClose(timeout);  
```  
  
 Implementace `Send()` a `BeginSend()` / `EndSend()`. Tím je prolomen na dvě hlavní části. Nejprve serializovat zprávu do bajtového pole:  
  
```csharp  
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 Odešlete na lince Výsledná data:  
  
```csharp  
this.socket.SendTo(  
  messageBuffer.Array,   
  messageBuffer.Offset,   
  messageBuffer.Count,   
  SocketFlags.None,   
  this.remoteEndPoint  
);  
```  
  
## <a name="see-also"></a>Viz také:

- [Vývoj kanálů](../../../../docs/framework/wcf/extending/developing-channels.md)
