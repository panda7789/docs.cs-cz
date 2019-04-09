---
title: 'Postupy: Přidání koncového bodu ASP.NET AJAX bez použití konfiguračního souboru'
ms.date: 03/30/2017
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
ms.openlocfilehash: caaa89573d272c5d11d179b08c2d9e24c76d21e6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59140618"
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a><span data-ttu-id="7c40d-102">Postupy: Přidání koncového bodu ASP.NET AJAX bez použití konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="7c40d-102">How to: Add an ASP.NET AJAX Endpoint Without Using Configuration</span></span>
<span data-ttu-id="7c40d-103">Windows Communication Foundation (WCF) umožňuje vytvořit službu, která zpřístupňuje koncový bod s podporou technologie ASP.NET AJAX, který může být volána z jazyka JavaScript na webové stránce klienta.</span><span class="sxs-lookup"><span data-stu-id="7c40d-103">Windows Communication Foundation (WCF) allows you to create a service that exposes an ASP.NET AJAX-enabled endpoint that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="7c40d-104">Vytvořit takové koncový bod, můžete použít konfigurační soubor, stejně jako u všech ostatních koncových bodů WCF nebo používat metodu, která nevyžaduje žádné konfigurační prvky.</span><span class="sxs-lookup"><span data-stu-id="7c40d-104">To create such an endpoint, you can either use a configuration file, as with all other WCF endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="7c40d-105">Toto téma popisuje druhý přístup.</span><span class="sxs-lookup"><span data-stu-id="7c40d-105">This topic demonstrates the second approach.</span></span>  
  
 <span data-ttu-id="7c40d-106">Vytvoření služby pomocí koncových bodů ASP.NET AJAX bez konfigurace, musí být služby hostovaný Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="7c40d-106">To create services with ASP.NET AJAX endpoints without configuration, the services must be hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="7c40d-107">Chcete-li aktivovat technologie ASP.NET AJAX koncový bod pomocí tohoto přístupu, zadejte <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> jako parametr objekt pro vytváření v [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) direktivy v souboru SVC.</span><span class="sxs-lookup"><span data-stu-id="7c40d-107">To activate an ASP.NET AJAX endpoint using this approach, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> as the Factory parameter in the [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive in the .svc file.</span></span> <span data-ttu-id="7c40d-108">Tento objekt pro vytváření vlastních je komponenta, která se automaticky nakonfiguruje koncového bodu ASP.NET AJAX tak, aby může být volána z jazyka JavaScript na webové stránce klienta.</span><span class="sxs-lookup"><span data-stu-id="7c40d-108">This custom factory is the component that automatically configures an ASP.NET AJAX endpoint so that it can be called from JavaScript on a client Web site.</span></span>  
  
 <span data-ttu-id="7c40d-109">Funkční příklad najdete v článku [služba AJAX bez konfigurace](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="7c40d-109">For a working example, see the [AJAX Service Without Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span></span>  
  
 <span data-ttu-id="7c40d-110">Přehled konfigurace koncového bodu ASP.NET AJAX pomocí konfigurační prvky, naleznete v tématu [jak: Použití konfigurace k přidání koncového bodu ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="7c40d-110">For an outline of how to configure an ASP.NET AJAX endpoint using configuration elements, see [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).</span></span>  
  
### <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="7c40d-111">Chcete-li vytvořit základní služby WCF</span><span class="sxs-lookup"><span data-stu-id="7c40d-111">To create a basic WCF service</span></span>  
  
1.  <span data-ttu-id="7c40d-112">Definování základní kontraktu služby WCF s rozhraním označené <xref:System.ServiceModel.ServiceContractAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="7c40d-112">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="7c40d-113">Označit každou operaci s <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="7c40d-113">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="7c40d-114">Nezapomeňte nastavit <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7c40d-114">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
    ```csharp  
    [ServiceContract(Namespace = "MyService")]]  
    public interface ICalculator  
    {  
        [OperationContract]  
        // This operation returns the sum of d1 and d2.  
        double Add(double n1, double n2);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2.  <span data-ttu-id="7c40d-115">Implementace `ICalculator` kontrakt služby s `CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="7c40d-115">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```csharp  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3.  <span data-ttu-id="7c40d-116">Definování oboru názvů pro `ICalculator` a `CalculatorService` implementace obalením v oboru bloku.</span><span class="sxs-lookup"><span data-stu-id="7c40d-116">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a><span data-ttu-id="7c40d-117">K hostování služby v Internetové informační službě bez konfigurace</span><span class="sxs-lookup"><span data-stu-id="7c40d-117">To host the service in Internet Information Services without configuration</span></span>  
  
1.  <span data-ttu-id="7c40d-118">Vytvořte nový soubor s názvem služby s příponou .svc v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7c40d-118">Create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="7c40d-119">Tento soubor upravit tak, že přidáte odpovídající [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) direktiv informace pro službu.</span><span class="sxs-lookup"><span data-stu-id="7c40d-119">Edit this file by adding the appropriate [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="7c40d-120">Určit, že <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> se použije [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) směrnice pro automatickou konfiguraci koncového bodu ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="7c40d-120">Specify that the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is to be used in the [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive to automatically configure an ASP.NET AJAX endpoint.</span></span>  
  
    ```  
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2.  <span data-ttu-id="7c40d-121">Sestavte službu a jeho volání z klienta.</span><span class="sxs-lookup"><span data-stu-id="7c40d-121">Build the service and call it from the client.</span></span> <span data-ttu-id="7c40d-122">Internetové informační služby (IIS) se aktivuje při volání služby.</span><span class="sxs-lookup"><span data-stu-id="7c40d-122">Internet Information Services (IIS) activates the service when called.</span></span> <span data-ttu-id="7c40d-123">Další informace o hostování ve službě IIS najdete v tématu [jak: Hostování služby WCF v IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span><span class="sxs-lookup"><span data-stu-id="7c40d-123">For more information about hosting in IIS, see [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
### <a name="to-call-the-service"></a><span data-ttu-id="7c40d-124">Volání služby</span><span class="sxs-lookup"><span data-stu-id="7c40d-124">To call the service</span></span>  
  
1.  <span data-ttu-id="7c40d-125">Koncový bod je nakonfigurována na prázdnou adresu relativní k souboru .svc tak, aby služba je nyní k dispozici a lze vyvolat pomocí zasílání požadavků na service.svc/\<operace > – například service.svc/Add pro `Add` operace.</span><span class="sxs-lookup"><span data-stu-id="7c40d-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="7c40d-126">Můžete ho tak, že zadáte adresu URL služby do kolekce skriptů ovládací prvek správce skriptů ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="7c40d-126">You can use it by entering the service URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="7c40d-127">Příklad najdete v tématu [služba AJAX bez konfigurace](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="7c40d-127">For an example, see the [AJAX Service Without Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c40d-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="7c40d-128">Example</span></span>  
  
 <span data-ttu-id="7c40d-129">Automaticky nakonfigurovat koncový bod se vytvoří prázdný adrese relativní k základní adrese URL.</span><span class="sxs-lookup"><span data-stu-id="7c40d-129">The automatically-configured endpoint is created at an empty address relative to the base URL.</span></span> <span data-ttu-id="7c40d-130">Konfigurační soubor lze také přidat a používat s tímto přístupem.</span><span class="sxs-lookup"><span data-stu-id="7c40d-130">A configuration file can also be added and used with this approach.</span></span> <span data-ttu-id="7c40d-131">Pokud konfigurační soubor obsahuje definic koncových bodů, tyto koncové body se přidají do koncového bodu automaticky nakonfigurované.</span><span class="sxs-lookup"><span data-stu-id="7c40d-131">If the configuration file contains endpoint definitions, these endpoints are added to the automatically-configured endpoint.</span></span>  
  
 <span data-ttu-id="7c40d-132">Například používá service.svc <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> a služba adresář obsahuje soubor Web.config, který definuje koncový bod pro stejnou službu pomocí <xref:System.ServiceModel.BasicHttpBinding> na relativní adrese "soap".</span><span class="sxs-lookup"><span data-stu-id="7c40d-132">For example, service.svc uses the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> and the service directory contains a Web.config file that defines an endpoint for the same service using the <xref:System.ServiceModel.BasicHttpBinding> at the "soap" relative address.</span></span> <span data-ttu-id="7c40d-133">V tomto případě služba obsahuje dva koncové body: jeden service.svc (která reaguje na požadavky technologie ASP.NET AJAX) a jiné na service.svc/soap (která reaguje na požadavky protokolu SOAP).</span><span class="sxs-lookup"><span data-stu-id="7c40d-133">In this case, the service contains two endpoints: one at service.svc (which responds to ASP.NET AJAX requests) and another at service.svc/soap (which responds to SOAP requests).</span></span>  
  
 <span data-ttu-id="7c40d-134">Pokud konfigurační soubor definuje koncový bod na prázdný relativní adrese a <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> se používá, je vyvolána výjimka a službu nepodaří spustit.</span><span class="sxs-lookup"><span data-stu-id="7c40d-134">If the configuration file defines an endpoint at an empty relative address and the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used, an exception is thrown and the service fails to start.</span></span>  
  
 <span data-ttu-id="7c40d-135">Konfiguraci nelze použít ke změně nastavení pro koncový bod automaticky nakonfigurované.</span><span class="sxs-lookup"><span data-stu-id="7c40d-135">You cannot use configuration to modify settings on the automatically-configured endpoint.</span></span> <span data-ttu-id="7c40d-136">Pokud žádné nastavení (např. čtečka kvóty) musí být změněn, nesmí používat bez konfigurace přístup tak, že odeberete <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> ze souboru .svc a vytvoření položky konfigurace pro koncový bod.</span><span class="sxs-lookup"><span data-stu-id="7c40d-136">If any setting (such as a reader quota) must be modified, you must not use the configuration-free approach by removing the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> from the .svc file and creating a configuration entry for the endpoint.</span></span>  
  
 <span data-ttu-id="7c40d-137">Pokud vaše služba vyžaduje režim kompatibility ASP.NET – například pokud se používá <xref:System.Web.HttpContext> třídy nebo mechanismy ověřování ASP.NET – konfigurační soubor je stále vyžadují k zapnutí nastavení v tomto režimu.</span><span class="sxs-lookup"><span data-stu-id="7c40d-137">If your service requires ASP.NET Compatibility Mode - for example, if it uses the <xref:System.Web.HttpContext> class or ASP.NET authorization mechanisms - a configuration file is still required to turn on this mode.</span></span> <span data-ttu-id="7c40d-138">Prvek konfigurace, vyžaduje se [ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) element, který musí být přidán následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="7c40d-138">The configuration element required is the [\<serviceHostingEnvironment>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) element, which must be added as follows.</span></span>  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 <span data-ttu-id="7c40d-139">Další informace najdete v tématu [služby WCF a ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="7c40d-139">For more information, see the [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) topic.</span></span>  
  
 <span data-ttu-id="7c40d-140"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> Třída je odvozená třída <xref:System.ServiceModel.Activation.ServiceHostFactory>.</span><span class="sxs-lookup"><span data-stu-id="7c40d-140">The <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> class is a derived class of <xref:System.ServiceModel.Activation.ServiceHostFactory>.</span></span> <span data-ttu-id="7c40d-141">Podrobné vysvětlení mechanizmus objekt pro vytváření hostitele služby, najdete v článku [rozšíření hostování pomocí ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="7c40d-141">For a detailed explanation of the service host factory mechanism, see the [Extending Hosting Using ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c40d-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7c40d-142">See also</span></span>

- [<span data-ttu-id="7c40d-143">Vytváření služeb WCF pro ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="7c40d-143">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [<span data-ttu-id="7c40d-144">Postupy: Migrace webových služeb ASP.NET s povolenou službou AJAX na WCF</span><span class="sxs-lookup"><span data-stu-id="7c40d-144">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
