---
title: Dispečer vlastního kanálu
ms.date: 03/30/2017
ms.assetid: 813acf03-9661-4d57-a3c7-eeab497321c6
ms.openlocfilehash: 20574b4c849f312cb2cf55709d8d5e2a9b5dbca7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43519887"
---
# <a name="custom-channel-dispatcher"></a>Dispečer vlastního kanálu
Tato ukázka předvádí, jak k vytvoření kanálu zásobníku vlastním způsobem pomocí implementace <xref:System.ServiceModel.ServiceHostBase> přímo a vytvoření dispečer vlastního kanálu v prostředí webového hostitele. Dispečer kanálu komunikuje s <xref:System.ServiceModel.Channels.IChannelListener> tak, aby přijímal kanály a načte zprávy z kanálu zásobníku. Tato ukázka také poskytuje základní ukázka na ukazují, jak vytvořit kanál zásobníku v prostředí webového hostitele pomocí <xref:System.ServiceModel.Activation.VirtualPathExtension>.  
  
## <a name="custom-servicehostbase"></a>Vlastní ServiceHostBase  
 Tato ukázka základní typ implementuje <xref:System.ServiceModel.ServiceHostBase> místo <xref:System.ServiceModel.ServiceHost> předvést způsob implementace zásobníku Windows Communication Foundation (WCF) nahraďte vlastní zprávu zpracování vrstvu nad rámec zásobníku kanálu. Přepsat virtuální metodu <xref:System.ServiceModel.ServiceHostBase.InitializeRuntime%2A> vytvářet moduly pro naslouchání kanálů a dispečer kanálu.  
  
 K implementaci hostované webové služby, získejte rozšíření služby <xref:System.ServiceModel.Activation.VirtualPathExtension> z <xref:System.ServiceModel.ServiceHostBase.Extensions%2A> kolekce a přidejte ho do <xref:System.ServiceModel.Channels.BindingParameterCollection> tak, aby přenosové vrstvy ví, jak nakonfigurovat modul pro naslouchání kanálu na základě hostování nastavení prostředí, která je Internetové informační služby (IIS) / nastavení Windows Process Activation Service (WAS).  
  
## <a name="custom-channel-dispatcher"></a>Dispečer vlastního kanálu  
 Dispečer vlastního kanálu rozšíří typ <xref:System.ServiceModel.Dispatcher.ChannelDispatcherBase>. Tento typ implementuje programovou logiku vrstvě kanálu. V této ukázce pouze <xref:System.ServiceModel.Channels.IReplyChannel> se podporuje pro vzorce výměny zpráv žádost odpověď, ale dispečer vlastního kanálu je možné snadno rozšířit na jiné typy kanálu.  
  
 Dispečer poprvé otevře modul pro naslouchání kanálu a potom přijímá kanálu odpovědi typu singleton. S kanálem začne posílat zprávy (požadavky) v nekonečné smyčce. Pro každý požadavek vytváří zprávy s odpovědí a odešle ho zpátky do klienta.  
  
## <a name="creating-a-response-message"></a>Vytváření zprávu odpovědi  
 Zpracování zpráv je implementován v typu `MyServiceManager`. V `HandleRequest` metody `Action` záhlaví zprávy je nejprve zkontroluje, zda je požadavek nepodporuje. A předdefinované akce SOAP "http://tempuri.org/HelloWorld/Hello" je definován poskytují filtrování zpráv. Je to podobný koncept kontraktu služby WCF provádění <xref:System.ServiceModel.ServiceHost>.  
  
 Pro správnou velikost akce SOAP ukázka načte data požadovaná zpráv a vygeneruje odpovídající odpověď na požadavek podobný co je zobrazena v <xref:System.ServiceModel.ServiceHost> případ.  
  
 Speciálně zpracovány příkaz HTTP GET vrácením vlastní zprávu ve formátu HTML, v tomto případě tak, že můžete procházet službu z prohlížeče, zobrazí se, že je správně kompilován. Pokud neodpovídá akci SOAP, Odeslat chybu zprávy zpět k označení, že žádost se nepodporuje.  
  
 Klient této ukázky je normální klienta WCF, která nepřebírá žádné ze služby. Tedy službu speciálně navržená tak, aby odpovídaly získáte od normální WCF<xref:System.ServiceModel.ServiceHost> implementace. V důsledku toho je v klientovi požadováno pouze kontraktu služby.  
  
## <a name="using-the-sample"></a>Pomocí ukázky  
 Spuštění klientské aplikace přímo vytvoří následující výstup.  
  
```Output  
Client is talking to a request/reply WCF service.   
Type what you want to say to the server: Howdy  
Server replied: You said: Howdy. Message id: 1  
Server replied: You said: Howdy. Message id: 2  
Server replied: You said: Howdy. Message id: 3  
Server replied: You said: Howdy. Message id: 4  
Server replied: You said: Howdy. Message id: 5  
```  
  
 Můžete také procházet službu z prohlížeče tak, aby zpracuje zprávu HTTP GET na serveru. To vám formátovaného textu HTML získá zpět.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\CustomChannelDispatcher`
