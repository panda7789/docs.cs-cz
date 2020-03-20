---
title: Vlastní filtr zpráv
ms.date: 03/30/2017
ms.assetid: 98dd0af8-fce6-4255-ac32-42eb547eea67
ms.openlocfilehash: 896407a218073eba53676baa4bcbd125593c80ca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183885"
---
# <a name="custom-message-filter"></a>Vlastní filtr zpráv
Tato ukázka ukazuje, jak nahradit filtry zpráv, které Windows Communication Foundation (WCF) používá k odesílání zpráv do koncových bodů.  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
 Když na server dorazí první zpráva na kanálu, musí server určit, které (pokud existuje) koncových bodů přidružených k tomuto identifikátoru URI by měly zprávu obdržet. Tento proces je <xref:System.ServiceModel.Dispatcher.MessageFilter> řízen objekty <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>připojenými k .  
  
 Každý koncový bod služby <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>má jeden . Má <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> jak <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> a <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>a . Sjednocení těchto dvou filtrů je filtr zpráv používaný pro tento koncový bod.  
  
 Ve výchozím <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> nastavení pro koncový bod odpovídá všechny zprávy, která je určena na <xref:System.ServiceModel.EndpointAddress>adresu, která odpovídá koncovému bodu služby . Ve výchozím <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> nastavení pro koncový bod kontroluje akci příchozí zprávy a porovnává všechny zprávy s akcí, která odpovídá jedné z akcí `IsInitiating` = `true` operací smlouvy koncového bodu služby (jsou považovány pouze akce). V důsledku toho ve výchozím nastavení filtr pro koncový bod odpovídá pouze v <xref:System.ServiceModel.EndpointAddress> případě, že obě záhlaví zprávy Do je koncového bodu a akce zprávy odpovídá jedné z akcí operace koncového bodu.  
  
 Tyto filtry lze změnit pomocí chování. Ve vzorku služba <xref:System.ServiceModel.Description.IEndpointBehavior> vytvoří, který nahradí <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> a <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>na :  
  
```csharp
class FilteringEndpointBehavior : IEndpointBehavior
{
    //...
}
```  
  
 Jsou definovány dva filtry adres:  
  
```csharp
// Matches any message whose To address contains the letter 'e'  
class MatchEAddressFilter : MessageFilter { }
// Matches any message whose To address does not contain the letter 'e'  
class MatchNoEAddressFilter : MessageFilter { }  
```  
  
 Je `FilteringEndpointBehavior` konfigurovatelný a umožňuje dvě různé varianty.  
  
```csharp
public class FilteringEndpointBehaviorExtension : BehaviorExtensionElement { }
```  
  
 Varianta 1 odpovídá pouze adresám, které obsahují "e" (ale které mají nějakou akci), zatímco varianta 2 odpovídá pouze adresám, které postrádají "e":  
  
```csharp
if (Variation == 1)  
    return new FilteringEndpointBehavior(  
        new MatchEAddressFilter(), new MatchAllMessageFilter());  
else  
    return new FilteringEndpointBehavior(  
        new MatchNoEAddressFilter(), new MatchAllMessageFilter());  
```  
  
 V konfiguračním souboru služba zaregistruje nové chování:  
  
```xml  
<extensions>  
    <behaviorExtensions>  
        <add name="filteringEndpointBehavior" type="Microsoft.ServiceModel.Samples.FilteringEndpointBehaviorExtension, service" />  
    </behaviorExtensions>  
</extensions>
```  
  
 Pak služba `endpointBehavior` vytvoří konfigurace pro každou variantu:  
  
```xml  
<endpointBehaviors>  
    <behavior name="endpoint1">  
        <filteringEndpointBehavior variation="1" />  
    </behavior>  
    <behavior name="endpoint2">  
        <filteringEndpointBehavior variation="2" />  
    </behavior>  
</endpointBehaviors>  
```  
  
 Nakonec koncový bod služby odkazuje na `behaviorConfigurations`jednu z :  
  
```xml  
<endpoint address=""  
        bindingConfiguration="ws"  
        listenUri=""
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IHello"
        behaviorConfiguration="endpoint2" />  
```  
  
 Implementace klientské aplikace je jednoduchá; vytvoří dva kanály uri služby (předáním této hodnoty`via`jako druhý <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> parametr ( ) a odešle jednu zprávu na každém kanálu, ale používá různé adresy koncového bodu pro každý. V důsledku toho odchozí zprávy z klienta mají různé To označení a server odpovídá odpovídajícím způsobem, o čemž svědčí výstup klienta:  
  
```console  
Sending message to urn:e...  
Exception: The message with To 'urn:e' cannot be processed at the receiver, due to an AddressFilter mismatch at the EndpointDispatcher.  Check that the sender and receiver's EndpointAddresses agree.  
  
Sending message to urn:a...  
Hello  
```  
  
 Přepnutí míchací v konfiguračním souboru serveru způsobí, že filtr bude `urn:e` prohozen a klient `urn:a` uvidí opačné chování (zpráva bude úspěšná, zatímco zpráva se nezdaří).  
  
```xml  
<endpoint address=""  
          bindingConfiguration="ws"  
          listenUri=""
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.IHello"
          behaviorConfiguration="endpoint1" />  
```  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageFilter`  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Chcete-li vytvořit řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Chcete-li spustit ukázku v konfiguraci jednoho počítače, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci mezi počítači, postupujte podle pokynů na [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md) a změňte následující řádek v Client.cs.  
  
    ```csharp
    Uri serviceVia = new Uri("http://localhost/ServiceModelSamples/service.svc");  
    ```  
  
     Nahraďte localhost názvem serveru.  
  
    ```csharp
    Uri serviceVia = new Uri("http://servermachinename/ServiceModelSamples/service.svc");  
    ```  
