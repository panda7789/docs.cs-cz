---
title: Dispečer vlastního kanálu
ms.date: 03/30/2017
ms.assetid: 813acf03-9661-4d57-a3c7-eeab497321c6
ms.openlocfilehash: ea1bdd470855d1b2f6572a15ce45f9b90d74fdca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145122"
---
# <a name="custom-channel-dispatcher"></a>Dispečer vlastního kanálu
Tato ukázka ukazuje, jak vytvořit zásobník kanálů vlastním <xref:System.ServiceModel.ServiceHostBase> způsobem implementací přímo a jak vytvořit vlastní dispečera kanálu v prostředí webhostingu. Dispečer kanálu <xref:System.ServiceModel.Channels.IChannelListener> spolupracuje s přijímat kanály a načítá zprávy ze zásobníku kanálu. Tato ukázka také obsahuje základní ukázku, která ukazuje, jak <xref:System.ServiceModel.Activation.VirtualPathExtension>vytvořit zásobník kanálů v prostředí webového hostitele pomocí aplikace .  
  
## <a name="custom-servicehostbase"></a>Vlastní servicehostbase  
 Tato ukázka implementuje základní typ <xref:System.ServiceModel.ServiceHostBase> namísto <xref:System.ServiceModel.ServiceHost> k předvedení, jak nahradit implementaci zásobníku Windows Communication Foundation (WCF) vlastní vrstvou zpracování zpráv v horní části zásobníku kanálu. Přepsat virtuální metodu <xref:System.ServiceModel.ServiceHostBase.InitializeRuntime%2A> k sestavení naslouchací procesy kanálu a dispečera kanálu.  
  
 Chcete-li implementovat webovou hostovnu, získejte rozšíření <xref:System.ServiceModel.Activation.VirtualPathExtension> služby z <xref:System.ServiceModel.ServiceHostBase.Extensions%2A> kolekce a přidejte ji <xref:System.ServiceModel.Channels.BindingParameterCollection> do aplikace tak, aby přenosová vrstva věděla, jak nakonfigurovat naslouchací proces kanálu na základě nastavení hostitelského prostředí, tj.  
  
## <a name="custom-channel-dispatcher"></a>Dispečer vlastního kanálu  
 Vlastní kanál dispečer <xref:System.ServiceModel.Dispatcher.ChannelDispatcherBase>rozšiřuje typ . Tento typ implementuje programovací logiku vrstvy kanálu. V této ukázce je podporována pouze <xref:System.ServiceModel.Channels.IReplyChannel> pro odběr-odpověď zprávy exchange vzor, ale vlastní kanál dispečera lze snadno rozšířit na jiné typy kanálů.  
  
 Dispečer nejprve otevře naslouchací proces kanálu a potom přijme kanál odpovědi singleton. S kanálem začne odesílat zprávy (požadavky) v nekonečné smyčce. Pro každý požadavek vytvoří zprávu s odpovědí a odešle ji zpět klientovi.  
  
## <a name="creating-a-response-message"></a>Vytvoření zprávy odpovědi  
 Zpracování zprávy je implementováno v typu `MyServiceManager`. V `HandleRequest` metodě `Action` záhlaví zprávy je nejprve zkontrolovat, zda je požadavek podporován. Předdefinovaná akcehttp://tempuri.org/HelloWorld/HelloSOAP " " je definována pro filtrování zpráv. To je podobné jako koncept smlouvy o <xref:System.ServiceModel.ServiceHost>poskytování služeb v implementaci WCF .  
  
 Pro správný případ akce SOAP ukázka načte data požadované zprávy a generuje odpovídající odpověď na <xref:System.ServiceModel.ServiceHost> požadavek podobné tomu, co je vidět v případě.  
  
 Speciálně zpracovány http-get sloveso vrácením vlastní zprávy HTML, v tomto případě tak, aby bylo možné procházet službu z prohlížeče vidět, že je zkompilován správně. Pokud se akce SOAP neshoduje, odešlete zpět zprávu o chybě, která označuje, že požadavek není podporován.  
  
 Klient této ukázky je normální WCF klienta, který nepředpokládá nic ze služby. Takže služba je speciálně navržen tak, aby odpovídaly co dostanete z normální implementace WCF.<xref:System.ServiceModel.ServiceHost> V důsledku toho je pro klienta vyžadována pouze servisní smlouva.  
  
## <a name="using-the-sample"></a>Použití vzorku  
 Spuštění klientské aplikace přímo vytváří následující výstup.  
  
```output  
Client is talking to a request/reply WCF service.
Type what you want to say to the server: Howdy  
Server replied: You said: Howdy. Message id: 1  
Server replied: You said: Howdy. Message id: 2  
Server replied: You said: Howdy. Message id: 3  
Server replied: You said: Howdy. Message id: 4  
Server replied: You said: Howdy. Message id: 5  
```  
  
 Službu můžete také procházet z prohlížeče tak, aby se na serveru zpracovala zpráva HTTP-GET. Tím získáte dobře formátovaný text HTML zpět.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\CustomChannelDispatcher`
