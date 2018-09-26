---
title: Ověřování zabezpečení
ms.date: 03/30/2017
ms.assetid: 48dcd496-0c4f-48ce-8b9b-0e25b77ffa58
author: BrucePerlerMS
ms.openlocfilehash: 4b80457fb551c2ee99f910710c5f30fa59c53a01
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47203421"
---
# <a name="security-validation"></a><span data-ttu-id="57088-102">Ověřování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="57088-102">Security Validation</span></span>
<span data-ttu-id="57088-103">Tento příklad ukazuje, jak použít vlastní chování k ověření služby v počítači a ujistěte se, že splňují určitá kritéria.</span><span class="sxs-lookup"><span data-stu-id="57088-103">This sample demonstrates how to use a custom behavior to validate services on a computer to ensure they meet specific criteria.</span></span> <span data-ttu-id="57088-104">V této ukázce jsou služby ověřený vlastní chování prohledáním prostřednictvím každého koncového bodu služby a zkontroluje, zda obsahují prvky zabezpečené vazby.</span><span class="sxs-lookup"><span data-stu-id="57088-104">In this sample, services are validated by the custom behavior by scanning through each endpoint on the service and checking to see whether they contain secure binding elements.</span></span> <span data-ttu-id="57088-105">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="57088-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="57088-106">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="57088-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="endpoint-validation-custom-behavior"></a><span data-ttu-id="57088-107">Vlastní chování koncového bodu ověření</span><span class="sxs-lookup"><span data-stu-id="57088-107">Endpoint Validation Custom Behavior</span></span>  
 <span data-ttu-id="57088-108">Přidejte uživatelský kód pro `Validate` metoda součástí <xref:System.ServiceModel.Description.IServiceBehavior> rozhraní, vlastní chování mohou být zadány služba nebo koncový bod k provedení akce definovaný uživatelem.</span><span class="sxs-lookup"><span data-stu-id="57088-108">By adding user code to the `Validate` method contained in the <xref:System.ServiceModel.Description.IServiceBehavior> interface, custom behavior can be given to a service or endpoint to perform user-defined actions.</span></span> <span data-ttu-id="57088-109">Následující kód slouží k procházení každý koncový bod služby, který prohledá jejich kolekce vazby pro zabezpečené vazby.</span><span class="sxs-lookup"><span data-stu-id="57088-109">The following code is used to loop through each endpoint contained in a service, which searches through their binding collections for secure bindings.</span></span>  
  
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
  
 <span data-ttu-id="57088-110">Přidáním následujícího kódu do souboru Web.config přidá `serviceValidate` chování rozšíření pro službu rozpoznávat.</span><span class="sxs-lookup"><span data-stu-id="57088-110">Adding the following code to Web.config file adds the `serviceValidate` behavior extension for the service to recognize.</span></span>  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="endpointValidate" type="Microsoft.ServiceModel.Samples.EndpointValidateElement, endpointValidate, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
    </extensions>  
