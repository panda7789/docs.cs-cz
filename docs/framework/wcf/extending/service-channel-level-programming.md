---
title: "Programování služby na úrovni kanálů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 8d8dcd85-0a05-4c44-8861-4a0b3b90cca9
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 718f3c8fd2d6ed3434f7231e3ccaf8cf1a663875
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="service-channel-level-programming"></a>Programování služby na úrovni kanálů
Toto téma popisuje, jak napsat [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikace bez použití služby <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> a jeho přidružený objekt modelu.  
  
## <a name="receiving-messages"></a>Přijímání zpráv  
 Bude připravená přijmout a zpracování zpráv, jsou požadovány následující kroky:  
  
1.  Vytvoření vazby.  
  
2.  Vytvořte naslouchací proces kanálu.  
  
3.  Otevřete naslouchací proces kanálu nástroje.  
  
4.  Čtení požadavku a odeslat odpověď.  
  
5.  Zavřete všechny objekty kanálu.  
  
#### <a name="creating-a-binding"></a>Vytváření vazby  
 Prvním krokem při čekání na a přijímání zpráv vytváří vazbu. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]se dodává s několik předdefinovaných nebo poskytované systémem vazby, které lze použít přímo po vytvoření instance jeden z nich. Kromě toho můžete také vytvořit vlastní vlastní vazby po vytvoření instance CustomBinding třídu, která je jaké kód v výpis 1.  
  
 Následující příklad kódu vytvoří instanci <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> a přidá <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> k jeho elementy kolekce, která je kolekce elementů, které se používají k vytvoření kanálu zásobníku vazby. V tomto příkladu protože kolekce elementů je k dispozici pouze <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, výsledný zásobník kanál má pouze přenosu kanál protokolu HTTP.  
  
#### <a name="building-a-channellistener"></a>Vytváření ChannelListener  
 Po vytvoření vazby, říkáme <!--zz<xref:System.ServiceModel.Channels.Binding.BuildChannelListener%601%2A?displayProperty=nameWithType>--> `System.ServiceModel.Channels.Binding.BuildChannelListener` vytvořit naslouchací proces kanálu, kde parametr typu je tvar kanál, který má vytvořit. V tomto příkladu používáme <xref:System.ServiceModel.Channels.IReplyChannel?displayProperty=nameWithType> vzhledem k tomu, že chceme přijímat příchozí zprávy v vzorce výměny zpráv požadavek nebo odpověď.  
  
 <xref:System.ServiceModel.Channels.IReplyChannel>používá se k přijetí žádosti, zpráv a odesílá zpět odpovídáte zprávy. Volání metody <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A?displayProperty=nameWithType> vrátí <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>, který může být použit pro příjem zprávy žádosti a má být zaslán zpět zprávu odpovědi.  
  
 Při vytváření naslouchací proces, jsme předat síťovou adresu, na kterém naslouchá, v takovém případě `http://localhost:8080/channelapp`. Obecně platí, každý kanál přenos podporuje jednu nebo může být několik adresu schémat, například přenos HTTP podporuje schémata http a https.  
  
 Můžeme také předat prázdnou <xref:System.ServiceModel.Channels.BindingParameterCollection?displayProperty=nameWithType> při vytváření naslouchací proces. Parametr vazby je mechanismus předat parametry, které řídí, jak by měly být vytvořeny naslouchací proces. V našem příkladu nejsou používáme tyto parametry, jsme předat prázdnou kolekci.  
  
#### <a name="listening-for-incoming-messages"></a>Čekání na příchozí zprávy  
 Potom říkáme <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> na naslouchací proces a počáteční přijetí kanály. Chování <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A?displayProperty=nameWithType> závisí na tom, zda přenos orientovaná na připojení nebo bez připojení. Pro přenosy připojovací <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A> zablokuje, dokud novou žádost o připojení se dodává na bod, který vrátí nový kanál, který představuje nové připojení. Pro připojení bez přenosy, jako je například HTTP <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A> vrátí okamžitě s ten a pouze kanálu, který vytvoří naslouchací proces přenosu.  
  
 V tomto příkladu vrací naslouchací proces kanálu, který implementuje <xref:System.ServiceModel.Channels.IReplyChannel>. Pro příjem zpráv v tomto kanálu jsme první volání <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> na něm pro jeho umístění ve stavu Připraveno pro komunikaci. Potom říkáme <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> které bloky, dokud doručení zprávy.  
  
#### <a name="reading-the-request-and-sending-a-reply"></a>Čtení požadavku a odeslání odpovědi  
 Když <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> vrátí <xref:System.ServiceModel.Channels.RequestContext>, se nám získat na přijatou zprávu pomocí jeho <xref:System.ServiceModel.Channels.RequestContext.RequestMessage%2A> vlastnost. Jsme zapsat akce a text zprávy obsah, (který předpokladu, že je řetězec).  
  
 Odesílat odpovědi, jsme vytvořte novou odpověď zprávu v tomto případě předávání zpět řetězec dat, že jsme dodán v žádosti. Potom říkáme <xref:System.ServiceModel.Channels.RequestContext.Reply%2A> odeslat zprávu odpovědi.  
  
#### <a name="closing-objects"></a>Zavírání objektů  
 Aby se zabránilo úniku prostředky, je velmi důležité zavřete objekty použitých při komunikaci, pokud už je potřeba. V tomto příkladu jsme zavřete zprávu požadavku, kontext požadavku, kanál a naslouchací proces.  
  
 Následující příklad kódu ukazuje základní služby, ve kterém naslouchací proces kanálu přijímá pouze jednu zprávu. Skutečné služba udržuje přijetí kanály a přijímání zpráv až do konce službu.  
  
 [!code-csharp[ChannelProgrammingBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/channelprogrammingbasic/cs/serviceprogram.cs#1)]
 [!code-vb[ChannelProgrammingBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelprogrammingbasic/vb/serviceprogram.vb#1)]
