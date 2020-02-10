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
# <a name="security-validation"></a><span data-ttu-id="b79aa-102">Ověřování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="b79aa-102">Security Validation</span></span>
<span data-ttu-id="b79aa-103">Tato ukázka předvádí, jak pomocí vlastního chování ověřit služby na počítači, abyste měli jistotu, že splňují určitá kritéria.</span><span class="sxs-lookup"><span data-stu-id="b79aa-103">This sample demonstrates how to use a custom behavior to validate services on a computer to ensure they meet specific criteria.</span></span> <span data-ttu-id="b79aa-104">V této ukázce se služby ověřují pomocí vlastního chování tím, že prochází každý koncový bod ve službě a kontroluje, jestli obsahují zabezpečené prvky vazby.</span><span class="sxs-lookup"><span data-stu-id="b79aa-104">In this sample, services are validated by the custom behavior by scanning through each endpoint on the service and checking to see whether they contain secure binding elements.</span></span> <span data-ttu-id="b79aa-105">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="b79aa-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b79aa-106">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="b79aa-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="endpoint-validation-custom-behavior"></a><span data-ttu-id="b79aa-107">Vlastní chování ověřování koncového bodu</span><span class="sxs-lookup"><span data-stu-id="b79aa-107">Endpoint Validation Custom Behavior</span></span>  
 <span data-ttu-id="b79aa-108">Přidáním uživatelského kódu do metody `Validate` obsažené v rozhraní <xref:System.ServiceModel.Description.IServiceBehavior> lze vlastní chování předávat službě nebo koncovému bodu pro provádění uživatelem definovaných akcí.</span><span class="sxs-lookup"><span data-stu-id="b79aa-108">By adding user code to the `Validate` method contained in the <xref:System.ServiceModel.Description.IServiceBehavior> interface, custom behavior can be given to a service or endpoint to perform user-defined actions.</span></span> <span data-ttu-id="b79aa-109">Následující kód se používá k procyklení každého koncového bodu obsaženého ve službě, který vyhledává v rámci svých vazeb vazby pro zabezpečené vazby.</span><span class="sxs-lookup"><span data-stu-id="b79aa-109">The following code is used to loop through each endpoint contained in a service, which searches through their binding collections for secure bindings.</span></span>  
  
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
  
 <span data-ttu-id="b79aa-110">Přidáním následujícího kódu do souboru Web. config dojde k rozpoznání rozšíření chování `serviceValidate` pro službu, která se má rozpoznat.</span><span class="sxs-lookup"><span data-stu-id="b79aa-110">Adding the following code to Web.config file adds the `serviceValidate` behavior extension for the service to recognize.</span></span>  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="endpointValidate" type="Microsoft.ServiceModel.Samples.EndpointValidateElement, endpointValidate, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
    </extensions>  
