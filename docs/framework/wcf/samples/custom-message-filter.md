---
title: Vlastní filtr zpráv
ms.date: 03/30/2017
ms.assetid: 98dd0af8-fce6-4255-ac32-42eb547eea67
ms.openlocfilehash: c9a6e436548d4d1f009833f80899721c4c085513
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43746623"
---
# <a name="custom-message-filter"></a>Vlastní filtr zpráv
Tato ukázka předvádí, jak nahradit filtry zpráv, které Windows Communication Foundation (WCF) používá k odeslání zpráv do koncových bodů.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Při první zprávu v kanálu dorazí na server, server třeba určit, které (pokud existuje) o koncových bodech spojených s, který identifikátor URI by měla zobrazit zpráva. Tento proces se řídí <xref:System.ServiceModel.Dispatcher.MessageFilter> objekty připojené k <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.  
  
 Každý koncový bod služby má jeden <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>. <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> Jsou obě <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> a <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>. Spojení těchto dvou filtry se filtr zpráv pro tento koncový bod.  
  
 Ve výchozím nastavení <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> pro koncový bod odpovídá všechny zprávy, které je určeno adresu, která odpovídá koncový bod služby <xref:System.ServiceModel.EndpointAddress>. Ve výchozím nastavení <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> pro koncový bod zkontroluje akce příchozí zprávy a odpovídá jakékoli zprávy s akcí, které odpovídá jedné z akcí operace kontraktu koncového bodu služby (pouze `IsInitiating` = `true`akce jsou považovány za). Proto ve výchozím nastavení, filtr pro koncový bod pouze odpovídá, pokud se obě zprávy do záhlaví <xref:System.ServiceModel.EndpointAddress> koncový bod a zprávy akce odpovídá jednomu z akce operace koncového bodu.  
  
 Tyto filtry lze změnit pomocí chování. V příkladu se vytvoří službu <xref:System.ServiceModel.Description.IEndpointBehavior> místo <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> a <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> na <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>:  
  
```  
class FilteringEndpointBehavior : IEndpointBehavior …  
```  
  
 Jsou definovány dvě filtry adres:  
  
```  
// Matches any message whose To address contains the letter 'e'  
class MatchEAddressFilter : MessageFilter …  
// Matches any message whose To address does not contain the letter 'e'  
class MatchNoEAddressFilter : MessageFilter  
```  
  
 `FilteringEndpointBehavior` Se provádí konfigurovatelné a umožňuje pro dvě různé varianty.  
  
```  
public class FilteringEndpointBehaviorExtension : BehaviorExtensionElement  
```  
  
 Variace 1 odpovídá pouze adresy, které obsahují "e" (ale, které mají jakoukoli akci) že variace 2 odpovídá jenom adresy, které nemají "e":  
  
```  
if (Variation == 1)  
    return new FilteringEndpointBehavior(  
        new MatchEAddressFilter(), new MatchAllMessageFilter());  
else  
    return new FilteringEndpointBehavior(  
        new MatchNoEAddressFilter(), new MatchAllMessageFilter());  
```  
  
 V konfiguračním souboru služby registruje nové chování:  
  
```xml  
<extensions>  
    <behaviorExtensions>  
        <add name="filteringEndpointBehavior" type="Microsoft.ServiceModel.Samples.FilteringEndpointBehaviorExtension, service" />  
    </behaviorExtensions>  
</extensions>      
```  
  
 Pak vytvoří službu `endpointBehavior` konfigurace pro každou změnu:  
  
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
  
 Nakonec, jeden z koncového bodu služby odkazuje `behaviorConfigurations`:  
  
```xml  
<endpoint address=""  
        bindingConfiguration="ws"  
        listenUri=""   
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IHello"   
        behaviorConfiguration="endpoint2" />  
```  
  
 Implementace klientské aplikace je jednoduchá; vytvoří dva kanály na identifikátor URI služby (předáním tuto hodnotu jako druhý (`via`) parametr k <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> a odešle zprávu jeden na každý kanál, ale používá jiný koncový bod adresy pro každý. V důsledku toho mají různé označení odchozích zpráv od klienta a serveru reagují odpovídajícím způsobem, jak je uvedeno ve výstupu klienta:  
  
```  
Sending message to urn:e...  
Exception: The message with To 'urn:e' cannot be processed at the receiver, due to an AddressFilter mismatch at the EndpointDispatcher.  Check that the sender and receiver's EndpointAddresses agree.  
  
Sending message to urn:a...  
Hello  
```  
  
 Přepínání variace v konfiguračním souboru serveru způsobí, že filtr pro záměnu a klient se zobrazí opačné chování (zpráva, která má `urn:e` proběhne úspěšně, zatímco zpráva, která má `urn:a` selže).  
  
```xml  
<endpoint address=""  
          bindingConfiguration="ws"  
          listenUri=""   
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.IHello"   
          behaviorConfiguration="endpoint1" />  
```  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageFilter`  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Spusťte ukázku v konfiguraci jednoho počítače, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
3.  Ke spuštění ukázky v konfiguraci mezi počítači, postupujte podle pokynů na adrese [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md) a změňte následující řádek v Client.cs.  
  
    ```  
    Uri serviceVia = new Uri("http://localhost/ServiceModelSamples/service.svc");  
    ```  
  
     Nahraďte názvem serveru localhost.  
  
    ```  
    Uri serviceVia = new Uri("http://servermachinename/ServiceModelSamples/service.svc");  
    ```  
  
## <a name="see-also"></a>Viz také
