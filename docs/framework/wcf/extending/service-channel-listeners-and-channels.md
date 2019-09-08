---
title: 'Služba: Naslouchací procesy kanálu a kanály'
ms.date: 03/30/2017
ms.assetid: 8ccbe0e8-7e55-441d-80de-5765f67542fa
ms.openlocfilehash: 0a740f5dcf682c3c140adb9c4c7c9678c4eae132
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797179"
---
# <a name="service-channel-listeners-and-channels"></a>Služba: Naslouchací procesy kanálu a kanály

Existují tři kategorie objektů kanálů: kanály, naslouchací procesy kanálu a továrny kanálů. Kanály jsou rozhraní mezi aplikací a zásobníkem kanálů. Naslouchací procesy kanálu jsou zodpovědné za vytváření kanálů na straně příjmu (nebo poslouchání), obvykle v reakci na novou příchozí zprávu nebo připojení. Továrny kanálů jsou zodpovědné za vytváření kanálů na straně odeslání pro zahájení komunikace s koncovým bodem.

## <a name="channel-listeners-and-channels"></a>Naslouchací procesy kanálu a kanály

Naslouchací procesy kanálu jsou zodpovědné za vytváření kanálů a příjem zpráv z vrstvy níže nebo ze sítě. Přijaté zprávy jsou doručeny do vrstvy výše pomocí kanálu vytvořeného pomocí naslouchacího procesu kanálu.

Následující diagram znázorňuje proces přijímání zpráv a jejich doručování do vrstvy výše.

![Naslouchací procesy kanálu a kanály](./media/wcfc-wcfchannelsigure1highlevelc.gif "wcfc_WCFChannelsigure1HighLevelc")

Naslouchací proces kanálu přijímá zprávy a doručuje je do vrstvy výše přes kanály.

Tento proces může být koncepčně modelován jako fronta uvnitř každého kanálu, i když implementace nemusí ve skutečnosti používat frontu. Naslouchací proces kanálu zodpovídá za příjem zpráv z vrstvy níže nebo z sítě a jejich vložení do fronty. Kanál zodpovídá za získávání zpráv z fronty a jejich předání do vrstvy výše, když tato vrstva požádá o zprávu, například voláním `Receive` na kanál.

WCF poskytuje pomocníky pro základní třídy pro tento proces. (Diagram pomocných tříd kanálu popsaných v tomto článku najdete v tématu [Přehled modelu kanálů](channel-model-overview.md).)

- Třída implementuje <xref:System.ServiceModel.ICommunicationObject> a vynutila Stavový počítač popsaný v kroku 2 [Vývoj kanálů.](developing-channels.md) <xref:System.ServiceModel.Channels.CommunicationObject>

- Třída implementuje <xref:System.ServiceModel.Channels.CommunicationObject> a poskytuje sjednocenou základní třídu pro <xref:System.ServiceModel.Channels.ChannelFactoryBase> a <xref:System.ServiceModel.Channels.ChannelListenerBase>. <xref:System.ServiceModel.Channels.ChannelManagerBase> Třída pracuje ve spojení s <xref:System.ServiceModel.Channels.ChannelBase>, což je základní třída, která implementuje <xref:System.ServiceModel.Channels.IChannel>. <xref:System.ServiceModel.Channels.ChannelManagerBase>

- <xref:System.ServiceModel.Channels.ChannelFactoryBase> Třída implementuje <xref:System.ServiceModel.Channels.ChannelManagerBase> a<xref:System.ServiceModel.Channels.IChannelFactory> konsoliduje přetíženído`OnCreateChannel` jedné abstraktní metody. `CreateChannel`

- <xref:System.ServiceModel.Channels.ChannelListenerBase> Třída implementuje<xref:System.ServiceModel.Channels.IChannelListener>. Je potřeba se starat o základní správu stavu.

Následující diskuze jsou založené [na přenosu: Ukázka](../samples/transport-udp.md) UDP

## <a name="creating-a-channel-listener"></a>Vytvoření naslouchacího procesu kanálu

Rozhraní `UdpChannelListener` , které ukázka implementuje, je odvozena <xref:System.ServiceModel.Channels.ChannelListenerBase> od třídy. K příjmu datagramů používá jeden soket UDP. `OnOpen` Metoda přijímá data pomocí soketu UDP v asynchronní smyčce. Data se pak převedou na zprávy pomocí systému kódování zpráv:

```csharp
message = UdpConstants.MessageEncoder.ReadMessage(
  new ArraySegment<byte>(buffer, 0, count),
  bufferManager
);
```

Vzhledem k tomu, že stejný kanál datagram představuje zprávy, které přicházejí z řady zdrojů `UdpChannelListener` , je naslouchací proces typu singleton. K tomuto naslouchacímu procesu je <xref:System.ServiceModel.Channels.IChannel> v jednu chvíli přidružená nejvýše jedna aktivní. Ukázka vygeneruje další pouze v případě, že kanál vrácený <xref:System.ServiceModel.Channels.ChannelListenerBase%601.AcceptChannel%2A> metodou je následně vyřazen. Po přijetí zprávy se tato zpráva zaznamená do fronty s tímto kanálem typu singleton.

### <a name="udpinputchannel"></a>UdpInputChannel

`UdpInputChannel` Třída implementuje<xref:System.ServiceModel.Channels.IInputChannel>. Skládá se z fronty příchozích zpráv, které jsou vyplněny `UdpChannelListener`soketem. Tyto zprávy jsou odřazeny <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A> metodou.
