---
title: Dispečer vlastního kanálu
ms.date: 03/30/2017
ms.assetid: 813acf03-9661-4d57-a3c7-eeab497321c6
ms.openlocfilehash: af225a0f31c843f2c3ca949af6d616f89dc83435
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039970"
---
# <a name="custom-channel-dispatcher"></a>Dispečer vlastního kanálu
Tato ukázka předvádí, jak vytvořit zásobník kanálů vlastním způsobem implementací <xref:System.ServiceModel.ServiceHostBase> přímo a vytvořením vlastního dispečera kanálu v prostředí webového hostitele. Dispečer kanálu komunikuje s <xref:System.ServiceModel.Channels.IChannelListener> tím, že přijímá kanály a načítá zprávy ze zásobníku kanálů. Tato ukázka také obsahuje základní ukázku, která ukazuje, jak vytvořit zásobník kanálu v prostředí webového hostitele pomocí <xref:System.ServiceModel.Activation.VirtualPathExtension>.  
  
## <a name="custom-servicehostbase"></a>Vlastní objektu ServiceHostBase  
 Tato ukázka implementuje základní typ <xref:System.ServiceModel.ServiceHostBase> <xref:System.ServiceModel.ServiceHost> místo k demonstraci toho, jak nahradit implementaci zásobníku Windows Communication Foundation (WCF) vlastní vrstvou zpracování zpráv nad zásobníkem kanálu. Přepíšete virtuální metodu <xref:System.ServiceModel.ServiceHostBase.InitializeRuntime%2A> pro sestavení naslouchacího procesu kanálu a dispečera kanálu.  
  
 Chcete-li implementovat službu hostovanou webem, Získejte rozšíření <xref:System.ServiceModel.Activation.VirtualPathExtension> služby <xref:System.ServiceModel.ServiceHostBase.Extensions%2A> z kolekce a přidejte je do rozhraní <xref:System.ServiceModel.Channels.BindingParameterCollection> , aby transportní vrstva věděla, jak nakonfigurovat naslouchací proces kanálu na základě nastavení hostitelského prostředí, které Internetová informační služba je to nastavení/Windows (služba IIS) Process Activation Service (WAS).  
  
## <a name="custom-channel-dispatcher"></a>Dispečer vlastního kanálu  
 Dispečer vlastního kanálu rozšiřuje typ <xref:System.ServiceModel.Dispatcher.ChannelDispatcherBase>. Tento typ implementuje logiku programování vrstvy kanálu. V této ukázce se podporuje <xref:System.ServiceModel.Channels.IReplyChannel> jenom vzor výměny zpráv požadavku a odpovědi, ale vlastní dispečer kanálu se dá snadno rozšířit na jiné typy kanálů.  
  
 Dispečer nejprve otevře naslouchací proces kanálu a pak přijme kanál odpovědí s jedním prvkem. S kanálem začíná odesílat zprávy (požadavky) v nekonečné smyčce. Pro každý požadavek vytvoří zprávu s odpovědí a pošle ji zpět klientovi.  
  
## <a name="creating-a-response-message"></a>Vytvoření zprávy s odpovědí  
 Zpracování zprávy je implementováno v typu `MyServiceManager`. V metodě je nejprve kontrolována Hlavička zprávy, aby bylo možné zjistit, zda je požadavek podporován. `Action` `HandleRequest` Předdefinovaná akce SOAP "http://tempuri.org/HelloWorld/Hello" je definována tak, aby poskytovala filtrování zpráv. To je podobné jako koncept kontraktu služby v implementaci <xref:System.ServiceModel.ServiceHost>WCF.  
  
 Pro správný případ akce SOAP ukázka načte požadovaná data zprávy a vygeneruje odpovídající odpověď na žádost podobnou tomu, co se v <xref:System.ServiceModel.ServiceHost> případu zobrazuje.  
  
 Operaci HTTP-GET jste speciálně vystavili tak, že vrátíte vlastní zprávu HTML, v tomto případě to znamená, že můžete procházet službu z prohlížeče a zjistit, zda je správně zkompilována. Pokud akce SOAP neodpovídá, odešlete chybovou zprávu, která indikuje, že žádost není podporována.  
  
 Klient této ukázky je normální klient služby WCF, který nepředpokládá žádnou ze služeb. Proto je tato služba speciálně navržená tak, aby odpovídala tomu, co se<xref:System.ServiceModel.ServiceHost> stává při běžné implementaci služby WCF. V důsledku toho se na straně klienta vyžaduje jenom kontrakt služby.  
  
## <a name="using-the-sample"></a>Použití ukázky  
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
  
 Službu můžete také procházet z prohlížeče, aby se na serveru zpracovala zpráva HTTP-GET. Tím se vrátí kód HTML ve správném formátu.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\CustomChannelDispatcher`
