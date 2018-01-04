---
title: "Ověřování zabezpečení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48dcd496-0c4f-48ce-8b9b-0e25b77ffa58
caps.latest.revision: "35"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 86a10a4117a5bbeb48e9d1d15b1ce8da9d7c7751
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="security-validation"></a>Ověřování zabezpečení
Tento příklad ukazuje, jak použít vlastní chování k ověření služby v počítači a ujistěte se, že splňují určitá kritéria. V této ukázce služby se ověří pomocí vlastní chování prohledáním prostřednictvím každý koncový bod služby a kontroluje, zda neobsahují elementy zabezpečené vazby. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
## <a name="endpoint-validation-custom-behavior"></a>Koncový bod ověření vlastní chování  
 Přidáním uživatelského kódu k `Validate` metoda součástí <xref:System.ServiceModel.Description.IServiceBehavior> rozhraní, vlastní chování je možné přidělit ke službě nebo koncový bod k provedení uživatelské akce. Následující kód slouží k procházení každý koncový bod součástí služby, která hledá prostřednictvím jejich kolekcí vazby pro zabezpečené vazby.  
  
```  
public void Validate(ServiceDescription serviceDescription,   
                                       ServiceHostBase serviceHostBase)  
{  
    // Loop through each endpoint individually gathering their    
       binding elements.  
    foreach (ServiceEndpoint endpoint in serviceDescription.Endpoints)  
    {  
        secureElementFound = false;  
  
        // Retrieve the endpoint's binding element collection.  
        BindingElementCollection bindingElements =   
            endpoint.Binding.CreateBindingElements();  
  
        // Look to see if the binding elements collection contains any   
        // secure binding elements. Transport, Asymmetric, and Symmetric      
        // binding elements are all derived from SecurityBindingElement.  
        if ((bindingElements.Find<SecurityBindingElement>() != null) || (bindingElements.Find<HttpsTransportBindingElement>() != null) || (bindingElements.Find<WindowsStreamSecurityBindingElement>() != null) || (bindingElements.Find<SslStreamSecurityBindingElement>() != null))  
        {  
            secureElementFound = true;  
        }  
  
    // Send a message to the system event viewer when an endpoint is deemed insecure.  
    if (!secureElementFound)  
        throw new Exception(System.DateTime.Now.ToString() + ": The endpoint \"" + endpoint.Name + "\" has no secure bindings.");  
    }  
}  
```  
  
 Přidání následující kód do souboru Web.config přidá `serviceValidate` chování rozšíření pro službu rozpoznat.  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="endpointValidate" type="Microsoft.ServiceModel.Samples.EndpointValidateElement, endpointValidate, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
    </extensions>  
...  
```  
  
 Po rozšíření chování je přidán ke službě, je nyní možné přidat `endpointValidate` chování do seznamu chování v souboru Web.config a proto do služby.  
  
```xml  
<behaviors>  
    <serviceBehaviors>  
        <behavior name="CalcServiceSEB1">  
            <serviceMetadata httpGetEnabled="true" />  
            <endpointValidate />  
        </behavior>  
    </serviceBehaviors>  
</behaviors>  
```  
  
 Chování a jejich rozšíření, které jsou přidány do souboru Web.config, platí pro jednotlivé služby, chování při při přidání do souboru Machine.config použít chování pro každou službu aktivní na počítači.  
  
> [!NOTE]
>  Při přidávání chování ke všem službám, doporučujeme zálohovat souboru Machine.config. před provedením jakékoli změny.  
  
 Teď spusťte klienta v adresáři client\bin této ukázky. Má k výjimce dochází s následující zprávou: "požadovaná služba 'http://localhost/servicemodelsamples/service.svc' se nepodařilo aktivovat." To je očekáváno, protože koncový bod je považován za nezabezpečené koncový bod ověřování chování a znemožní spuštění služby. Chování také vyvolá vnitřní výjimka, která popisuje, kterému koncovému bodu je nezabezpečené a zapíše zprávu do systému prohlížeč událostí v části zdroj "System.ServiceModel 4.0.0.0" a "Webového hostitele" kategorie. Také je možné zapnout trasování služby v této ukázce. To umožňuje uživatelům zobrazit výjimky vyvolané koncový bod ověřování chování otevřením výsledné trasování služby pomocí nástroje prohlížeče trasování služeb.  
  
#### <a name="to-view-failed-endpoint-validation-exception-messages-in-the-event-viewer"></a>Chcete-li zobrazit se nezdařilo zprávy o výjimkách ověření koncového bodu v prohlížeči událostí  
  
1.  Klikněte **spustit** nabídku a vyberte **spustit...** .  
  
2.  Typ `eventvwr` a klikněte na tlačítko **OK**.  
  
3.  V okně prohlížeče událostí, klikněte na **aplikace**.  
  
4.  Klikněte dvakrát na nedávno přidané "System.ServiceModel 4.0.0.0" události v kategorii "Tomuto webovému hostiteli" v **aplikace** okno zobrazení zpráv nezabezpečené koncový bod.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ServiceValidation`  
  
## <a name="see-also"></a>Viz také  
 [Ukázky monitorování AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
