---
title: Programování služby na úrovni kanálů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8d8dcd85-0a05-4c44-8861-4a0b3b90cca9
ms.openlocfilehash: e00b5ae2c72a4d4dcd2140e9c280d5bfda3531c2
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50197194"
---
# <a name="service-channel-level-programming"></a>Programování služby na úrovni kanálů
Toto téma popisuje, jak psát aplikace služby Windows Communication Foundation (WCF) bez použití <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> a jeho přidruženého objektu modelu.  
  
## <a name="receiving-messages"></a>Příjem zpráv  
 Až bude připravená přijímat a zpracovávat zprávy, se vyžaduje následující kroky:  
  
1.  Vytvoření vazby.  
  
2.  Vytvoření naslouchacího procesu kanálu.  
  
3.  Otevřete modul pro naslouchání kanálu.  
  
4.  Přečtení požadavku a odeslat odpověď.  
  
5.  Zavřete všechny objekty kanálu.  
  
#### <a name="creating-a-binding"></a>Vytvoření vazby  
 Prvním krokem při naslouchání a přijímání zpráv vytváří vazbu. WCF se dodává s několik předdefinovaných nebo poskytované systémem vazby, se dají přímo po vytvoření instance jeden z nich. Navíc můžete také vytvořit vlastní vlastní vazby po vytvoření instance CustomBinding třídu, která je čemu kód v informacích 1.  
  
 Následující příklad kódu vytvoří instanci <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> a přidá <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> jeho elementů kolekce, což je kolekce elementů, které se používají k vytvoření kanálu zásobníku vazby. V tomto příkladu protože obsahuje kolekci prvků pouze <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, výsledný zásobník kanál obsahuje pouze přenosový kanál protokolu HTTP.  
  
#### <a name="building-a-channellistener"></a>Vytváření ChannelListener  
 Po vytvoření vazby, říkáme <xref:System.ServiceModel.Channels.Binding.BuildChannelListener%2A?displayProperty=nameWithType> k vytvoření naslouchacího procesu kanálu, kde parametr typu je tvar kanálu k vytvoření. V tomto příkladu používáme <xref:System.ServiceModel.Channels.IReplyChannel?displayProperty=nameWithType> protože chceme, aby k naslouchání pro příchozí zprávy ve vzoru výměny zpráv žádost odpověď.  
  
 <xref:System.ServiceModel.Channels.IReplyChannel> se používá pro příjem zpráv a odesílá zpět odpověď zprávy požadavku. Volání <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A?displayProperty=nameWithType> vrátí <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>, kterou lze použít pro příjem zprávy žádosti a má být zaslán zpět zprávu odpovědi.  
  
 Při vytváření naslouchací proces, předáme síťovou adresu, na které naslouchá, v tomto případě `http://localhost:8080/channelapp`. Obecně každý kanál přenosu podporuje jednu nebo může být několik adres schémata, třeba přenos pomocí protokolu HTTP podporuje schémata http a https.  
  
 Můžeme také předat prázdnou <xref:System.ServiceModel.Channels.BindingParameterCollection?displayProperty=nameWithType> při vytváření naslouchacího procesu. Parametr vazby je mechanismus pro předání parametrů, které řídí, jak by měly být sestaveny naslouchací proces. V našem příkladu nepoužíváme tyto parametry, takže jsme předat prázdnou kolekci.  
  
#### <a name="listening-for-incoming-messages"></a>Naslouchání pro příchozí zprávy  
 Potom říkáme <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> na naslouchací proces a začít přijímat kanály. Chování <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A?displayProperty=nameWithType> závisí na tom, zda přenos orientované na připojení nebo připojení bez. Pro přenosy tohoto připojení založenému na záznamech <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A> blokuje, dokud se nová žádost o připojení k dispozici ve v tom okamžiku vrátí nový kanál, který představuje toto nové připojení. Pro přenosy tohoto připojení bez, jako je například HTTP <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A> vrátí okamžitě jeden a pouze kanál, který vytvoří naslouchací proces přenosu.  
  
 V tomto příkladu vrátí naslouchací proces kanálu, který implementuje <xref:System.ServiceModel.Channels.IReplyChannel>. Pro příjem zpráv v tomto kanálu jsme první volání <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> na něj umístit ve stavu Připraveno pro komunikaci. Potom říkáme <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> která blokuje, dokud se přijetí e-mailu.  
  
#### <a name="reading-the-request-and-sending-a-reply"></a>Čtení požadavku a odeslání odpovědi  
 Když <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> vrátí <xref:System.ServiceModel.Channels.RequestContext>, získáme na přijatou zprávu pomocí jeho <xref:System.ServiceModel.Channels.RequestContext.RequestMessage%2A> vlastnost. Jsme vypsat akce a tělo zprávy obsah, (který předpokládáme je řetězec).  
  
 Odeslání odpovědi, vytvoříme novou odpověď v tomto případě předávání zpátky data řetězce, že dostali jsme požadavek. Potom říkáme <xref:System.ServiceModel.Channels.RequestContext.Reply%2A> k odeslání zprávy s odpovědí.  
  
#### <a name="closing-objects"></a>Zavírání objektů  
 Aby se zabránilo nevrácení prostředků, je velmi důležité zavřete objekty používané v rámci komunikace, když už nejsou povinné. V tomto příkladu jsme zavřete zprávu požadavku, kontext požadavku, kanál a naslouchací proces.  
  
 Následující příklad kódu ukazuje základní službu, ve kterém přijímá modul pro naslouchání kanálu pouze jednu zprávu. Skutečná služba zajišťuje přijímání kanály a přijímání zpráv až do ukončení služby.  
  
 [!code-csharp[ChannelProgrammingBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/channelprogrammingbasic/cs/serviceprogram.cs#1)]
 [!code-vb[ChannelProgrammingBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelprogrammingbasic/vb/serviceprogram.vb#1)]
