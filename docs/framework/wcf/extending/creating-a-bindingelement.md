---
title: "Vytvoření BindingElement"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 01a35307-a41f-4ef6-a3db-322af40afc99
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6fa68698c6c343b29ca39e66150753502cb8f673
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="creating-a-bindingelement"></a>Vytvoření BindingElement
Vazby a prvky vazeb (objekty, které rozšiřují <xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType> a <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>, v uvedeném pořadí) jsou na místě kde [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikačního modelu souvisí s objektů factory kanálu a moduly pro naslouchání kanálu. Bez vazby, použití vlastních kanály vyžaduje programování na úrovni kanálu jak je popsáno v [programování na úrovni služby kanálů](../../../../docs/framework/wcf/extending/service-channel-level-programming.md) a [programování na úrovni kanálu klienta](../../../../docs/framework/wcf/extending/client-channel-level-programming.md). Toto téma popisuje minimální požadavek na povolit pomocí kanálu v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], vývoj <xref:System.ServiceModel.Channels.BindingElement> pro kanál a povolit použití z aplikace, jak je popsáno v kroku 4 v [rozvojových kanály](../../../../docs/framework/wcf/extending/developing-channels.md).  
  
## <a name="overview"></a>Přehled  
 Vytváření <xref:System.ServiceModel.Channels.BindingElement> pro kanál umožňuje vývojářům používat ho [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace. <xref:System.ServiceModel.Channels.BindingElement>objekty lze z <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> třídy pro připojení [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikaci do kanálu bez nutnosti přesné typ informace kanálu.  
  
 Jednou <xref:System.ServiceModel.Channels.BindingElement> byl vytvořen, můžete povolit v závislosti na požadavcích podle kroků zbývající kanál vývoj kroky popsané v další funkce [rozvojových kanály](../../../../docs/framework/wcf/extending/developing-channels.md).  
  
## <a name="adding-a-binding-element"></a>Přidání prvku vazby  
 Chcete-li implementovat vlastní <xref:System.ServiceModel.Channels.BindingElement>, zápis třídu, která dědí z <xref:System.ServiceModel.Channels.BindingElement>. Například, pokud jste si vytvořili `ChunkingChannel` , můžete rozdělit velké zprávy do bloků a jejich sestavovat na druhém konci, můžete tento kanál v žádné vazbě implementací <xref:System.ServiceModel.Channels.BindingElement> a konfiguraci vazby pro použití. Zbývající část tohoto tématu používá `ChunkingChannel` jako příklad k předvedení požadavky na implementaci prvku vazby.  
  
 A `ChunkingBindingElement` zodpovídá za vytvoření `ChunkingChannelFactory` a `ChunkingChannelListener`. Přepíše <xref:System.ServiceModel.Channels.BindingElement.CanBuildChannelFactory%2A> a <xref:System.ServiceModel.Channels.BindingElement.CanBuildChannelListener%2A> implementace a kontroly, které parametr typu je <xref:System.ServiceModel.Channels.IDuplexSessionChannel> (v našem příkladu je to pouze tvar kanálu nepodporuje `ChunkingChannel`) a další prvky vazby vazba podporují tuto tvar kanálu.  
  
 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A>nejprve ověří, že požadovaný tvar kanálu se dají vytvářet a pak získá seznam zpráv akce, které mají být blokové. Ta poté vytvoří nový `ChunkingChannelFactory`, předání vnitřní kanálu. (Pokud vytváříte element vazby přenosu, tento element je naposledy v zásobníku vazby a proto musíte vytvořit naslouchací proces kanálu nebo kanálu.)  
  
 <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A>má podobné implementace pro vytvoření `ChunkingChannelListener` a předání naslouchací proces vnitřní kanálu.  
  
 Další příklad použití přenosu kanál [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) ukázka poskytuje následující přepsání.  
  
 V ukázce je prvku vazby `UdpTransportBindingElement`, která je odvozena z <xref:System.ServiceModel.Channels.TransportBindingElement>. Přepíše následující metody pro vytvoření objektů Factory související s kanálem.  
  
```  
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
 Nové prvky vazby můžete nahradit nebo posílení všechny prvky zahrnuté vazby, přidání nové přenosy, kódování nebo protokolů vyšší úrovně. Chcete-li vytvořit nového elementu vazby protokolu, spusťte rozšíření <xref:System.ServiceModel.Channels.BindingElement> třídy. Minimálně musí pak implementovat <xref:System.ServiceModel.Channels.BindingElement.Clone%2A?displayProperty=nameWithType> a implementovat `ChannelProtectionRequirements` pomocí <xref:System.ServiceModel.Channels.IChannel.GetProperty%2A?displayProperty=nameWithType>. Tento příkaz vrátí <xref:System.ServiceModel.Security.ChannelProtectionRequirements> pro tento element vazby.  Další informace naleznete v tématu <xref:System.ServiceModel.Security.ChannelProtectionRequirements>.  
  
 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>by měl vrátit novou kopii tohoto prvku vazby. Jako osvědčený postup doporučujeme tohoto prvku vazby vytvoří implementace <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> pomocí kopírovací konstruktor, který volá konstruktor copy základní pak provede klonování jakýchkoli dalších polí v této třídě.  
  
#### <a name="transport-binding-elements"></a>Elementů přenosové vazby  
 Pokud chcete vytvořit nového elementu vazby přenosu, rozšířit <xref:System.ServiceModel.Channels.TransportBindingElement> rozhraní. Minimálně musí pak implementovat <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> metoda a <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A?displayProperty=nameWithType> vlastnost.  
  
 <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>– By měl vrátit novou kopii tohoto elementu vazby.  Jako osvědčený postup doporučujeme, že vazba Element autoři implementovat klon prostřednictvím kopírovací konstruktor, který volá konstruktor copy základní a potom provede klonování jakýchkoli dalších polí v této třídě.  
  
 <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A>– Na <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> získat vlastnosti vrátí schéma identifikátoru URI pro přenosový protokol reprezentována prvku vazby. Například <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> a <xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=nameWithType> vrácení "http" a "net.tcp" z jejich odpovídajících <xref:System.ServiceModel.Channels.TransportBindingElement.Scheme%2A> vlastnosti.  
  
#### <a name="encoding-binding-elements"></a>Kódování elementů vazby  
 Chcete-li vytvořit nové kódování vazby prvky, začněte tím, že rozšíření <xref:System.ServiceModel.Channels.BindingElement> třídy a implementace <xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=nameWithType> třídy. Minimálně musí pak implementovat <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>, <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A?displayProperty=nameWithType> metody a <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.MessageVersion%2A?displayProperty=nameWithType> vlastnost.  
  
-   <xref:System.ServiceModel.Channels.BindingElement.Clone%2A>. Vrátí novou kopii tohoto prvku vazby. Jako osvědčený postup doporučujeme tohoto prvku vazby vytvoří implementace <xref:System.ServiceModel.Channels.BindingElement.Clone%2A> pomocí kopírovací konstruktor, který volá konstruktor copy základní pak provede klonování jakýchkoli dalších polí v této třídě.  
  
-   <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A>. Vrátí <xref:System.ServiceModel.Channels.MessageEncoderFactory>, který poskytuje popisovač pro skutečné třídě, implementuje nový kodér a který by měl rozšířit <xref:System.ServiceModel.Channels.MessageEncoder>. Další informace naleznete v tématu <xref:System.ServiceModel.Channels.MessageEncoderFactory> a <xref:System.ServiceModel.Channels.MessageEncoder>.  
  
-   <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.MessageVersion%2A>. Vrátí <xref:System.ServiceModel.Channels.MessageVersion> používá v toto kódování, která představuje verze protokolu SOAP a WS-Addressing používá.  
  
 Úplný seznam volitelné metod a vlastností pro uživatelská kódování prvky vazby, naleznete v <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.  
  
 Další informace o vytváření nového elementu vazby najdete v tématu [Creating User-Defined vazby](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).  
  
 Po vytvoření prvku vazby pro kanál, vraťte se do [rozvojových kanály](../../../../docs/framework/wcf/extending/developing-channels.md) tématu, jestli chcete přidat podporu konfigurace soubor do vaší prvku vazby Pokud a přidání podpory metadata publikace, a zda a jak vytvořit vazbu definovaný uživatelem, který používá vaše prvku vazby.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.BindingElement>  
 [Vývoj kanálů](../../../../docs/framework/wcf/extending/developing-channels.md)  
 [Přenos: UDP](../../../../docs/framework/wcf/samples/transport-udp.md)
