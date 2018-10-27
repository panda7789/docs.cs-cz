---
title: Vytvoření BindingElement
ms.date: 03/30/2017
ms.assetid: 01a35307-a41f-4ef6-a3db-322af40afc99
ms.openlocfilehash: 5b7fd3e88fa12a66e086906de6f0d7d6a7d1aa17
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2018
ms.locfileid: "49454457"
---
# <a name="creating-a-bindingelement"></a>Vytvoření BindingElement
Vazby a prvky vazeb (objekty, které rozšiřují <xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType> a <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>v uvedeném pořadí) jsou místo, kde se spojená s objekty pro vytváření kanálů a moduly pro naslouchání kanálů model aplikace Windows Communication Foundation (WCF). Bez vazby, použití vlastních kanálů vyžaduje programování na úrovni kanálu jak je popsáno v [programování na úrovni kanálu služby](../../../../docs/framework/wcf/extending/service-channel-level-programming.md) a [programování na úrovni kanálu klienta](../../../../docs/framework/wcf/extending/client-channel-level-programming.md). Toto téma popisuje minimální požadavky na povolení s využitím kanálu ve službě WCF, vývoj <xref:System.ServiceModel.Channels.BindingElement> pro kanál a povolit používání instrukcí z aplikace, jak je popsáno v kroku 4 [vývoj kanálů](../../../../docs/framework/wcf/extending/developing-channels.md).  
  
## <a name="overview"></a>Přehled  
 Vytváření <xref:System.ServiceModel.Channels.BindingElement> pro váš kanál umožňuje vývojářům používat v aplikaci WCF. <xref:System.ServiceModel.Channels.BindingElement> objekty lze z <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> třídy připojit aplikaci WCF na váš kanál bez nutnosti informace přesný typ kanálu.  
  
 Jednou <xref:System.ServiceModel.Channels.BindingElement> byl vytvořen, můžete povolit další funkce, v závislosti na vašich požadavků ve zbývajících krocích vývoj kanálu je popsáno v následující [vývoj kanálů](../../../../docs/framework/wcf/extending/developing-channels.md).  
  
## <a name="adding-a-binding-element"></a>Přidání elementu vazby  
 Chcete-li implementovat vlastní <xref:System.ServiceModel.Channels.BindingElement>, zápis, která dědí z třídy <xref:System.ServiceModel.Channels.BindingElement>. Například, pokud jste vytvořili `ChunkingChannel` , rozdělte objemné zprávy do bloků dat a sestavení na druhém konci, můžete použít tento kanál ve vazbě implementací <xref:System.ServiceModel.Channels.BindingElement> a konfiguraci vazby pro použití. Zbývající část tohoto tématu používá `ChunkingChannel` jako příklad k předvedení požadavky implementace element vazby.  
  
 A `ChunkingBindingElement` zodpovídá za vytvoření `ChunkingChannelFactory` a `ChunkingChannelListener`. Přepíše <xref:System.ServiceModel.Channels.BindingElement.CanBuildChannelFactory%2A> a <xref:System.ServiceModel.Channels.BindingElement.CanBuildChannelListener%2A> implementace a kontroly, které je parametr typu <xref:System.ServiceModel.Channels.IDuplexSessionChannel> (v našem příkladu to je jediný tvar kanálu podporována `ChunkingChannel`) a další prvky vazby ve vazbě podporu tohoto tvar kanálu.  
  
 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> nejprve zkontroluje, že požadovaný tvar kanálu může být sestaven a potom získá seznam zpráv akce, které mají být rozdělený do bloků dat. Potom vytvoří nový `ChunkingChannelFactory`, předají se jí výroba vnitřního kanálu. (Pokud vytváříte element vazby přenosu, tento prvek je poslední v zásobníku vazby a proto musíte vytvořit naslouchací proces kanálu nebo objekt pro vytváření kanálů.)  
  
 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> má podobné implementace pro vytvoření `ChunkingChannelListener` a předají se jí vnitřního kanálu naslouchacího procesu.  
  
 Další příklad použití přenosový kanál [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) ukázka poskytuje následující přepsání.  
  
 V ukázce je element vazby `UdpTransportBindingElement`, která je odvozena z <xref:System.ServiceModel.Channels.TransportBindingElement>. Přepíše následujících metod k vytváření továrny připojená ke kanálu.  
  
```csharp  
public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)  
{  
    return (IChannelFactory<TChannel>)(object)new UdpChannelFactory(this, context);  
}  
  
public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)  
{  
    return (IChannelListener<TChannel>)(object)new UdpChannelListener(this, context);  
}  
```  
  
 Také obsahuje členy pro klonování `BindingElement` a vrácení naše schéma (soap.udp).  
  
