---
title: 'Postupy: Použití konfigurace k přidání koncového bodu ASP.NET AJAX'
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: 3a3474dc04ce2cda63157e68597d1184e9b2bf15
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43559948"
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a><span data-ttu-id="d000f-102">Postupy: Použití konfigurace k přidání koncového bodu ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="d000f-102">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>
<span data-ttu-id="d000f-103">Windows Communication Foundation (WCF) umožňuje vytvořit službu, která umožňuje použití technologie ASP.NET AJAX koncový bod k dispozici, který může být volána z jazyka JavaScript na webové stránce klienta.</span><span class="sxs-lookup"><span data-stu-id="d000f-103">Windows Communication Foundation (WCF) allows you to create a service that makes an ASP.NET AJAX-enabled endpoint available that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="d000f-104">Vytvořit takové koncový bod, můžete použít konfigurační soubor, stejně jako všechny ostatní koncové body Windows Communication Foundation (WCF) nebo používat metodu, která nevyžaduje žádné konfigurační prvky.</span><span class="sxs-lookup"><span data-stu-id="d000f-104">To create such an endpoint, you can either use a configuration file, as with all other Windows Communication Foundation (WCF) endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="d000f-105">Toto téma popisuje postup konfigurace.</span><span class="sxs-lookup"><span data-stu-id="d000f-105">This topic demonstrates the configuration approach.</span></span>  
  
 <span data-ttu-id="d000f-106">Součást procesu, který umožňuje koncový bod služby se podporou technologie ASP.NET AJAX se skládá z konfigurace koncového bodu pro použití <xref:System.ServiceModel.WebHttpBinding> a přidat [ \<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="d000f-106">The part of the procedure that enables the service endpoint to become ASP.NET AJAX-enabled consists of configuring the endpoint to use the <xref:System.ServiceModel.WebHttpBinding> and to add the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) endpoint behavior.</span></span> <span data-ttu-id="d000f-107">Po dokončení konfigurace koncového bodu, kroky pro implementaci služby hostování jsou podobné těm, které jsou používané libovolnou službu WCF.</span><span class="sxs-lookup"><span data-stu-id="d000f-107">After configuring the endpoint, the steps to implement and host the service are similar to those used by any WCF service.</span></span> <span data-ttu-id="d000f-108">Funkční příklad najdete v článku [AJAX služba využívající HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="d000f-108">For a working example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
 <span data-ttu-id="d000f-109">Další informace týkající se konfigurace koncového bodu ASP.NET AJAX bez použití konfigurace najdete v tématu [postupy: Přidání ASP.NET AJAX konfigurace koncového bodu bez použití](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="d000f-109">For more information about how to configure an ASP.NET AJAX endpoint without using configuration, see [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
### <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="d000f-110">Chcete-li vytvořit základní služby WCF</span><span class="sxs-lookup"><span data-stu-id="d000f-110">To create a basic WCF service</span></span>  
  
1.  <span data-ttu-id="d000f-111">Definování základní kontraktu služby WCF s rozhraním označené <xref:System.ServiceModel.ServiceContractAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="d000f-111">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="d000f-112">Označit každou operaci s <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="d000f-112">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="d000f-113">Nezapomeňte nastavit <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d000f-113">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
    ```  
    [ServiceContract(Namespace = "MyService")]  
    public interface ICalculator  
    {  
        [OperationContract]  
         // This operation returns the sum of d1 and d2.  
        double Add(double n1, double n2);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2.  <span data-ttu-id="d000f-114">Implementace `ICalculator` kontrakt služby s `CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="d000f-114">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3.  <span data-ttu-id="d000f-115">Definování oboru názvů pro `ICalculator` a `CalculatorService` implementace obalením v oboru bloku.</span><span class="sxs-lookup"><span data-stu-id="d000f-115">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a><span data-ttu-id="d000f-116">Vytvoření koncového bodu ASP.NET AJAX pro služby</span><span class="sxs-lookup"><span data-stu-id="d000f-116">To create an ASP.NET AJAX endpoint for the service</span></span>  
  
1.  <span data-ttu-id="d000f-117">Vytvořte konfiguraci chování a zadejte [ \<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) chování při použití technologie ASP.NET AJAX koncových bodů služby.</span><span class="sxs-lookup"><span data-stu-id="d000f-117">Create a behavior configuration and specify the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior for ASP.NET AJAX-enabled endpoints of the service.</span></span>  
  
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
  
2.  <span data-ttu-id="d000f-118">Vytvoření koncového bodu služby, který používá <xref:System.ServiceModel.WebHttpBinding> a ASP.NET AJAX chování definované v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="d000f-118">Create an endpoint for the service that uses the <xref:System.ServiceModel.WebHttpBinding> and the ASP.NET AJAX behavior defined in the previous step.</span></span>  
  
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
  
### <a name="to-host-the-service-in-iis"></a><span data-ttu-id="d000f-119">K hostování služby ve službě IIS</span><span class="sxs-lookup"><span data-stu-id="d000f-119">To host the service in IIS</span></span>  
  
1.  <span data-ttu-id="d000f-120">K hostování služby ve službě IIS, vytvořte nový soubor s názvem služby s příponou .svc v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d000f-120">To host the service in IIS, create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="d000f-121">Tento soubor upravit tak, že přidáte odpovídající [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) direktiv informace pro službu.</span><span class="sxs-lookup"><span data-stu-id="d000f-121">Edit this file by adding the appropriate [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="d000f-122">Například obsah do souboru definice služby pro `CalculatorService` vzorek obsahuje následující informace.</span><span class="sxs-lookup"><span data-stu-id="d000f-122">For example, the content in the service file for the `CalculatorService` sample contains the following information.</span></span>  
  
    ```  
    <%@ServiceHost   
    language=c#   
    Debug="true"   
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2.  <span data-ttu-id="d000f-123">Další informace o hostování ve službě IIS najdete v tématu [postupy: hostování služby WCF v IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span><span class="sxs-lookup"><span data-stu-id="d000f-123">For more information about hosting in IIS, see [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
### <a name="to-call-the-service"></a><span data-ttu-id="d000f-124">Volání služby</span><span class="sxs-lookup"><span data-stu-id="d000f-124">To call the service</span></span>  
  
1.  <span data-ttu-id="d000f-125">Koncový bod je nakonfigurována na prázdnou adresu relativní k souboru .svc tak, aby služba je nyní k dispozici a lze vyvolat pomocí zasílání požadavků na service.svc/\<operace > – například service.svc/Add pro `Add` operace.</span><span class="sxs-lookup"><span data-stu-id="d000f-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="d000f-126">Můžete ho tak, že zadáte adresu URL koncového bodu do kolekce skriptů ovládací prvek správce skriptů ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="d000f-126">You can use it by entering the endpoint URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="d000f-127">Příklad najdete v tématu [AJAX služba využívající HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="d000f-127">For an example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d000f-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="d000f-128">See Also</span></span>  
 [<span data-ttu-id="d000f-129">Vytváření služeb WCF pro ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="d000f-129">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [<span data-ttu-id="d000f-130">Postupy: Migrace webových služeb ASP.NET s podporou AJAX na WCF</span><span class="sxs-lookup"><span data-stu-id="d000f-130">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