...  
```  
  
 <span data-ttu-id="b79aa-111">Jakmile je rozšíření chování přidáno ke službě, je nyní možné přidat chování `endpointValidate` do seznamu chování v souboru Web. config a tedy do služby.</span><span class="sxs-lookup"><span data-stu-id="b79aa-111">Once the behavior extension is added to the service, it is now possible to add the `endpointValidate` behavior to the list of behaviors in the Web.config file and thus, to the service.</span></span>  
  
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
  
 <span data-ttu-id="b79aa-112">Chování a jejich rozšíření, která jsou přidána do souboru Web. config, aplikují chování na jednotlivé služby, zatímco když přidáte do souboru Machine. config, použije se chování pro všechny aktivní služby v počítači.</span><span class="sxs-lookup"><span data-stu-id="b79aa-112">Behaviors and their extensions that are added to the Web.config file apply behavior to individual services, while when added to the Machine.config file apply behavior to every service active on the computer.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b79aa-113">Při přidávání chování do všech služeb je navrženo zálohování souboru Machine. config před provedením jakékoli změny.</span><span class="sxs-lookup"><span data-stu-id="b79aa-113">When adding behavior to all services, it is suggested to backup the Machine.config file before making any change.</span></span>  
  
 <span data-ttu-id="b79aa-114">Nyní spusťte klienta, který je k dispozici v adresáři client\bin této ukázky.</span><span class="sxs-lookup"><span data-stu-id="b79aa-114">Now run the client provided in the client\bin directory of this sample.</span></span> <span data-ttu-id="b79aa-115">Došlo k výjimce s následující zprávou: "požadovaná služba, 'http://localhost/servicemodelsamples/service.svc' nemohla být aktivována."</span><span class="sxs-lookup"><span data-stu-id="b79aa-115">An exception has occurs with the following message: "The requested service, 'http://localhost/servicemodelsamples/service.svc' could not be activated."</span></span> <span data-ttu-id="b79aa-116">To se očekává, protože koncový bod se považuje za nezabezpečený pomocí chování při ověřování koncového bodu a zabrání spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="b79aa-116">This is expected because an endpoint is considered insecure by the endpoint validating behavior and prevents the service from being started.</span></span> <span data-ttu-id="b79aa-117">Chování také vyvolá interní výjimku, která popisuje, který koncový bod je nezabezpečený a zapisuje do systému zprávu Prohlížeč událostí pod zdrojem "System. ServiceModel 4.0.0.0" a "webhost" kategorie.</span><span class="sxs-lookup"><span data-stu-id="b79aa-117">The behavior also throws an internal exception that describes which endpoint is insecure and writes a message to the system Event Viewer under the "System.ServiceModel 4.0.0.0" source and the "WebHost" category.</span></span> <span data-ttu-id="b79aa-118">V této ukázce je také možné zapnout trasování pro službu.</span><span class="sxs-lookup"><span data-stu-id="b79aa-118">It is also possible to turn on tracing on the service in this sample.</span></span> <span data-ttu-id="b79aa-119">To uživateli umožňuje zobrazit výjimky vyvolané chováním ověřování koncového bodu otevřením výsledných trasování služby pomocí nástroje Service Trace Viewer.</span><span class="sxs-lookup"><span data-stu-id="b79aa-119">This allows the user to view the exceptions thrown by endpoint validating behavior by opening the resulting service traces using the Service Trace Viewer tool.</span></span>  
  
#### <a name="to-view-failed-endpoint-validation-exception-messages-in-the-event-viewer"></a><span data-ttu-id="b79aa-120">Zobrazení zpráv výjimky ověřování koncového bodu, které selhaly v Prohlížeč událostí</span><span class="sxs-lookup"><span data-stu-id="b79aa-120">To view failed endpoint validation exception messages in the Event Viewer</span></span>  
  
1. <span data-ttu-id="b79aa-121">Klikněte na nabídku **Start** a vyberte možnost **Spustit...** .</span><span class="sxs-lookup"><span data-stu-id="b79aa-121">Click the **Start** menu and select **Run…**.</span></span>  
  
2. <span data-ttu-id="b79aa-122">Zadejte `eventvwr` a klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="b79aa-122">Type `eventvwr` and click **OK**.</span></span>  
  
3. <span data-ttu-id="b79aa-123">V okně Prohlížeč událostí klikněte na možnost **aplikace**.</span><span class="sxs-lookup"><span data-stu-id="b79aa-123">In the Event Viewer window, click **Application**.</span></span>  
  
4. <span data-ttu-id="b79aa-124">Poklikejte na nedávno přidanou událost System. ServiceModel 4.0.0.0 do kategorie webhost v okně **aplikace** a zobrazte nezabezpečené zprávy koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="b79aa-124">Double-click the recently added "System.ServiceModel 4.0.0.0" event under the "WebHost" category in the **Application** window to view insecure endpoint messages.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b79aa-125">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="b79aa-125">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b79aa-126">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b79aa-126">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="b79aa-127">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b79aa-127">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="b79aa-128">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b79aa-128">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b79aa-129">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="b79aa-129">The samples may already be installed on your computer.</span></span> <span data-ttu-id="b79aa-130">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="b79aa-130">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="b79aa-131">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="b79aa-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b79aa-132">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="b79aa-132">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ServiceValidation`  
  
## <a name="see-also"></a><span data-ttu-id="b79aa-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="b79aa-133">See also</span></span>

- <span data-ttu-id="b79aa-134">[Ukázky monitorování technologie AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="b79aa-134">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
