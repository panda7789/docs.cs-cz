---
title: 'Služba: Moduly pro naslouchání kanálů a kanály'
ms.date: 03/30/2017
ms.assetid: 8ccbe0e8-7e55-441d-80de-5765f67542fa
ms.openlocfilehash: eca7061243fa7f006079d19c3eaaf86ba906bca2
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="service-channel-listeners-and-channels"></a>Služba: Moduly pro naslouchání kanálů a kanály
Existují tři kategorie objektů kanál: kanály, kanál naslouchací procesy a objekty factory kanálu. Kanály jsou rozhraní mezi aplikací a zásobník kanálu. Kanál moduly pro naslouchání jsou zodpovědní za vytváření kanály na straně příjmu (nebo naslouchání), obvykle v reakci na nové příchozí zprávy nebo připojení. Objekty Factory kanál jsou zodpovědní za vytváření kanály na straně odesílání zahájíte komunikaci s koncovým bodem.  
  
## <a name="channel-listeners-and-channels"></a>Moduly pro naslouchání kanálů a kanály  
 Kanál moduly pro naslouchání jsou zodpovědní za vytváření kanálů a příjmu zprávy z vrstvy níže nebo ze sítě. Přijaté zprávy jsou doručovány na vrstvu nad pomocí kanálu, který byl vytvořený naslouchací proces kanálu nástroje.  
  
 Následující diagram znázorňuje proces přijímání zpráv a jejich předání do vrstvy výše.  
  
 ![Kanálu naslouchací procesy a kanály](../../../../docs/framework/wcf/extending/media/wcfc-wcfchannelsigure1highlevelc.gif "wcfc_WCFChannelsigure1HighLevelc")  
Kanál naslouchání přijímání zpráv a doručování vrstvu nad prostřednictvím kanálů.  
  
 Proces můžete ale implementace nesmíte používat ve skutečnosti fronty koncepčně modelovaná jako fronty uvnitř každý kanál. Naslouchací proces kanálu nástroje zodpovídá za příjmu zprávy z vrstvy níže nebo síti a jejich uvádění ve frontě. Kanál zodpovídá za načítání zpráv z fronty a předat je vrstvu nad při této vrstvy vyzve k zadání zprávy, například voláním `Receive` na kanálu.  
  
 WCF poskytuje pomocné rutiny základní třídy pro tento proces. (Diagram kanál pomocných tříd, popsané v tomto tématu, najdete v části [přehled modelu kanálu](../../../../docs/framework/wcf/extending/channel-model-overview.md).)  
  
-   <xref:System.ServiceModel.Channels.CommunicationObject> Třída implementuje <xref:System.ServiceModel.ICommunicationObject> a vynucuje stav stavového stroje popsané v kroku 2 [rozvojových kanály](../../../../docs/framework/wcf/extending/developing-channels.md).  
  
-   <xref:System.ServiceModel.Channels.ChannelManagerBase> Třída implementuje <xref:System.ServiceModel.Channels.CommunicationObject> a poskytuje jednotnou základní třídu pro <xref:System.ServiceModel.Channels.ChannelFactoryBase> a <xref:System.ServiceModel.Channels.ChannelListenerBase>. <xref:System.ServiceModel.Channels.ChannelManagerBase> Třída pracuje ve spojení s <xref:System.ServiceModel.Channels.ChannelBase>, což je základní třídu, která implementuje <xref:System.ServiceModel.Channels.IChannel>.  
  
-   ''<xref:System.ServiceModel.Channels.ChannelFactoryBase> Třída implementuje <xref:System.ServiceModel.Channels.ChannelManagerBase> a <xref:System.ServiceModel.Channels.IChannelFactory> a dojde ke konsolidaci `CreateChannel` přetížení do jednoho `OnCreateChannel` abstraktní metodu.  
  
-   <xref:System.ServiceModel.Channels.ChannelListenerBase> Třída implementuje <xref:System.ServiceModel.Channels.IChannelListener>. Se má na starosti správu základních stavu.  
  
 Podle následující diskuzi [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) ukázka.  
  
## <a name="creating-a-channel-listener"></a>Vytváření naslouchací proces kanálu  
 '' UdpChannelListener, který implementuje ukázce je odvozena z <xref:System.ServiceModel.Channels.ChannelListenerBase> třídy. Pro jediný soket UDP používá pro příjem datagramy. `OnOpen` Metoda přijímá data pomocí soketu UDP v asynchronní smyčce. Data se pak převedou na zprávy pomocí zprávy kódování systému:  
  
```  
message = UdpConstants.MessageEncoder.ReadMessage(  
  new ArraySegment<byte>(buffer, 0, count),   
  bufferManager  
);  
```  
  
 Protože stejné kanálu datagramu představuje zprávy, které přicházejí z mnoha zdrojů, `UdpChannelListener` naslouchací proces typu singleton. Ve většině jednu aktivní je <xref:System.ServiceModel.Channels.IChannel>'' přidružené k této naslouchací proces najednou. Ukázka generuje jiný pouze v případě, že kanál, který je vrácen rutinou <xref:System.ServiceModel.Channels.ChannelListenerBase%601.AcceptChannel%2A> metoda je následně zlikvidován. Při příjmu zprávy je zařazených do fronty do tohoto kanálu, typu singleton.  
  
### <a name="udpinputchannel"></a>UdpInputChannel  
 `UdpInputChannel` Třída implementuje <xref:System.ServiceModel.Channels.IInputChannel>. Skládá se z fronty příchozích zpráv, které se nacházejí `UdpChannelListener`je soketu. Tyto zprávy jsou vyjmutou pomocí <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A> metoda.
