---
title: "Vlastní filtr zpráv"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98dd0af8-fce6-4255-ac32-42eb547eea67
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 37b8721fe1e56bda400f3254fd5d19f828df523e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="custom-message-filter"></a>Vlastní filtr zpráv
Tento příklad ukazuje, jak nahradit filtruje zprávu, která [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] používá k odeslání zprávy do koncových bodů.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Při první zprávu ve kanálu dorazí na server, server třeba zjistit, který (pokud existuje) koncových bodů, která přidružené URI měla zobrazit zpráva. Tento proces se řídí <xref:System.ServiceModel.Dispatcher.MessageFilter> objekty připojené k <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>.  
  
 Každý koncový bod služby má jeden <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>. <xref:System.ServiceModel.Dispatcher.EndpointDispatcher> Má oba <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> a <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A>. Sjednocení tyto dva filtry je filtr zpráv použít pro tento koncový bod.  
  
 Ve výchozím nastavení <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> pro koncový bod odpovídá všechny zprávy, které je určeno adresu, která odpovídá koncový bod služby <xref:System.ServiceModel.EndpointAddress>. Ve výchozím nastavení <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> pro koncový bod zkontroluje akce příchozí zprávy a odpovídá všechny zprávy s akci, která odpovídá jednomu z akce koncového bodu kontraktu služby operací (pouze `IsInitiating` = `true`akce jsou považovány za). V důsledku toho ve výchozím nastavení, filtr pro koncový bod odpovídá jen pokud obě zprávy do záhlaví <xref:System.ServiceModel.EndpointAddress> koncový bod a zprávy akce odpovídá jednomu z akce operace koncového bodu.  
  
 Tyto filtry lze změnit pomocí chování. V ukázce vytvoří službu <xref:System.ServiceModel.Description.IEndpointBehavior> který nahrazuje <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.AddressFilter%2A> a <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> na <xref:System.ServiceModel.Dispatcher.EndpointDispatcher>:  
  
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
  
 `FilteringEndpointBehavior` Lze konfigurovat a umožňuje dvě různé varianty.  
  
```  
public class FilteringEndpointBehaviorExtension : BehaviorExtensionElement  
```  
  
 Variace 1 odpovídá pouze adresy, které obsahují "e" (ale mají žádnou akci) zatímco variace 2 odpovídá pouze adresy, která nemají "e":  
  
```  
if (Variation == 1)  
    return new FilteringEndpointBehavior(  
        new MatchEAddressFilter(), new MatchAllMessageFilter());  
else  
    return new FilteringEndpointBehavior(  
        new MatchNoEAddressFilter(), new MatchAllMessageFilter());  
```  
  
 V konfiguračním souboru služby zaregistruje nové chování:  
  
```xml  
<extensions>  
    <behaviorExtensions>  
        <add name="filteringEndpointBehavior" type="Microsoft.ServiceModel.Samples.FilteringEndpointBehaviorExtension, service" />  
    </behaviorExtensions>  
</extensions>      
```  
  
 Potom vytvoří služba `endpointBehavior` konfigurace pro každou požadovanou změnu:  
  
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
  
 Nakonec koncový bod služby odkazuje jeden z `behaviorConfigurations`:  
  
```xml  
<endpoint address=""  
        bindingConfiguration="ws"  
        listenUri=""   
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IHello"   
        behaviorConfiguration="endpoint2" />  
```  
  
 Implementace klientské aplikace je jednoduchá; vytvoří dva kanály na identifikátor URI služby (předáním tuto hodnotu jako druhý (`via`) parametr <xref:System.ServiceModel.Channels.IChannelFactory%601.CreateChannel%28System.ServiceModel.EndpointAddress%29> a odesílá zprávy jeden na každý kanál, ale používá jiný koncový bod adresy pro každou. V důsledku toho mají různé k označení odchozí zprávy z klienta a serveru reagují odpovídajícím způsobem, jak je uvedeno ve výstupu klienta:  
  
```  
Sending message to urn:e...  
Exception: The message with To 'urn:e' cannot be processed at the receiver, due to an AddressFilter mismatch at the EndpointDispatcher.  Check that the sender and receiver's EndpointAddresses agree.  
  
Sending message to urn:a...  
Hello  
```  
  
 Přepínání variace v konfiguračním souboru serveru způsobí, že filtr, aby si místo a klient se zobrazí opačné chování (zprávu, která se `urn:e` úspěšné, zatímco zprávu, která se `urn:a` selže).  
  
```xml  
<endpoint address=""  
          bindingConfiguration="ws"  
          listenUri=""   
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.IHello"   
          behaviorConfiguration="endpoint1" />  
```  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageFilter`  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Spustit ukázku v jednom počítači konfiguraci, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md) a změňte následující řádek v Client.cs.  
  
    ```  
    Uri serviceVia = new Uri("http://localhost/ServiceModelSamples/service.svc");  
    ```  
  
     Nahraďte název serveru localhost.  
  
    ```  
    Uri serviceVia = new Uri("http://servermachinename/ServiceModelSamples/service.svc");  
    ```  
  
## <a name="see-also"></a>Viz také
