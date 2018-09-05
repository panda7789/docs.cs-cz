---
title: Ověřování zabezpečení
ms.date: 03/30/2017
ms.assetid: 48dcd496-0c4f-48ce-8b9b-0e25b77ffa58
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 0aaa88268959561cabe4613d51feb0f219275634
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43746740"
---
# <a name="security-validation"></a>Ověřování zabezpečení
Tento příklad ukazuje, jak použít vlastní chování k ověření služby v počítači a ujistěte se, že splňují určitá kritéria. V této ukázce jsou služby ověřený vlastní chování prohledáním prostřednictvím každého koncového bodu služby a zkontroluje, zda obsahují prvky zabezpečené vazby. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
## <a name="endpoint-validation-custom-behavior"></a>Vlastní chování koncového bodu ověření  
 Přidejte uživatelský kód pro `Validate` metoda součástí <xref:System.ServiceModel.Description.IServiceBehavior> rozhraní, vlastní chování mohou být zadány služba nebo koncový bod k provedení akce definovaný uživatelem. Následující kód slouží k procházení každý koncový bod služby, který prohledá jejich kolekce vazby pro zabezpečené vazby.  
  
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
  
 Přidáním následujícího kódu do souboru Web.config přidá `serviceValidate` chování rozšíření pro službu rozpoznávat.  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="endpointValidate" type="Microsoft.ServiceModel.Samples.EndpointValidateElement, endpointValidate, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
    </extensions>  
...  
```  
  
 Po přidání rozšíření chování ve službě, je teď možné přidat `endpointValidate` chování do seznamu chování v souboru Web.config a díky tomu se ke službě.  
  
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
  
 Chování a jejich rozšíření, které jsou přidány do souboru Web.config pro chování jednotlivých služeb, while, když se přidá do souboru Machine.config použít chování pro každou službu aktivní na počítači.  
  
> [!NOTE]
>  Při přidávání chování ke všem službám, doporučujeme, abyste zálohování před provedením jakékoli změny souboru Machine.config.  
  
 Nyní spusťte klienta v adresáři client\bin této ukázky. Má výjimku vyvolá s následující zprávou: "požadovanou službu"http://localhost/servicemodelsamples/service.svc"nebylo možné aktivovat." To je očekáváno, protože koncový bod se považuje za nezabezpečené koncový bod ověřování chování a zabrání spuštění služby. Chování také vyvolá vnitřní výjimka, která popisuje, který koncový bod není bezpečné a zapíše zprávu do systému prohlížeč událostí v části "System.ServiceModel 4.0.0.0" zdroje a kategorie "WebHost". Je také možné zapnout trasování služby v této ukázce. To umožňuje uživateli zobrazit výjimky vyvolané ověřování chování koncového bodu tak, že otevřete výsledné trasování služby pomocí nástroje prohlížeče trasování služeb.  
  
#### <a name="to-view-failed-endpoint-validation-exception-messages-in-the-event-viewer"></a>Chcete-li zobrazit zprávy o neúspěchu v koncový bod ověření výjimky v prohlížeči událostí  
  
1.  Klikněte na tlačítko **Start** nabídky a vybereme **spuštění...** .  
  
2.  Typ `eventvwr` a klikněte na tlačítko **OK**.  
  
3.  V okně prohlížeče událostí, klikněte na tlačítko **aplikace**.  
  
4.  Poklikáním na událost naposledy přidané "System.ServiceModel 4.0.0.0" v kategorii "WebHost" v **aplikace** okno k zobrazení zpráv nezabezpečené koncový bod.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ServiceValidation`  
  
## <a name="see-also"></a>Viz také  
 [Ukázky AppFabric monitorování](https://go.microsoft.com/fwlink/?LinkId=193959)
