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
# <a name="security-validation"></a><span data-ttu-id="8bdf6-102">Ověřování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="8bdf6-102">Security Validation</span></span>
<span data-ttu-id="8bdf6-103">Tato ukázka ukazuje, jak používat vlastní chování k ověření služeb v počítači, aby bylo zajištěno, že splňují určitá kritéria.</span><span class="sxs-lookup"><span data-stu-id="8bdf6-103">This sample demonstrates how to use a custom behavior to validate services on a computer to ensure they meet specific criteria.</span></span> <span data-ttu-id="8bdf6-104">V této ukázce služby jsou ověřeny vlastní chování skenování prostřednictvím každého koncového bodu ve službě a zkontrolujte, zda obsahují zabezpečené prvky vazby.</span><span class="sxs-lookup"><span data-stu-id="8bdf6-104">In this sample, services are validated by the custom behavior by scanning through each endpoint on the service and checking to see whether they contain secure binding elements.</span></span> <span data-ttu-id="8bdf6-105">Tato ukázka je založena na [začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="8bdf6-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8bdf6-106">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="8bdf6-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="endpoint-validation-custom-behavior"></a><span data-ttu-id="8bdf6-107">Vlastní chování ověření koncového bodu</span><span class="sxs-lookup"><span data-stu-id="8bdf6-107">Endpoint Validation Custom Behavior</span></span>  
 <span data-ttu-id="8bdf6-108">Přidáním uživatelského `Validate` kódu k metodě obsažené v <xref:System.ServiceModel.Description.IServiceBehavior> rozhraní může být vlastní chování poskytnuto službě nebo koncovému bodu k provádění akcí definovaných uživatelem.</span><span class="sxs-lookup"><span data-stu-id="8bdf6-108">By adding user code to the `Validate` method contained in the <xref:System.ServiceModel.Description.IServiceBehavior> interface, custom behavior can be given to a service or endpoint to perform user-defined actions.</span></span> <span data-ttu-id="8bdf6-109">Následující kód se používá ke smyčku prostřednictvím každý koncový bod obsažený ve službě, která prohledává jejich kolekce vazby pro zabezpečené vazby.</span><span class="sxs-lookup"><span data-stu-id="8bdf6-109">The following code is used to loop through each endpoint contained in a service, which searches through their binding collections for secure bindings.</span></span>  
  
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
  
 <span data-ttu-id="8bdf6-110">Přidáním následujícího kódu do souboru `serviceValidate` Web.config přidáte příponu chování, kterou má služba rozpoznat.</span><span class="sxs-lookup"><span data-stu-id="8bdf6-110">Adding the following code to Web.config file adds the `serviceValidate` behavior extension for the service to recognize.</span></span>  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="endpointValidate" type="Microsoft.ServiceModel.Samples.EndpointValidateElement, endpointValidate, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
    </extensions>  
...  
```  
  
 <span data-ttu-id="8bdf6-111">Jakmile je rozšíření chování přidáno do služby, `endpointValidate` je nyní možné přidat chování do seznamu chování v souboru Web.config a tím i do služby.</span><span class="sxs-lookup"><span data-stu-id="8bdf6-111">Once the behavior extension is added to the service, it is now possible to add the `endpointValidate` behavior to the list of behaviors in the Web.config file and thus, to the service.</span></span>  
  
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
  
 <span data-ttu-id="8bdf6-112">Chování a jejich rozšíření, které jsou přidány do souboru Web.config použít chování pro jednotlivé služby, zatímco při přidání do souboru Machine.config použít chování pro každou službu aktivní v počítači.</span><span class="sxs-lookup"><span data-stu-id="8bdf6-112">Behaviors and their extensions that are added to the Web.config file apply behavior to individual services, while when added to the Machine.config file apply behavior to every service active on the computer.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8bdf6-113">Při přidávání chování do všech služeb se doporučuje zálohovat soubor Machine.config před provedením jakékoli změny.</span><span class="sxs-lookup"><span data-stu-id="8bdf6-113">When adding behavior to all services, it is suggested to backup the Machine.config file before making any change.</span></span>  
  
 <span data-ttu-id="8bdf6-114">Nyní spusťte klienta uvedeného v adresáři client\bin této ukázky.</span><span class="sxs-lookup"><span data-stu-id="8bdf6-114">Now run the client provided in the client\bin directory of this sample.</span></span> <span data-ttu-id="8bdf6-115">Dojde k výjimce s následující zprávou:http://localhost/servicemodelsamples/service.svc"Požadovaná služba , " nelze aktivovat."</span><span class="sxs-lookup"><span data-stu-id="8bdf6-115">An exception has occurs with the following message: "The requested service, 'http://localhost/servicemodelsamples/service.svc' could not be activated."</span></span> <span data-ttu-id="8bdf6-116">To je očekáváno, protože koncový bod je považován za nezabezpečený koncovým bodem ověřování chování a zabraňuje spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="8bdf6-116">This is expected because an endpoint is considered insecure by the endpoint validating behavior and prevents the service from being started.</span></span> <span data-ttu-id="8bdf6-117">Chování také vyvolá vnitřní výjimku, která popisuje, který koncový bod je nezabezpečený a zapíše zprávu do systému Prohlížeč událostí pod zdrojem "System.ServiceModel 4.0.0" a kategorie "WebHost".</span><span class="sxs-lookup"><span data-stu-id="8bdf6-117">The behavior also throws an internal exception that describes which endpoint is insecure and writes a message to the system Event Viewer under the "System.ServiceModel 4.0.0.0" source and the "WebHost" category.</span></span> <span data-ttu-id="8bdf6-118">Je také možné zapnout trasování na službu v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="8bdf6-118">It is also possible to turn on tracing on the service in this sample.</span></span> <span data-ttu-id="8bdf6-119">To umožňuje uživateli zobrazit výjimky vyvoláné koncovým bodem ověřování chování otevřením výsledné trasování služby pomocí nástroje Sledování služby.</span><span class="sxs-lookup"><span data-stu-id="8bdf6-119">This allows the user to view the exceptions thrown by endpoint validating behavior by opening the resulting service traces using the Service Trace Viewer tool.</span></span>  
  
#### <a name="to-view-failed-endpoint-validation-exception-messages-in-the-event-viewer"></a><span data-ttu-id="8bdf6-120">Zobrazení neúspěšných zpráv o výjimce ověření koncového bodu v Prohlížeči událostí</span><span class="sxs-lookup"><span data-stu-id="8bdf6-120">To view failed endpoint validation exception messages in the Event Viewer</span></span>  
  
1. <span data-ttu-id="8bdf6-121">Klepněte na nabídku **Start** a vyberte **spustit...**.</span><span class="sxs-lookup"><span data-stu-id="8bdf6-121">Click the **Start** menu and select **Run…**.</span></span>  
  
2. <span data-ttu-id="8bdf6-122">Zadejte `eventvwr` a klepněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="8bdf6-122">Type `eventvwr` and click **OK**.</span></span>  
  
3. <span data-ttu-id="8bdf6-123">V okně Prohlížeč událostí klepněte na **položku Aplikace**.</span><span class="sxs-lookup"><span data-stu-id="8bdf6-123">In the Event Viewer window, click **Application**.</span></span>  
  
4. <span data-ttu-id="8bdf6-124">Poklepáním na nedávno přidanou událost System.ServiceModel 4.0.0.0 v kategorii "WebHost" v okně **Aplikace** zobrazíte nezabezpečené zprávy koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="8bdf6-124">Double-click the recently added "System.ServiceModel 4.0.0.0" event under the "WebHost" category in the **Application** window to view insecure endpoint messages.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8bdf6-125">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="8bdf6-125">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="8bdf6-126">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8bdf6-126">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="8bdf6-127">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8bdf6-127">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="8bdf6-128">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8bdf6-128">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8bdf6-129">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="8bdf6-129">The samples may already be installed on your computer.</span></span> <span data-ttu-id="8bdf6-130">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="8bdf6-130">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="8bdf6-131">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="8bdf6-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8bdf6-132">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="8bdf6-132">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ServiceValidation`  
  
## <a name="see-also"></a><span data-ttu-id="8bdf6-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="8bdf6-133">See also</span></span>

- <span data-ttu-id="8bdf6-134">[Vzorky monitorování appfabricu](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="8bdf6-134">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
