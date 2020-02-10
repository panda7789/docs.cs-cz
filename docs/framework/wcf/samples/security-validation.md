---
title: Ověřování zabezpečení
ms.date: 03/30/2017
ms.assetid: 48dcd496-0c4f-48ce-8b9b-0e25b77ffa58
ms.openlocfilehash: c47f8910076590dae1ee6aabbddcb072d76bfc27
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094927"
---
# <a name="security-validation"></a>Ověřování zabezpečení
Tato ukázka předvádí, jak pomocí vlastního chování ověřit služby na počítači, abyste měli jistotu, že splňují určitá kritéria. V této ukázce se služby ověřují pomocí vlastního chování tím, že prochází každý koncový bod ve službě a kontroluje, jestli obsahují zabezpečené prvky vazby. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
## <a name="endpoint-validation-custom-behavior"></a>Vlastní chování ověřování koncového bodu  
 Přidáním uživatelského kódu do metody `Validate` obsažené v rozhraní <xref:System.ServiceModel.Description.IServiceBehavior> lze vlastní chování předávat službě nebo koncovému bodu pro provádění uživatelem definovaných akcí. Následující kód se používá k procyklení každého koncového bodu obsaženého ve službě, který vyhledává v rámci svých vazeb vazby pro zabezpečené vazby.  
  
```csharp
public void Validate(ServiceDescription serviceDescription,   
                                       ServiceHostBase serviceHostBase)  
{  
    // Loop through each endpoint individually, gathering their    
    // binding elements.  
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
  
 Přidáním následujícího kódu do souboru Web. config dojde k rozpoznání rozšíření chování `serviceValidate` pro službu, která se má rozpoznat.  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="endpointValidate" type="Microsoft.ServiceModel.Samples.EndpointValidateElement, endpointValidate, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
    </extensions>  
...  
```  
  
 Jakmile je rozšíření chování přidáno ke službě, je nyní možné přidat chování `endpointValidate` do seznamu chování v souboru Web. config a tedy do služby.  
  
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
  
 Chování a jejich rozšíření, která jsou přidána do souboru Web. config, aplikují chování na jednotlivé služby, zatímco když přidáte do souboru Machine. config, použije se chování pro všechny aktivní služby v počítači.  
  
> [!NOTE]
> Při přidávání chování do všech služeb je navrženo zálohování souboru Machine. config před provedením jakékoli změny.  
  
 Nyní spusťte klienta, který je k dispozici v adresáři client\bin této ukázky. Došlo k výjimce s následující zprávou: "požadovaná služba, 'http://localhost/servicemodelsamples/service.svc' nemohla být aktivována." To se očekává, protože koncový bod se považuje za nezabezpečený pomocí chování při ověřování koncového bodu a zabrání spuštění služby. Chování také vyvolá interní výjimku, která popisuje, který koncový bod je nezabezpečený a zapisuje do systému zprávu Prohlížeč událostí pod zdrojem "System. ServiceModel 4.0.0.0" a "webhost" kategorie. V této ukázce je také možné zapnout trasování pro službu. To uživateli umožňuje zobrazit výjimky vyvolané chováním ověřování koncového bodu otevřením výsledných trasování služby pomocí nástroje Service Trace Viewer.  
  
#### <a name="to-view-failed-endpoint-validation-exception-messages-in-the-event-viewer"></a>Zobrazení zpráv výjimky ověřování koncového bodu, které selhaly v Prohlížeč událostí  
  
1. Klikněte na nabídku **Start** a vyberte možnost **Spustit...** .  
  
2. Zadejte `eventvwr` a klikněte na **OK**.  
  
3. V okně Prohlížeč událostí klikněte na možnost **aplikace**.  
  
4. Poklikejte na nedávno přidanou událost System. ServiceModel 4.0.0.0 do kategorie webhost v okně **aplikace** a zobrazte nezabezpečené zprávy koncového bodu.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ServiceValidation`  
  
## <a name="see-also"></a>Viz také

- [Ukázky monitorování technologie AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
