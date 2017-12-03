---
title: "Klienta: Objekty pro vytváření kanálů a kanály"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef245191-fdab-4468-a0da-7c6f25d2110f
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f4a841fec01b3a0ef29cd836cccf3f337f29ddb6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="client-channel-factories-and-channels"></a>Klienta: Objekty pro vytváření kanálů a kanály
Toto téma popisuje vytvářet objekty pro vytváření kanálů a kanály.  
  
## <a name="channel-factories-and-channels"></a>Objekty pro vytváření kanálů a kanály  
 Objekty Factory kanál jsou zodpovědní za vytváření kanálů. Kanály vytvořený kanál objekty Factory se používají pro odesílání zpráv. Tyto kanály jsou zodpovědní za načtení zprávy z vrstvy výše, provádění, ať zpracování je nezbytné, pak odeslání zprávy do vrstvy níže. Tento proces je znázorněný na následujícím obrázku.  
  
 ![Objekty Factory klienta a kanály](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")  
Postup kanálu vytvoří kanály.  
  
 Při zavření, objekty Factory kanál jsou zodpovědní za zavřením žádné kanály, které se vytvářely, které nejsou dosud zavřena. Všimněte si, že model asymetrické zde vzhledem k tomu, že při zavření naslouchací proces kanálu pouze zastaví přijetí nové kanály, ale nechá, které existující kanály otevřete tak, aby může i dál přijímání zpráv.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Poskytuje pomocné rutiny základní třídy pro tento proces. (Diagram kanál pomocných tříd, popsané v tomto tématu, najdete v části [přehled modelu kanálu](../../../../docs/framework/wcf/extending/channel-model-overview.md).)  
  
-   <xref:System.ServiceModel.Channels.CommunicationObject> Třída implementuje <xref:System.ServiceModel.ICommunicationObject> a vynucuje stav stavového stroje popsané v kroku 2 [rozvojových kanály](../../../../docs/framework/wcf/extending/developing-channels.md).  
  
-   ''<xref:System.ServiceModel.Channels.ChannelManagerBase> Třída implementuje <xref:System.ServiceModel.Channels.CommunicationObject> a poskytuje jednotnou základní třídu pro <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> a <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>. <xref:System.ServiceModel.Channels.ChannelManagerBase> Třída pracuje ve spojení s <xref:System.ServiceModel.Channels.ChannelBase>, což je základní třídu, která implementuje <xref:System.ServiceModel.Channels.IChannel>.  
  
-   ''<xref:System.ServiceModel.Channels.ChannelFactoryBase> Třída implementuje <xref:System.ServiceModel.Channels.ChannelManagerBase> a <xref:System.ServiceModel.Channels.IChannelFactory> a dojde ke konsolidaci `CreateChannel` přetížení do jednoho `OnCreateChannel` abstraktní metodu.  
  
-   ''<xref:System.ServiceModel.Channels.ChannelListenerBase> Třída implementuje <xref:System.ServiceModel.Channels.IChannelListener>. Se má na starosti správu základních stavu.  
  
 Podle následující diskuzi [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) ukázka.  
  
### <a name="creating-a-channel-factory"></a>Vytvoření postupu kanálu  
 `UdpChannelFactory` Je odvozena z <xref:System.ServiceModel.Channels.ChannelFactoryBase>. Ukázka přepsání <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> k poskytování přístupu k zpráva verzi kodér zpráv. Ukázka také přepsání <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> přerušit naše instanci <xref:System.ServiceModel.Channels.BufferManager> když přejde stav stavového stroje.  
  
#### <a name="the-udp-output-channel"></a>Výstupní kanál UDP  
 `UdpOutputChannel` Implementuje <xref:System.ServiceModel.Channels.IOutputChannel>. Ověří argumenty konstruktoru a vytvoří cíl <xref:System.Net.EndPoint> na základě objektu <xref:System.ServiceModel.EndpointAddress> , je předaná.  
  
 Přepsané <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> vytvoří soketu, který se používá k odeslání zprávy do tohoto <xref:System.Net.EndPoint>.  
  
 `this.socket = new Socket(`  
  
 `this.remoteEndPoint.AddressFamily,`  
  
 `SocketType.Dgram,`  
  
 `ProtocolType.Udp`  
  
 `);`  
  
 Kanál je možné uzavřít řádně nebo ungracefully. Pokud je kanál řádně uzavřen soketu se zavře a je volána v základní třídě `OnClose` metoda. Pokud to vyvolá výjimku, zavolá infrastruktury `Abort` zajistit kanál je vyčištěna.  
  
```  
this.socket.Close();  
base.OnClose(timeout);  
```  
  
 Implementace `Send()` a `BeginSend()` / `EndSend()`. To rozdělí na dvě hlavní části. Nejprve serializovat zprávy do bajtového pole:  
  
```  
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 Potom odešlete Výsledná data v drátové síti:  
  
```  
this.socket.SendTo(  
  messageBuffer.Array,   
  messageBuffer.Offset,   
  messageBuffer.Count,   
  SocketFlags.None,   
  this.remoteEndPoint  
);  
```  
  
## <a name="see-also"></a>Viz také  
 [Vývoj kanálů](../../../../docs/framework/wcf/extending/developing-channels.md)
