---
title: "Dispečer vlastního kanálu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 813acf03-9661-4d57-a3c7-eeab497321c6
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5814850b3d5a25f5f3c118e732930168f9489d9d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="custom-channel-dispatcher"></a>Dispečer vlastního kanálu
Tato ukázka ukazuje, jak vytvořit kanál zásobníku vlastní způsobem implementací <xref:System.ServiceModel.ServiceHostBase> přímo a jak vytvořit vlastní kanál dispečera v prostředí hostitele webu. Dispečera kanál komunikuje s <xref:System.ServiceModel.Channels.IChannelListener> tak, aby přijímal zprávy kanály a načte z zásobníku kanálu. Tato ukázka také poskytuje základní ukázka, jak vytvořit kanál zásobníku v prostředí webové hostitele pomocí <xref:System.ServiceModel.Activation.VirtualPathExtension>.  
  
## <a name="custom-servicehostbase"></a>Vlastní ServiceHostBase  
 Tato ukázka implementuje základní typ <xref:System.ServiceModel.ServiceHostBase> místo <xref:System.ServiceModel.ServiceHost> abychom ukázali, jak nahradit [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] zásobník implementace vlastní zprávu zpracování vrstvu nad zásobníku kanálu. Potlačení virtuální metody <xref:System.ServiceModel.ServiceHostBase.InitializeRuntime%2A> k vytvoření naslouchacího procesu kanálu a dispečera kanálu.  
  
 K implementaci hostované webové služby, získat rozšíření služby <xref:System.ServiceModel.Activation.VirtualPathExtension> z <xref:System.ServiceModel.ServiceHostBase.Extensions%2A> kolekce a přidejte ho do <xref:System.ServiceModel.Channels.BindingParameterCollection> tak, aby přenosové vrstvy umí nakonfigurovat naslouchací proces kanálu nástroje na základě hostitelských nastaveních prostředí, který je Internetové informační služby (IIS) nebo nastavení služby Aktivace procesů systému Windows (WAS).  
  
## <a name="custom-channel-dispatcher"></a>Dispečer vlastního kanálu  
 Dispečer vlastního kanálu rozšiřuje typ <xref:System.ServiceModel.Dispatcher.ChannelDispatcherBase>. Tento typ implementuje programovací logiku vrstvy kanálu. V této ukázce pouze <xref:System.ServiceModel.Channels.IReplyChannel> je podporována pro vzorce výměny zpráv požadavku a odpovědi, ale dispečer vlastního kanálu lze snadno rozšířit na jiné typy kanálu.  
  
 Dispečera prvním otevření naslouchací proces kanálu nástroje a potom přijímá kanál odpověď typu singleton. S kanálem začne odesílat zprávy (počet požadavků) v nekonečné smyčce. Pro každý požadavek vytvoří zprávu odpovědi a odešle ho zpátky do klienta.  
  
## <a name="creating-a-response-message"></a>Vytváření zprávu odpovědi  
 Zpracování zpráv je implementován v typu `MyServiceManager`. V `HandleRequest` metody `Action` záhlaví zprávy nejdřív zkontroluje se zda žádost je podporováno. Předdefinované akce SOAP "http://tempuri.org/HelloWorld/Hello" je definována k poskytnutí filtrování zprávy. Toto je podobný koncept kontraktu služby ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementace <xref:System.ServiceModel.ServiceHost>.  
  
 Pro správnou velikost akce SOAP ukázku načte data pro požadovaný zprávu a vygeneruje odpovídající odpověď na žádost o podobná co je vidět v <xref:System.ServiceModel.ServiceHost> případu.  
  
 Speciálně zpracovává operaci HTTP GET, ve kterém můžete vyhledat službu z prohlížeče, zobrazí se, že zdařilo vrácením vlastní zprávu ve formátu HTML, v tomto případě. Pokud akce SOAP neodpovídá, Odeslat chybu zpět zpráva indikující, že tento požadavek není podporován.  
  
 Klient Tato ukázka je z něj normální [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, který nepředpokládá nic ze služby. Ano, službu speciálně navržené tak, aby odpovídaly, co můžete získat z něj normální [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <xref:System.ServiceModel.ServiceHost> implementace. V důsledku toho je v klientovi požadováno pouze kontraktu služby.  
  
## <a name="using-the-sample"></a>Pomocí vzorku  
 Spuštění klienta aplikace přímo vytvoří následující výstup.  
  
```Output  
Client is talking to a request/reply WCF service.   
Type what you want to say to the server: Howdy  
Server replied: You said: Howdy. Message id: 1  
Server replied: You said: Howdy. Message id: 2  
Server replied: You said: Howdy. Message id: 3  
Server replied: You said: Howdy. Message id: 4  
Server replied: You said: Howdy. Message id: 5  
```  
  
 Můžete také vyhledat službu z prohlížeče tak, aby na serveru získá zpracovat zprávu HTTP GET. Toto je dobře formátovaný text HTML získá zpět.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\CustomChannelDispatcher`
