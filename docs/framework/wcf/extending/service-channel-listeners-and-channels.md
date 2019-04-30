---
title: 'Služba: Moduly pro naslouchání kanálů a kanály'
ms.date: 03/30/2017
ms.assetid: 8ccbe0e8-7e55-441d-80de-5765f67542fa
ms.openlocfilehash: 88bfdc879e4f3c7df6b2c4035c7ed7fdc2b4c41d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771457"
---
# <a name="service-channel-listeners-and-channels"></a>Služba: Moduly pro naslouchání kanálů a kanály

Existují tři kategorie objekty kanálu: kanály, moduly pro naslouchání kanálů a objekty pro vytváření kanálů. Kanály představují rozhraní mezi aplikací a kanálů zásobníku. Moduly pro naslouchání kanálů zodpovídají za vytváření kanálů na straně příjmu (nebo naslouchání), obvykle v reakci na nové příchozí zprávy nebo připojení. Objekty pro vytváření kanálů zodpovídají za vytváření kanálů na straně odesílání inicializovat komunikaci s koncovým bodem.

## <a name="channel-listeners-and-channels"></a>Moduly pro naslouchání kanálů a kanály

Moduly pro naslouchání kanálů zodpovídají za vytváření kanálů a přijímání zpráv z vrstvy pod nebo ze sítě. Přijaté zprávy doručovaly do vrstvy nad pomocí kanálu, který je vytvořen naslouchací proces kanálu.

Následující obrázek znázorňuje proces přijímání zpráv a jejich doručování vrstvě nad ní.

![Naslouchací objekty kanálů a kanály](./media/wcfc-wcfchannelsigure1highlevelc.gif "wcfc_WCFChannelsigure1HighLevelc")

Naslouchací službu kanálu přijímání zpráv a doručování do vrstvy nad prostřednictvím kanálů.

Proces můžete ale implementace nelze použít ve skutečnosti fronty koncepčně nemodelují jako fronty uvnitř každý kanál. Modul pro naslouchání kanálu je zodpovědná za příjmu zprávy z vrstvy pod nebo sítě a umístit je do fronty. Kanál je zodpovědný za získání zpráv z fronty a předat je do vrstvy nad při této vrstvy vyzve k zadání zprávy, například voláním `Receive` na kanálu.

WCF poskytuje pomocné rutiny základní třídy pro tento proces. (Diagram tříd pomocných rutin kanál popisovaných v tomto článku, najdete v části [přehled modelu kanálu](channel-model-overview.md).)

- <xref:System.ServiceModel.Channels.CommunicationObject> Implementuje třída <xref:System.ServiceModel.ICommunicationObject> a vynucuje stavového stroje popsaný v kroku 2 z [vývoj kanálů](developing-channels.md).

- <xref:System.ServiceModel.Channels.ChannelManagerBase> Implementuje třída <xref:System.ServiceModel.Channels.CommunicationObject> a poskytuje jednotné základní třídu pro <xref:System.ServiceModel.Channels.ChannelFactoryBase> a <xref:System.ServiceModel.Channels.ChannelListenerBase>. <xref:System.ServiceModel.Channels.ChannelManagerBase> Třídy funguje ve spojení s <xref:System.ServiceModel.Channels.ChannelBase>, což je základní třídy, která implementuje <xref:System.ServiceModel.Channels.IChannel>.

- <xref:System.ServiceModel.Channels.ChannelFactoryBase> Implementuje třída <xref:System.ServiceModel.Channels.ChannelManagerBase> a <xref:System.ServiceModel.Channels.IChannelFactory> a slučuje `CreateChannel` přetížení do jedné `OnCreateChannel` abstraktní metody.

- <xref:System.ServiceModel.Channels.ChannelListenerBase> Implementuje třída <xref:System.ServiceModel.Channels.IChannelListener>. Postará se o správu základního stavu.

Podle následující diskuse [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) vzorku.

## <a name="creating-a-channel-listener"></a>Vytváření naslouchacího procesu kanálu

`UdpChannelListener` , Že implementuje vzorek je odvozen od <xref:System.ServiceModel.Channels.ChannelListenerBase> třídy. Pro příjem datagramy používá pro jediný soket UDP. `OnOpen` Metoda přijímá data pomocí soketu UDP v asynchronní smyčka. Data se potom převedou na zpráv s použitím systému kódování zprávy:

```csharp
message = UdpConstants.MessageEncoder.ReadMessage(
  new ArraySegment<byte>(buffer, 0, count),
  bufferManager
);
```

Vzhledem k tomu, že představuje stejný kanálu datagramu zprávy přicházející z mnoha různých zdrojů, `UdpChannelListener` běží naslouchací proces typu singleton. Ve většině jednu aktivní je <xref:System.ServiceModel.Channels.IChannel> spojené s tímto naslouchacím procesem najednou. Ukázka generuje jiný pouze v případě, že kanál, který je vrácený <xref:System.ServiceModel.Channels.ChannelListenerBase%601.AcceptChannel%2A> metoda následně uvolněn. Při doručení zprávy do je zařazených do fronty do tohoto kanálu typu singleton.

### <a name="udpinputchannel"></a>UdpInputChannel

`UdpInputChannel` Implementuje třída <xref:System.ServiceModel.Channels.IInputChannel>. Skládá se z front příchozích zpráv, které je vyplněn `UdpChannelListener`uživatele soketu. Tyto zprávy jsou odstraněné z fronty podle <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A> metody.
