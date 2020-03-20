---
title: Ověřování zabezpečení
ms.date: 03/30/2017
ms.assetid: 48dcd496-0c4f-48ce-8b9b-0e25b77ffa58
ms.openlocfilehash: 17e6e250c6b345477f7c9b377eb8e16ff4331ca7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183373"
---
# <a name="security-validation"></a>Ověřování zabezpečení
Tato ukázka ukazuje, jak používat vlastní chování k ověření služeb v počítači, aby bylo zajištěno, že splňují určitá kritéria. V této ukázce služby jsou ověřeny vlastní chování skenování prostřednictvím každého koncového bodu ve službě a zkontrolujte, zda obsahují zabezpečené prvky vazby. Tato ukázka je založena na [začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
## <a name="endpoint-validation-custom-behavior"></a>Vlastní chování ověření koncového bodu  
 Přidáním uživatelského `Validate` kódu k metodě obsažené v <xref:System.ServiceModel.Description.IServiceBehavior> rozhraní může být vlastní chování poskytnuto službě nebo koncovému bodu k provádění akcí definovaných uživatelem. Následující kód se používá ke smyčku prostřednictvím každý koncový bod obsažený ve službě, která prohledává jejich kolekce vazby pro zabezpečené vazby.  
  
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
  
 Přidáním následujícího kódu do souboru `serviceValidate` Web.config přidáte příponu chování, kterou má služba rozpoznat.  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="endpointValidate" type="Microsoft.ServiceModel.Samples.EndpointValidateElement, endpointValidate, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
    </extensions>  
...  
```  
  
 Jakmile je rozšíření chování přidáno do služby, `endpointValidate` je nyní možné přidat chování do seznamu chování v souboru Web.config a tím i do služby.  
  
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
  
 Chování a jejich rozšíření, které jsou přidány do souboru Web.config použít chování pro jednotlivé služby, zatímco při přidání do souboru Machine.config použít chování pro každou službu aktivní v počítači.  
  
> [!NOTE]
> Při přidávání chování do všech služeb se doporučuje zálohovat soubor Machine.config před provedením jakékoli změny.  
  
 Nyní spusťte klienta uvedeného v adresáři client\bin této ukázky. Dojde k výjimce s následující zprávou:http://localhost/servicemodelsamples/service.svc"Požadovaná služba , " nelze aktivovat." To je očekáváno, protože koncový bod je považován za nezabezpečený koncovým bodem ověřování chování a zabraňuje spuštění služby. Chování také vyvolá vnitřní výjimku, která popisuje, který koncový bod je nezabezpečený a zapíše zprávu do systému Prohlížeč událostí pod zdrojem "System.ServiceModel 4.0.0" a kategorie "WebHost". Je také možné zapnout trasování na službu v této ukázce. To umožňuje uživateli zobrazit výjimky vyvoláné koncovým bodem ověřování chování otevřením výsledné trasování služby pomocí nástroje Sledování služby.  
  
#### <a name="to-view-failed-endpoint-validation-exception-messages-in-the-event-viewer"></a>Zobrazení neúspěšných zpráv o výjimce ověření koncového bodu v Prohlížeči událostí  
  
1. Klepněte na nabídku **Start** a vyberte **spustit...**.  
  
2. Zadejte `eventvwr` a klepněte na tlačítko **OK**.  
  
3. V okně Prohlížeč událostí klepněte na **položku Aplikace**.  
  
4. Poklepáním na nedávno přidanou událost System.ServiceModel 4.0.0.0 v kategorii "WebHost" v okně **Aplikace** zobrazíte nezabezpečené zprávy koncového bodu.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ServiceValidation`  
  
## <a name="see-also"></a>Viz také

- [Vzorky monitorování appfabricu](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