#### <a name="protocol-binding-elements"></a>Prvky vazeb protokolu  
 Nové prvky vazeb můžete nahradit nebo rozšířit některý z elementů vazby součástí, přidáte nové přenosy, kódování nebo vyšší úrovně protokoly. Chcete-li vytvořit nový prvek vazby protokolu, začněte tím, že rozšíření <xref:System.ServiceModel.Channels.BindingElement> třídy. Minimálně musíte pak implementovat <xref:System.ServiceModel.Channels.BindingElement.Clone%2A?displayProperty=nameWithType> a implementovat `ChannelProtectionRequirements` pomocí <xref:System.ServiceModel.Channels.IChannel.GetProperty%2A?displayProperty=nameWithType>. Tím se vrátí <xref:System.ServiceModel.Security.ChannelProtectionRequirements> pro tento element vazby.  Další informace naleznete v tématu <xref:System.ServiceModel.Security.ChannelProtectionRequirements>.  
  
 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> by měl vrátit novou kopii tohoto prvku vazby. Jako osvědčený postup doporučujeme, abyste tento element vazby autory implementace <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> pomocí kopírovací konstruktor, který volá základní konstruktor, poté duplicity všechna další pole v této třídě.  
  
#### <a name="transport-binding-elements"></a>Elementů přenosové vazby  
 Chcete-li vytvořit nový Element vazby přenosu, rozšířit <xref:System.ServiceModel.Channels.TransportBindingElement> rozhraní. Minimálně musíte pak implementovat <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> metoda a <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A?displayProperty=nameWithType> vlastnost.  
  
 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> – By měl vrátit novou kopii tohoto prvku vazby.  Jako osvědčený postup doporučujeme, že autoři prvku vazby implementovat klonování pomocí konstruktoru kopie, která volá základní konstruktor, a pak duplicity všechna další pole v této třídě.  
  
 <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> – Tím <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> získat schéma identifikátoru URI vrátí vlastnost reprezentována element vazby protokolu přenosu. Například <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> a <xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=nameWithType> vrátit "http" a "net.tcp" z jejich odpovídajících <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> vlastnosti.  
  
#### <a name="encoding-binding-elements"></a>Kódování elementů vazby  
 Pokud chcete vytvořit nové kódování vazby prvky, začněte tím, že rozšíření <xref:System.ServiceModel.Channels.BindingElement> třídy a implementace <xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=nameWithType> třídy. Minimálně musíte pak implementovat <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>, <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A?displayProperty=nameWithType> metody a <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.MessageVersion%2A?displayProperty=nameWithType> vlastnost.  
  
-   <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>. Vrátí novou kopii tohoto prvku vazby. Jako osvědčený postup doporučujeme, abyste tento element vazby autory implementace <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> pomocí kopírovací konstruktor, který volá základní konstruktor, poté duplicity všechna další pole v této třídě.  
  
-   <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A>. Vrátí <xref:System.ServiceModel.Channels.MessageEncoderFactory>, která poskytuje popisovač pro daná třída, která implementuje nový kodér a který by měl rozšířit <xref:System.ServiceModel.Channels.MessageEncoder>. Další informace naleznete v tématu <xref:System.ServiceModel.Channels.MessageEncoderFactory> a <xref:System.ServiceModel.Channels.MessageEncoder>.  
  
-   <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.MessageVersion%2A>. Vrátí <xref:System.ServiceModel.Channels.MessageVersion> použít v platném kódování, která představuje verze protokolu SOAP a WS-Addressing používá.  
  
 Úplný seznam všech volitelné metody a vlastnosti pro uživatelem definované kódování elementy vazby, naleznete v tématu <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.  
  
 Další informace o vytváření nového elementu vazby najdete v tématu [Creating User-Defined vazby](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).  
  
 Po vytvoření element vazby kanálu vrátit [vývoj kanálů](../../../../docs/framework/wcf/extending/developing-channels.md) tématu Určuje, zda chcete přidat konfigurační soubor podporu prvek vazby, pokud a jak přidat podporu publikování metadat, a zda a jak vytvořit vazbu definovaný uživatelem, který používá vaše element vazby.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.BindingElement>  
 [Vývoj kanálů](../../../../docs/framework/wcf/extending/developing-channels.md)  
 [Přenos: UDP](../../../../docs/framework/wcf/samples/transport-udp.md)
