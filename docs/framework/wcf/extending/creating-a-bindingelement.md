---
title: Vytvoření BindingElement
ms.date: 03/30/2017
ms.assetid: 01a35307-a41f-4ef6-a3db-322af40afc99
ms.openlocfilehash: 4b760f9373e64e153bd5a21469eb7a503283d35c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795821"
---
# <a name="creating-a-bindingelement"></a>Vytvoření BindingElement
Vazby a prvky vazby (objekty, které <xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType> přesahují <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>a v uvedeném pořadí) jsou místo, kde je model aplikace Windows Communication Foundation (WCF) spojený s objekty pro vytváření kanálů a naslouchacími procesy kanálu. Bez vazeb vyžaduje použití vlastních kanálů programování na úrovni kanálu, jak je popsáno v tématu [programování na úrovni kanálu služby](service-channel-level-programming.md) a [programování na úrovni kanálu klienta](client-channel-level-programming.md). Toto téma popisuje minimální požadavek na povolení použití kanálu v technologii WCF, vývoj <xref:System.ServiceModel.Channels.BindingElement> pro kanál a povolení použití z aplikace, jak je popsáno v kroku 4 [Vývoj kanálů](developing-channels.md).  
  
## <a name="overview"></a>Přehled  
 Vytvořením <xref:System.ServiceModel.Channels.BindingElement> pro kanál umožníte vývojářům používat ho v aplikaci WCF. <xref:System.ServiceModel.Channels.BindingElement>objekty lze použít z <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> třídy pro připojení aplikace WCF k kanálu bez nutnosti zadávat přesné informace o typu vašeho kanálu.  
  
 Po vytvoření můžete povolit více funkcí v závislosti na vašich požadavcích podle pokynů pro vývoj zbývajících kanálů popsaných v tématu [Vývoj kanálů.](developing-channels.md) <xref:System.ServiceModel.Channels.BindingElement>  
  
## <a name="adding-a-binding-element"></a>Přidání elementu vazby  
 Chcete-li implementovat <xref:System.ServiceModel.Channels.BindingElement>vlastní, zapište třídu, která <xref:System.ServiceModel.Channels.BindingElement>dědí z. Pokud jste například vytvořili `ChunkingChannel` a mohli rozdělit velké zprávy do bloků dat a znovu je sestavit na druhý konec, můžete tento kanál použít v jakékoli vazbě <xref:System.ServiceModel.Channels.BindingElement> implementací a konfigurací vazby pro jeho použití. Zbývající část tohoto tématu používá `ChunkingChannel` jako příklad k předvedení požadavků implementace prvku vazby.  
  
 Je zodpovědný za `ChunkingChannelFactory` vytváření a `ChunkingChannelListener`. `ChunkingBindingElement` Přepisuje <xref:System.ServiceModel.Channels.BindingElement.CanBuildChannelFactory%2A> a <xref:System.ServiceModel.Channels.BindingElement.CanBuildChannelListener%2A> implementuje a kontroluje, zda je <xref:System.ServiceModel.Channels.IDuplexSessionChannel> parametr typu (v našem příkladu je to jediný tvar kanálu podporovaný rozhraním `ChunkingChannel`) a že ostatní prvky vazby ve vazbě tuto podporu podporují. obrazec kanálu  
  
 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A>Nejdřív zkontroluje, jestli je možné vytvořit požadovaný obrazec kanálu, a pak získá seznam akcí zprávy, které se mají zablokovat. Pak vytvoří nový `ChunkingChannelFactory`a předá objekt pro vytváření interních kanálů. (Pokud vytváříte element vazby přenosu, tento prvek je poslední v zásobníku vazby, a proto musí vytvořit naslouchací proces kanálu nebo objekt pro vytváření kanálů.)  
  
 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A>má podobnou implementaci pro vytvoření `ChunkingChannelListener` a předání naslouchací proces vnitřního kanálu.  
  
 Dalším příkladem použití transportního kanálu [je přenos: Ukázka](../samples/transport-udp.md) UDP poskytuje následující přepsání.  
  
 V ukázce je prvek vazby, který je `UdpTransportBindingElement`odvozen z. <xref:System.ServiceModel.Channels.TransportBindingElement> Přepíše následující metody pro sestavení továrn přidružených k kanálu.  
  
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
  
 Obsahuje také členy pro klonování `BindingElement` a vracení našeho schématu (SOAP. UDP).  
  
