---
title: 'Postupy: Použití konfigurace k přidání koncového bodu ASP.NET AJAX'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 28051dbed626dc0073a38e72f2cdc21ea108a32e
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a><span data-ttu-id="fa6d6-102">Postupy: Použití konfigurace k přidání koncového bodu ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="fa6d6-102">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="fa6d6-103"> Umožňuje vytvořit službu, která umožňuje použití ASP.NET AJAX koncový bod k dispozici, které lze volat z jazyka JavaScript na webovém serveru klienta.</span><span class="sxs-lookup"><span data-stu-id="fa6d6-103"> allows you to create a service that makes an ASP.NET AJAX-enabled endpoint available that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="fa6d6-104">Pokud chcete vytvořit takové koncový bod, můžete použít buď konfigurační soubor s jiných [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] koncových bodů, nebo použijte metodu, která nevyžaduje, aby všechny konfigurace – elementy.</span><span class="sxs-lookup"><span data-stu-id="fa6d6-104">To create such an endpoint, you can either use a configuration file, as with all other [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="fa6d6-105">Toto téma popisuje postup konfigurace.</span><span class="sxs-lookup"><span data-stu-id="fa6d6-105">This topic demonstrates the configuration approach.</span></span>  
  
 <span data-ttu-id="fa6d6-106">V části procedury, která umožňuje koncovému bodu služby k použití ASP.NET AJAX je konfigurace koncového bodu používat <xref:System.ServiceModel.WebHttpBinding> a přidat [ \<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="fa6d6-106">The part of the procedure that enables the service endpoint to become ASP.NET AJAX-enabled consists of configuring the endpoint to use the <xref:System.ServiceModel.WebHttpBinding> and to add the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) endpoint behavior.</span></span> <span data-ttu-id="fa6d6-107">Po dokončení konfigurace koncového bodu, jsou podobné těm, které jsou použity žádné kroky pro implementaci a hostitelem služby [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="fa6d6-107">After configuring the endpoint, the steps to implement and host the service are similar to those used by any [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="fa6d6-108">Příklad pracovní najdete v tématu [AJAX služby pomocí HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="fa6d6-108">For a working example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
 <span data-ttu-id="fa6d6-109">Další informace o konfiguraci koncového bodu ASP.NET AJAX bez použití konfigurace najdete v tématu [postupy: Přidání aplikace ASP.NET AJAX konfigurace koncového bodu bez pomocí](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="fa6d6-109">For more information about how to configure an ASP.NET AJAX endpoint without using configuration, see [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
### <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="fa6d6-110">Chcete-li vytvořit základní služby WCF</span><span class="sxs-lookup"><span data-stu-id="fa6d6-110">To create a basic WCF service</span></span>  
  
1.  <span data-ttu-id="fa6d6-111">Zadejte základní [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kontrakt služby s rozhraním označené jako <xref:System.ServiceModel.ServiceContractAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="fa6d6-111">Define a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="fa6d6-112">Označit každou operaci s <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="fa6d6-112">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="fa6d6-113">Nastavte <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="fa6d6-113">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
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
  
2.  <span data-ttu-id="fa6d6-114">Implementace `ICalculator` kontrakt služby s `CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="fa6d6-114">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3.  <span data-ttu-id="fa6d6-115">Zadejte obor názvů pro `ICalculator` a `CalculatorService` implementace podle jejich zabalení v bloku oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="fa6d6-115">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a><span data-ttu-id="fa6d6-116">K vytvoření koncového bodu ASP.NET AJAX pro službu</span><span class="sxs-lookup"><span data-stu-id="fa6d6-116">To create an ASP.NET AJAX endpoint for the service</span></span>  
  
1.  <span data-ttu-id="fa6d6-117">Vytvoření konfigurace chování a zadejte [ \<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) chování pro použití ASP.NET AJAX koncové body služby.</span><span class="sxs-lookup"><span data-stu-id="fa6d6-117">Create a behavior configuration and specify the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior for ASP.NET AJAX-enabled endpoints of the service.</span></span>  
  
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
  
2.  <span data-ttu-id="fa6d6-118">Vytvořit koncový bod pro službu, kterou používá <xref:System.ServiceModel.WebHttpBinding> a chování prvku ASP.NET AJAX, které jsou definované v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="fa6d6-118">Create an endpoint for the service that uses the <xref:System.ServiceModel.WebHttpBinding> and the ASP.NET AJAX behavior defined in the previous step.</span></span>  
  
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
  
### <a name="to-host-the-service-in-iis"></a><span data-ttu-id="fa6d6-119">K hostování služby ve službě IIS</span><span class="sxs-lookup"><span data-stu-id="fa6d6-119">To host the service in IIS</span></span>  
  
1.  <span data-ttu-id="fa6d6-120">K hostování služby ve službě IIS, vytvořte nový soubor s názvem služby s příponou .svc v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="fa6d6-120">To host the service in IIS, create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="fa6d6-121">Tento soubor upravit přidáním odpovídající [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) direktivy informace pro službu.</span><span class="sxs-lookup"><span data-stu-id="fa6d6-121">Edit this file by adding the appropriate [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="fa6d6-122">Například obsah v souboru služby pro `CalculatorService` ukázka obsahuje následující informace.</span><span class="sxs-lookup"><span data-stu-id="fa6d6-122">For example, the content in the service file for the `CalculatorService` sample contains the following information.</span></span>  
  
    ```  
    <%@ServiceHost   
    language=c#   
    Debug="true"   
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2.  <span data-ttu-id="fa6d6-123">Další informace o hostování ve službě IIS najdete v tématu [postupy: hostování služby WCF ve službě IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span><span class="sxs-lookup"><span data-stu-id="fa6d6-123">For more information about hosting in IIS, see [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
### <a name="to-call-the-service"></a><span data-ttu-id="fa6d6-124">Pro volání služby</span><span class="sxs-lookup"><span data-stu-id="fa6d6-124">To call the service</span></span>  
  
1.  <span data-ttu-id="fa6d6-125">Koncový bod je konfigurována na prázdnou adresu relativně k souboru .svc tak, aby služba je nyní k dispozici a může vyvolat odesílání požadavků na service.svc/\<operaci > – například service.svc/Add pro `Add` operaci.</span><span class="sxs-lookup"><span data-stu-id="fa6d6-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="fa6d6-126">Můžete ji tak, že zadáte adresu URL koncového bodu do kolekce skripty ovládacího prvku ASP.NET AJAX skript správce.</span><span class="sxs-lookup"><span data-stu-id="fa6d6-126">You can use it by entering the endpoint URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="fa6d6-127">Příklad, naleznete v části [AJAX služby pomocí HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span><span class="sxs-lookup"><span data-stu-id="fa6d6-127">For an example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa6d6-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="fa6d6-128">See Also</span></span>  
 [<span data-ttu-id="fa6d6-129">Vytváření služeb WCF pro ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="fa6d6-129">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [<span data-ttu-id="fa6d6-130">Postupy: Migrace webových služeb ASP.NET s podporou AJAX na WCF</span><span class="sxs-lookup"><span data-stu-id="fa6d6-130">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