...  
```  
  
 <span data-ttu-id="57088-111">Po přidání rozšíření chování ve službě, je teď možné přidat `endpointValidate` chování do seznamu chování v souboru Web.config a díky tomu se ke službě.</span><span class="sxs-lookup"><span data-stu-id="57088-111">Once the behavior extension is added to the service, it is now possible to add the `endpointValidate` behavior to the list of behaviors in the Web.config file and thus, to the service.</span></span>  
  
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
  
 <span data-ttu-id="57088-112">Chování a jejich rozšíření, které jsou přidány do souboru Web.config pro chování jednotlivých služeb, while, když se přidá do souboru Machine.config použít chování pro každou službu aktivní na počítači.</span><span class="sxs-lookup"><span data-stu-id="57088-112">Behaviors and their extensions that are added to the Web.config file apply behavior to individual services, while when added to the Machine.config file apply behavior to every service active on the computer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="57088-113">Při přidávání chování ke všem službám, doporučujeme, abyste zálohování před provedením jakékoli změny souboru Machine.config.</span><span class="sxs-lookup"><span data-stu-id="57088-113">When adding behavior to all services, it is suggested to backup the Machine.config file before making any change.</span></span>  
  
 <span data-ttu-id="57088-114">Nyní spusťte klienta v adresáři client\bin této ukázky.</span><span class="sxs-lookup"><span data-stu-id="57088-114">Now run the client provided in the client\bin directory of this sample.</span></span> <span data-ttu-id="57088-115">Má výjimku vyvolá s následující zprávou: "požadovanou službu"http://localhost/servicemodelsamples/service.svc"nebylo možné aktivovat."</span><span class="sxs-lookup"><span data-stu-id="57088-115">An exception has occurs with the following message: "The requested service, 'http://localhost/servicemodelsamples/service.svc' could not be activated."</span></span> <span data-ttu-id="57088-116">To je očekáváno, protože koncový bod se považuje za nezabezpečené koncový bod ověřování chování a zabrání spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="57088-116">This is expected because an endpoint is considered insecure by the endpoint validating behavior and prevents the service from being started.</span></span> <span data-ttu-id="57088-117">Chování také vyvolá vnitřní výjimka, která popisuje, který koncový bod není bezpečné a zapíše zprávu do systému prohlížeč událostí v části "System.ServiceModel 4.0.0.0" zdroje a kategorie "WebHost".</span><span class="sxs-lookup"><span data-stu-id="57088-117">The behavior also throws an internal exception that describes which endpoint is insecure and writes a message to the system Event Viewer under the "System.ServiceModel 4.0.0.0" source and the "WebHost" category.</span></span> <span data-ttu-id="57088-118">Je také možné zapnout trasování služby v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="57088-118">It is also possible to turn on tracing on the service in this sample.</span></span> <span data-ttu-id="57088-119">To umožňuje uživateli zobrazit výjimky vyvolané ověřování chování koncového bodu tak, že otevřete výsledné trasování služby pomocí nástroje prohlížeče trasování služeb.</span><span class="sxs-lookup"><span data-stu-id="57088-119">This allows the user to view the exceptions thrown by endpoint validating behavior by opening the resulting service traces using the Service Trace Viewer tool.</span></span>  
  
#### <a name="to-view-failed-endpoint-validation-exception-messages-in-the-event-viewer"></a><span data-ttu-id="57088-120">Chcete-li zobrazit zprávy o neúspěchu v koncový bod ověření výjimky v prohlížeči událostí</span><span class="sxs-lookup"><span data-stu-id="57088-120">To view failed endpoint validation exception messages in the Event Viewer</span></span>  
  
1.  <span data-ttu-id="57088-121">Klikněte na tlačítko **Start** nabídky a vybereme **spuštění...** .</span><span class="sxs-lookup"><span data-stu-id="57088-121">Click the **Start** menu and select **Run…**.</span></span>  
  
2.  <span data-ttu-id="57088-122">Typ `eventvwr` a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="57088-122">Type `eventvwr` and click **OK**.</span></span>  
  
3.  <span data-ttu-id="57088-123">V okně prohlížeče událostí, klikněte na tlačítko **aplikace**.</span><span class="sxs-lookup"><span data-stu-id="57088-123">In the Event Viewer window, click **Application**.</span></span>  
  
4.  <span data-ttu-id="57088-124">Poklikáním na událost naposledy přidané "System.ServiceModel 4.0.0.0" v kategorii "WebHost" v **aplikace** okno k zobrazení zpráv nezabezpečené koncový bod.</span><span class="sxs-lookup"><span data-stu-id="57088-124">Double-click the recently added "System.ServiceModel 4.0.0.0" event under the "WebHost" category in the **Application** window to view insecure endpoint messages.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="57088-125">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="57088-125">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="57088-126">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="57088-126">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="57088-127">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="57088-127">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="57088-128">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="57088-128">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="57088-129">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="57088-129">The samples may already be installed on your computer.</span></span> <span data-ttu-id="57088-130">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="57088-130">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="57088-131">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="57088-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="57088-132">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="57088-132">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ServiceValidation`  
  
## <a name="see-also"></a><span data-ttu-id="57088-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="57088-133">See Also</span></span>  
 [<span data-ttu-id="57088-134">Ukázky AppFabric monitorování</span><span class="sxs-lookup"><span data-stu-id="57088-134">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