#### <a name="protocol-binding-elements"></a>Prvky vazby protokolu  
 Nové prvky vazby mohou nahradit nebo rozšířit libovolné vložené prvky vazby, přidat nové přenosy, kódování nebo protokoly vyšší úrovně. Chcete-li vytvořit nový element vazby protokolu, začněte tím, <xref:System.ServiceModel.Channels.BindingElement> že rozšíříte třídu. Přinejmenším je nutné implementovat <xref:System.ServiceModel.Channels.BindingElement.Clone%2A?displayProperty=nameWithType> a `ChannelProtectionRequirements` implementovat použití <xref:System.ServiceModel.Channels.IChannel.GetProperty%2A?displayProperty=nameWithType>. Tato funkce vrátí <xref:System.ServiceModel.Security.ChannelProtectionRequirements> pro tento prvek vazby.  Další informace naleznete v tématu <xref:System.ServiceModel.Security.ChannelProtectionRequirements>.  
  
 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>by měl vracet novou kopii tohoto elementu vazby. Jako osvědčený postup doporučujeme, aby tvůrci elementů vazby implementovali <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> pomocí kopírovacího konstruktoru, který volá konstruktor základní kopie, a potom naklonuje všechna další pole v této třídě.  
  
#### <a name="transport-binding-elements"></a>Elementy vazby přenosu  
 Chcete-li vytvořit nový prvek vazby přenosu, rozšíříte <xref:System.ServiceModel.Channels.TransportBindingElement> rozhraní. Přinejmenším je nutné implementovat <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> metodu <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A?displayProperty=nameWithType> a vlastnost.  
  
 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>– Má vrátit novou kopii tohoto elementu vazby.  Jako osvědčený postup doporučujeme, aby autoři elementů vazby implementovali klon pomocí kopírovacího konstruktoru, který volá konstruktor základní kopie, a potom naklonuje všechna další pole v této třídě.  
  
 <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A>– Vlastnost <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> get vrátí schéma identifikátoru URI pro transportní protokol reprezentovaný prvkem vazby. Například <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> a vrátí "http" a "NET. TCP" z odpovídajících vlastností. <xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=nameWithType>  
  
#### <a name="encoding-binding-elements"></a>Kódování elementů vazby  
 Chcete-li vytvořit nové prvky vazby kódování, začněte rozšířením <xref:System.ServiceModel.Channels.BindingElement> třídy a <xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=nameWithType> implementací třídy. Minimální je nutné implementovat <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>metody, <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A?displayProperty=nameWithType> a <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.MessageVersion%2A?displayProperty=nameWithType> vlastnost.  
  
- <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>. Vrátí novou kopii tohoto elementu vazby. Jako osvědčený postup doporučujeme, aby tvůrci elementů vazby implementovali <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> pomocí kopírovacího konstruktoru, který volá konstruktor základní kopie, a potom naklonuje všechna další pole v této třídě.  
  
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A>. Vrátí, který poskytuje popisovač ke skutečné třídě, která implementuje váš nový kodér a který by měl být rozšířen <xref:System.ServiceModel.Channels.MessageEncoder>. <xref:System.ServiceModel.Channels.MessageEncoderFactory> Další informace naleznete v tématu <xref:System.ServiceModel.Channels.MessageEncoderFactory> a <xref:System.ServiceModel.Channels.MessageEncoder>.  
  
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.MessageVersion%2A>. <xref:System.ServiceModel.Channels.MessageVersion> Vrátí použitý v tomto kódování, který představuje verze protokolu SOAP a adresování, které se používají.  
  
 Úplný seznam volitelných metod a vlastností pro uživatelsky definované prvky vazby kódování naleznete v tématu <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.  
  
 Další informace o vytvoření nového prvku vazby naleznete v tématu [vytváření uživatelsky definovaných vazeb](creating-user-defined-bindings.md).  
  
 Po vytvoření prvku vazby pro váš kanál se vraťte do tématu [vývojové kanály](developing-channels.md) , abyste viděli, zda chcete přidat podporu konfiguračního souboru do prvku vazby, pokud a jak přidat podporu publikace metadat a zda a jak konstrukce uživatelsky definované vazby, která používá váš element vazby.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Channels.BindingElement>
- [Vývoj kanálů](developing-channels.md)
- [Přepravu UDP](../samples/transport-udp.md)
