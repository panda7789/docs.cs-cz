---
title: 'Služba: naslouchací procesy kanálu a kanály'
ms.date: 03/30/2017
ms.assetid: 8ccbe0e8-7e55-441d-80de-5765f67542fa
ms.openlocfilehash: 4367d844867db7fdad013e30d047f9385addbce5
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834801"
---
# <a name="service-channel-listeners-and-channels"></a>Služba: naslouchací procesy kanálu a kanály

Existují tři kategorie objektů kanálů: kanály, naslouchací procesy kanálu a továrny kanálů. Kanály jsou rozhraní mezi aplikací a zásobníkem kanálů. Naslouchací procesy kanálu jsou zodpovědné za vytváření kanálů na straně příjmu (nebo poslouchání), obvykle v reakci na novou příchozí zprávu nebo připojení. Továrny kanálů jsou zodpovědné za vytváření kanálů na straně odeslání pro zahájení komunikace s koncovým bodem.

## <a name="channel-listeners-and-channels"></a>Naslouchací procesy kanálu a kanály

Naslouchací procesy kanálu jsou zodpovědné za vytváření kanálů a příjem zpráv z vrstvy níže nebo ze sítě. Přijaté zprávy jsou doručeny do vrstvy výše pomocí kanálu vytvořeného pomocí naslouchacího procesu kanálu.

Následující diagram znázorňuje proces přijímání zpráv a jejich doručování do vrstvy výše.

![Naslouchací procesy kanálu a kanály](./media/wcfc-wcfchannelsigure1highlevelc.gif "wcfc_WCFChannelsigure1HighLevelc")

Naslouchací proces kanálu přijímá zprávy a doručuje je do vrstvy výše přes kanály.

Tento proces může být koncepčně modelován jako fronta uvnitř každého kanálu, i když implementace nemusí ve skutečnosti používat frontu. Naslouchací proces kanálu zodpovídá za příjem zpráv z vrstvy níže nebo z sítě a jejich vložení do fronty. Kanál zodpovídá za získávání zpráv z fronty a jejich předání do vrstvy výše, když tato vrstva požádá o zprávu, například voláním `Receive` na kanálu.

WCF poskytuje pomocníky pro základní třídy pro tento proces. Diagram pomocných tříd kanálu popsaných v tomto článku najdete v tématu [Přehled modelů kanálů](channel-model-overview.md).

- Třída <xref:System.ServiceModel.Channels.CommunicationObject> implementuje <xref:System.ServiceModel.ICommunicationObject> a vynutila Stavový počítač popsaný v kroku 2 [Vývoj kanálů](developing-channels.md).

- Třída <xref:System.ServiceModel.Channels.ChannelManagerBase> implementuje <xref:System.ServiceModel.Channels.CommunicationObject> a poskytuje jednotnou základní třídu pro <xref:System.ServiceModel.Channels.ChannelFactoryBase> a <xref:System.ServiceModel.Channels.ChannelListenerBase>. Třída <xref:System.ServiceModel.Channels.ChannelManagerBase> funguje ve spojení s <xref:System.ServiceModel.Channels.ChannelBase>, což je základní třída, která implementuje <xref:System.ServiceModel.Channels.IChannel>.

- Třída <xref:System.ServiceModel.Channels.ChannelFactoryBase> implementuje <xref:System.ServiceModel.Channels.ChannelManagerBase> a <xref:System.ServiceModel.Channels.IChannelFactory> a konsoliduje `CreateChannel` přetížení do jedné abstraktní metody `OnCreateChannel`.

- Třída <xref:System.ServiceModel.Channels.ChannelListenerBase> implementuje <xref:System.ServiceModel.Channels.IChannelListener>. Je potřeba se starat o základní správu stavu.

Následující diskuze jsou založené na ukázce [Transport: UDP](../samples/transport-udp.md) .

## <a name="creating-a-channel-listener"></a>Vytvoření naslouchacího procesu kanálu

@No__t-0, který ukázka implementuje, je odvozena od třídy <xref:System.ServiceModel.Channels.ChannelListenerBase>. K příjmu datagramů používá jeden soket UDP. Metoda `OnOpen` přijímá data pomocí soketu UDP v asynchronní smyčce. Data se pak převedou na zprávy pomocí systému kódování zpráv:

```csharp
message = UdpConstants.MessageEncoder.ReadMessage(
  new ArraySegment<byte>(buffer, 0, count),
  bufferManager
);
```

Vzhledem k tomu, že stejný kanál datagram představuje zprávy, které přicházejí z řady zdrojů, je `UdpChannelListener` naslouchací proces typu singleton. K tomuto naslouchacímu procesu je v tuto chvíli přidružená nejvýše jedna aktivní <xref:System.ServiceModel.Channels.IChannel>. Ukázka vygeneruje další pouze v případě, že je kanál vrácený metodou <xref:System.ServiceModel.Channels.ChannelListenerBase%601.AcceptChannel%2A> následně vyřazen. Po přijetí zprávy se tato zpráva zaznamená do fronty s tímto kanálem typu singleton.

### <a name="udpinputchannel"></a>UdpInputChannel

Třída `UdpInputChannel` implementuje <xref:System.ServiceModel.Channels.IInputChannel>. Skládá se z fronty příchozích zpráv, které jsou naplněné soketem `UdpChannelListener`. Tyto zprávy se odřadí do fronty metodou <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A>.
