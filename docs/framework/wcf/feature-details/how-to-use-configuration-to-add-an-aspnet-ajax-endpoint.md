---
title: 'Postupy: Použití konfigurace k přidání koncového bodu ASP.NET AJAX'
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: 3ccfb34614707c17885da3ed37f545bbab808869
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978270"
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a><span data-ttu-id="549fb-102">Postupy: Použití konfigurace k přidání koncového bodu ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="549fb-102">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>
<span data-ttu-id="549fb-103">Windows Communication Foundation (WCF) umožňuje vytvořit službu, která zpřístupňuje koncový bod s povoleným ASP.NET AJAX, který lze volat z JavaScriptu na klientském webu.</span><span class="sxs-lookup"><span data-stu-id="549fb-103">Windows Communication Foundation (WCF) allows you to create a service that makes an ASP.NET AJAX-enabled endpoint available that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="549fb-104">Chcete-li vytvořit takový koncový bod, můžete buď použít konfigurační soubor, stejně jako všechny ostatní koncové body služby Windows Communication Foundation (WCF), nebo použít metodu, která nevyžaduje žádné konfigurační prvky.</span><span class="sxs-lookup"><span data-stu-id="549fb-104">To create such an endpoint, you can either use a configuration file, as with all other Windows Communication Foundation (WCF) endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="549fb-105">Toto téma ukazuje přístup ke konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="549fb-105">This topic demonstrates the configuration approach.</span></span>  
  
 <span data-ttu-id="549fb-106">Část postupu umožňující, aby se koncový bod služby stal ASP.NET AJAX, se skládá z konfigurace koncového bodu pro použití <xref:System.ServiceModel.WebHttpBinding> a přidání [\<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="549fb-106">The part of the procedure that enables the service endpoint to become ASP.NET AJAX-enabled consists of configuring the endpoint to use the <xref:System.ServiceModel.WebHttpBinding> and to add the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) endpoint behavior.</span></span> <span data-ttu-id="549fb-107">Po nakonfigurování koncového bodu jsou kroky pro implementaci a hostování služby podobné těm, které používá jakákoli služba WCF.</span><span class="sxs-lookup"><span data-stu-id="549fb-107">After configuring the endpoint, the steps to implement and host the service are similar to those used by any WCF service.</span></span> <span data-ttu-id="549fb-108">Pracovní příklad naleznete v tématu [Služba AJAX pomocí HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="549fb-108">For a working example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
 <span data-ttu-id="549fb-109">Další informace o tom, jak nakonfigurovat koncový bod ASP.NET AJAX bez použití konfigurace, najdete v tématu [How to: Add a ASP.NET AJAX Endpoint bez použití Configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="549fb-109">For more information about how to configure an ASP.NET AJAX endpoint without using configuration, see [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
## <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="549fb-110">Vytvoření základní služby WCF</span><span class="sxs-lookup"><span data-stu-id="549fb-110">To create a basic WCF service</span></span>  
  
1. <span data-ttu-id="549fb-111">Definujte základní kontrakt služby WCF s rozhraním označeným atributem <xref:System.ServiceModel.ServiceContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="549fb-111">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="549fb-112">Označte každou operaci pomocí <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="549fb-112">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="549fb-113">Nezapomeňte nastavit vlastnost <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A>.</span><span class="sxs-lookup"><span data-stu-id="549fb-113">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
    ```csharp
    [ServiceContract(Namespace = "MyService")]  
    public interface ICalculator  
    {  
        [OperationContract]  
         // This operation returns the sum of d1 and d2.  
        double Add(double n1, double n2);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2. <span data-ttu-id="549fb-114">Implementujte kontrakt služby `ICalculator` pomocí `CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="549fb-114">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```csharp
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }
        // Other operations omitted…
    }
    ```  
  
3. <span data-ttu-id="549fb-115">Definujte obor názvů pro `ICalculator` a `CalculatorService` implementace jejich zabalením do bloku oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="549fb-115">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```csharp
    namespace Microsoft.Ajax.Samples
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
## <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a><span data-ttu-id="549fb-116">Vytvoření koncového bodu ASP.NET AJAX pro službu</span><span class="sxs-lookup"><span data-stu-id="549fb-116">To create an ASP.NET AJAX endpoint for the service</span></span>  
  
1. <span data-ttu-id="549fb-117">Vytvořte konfiguraci chování a určete\<chování [> enableWebScript](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) pro koncové body služby s povoleným AJAX ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="549fb-117">Create a behavior configuration and specify the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior for ASP.NET AJAX-enabled endpoints of the service.</span></span>  
  
    ```xml  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="AspNetAjaxBehavior">  
                    <enableWebScript />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
    </system.serviceModel>  
    ```  
  
2. <span data-ttu-id="549fb-118">Vytvořte koncový bod pro službu, která používá <xref:System.ServiceModel.WebHttpBinding> a chování AJAX ASP.NET definované v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="549fb-118">Create an endpoint for the service that uses the <xref:System.ServiceModel.WebHttpBinding> and the ASP.NET AJAX behavior defined in the previous step.</span></span>  
  
    ```xml  
    <system.serviceModel>  
        <services>  
            <service name="Microsoft.Ajax.Samples.CalculatorService">  
                <endpoint address=""  
                    behaviorConfiguration="AspNetAjaxBehavior"   
                    binding="webHttpBinding"  
                    contract="Microsoft.Ajax.Samples.ICalculator" />  
            </service>  
        </services>  
    </system.serviceModel>   
    ```  
  
## <a name="to-host-the-service-in-iis"></a><span data-ttu-id="549fb-119">Hostování služby ve službě IIS</span><span class="sxs-lookup"><span data-stu-id="549fb-119">To host the service in IIS</span></span>  
  
1. <span data-ttu-id="549fb-120">Pokud chcete službu hostovat ve službě IIS, vytvořte v aplikaci nový soubor s názvem služba s příponou. svc.</span><span class="sxs-lookup"><span data-stu-id="549fb-120">To host the service in IIS, create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="549fb-121">Upravte tento soubor přidáním příslušné informace o direktivě [ServiceHost\@](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) pro tuto službu.</span><span class="sxs-lookup"><span data-stu-id="549fb-121">Edit this file by adding the appropriate [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="549fb-122">Například obsah v souboru služby pro ukázku `CalculatorService` obsahuje následující informace.</span><span class="sxs-lookup"><span data-stu-id="549fb-122">For example, the content in the service file for the `CalculatorService` sample contains the following information.</span></span>  
  
    ```
    <%@ServiceHost   
    language=c#   
    Debug="true"   
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2. <span data-ttu-id="549fb-123">Další informace o hostování ve službě IIS najdete v tématu [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span><span class="sxs-lookup"><span data-stu-id="549fb-123">For more information about hosting in IIS, see [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
## <a name="to-call-the-service"></a><span data-ttu-id="549fb-124">Volání služby</span><span class="sxs-lookup"><span data-stu-id="549fb-124">To call the service</span></span>  
  
1. <span data-ttu-id="549fb-125">Koncový bod je nakonfigurován na prázdné adrese relativní vzhledem k souboru. svc, takže služba je nyní k dispozici a je možné ji vyvolat odesláním žádostí do operace Service. svc/\<>-například Service. svc/Add pro `Add` operace.</span><span class="sxs-lookup"><span data-stu-id="549fb-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="549fb-126">Můžete ji použít tak, že zadáte adresu URL koncového bodu do kolekce Scripts ovládacího prvku Správce skriptů ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="549fb-126">You can use it by entering the endpoint URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="549fb-127">Příklad najdete v tématu [Služba AJAX pomocí HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="549fb-127">For an example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="549fb-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="549fb-128">See also</span></span>

- [<span data-ttu-id="549fb-129">Vytváření služeb WCF pro ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="549fb-129">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [<span data-ttu-id="549fb-130">Postupy: Migrace webových služeb ASP.NET s podporou AJAX na WCF</span><span class="sxs-lookup"><span data-stu-id="549fb-130">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
