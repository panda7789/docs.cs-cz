---
title: 'Klient: Objekty pro vytváření kanálů a kanály'
ms.date: 03/30/2017
ms.assetid: ef245191-fdab-4468-a0da-7c6f25d2110f
ms.openlocfilehash: 25e2c034d1fefc7728667231040a97c3aeecabbd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185697"
---
# <a name="client-channel-factories-and-channels"></a>Klient: Objekty pro vytváření kanálů a kanály
Toto téma popisuje vytvoření kanálu továrny a kanály.  
  
## <a name="channel-factories-and-channels"></a>Objekty pro vytváření kanálů a kanály  
 Továrny kanálu jsou zodpovědné za vytváření kanálů. Kanály vytvořené továrnami kanálů se používají pro odesílání zpráv. Tyto kanály jsou zodpovědné za získání zprávy z výše uvedené vrstvy, provádění jakéhokoli zpracování je nezbytné, pak odeslání zprávy do vrstvy níže. Následující obrázek ilustruje tento proces.  
  
 ![Klientské továrny a kanály](./media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")  
Factory kanálu vytvoří kanály.  
  
 Při zavření jsou továrny kanálů zodpovědné za uzavření všech kanálů, které vytvořily a které ještě nejsou uzavřeny. Všimněte si, že model je asymetrický, protože když je naslouchací proces kanálu uzavřen, přestane přijímat pouze nové kanály, ale ponechá existující kanály otevřené, aby mohly pokračovat v přijímání zpráv.  
  
 WCF poskytuje základní třídy pomocné soubory pro tento proces. (Diagram tříd pomocných kanálů popsaných v tomto tématu naleznete v tématu [Přehled modelu kanálu](channel-model-overview.md).)  
  
- Třída <xref:System.ServiceModel.Channels.CommunicationObject> implementuje <xref:System.ServiceModel.ICommunicationObject> a vynucuje stavový počítač popsaný v kroku 2 [vývoj kanálů](developing-channels.md).  
  
- Třída <xref:System.ServiceModel.Channels.ChannelManagerBase> implementuje <xref:System.ServiceModel.Channels.CommunicationObject> a poskytuje jednotnou základní třídu pro <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> a <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>. Třída <xref:System.ServiceModel.Channels.ChannelManagerBase> pracuje ve <xref:System.ServiceModel.Channels.ChannelBase>spojení s , což je <xref:System.ServiceModel.Channels.IChannel>základní třída, která implementuje .
  
- Třída <xref:System.ServiceModel.Channels.ChannelFactoryBase> <xref:System.ServiceModel.Channels.ChannelManagerBase> implementuje <xref:System.ServiceModel.Channels.IChannelFactory> a `CreateChannel` konsoliduje `OnCreateChannel` přetížení do jedné abstraktní metody.
  
- Třída <xref:System.ServiceModel.Channels.ChannelListenerBase> implementuje <xref:System.ServiceModel.Channels.IChannelListener>. Stará se o základní státní řízení.
  
 Následující diskuse je založena na [transportu: UDP](../samples/transport-udp.md) vzorku.  
  
### <a name="creating-a-channel-factory"></a>Vytvoření továrny kanálu  
 Pochází `UdpChannelFactory` z <xref:System.ServiceModel.Channels.ChannelFactoryBase>. Ukázka přepíše <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> poskytnout přístup k verzi zprávy kodéru zprávy. Ukázka také <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> přepíše strhnout <xref:System.ServiceModel.Channels.BufferManager> naši instanci při přechodu stavového počítače.  
  
#### <a name="the-udp-output-channel"></a>Výstupní kanál UDP  
 Nářadí `UdpOutputChannel` <xref:System.ServiceModel.Channels.IOutputChannel>. Konstruktor ověří argumenty a vytvoří <xref:System.Net.EndPoint> cílový objekt <xref:System.ServiceModel.EndpointAddress> na základě, který je předán palců  
  
 Přepsání <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> vytvoří soket, který slouží <xref:System.Net.EndPoint>k odesílání zpráv do tohoto .  
  
 ```csharp
this.socket = new Socket(  
this.remoteEndPoint.AddressFamily,
   SocketType.Dgram,
   ProtocolType.Udp
);  
```  

 Kanál může být uzavřen elegantně nebo ungracefully. Pokud je kanál řádně uzavřen, soket je uzavřen a `OnClose` je provedeno volání metody základní třídy. Pokud to vyvolá výjimku, `Abort` volání infrastruktury k zajištění kanálu je vyčištěna.  
  
```csharp  
this.socket.Close();  
base.OnClose(timeout);  
```  
  
 `Send()` Implementovat `BeginSend()` / `EndSend()`a . To se rozdělí na dvě hlavní části. Nejprve serialize zprávy do bajtového pole:  
  
```csharp  
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 Poté odešlete výsledná data na drát:  
  
```csharp  
this.socket.SendTo(  
  messageBuffer.Array,
  messageBuffer.Offset,
  messageBuffer.Count,
  SocketFlags.None,
  this.remoteEndPoint  
);  
```  
  
## <a name="see-also"></a>Viz také

- [Vývoj kanálů](developing-channels.md)
