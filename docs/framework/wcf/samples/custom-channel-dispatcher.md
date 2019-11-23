---
title: Dispečer vlastního kanálu
ms.date: 03/30/2017
ms.assetid: 813acf03-9661-4d57-a3c7-eeab497321c6
ms.openlocfilehash: 0bd83e068de7cfa9cc531ee6b46b9b51c44c1b1d
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291538"
---
# <a name="custom-channel-dispatcher"></a>Dispečer vlastního kanálu
Tato ukázka předvádí, jak vytvořit zásobník kanálu vlastním způsobem implementací <xref:System.ServiceModel.ServiceHostBase> přímo a vytvořením vlastního dispečera kanálu v prostředí webového hostitele. Dispečer kanálu komunikuje s <xref:System.ServiceModel.Channels.IChannelListener>, aby přijímal kanály a načítají zprávy ze zásobníku kanálů. Tato ukázka také obsahuje základní ukázku, která ukazuje, jak vytvořit zásobník kanálu v prostředí webového hostitele pomocí <xref:System.ServiceModel.Activation.VirtualPathExtension>.  
  
## <a name="custom-servicehostbase"></a>Vlastní objektu ServiceHostBase  
 Tato ukázka implementuje základní typ <xref:System.ServiceModel.ServiceHostBase> namísto <xref:System.ServiceModel.ServiceHost> demonstruje, jak nahradit implementaci zásobníku Windows Communication Foundation (WCF) vlastní vrstvou zpracování zpráv nad zásobníkem kanálu. Přepíšete virtuální metodu <xref:System.ServiceModel.ServiceHostBase.InitializeRuntime%2A> k sestavení naslouchacího procesu kanálu a dispečeru kanálu.  
  
 K implementaci služby hostované na webu, Získejte rozšíření služby <xref:System.ServiceModel.Activation.VirtualPathExtension> z kolekce <xref:System.ServiceModel.ServiceHostBase.Extensions%2A> a přidejte ho do <xref:System.ServiceModel.Channels.BindingParameterCollection>, aby transportní vrstva věděla, jak nakonfigurovat naslouchací proces kanálu na základě nastavení hostitelského prostředí, to znamená Internetová informační služba (IIS)/Windows Process Activation Service (WAS).  
  
## <a name="custom-channel-dispatcher"></a>Dispečer vlastního kanálu  
 Dispečer vlastního kanálu rozšiřuje typ <xref:System.ServiceModel.Dispatcher.ChannelDispatcherBase>. Tento typ implementuje logiku programování vrstvy kanálu. V této ukázce je pro vzor výměny zpráv požadavek-odpověď podporován pouze <xref:System.ServiceModel.Channels.IReplyChannel>, ale vlastní dispečer kanálu lze snadno rozšířit na jiné typy kanálů.  
  
 Dispečer nejprve otevře naslouchací proces kanálu a pak přijme kanál odpovědí s jedním prvkem. S kanálem začíná odesílat zprávy (požadavky) v nekonečné smyčce. Pro každý požadavek vytvoří zprávu s odpovědí a pošle ji zpět klientovi.  
  
## <a name="creating-a-response-message"></a>Vytvoření zprávy s odpovědí  
 Zpracování zprávy je implementováno v typu `MyServiceManager`. V metodě `HandleRequest` se nejprve kontroluje `Action` záhlaví zprávy, aby se zobrazila informace o tom, jestli je požadavek podporovaný. Předdefinovaná akce SOAP "http://tempuri.org/HelloWorld/Hello" je definována tak, aby poskytovala filtrování zpráv. To je podobné jako koncept kontraktu služby v implementaci <xref:System.ServiceModel.ServiceHost>WCF.  
  
 Pro správný případ akce SOAP načte ukázka požadovaná data zprávy a vygeneruje odpovídající odpověď na žádost podobnou tomu, co se zobrazuje v případě <xref:System.ServiceModel.ServiceHost>.  
  
 Operaci HTTP-GET jste speciálně vystavili tak, že vrátíte vlastní zprávu HTML, v tomto případě to znamená, že můžete procházet službu z prohlížeče a zjistit, zda je správně zkompilována. Pokud akce SOAP neodpovídá, odešlete chybovou zprávu, která indikuje, že žádost není podporována.  
  
 Klient této ukázky je normální klient služby WCF, který nepředpokládá žádnou ze služeb. Proto je tato služba speciálně navržená tak, aby odpovídala tomu, co obdržíte z běžné implementace<xref:System.ServiceModel.ServiceHost> WCF. V důsledku toho se na straně klienta vyžaduje jenom kontrakt služby.  
  
## <a name="using-the-sample"></a>Použití ukázky  
 Spuštění klientské aplikace přímo vytvoří následující výstup.  
  
```output  
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
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\CustomChannelDispatcher`
