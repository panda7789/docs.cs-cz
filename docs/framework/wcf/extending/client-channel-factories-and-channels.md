---
title: 'Klient: Objekty pro vytváření kanálů a kanály'
ms.date: 03/30/2017
ms.assetid: ef245191-fdab-4468-a0da-7c6f25d2110f
ms.openlocfilehash: 3dfcca0d5492a3fa376ec184f4bdd9bfa03b53c0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795860"
---
# <a name="client-channel-factories-and-channels"></a>Klient: Objekty pro vytváření kanálů a kanály
Toto téma popisuje vytváření kanálů a kanálů kanálu.  
  
## <a name="channel-factories-and-channels"></a>Objekty pro vytváření kanálů a kanály  
 Továrny kanálů jsou zodpovědné za vytváření kanálů. Kanály vytvořené pomocí kanálů kanálu se používají pro posílání zpráv. Tyto kanály jsou zodpovědné za získání zprávy z vrstvy výše, provádění jakéhokoli zpracování je nezbytné a následné odeslání zprávy do vrstvy níže. Tento proces je znázorněn na následujícím obrázku.  
  
 ![Klientské továrny a kanály](./media/wcfc-wcfchannelsigure2highlevelfactgoriesc.gif "wcfc_WCFChannelsigure2HIghLevelFactgoriesc")  
Objekt pro vytváření kanálů vytvoří kanály.  
  
 Po uzavření jsou objekty kanálů zodpovědné za uzavírání všech kanálů, které vytvořili, které ještě nejsou uzavřené. Model je tady asymetrická, protože když se spustí naslouchací proces kanálu, zastaví se jenom příjem nových kanálů, ale existující kanály zůstanou otevřené, aby mohli dál přijímat zprávy.  
  
 WCF poskytuje pomocníky pro základní třídy pro tento proces. (Diagram pomocných tříd kanálu popsaných v tomto tématu najdete v tématu [Přehled modelu kanálů](channel-model-overview.md).)  
  
- Třída implementuje <xref:System.ServiceModel.ICommunicationObject> a vynutila Stavový počítač popsaný v kroku 2 [Vývoj kanálů.](developing-channels.md) <xref:System.ServiceModel.Channels.CommunicationObject>  
  
- Třída implementuje <xref:System.ServiceModel.Channels.CommunicationObject> a poskytuje sjednocenou základní třídu pro <xref:System.ServiceModel.Channels.ChannelFactoryBase?displayProperty=nameWithType> a <xref:System.ServiceModel.Channels.ChannelListenerBase?displayProperty=nameWithType>. <xref:System.ServiceModel.Channels.ChannelManagerBase> Třída pracuje ve spojení s <xref:System.ServiceModel.Channels.ChannelBase>, což je základní třída, která implementuje <xref:System.ServiceModel.Channels.IChannel>. <xref:System.ServiceModel.Channels.ChannelManagerBase>
  
- <xref:System.ServiceModel.Channels.ChannelFactoryBase> Třída implementuje <xref:System.ServiceModel.Channels.ChannelManagerBase> a<xref:System.ServiceModel.Channels.IChannelFactory> konsoliduje přetíženído`OnCreateChannel` jedné abstraktní metody. `CreateChannel`
  
- <xref:System.ServiceModel.Channels.ChannelListenerBase> Třída implementuje<xref:System.ServiceModel.Channels.IChannelListener>. Je potřeba se starat o základní správu stavu. 
  
 Následující diskuze jsou založené [na přenosu: Ukázka](../samples/transport-udp.md) UDP  
  
### <a name="creating-a-channel-factory"></a>Vytvoření objektu pro vytváření kanálů  
 Je `UdpChannelFactory` odvozen z <xref:System.ServiceModel.Channels.ChannelFactoryBase>. Vzor přepíše <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> , aby poskytoval přístup k verzi zprávy kodéru zpráv. Tato ukázka také přepisuje <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> , aby <xref:System.ServiceModel.Channels.BufferManager> při přechodu na stav počítače nemohly vztrhnout naši instanci.  
  
#### <a name="the-udp-output-channel"></a>Výstupní kanál UDP  
 `UdpOutputChannel` Implementuje<xref:System.ServiceModel.Channels.IOutputChannel>rozhraní. Konstruktor ověřuje argumenty a vytvoří cílový <xref:System.Net.EndPoint> objekt na základě <xref:System.ServiceModel.EndpointAddress> předaného objektu.  
  
 Přepsání <xref:System.ServiceModel.Channels.CommunicationObject.OnOpen%2A> vytvoří soket, který slouží k posílání zpráv <xref:System.Net.EndPoint>.  
  
 ```csharp 
this.socket = new Socket(  
this.remoteEndPoint.AddressFamily,
   SocketType.Dgram,
   ProtocolType.Udp
);  
```  

 Kanál může být řádně uzavřený nebo neřádný. Pokud je kanál řádně uzavřený, soket je uzavřen a volání metody základní třídy `OnClose` je provedeno. Pokud to vyvolá výjimku, zavolá `Abort` infrastruktura, aby zajistila vyčištění kanálu.  
  
```csharp  
this.socket.Close();  
base.OnClose(timeout);  
```  
  
 `Send()` Implementujte `BeginSend()`a ./ `EndSend()` Tato část se rozdělí na dvě hlavní části. Nejdřív zaserializovat zprávu do bajtového pole:  
  
```csharp  
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 Pak odešlete výsledná data na kabel:  
  
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

- [Vývoj kanálů](developing-channels.md)
