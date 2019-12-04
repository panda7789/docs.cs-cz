---
title: Vlastní filtr zpráv
ms.date: 03/30/2017
ms.assetid: 98dd0af8-fce6-4255-ac32-42eb547eea67
ms.openlocfilehash: 79edba14eff5403591cf43592415d923dbd321be
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716826"
---
# <a name="custom-message-filter"></a>Vlastní filtr zpráv
Tato ukázka demonstruje, jak nahradit filtry zpráv, které Windows Communication Foundation (WCF) používá k odesílání zpráv do koncových bodů.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Když první zpráva na kanálu dorazí na server, server musí určit, který (pokud existuje) koncových bodů přidružených k tomuto identifikátoru URI by měla obdržet zprávu. Tento proces je řízen <xref:System.ServiceModel.Dispatcher.MessageFilter> objekty připojenými k <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.  
  
 Každý koncový bod služby má jednu <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>. <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> má <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> a <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>. Sjednocením těchto dvou filtrů je filtr zpráv použitý pro tento koncový bod.  
  
 Ve výchozím nastavení se <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> pro koncový bod shoduje se všemi zprávami, které jsou adresovány na adresu, která odpovídá <xref:System.ServiceModel.EndpointAddress>koncového bodu služby. Ve výchozím nastavení <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> pro koncový bod kontroluje akci příchozí zprávy a odpovídá jakékoli zprávě s akcí, která odpovídá jedné z akcí operací kontraktu koncového bodu služby (jenom `IsInitiating`=jsou zvažovány `true` akce). V důsledku toho filtr pro koncový bod ve výchozím nastavení odpovídá pouze v případě, že se jedná o <xref:System.ServiceModel.EndpointAddress> koncového bodu a akce zprávy odpovídá jedné z akcí operace koncového bodu.  
  
 Tyto filtry je možné změnit pomocí chování. V ukázce služba vytvoří <xref:System.ServiceModel.Description.IEndpointBehavior>, která nahrazuje <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> a <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> na <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>:  
  
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
  
 `FilteringEndpointBehavior` je možné konfigurovat a umožňuje dvě různé varianty.  
  
```csharp
public class FilteringEndpointBehaviorExtension : BehaviorExtensionElement { }
```  
  
 Variace 1 odpovídá jenom adresám, které obsahují "e" (ale mají jakoukoliv akci), zatímco variace 2 odpovídá jenom adresám, které nemají:  
  
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
  
 Potom služba vytvoří `endpointBehavior` konfigurace pro každou variaci:  
  
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
  
 Nakonec koncový bod služby odkazuje na jednu z `behaviorConfigurations`:  
  
```xml  
<endpoint address=""  
        bindingConfiguration="ws"  
        listenUri=""   
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IHello"   
        behaviorConfiguration="endpoint2" />  
```  
  
 Implementace klientské aplikace je jednoduchá; k identifikátoru URI služby vytvoří dva kanály (předáním této hodnoty jako druhý parametr (`via`) <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> a pošle jednu zprávu na každý kanál, ale pro každou z nich používá jiné adresy koncových bodů. Výsledkem je, že odchozí zprávy z klienta se liší od označení a server reaguje odpovídajícím způsobem, jak ukazuje výstup klienta:  
  
```console  
Sending message to urn:e...  
Exception: The message with To 'urn:e' cannot be processed at the receiver, due to an AddressFilter mismatch at the EndpointDispatcher.  Check that the sender and receiver's EndpointAddresses agree.  
  
Sending message to urn:a...  
Hello  
```  
  
 Přepnutí změn v konfiguračním souboru serveru způsobí, že se filtr promění a klient uvidí opačné chování (zpráva pro `urn:e` úspěšná, zatímco zpráva, která `urn:a` selže).  
  
```xml  
<endpoint address=""  
          bindingConfiguration="ws"  
          listenUri=""   
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.IHello"   
          behaviorConfiguration="endpoint1" />  
```  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageFilter`  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Pokud chcete ukázku spustit v konfiguraci s jedním počítačem, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
3. Pokud chcete ukázku spustit v konfiguraci mezi počítači, postupujte podle pokynů v článku [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md) a v Client.cs změňte následující řádek.  
  
    ```csharp
    Uri serviceVia = new Uri("http://localhost/ServiceModelSamples/service.svc");  
    ```  
  
     Položku localhost nahraďte názvem serveru.  
  
    ```csharp
    Uri serviceVia = new Uri("http://servermachinename/ServiceModelSamples/service.svc");  
    ```  
