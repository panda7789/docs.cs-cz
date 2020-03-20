---
title: 'Postupy: Přidání koncového bodu ASP.NET AJAX bez použití konfiguračního souboru'
ms.date: 03/30/2017
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
ms.openlocfilehash: 9935e2a7738796fff9a037b09237a6acbf7bf988
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185133"
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a><span data-ttu-id="50490-102">Postupy: Přidání koncového bodu ASP.NET AJAX bez použití konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="50490-102">How to: Add an ASP.NET AJAX Endpoint Without Using Configuration</span></span>
<span data-ttu-id="50490-103">Windows Communication Foundation (WCF) umožňuje vytvořit službu, která zveřejňuje koncový bod s podporou ASP.NET AJAX, který lze volat z Jazyka JavaScript na klientském webu.</span><span class="sxs-lookup"><span data-stu-id="50490-103">Windows Communication Foundation (WCF) allows you to create a service that exposes an ASP.NET AJAX-enabled endpoint that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="50490-104">Chcete-li vytvořit takový koncový bod, můžete buď použít konfigurační soubor, stejně jako u všech ostatních koncových bodů WCF, nebo použít metodu, která nevyžaduje žádné konfigurační prvky.</span><span class="sxs-lookup"><span data-stu-id="50490-104">To create such an endpoint, you can either use a configuration file, as with all other WCF endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="50490-105">Toto téma ukazuje druhý přístup.</span><span class="sxs-lookup"><span data-stu-id="50490-105">This topic demonstrates the second approach.</span></span>  
  
 <span data-ttu-id="50490-106">Chcete-li vytvořit služby s ASP.NET koncovými body AJAX bez konfigurace, musí být služby hostovány internetovou informační službou (IIS).</span><span class="sxs-lookup"><span data-stu-id="50490-106">To create services with ASP.NET AJAX endpoints without configuration, the services must be hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="50490-107">Chcete-li aktivovat koncový bod ASP.NET <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> AJAX pomocí tohoto přístupu, zadejte parametr Factory ve směrnici [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) v souboru .svc.</span><span class="sxs-lookup"><span data-stu-id="50490-107">To activate an ASP.NET AJAX endpoint using this approach, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> as the Factory parameter in the [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive in the .svc file.</span></span> <span data-ttu-id="50490-108">Tato vlastní továrna je komponenta, která automaticky konfiguruje koncový bod ASP.NET AJAX tak, aby jej bylo možné volat z JavaScriptu na klientském webu.</span><span class="sxs-lookup"><span data-stu-id="50490-108">This custom factory is the component that automatically configures an ASP.NET AJAX endpoint so that it can be called from JavaScript on a client Web site.</span></span>  
  
 <span data-ttu-id="50490-109">Pracovní příklad naleznete v tématu [služba AJAX bez konfigurace](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="50490-109">For a working example, see the [AJAX Service Without Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span></span>  
  
 <span data-ttu-id="50490-110">Přehled konfigurace koncového bodu ASP.NET AJAX pomocí konfiguračních prvků naleznete v tématu [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="50490-110">For an outline of how to configure an ASP.NET AJAX endpoint using configuration elements, see [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).</span></span>  
  
### <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="50490-111">Vytvoření základní služby WCF</span><span class="sxs-lookup"><span data-stu-id="50490-111">To create a basic WCF service</span></span>  
  
1. <span data-ttu-id="50490-112">Definujte základní servisní smlouvu WCF <xref:System.ServiceModel.ServiceContractAttribute> s rozhraním označeným atributem.</span><span class="sxs-lookup"><span data-stu-id="50490-112">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="50490-113">Každou operaci označte pomocí <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="50490-113">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="50490-114">Nezapomeňte nastavit <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="50490-114">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
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
  
2. <span data-ttu-id="50490-115">Dokončujte `ICalculator` `CalculatorService`servisní smlouvu s .</span><span class="sxs-lookup"><span data-stu-id="50490-115">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```csharp  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3. <span data-ttu-id="50490-116">Definujte obor názvů `ICalculator` `CalculatorService` pro a implementace zabalením do bloku oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="50490-116">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a><span data-ttu-id="50490-117">Hostování služby v Internetové informační službě bez konfigurace</span><span class="sxs-lookup"><span data-stu-id="50490-117">To host the service in Internet Information Services without configuration</span></span>  
  
1. <span data-ttu-id="50490-118">Vytvořte nový soubor s názvem služby s příponou SVC v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="50490-118">Create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="50490-119">Upravte tento soubor [ \@](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) přidáním příslušných informací směrnice ServiceHost pro službu.</span><span class="sxs-lookup"><span data-stu-id="50490-119">Edit this file by adding the appropriate [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="50490-120">Určete, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> že má být použit v [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) směrnice automaticky konfigurovat koncový bod ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="50490-120">Specify that the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is to be used in the [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive to automatically configure an ASP.NET AJAX endpoint.</span></span>  
  
    ```text
    <%@ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2. <span data-ttu-id="50490-121">Sestavení služby a volání z klienta.</span><span class="sxs-lookup"><span data-stu-id="50490-121">Build the service and call it from the client.</span></span> <span data-ttu-id="50490-122">Internetová informační služba (IIS) aktivuje službu při volání.</span><span class="sxs-lookup"><span data-stu-id="50490-122">Internet Information Services (IIS) activates the service when called.</span></span> <span data-ttu-id="50490-123">Další informace o hostování ve službě IIS naleznete v [tématu How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span><span class="sxs-lookup"><span data-stu-id="50490-123">For more information about hosting in IIS, see [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
### <a name="to-call-the-service"></a><span data-ttu-id="50490-124">Chcete-li volat službu</span><span class="sxs-lookup"><span data-stu-id="50490-124">To call the service</span></span>  
  
1. <span data-ttu-id="50490-125">Koncový bod je konfigurován na prázdnou adresu vzhledem k souboru .svc, takže služba je nyní k dispozici\<a může být vyvolána odesláním požadavků `Add` na service.svc/ operace> - například service.svc/Add pro operaci.</span><span class="sxs-lookup"><span data-stu-id="50490-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="50490-126">Můžete jej použít zadáním adresy URL služby do kolekce Skripty ovládacího prvku ASP.NET AJAX Script Manager.</span><span class="sxs-lookup"><span data-stu-id="50490-126">You can use it by entering the service URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="50490-127">Příklad naleznete v tématu [služba AJAX bez konfigurace](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="50490-127">For an example, see the [AJAX Service Without Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="50490-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="50490-128">Example</span></span>  
  
 <span data-ttu-id="50490-129">Automaticky nakonfigurovaný koncový bod je vytvořen na prázdné adrese vzhledem k základní adrese URL.</span><span class="sxs-lookup"><span data-stu-id="50490-129">The automatically-configured endpoint is created at an empty address relative to the base URL.</span></span> <span data-ttu-id="50490-130">Konfigurační soubor lze také přidat a použít s tímto přístupem.</span><span class="sxs-lookup"><span data-stu-id="50490-130">A configuration file can also be added and used with this approach.</span></span> <span data-ttu-id="50490-131">Pokud konfigurační soubor obsahuje definice koncových bodů, budou tyto koncové body přidány do automaticky nakonfigurovaného koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="50490-131">If the configuration file contains endpoint definitions, these endpoints are added to the automatically-configured endpoint.</span></span>  
  
 <span data-ttu-id="50490-132">Například service.svc používá <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> a adresář služby obsahuje soubor Web.config, který definuje koncový <xref:System.ServiceModel.BasicHttpBinding> bod pro stejnou službu pomocí relativní adresy "soap".</span><span class="sxs-lookup"><span data-stu-id="50490-132">For example, service.svc uses the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> and the service directory contains a Web.config file that defines an endpoint for the same service using the <xref:System.ServiceModel.BasicHttpBinding> at the "soap" relative address.</span></span> <span data-ttu-id="50490-133">V tomto případě služba obsahuje dva koncové body: jeden na service.svc (který reaguje na ASP.NET požadavky AJAX) a další na service.svc/soap (který reaguje na požadavky SOAP).</span><span class="sxs-lookup"><span data-stu-id="50490-133">In this case, the service contains two endpoints: one at service.svc (which responds to ASP.NET AJAX requests) and another at service.svc/soap (which responds to SOAP requests).</span></span>  
  
 <span data-ttu-id="50490-134">Pokud konfigurační soubor definuje koncový bod na <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> prázdnou relativní adresu a používá se, je vyvolána výjimka a služba se nespustí.</span><span class="sxs-lookup"><span data-stu-id="50490-134">If the configuration file defines an endpoint at an empty relative address and the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used, an exception is thrown and the service fails to start.</span></span>  
  
 <span data-ttu-id="50490-135">Konfiguraci nelze použít k úpravě nastavení automaticky konfigurovaného koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="50490-135">You cannot use configuration to modify settings on the automatically-configured endpoint.</span></span> <span data-ttu-id="50490-136">Pokud je nutné změnit jakékoli nastavení (například kvótu čtečky), nesmíte použít <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> přístup bez konfigurace odebráním souboru SVC a vytvořením položky konfigurace pro koncový bod.</span><span class="sxs-lookup"><span data-stu-id="50490-136">If any setting (such as a reader quota) must be modified, you must not use the configuration-free approach by removing the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> from the .svc file and creating a configuration entry for the endpoint.</span></span>  
  
 <span data-ttu-id="50490-137">Pokud vaše služba vyžaduje ASP.NET režimu kompatibility <xref:System.Web.HttpContext> – například pokud používá mechanismy autorizace třídy nebo ASP.NET – konfigurační soubor je stále nutné zapnout tento režim.</span><span class="sxs-lookup"><span data-stu-id="50490-137">If your service requires ASP.NET Compatibility Mode - for example, if it uses the <xref:System.Web.HttpContext> class or ASP.NET authorization mechanisms - a configuration file is still required to turn on this mode.</span></span> <span data-ttu-id="50490-138">Požadovaný konfigurační prvek je [ \<serviceHostingEnvironment>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) prvek, který musí být přidán následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="50490-138">The configuration element required is the [\<serviceHostingEnvironment>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) element, which must be added as follows.</span></span>  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 <span data-ttu-id="50490-139">Další informace naleznete v tématu [WCF Services a ASP.NET.](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)</span><span class="sxs-lookup"><span data-stu-id="50490-139">For more information, see the [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) topic.</span></span>  
  
 <span data-ttu-id="50490-140">Třída <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> je odvozené třídy <xref:System.ServiceModel.Activation.ServiceHostFactory>.</span><span class="sxs-lookup"><span data-stu-id="50490-140">The <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> class is a derived class of <xref:System.ServiceModel.Activation.ServiceHostFactory>.</span></span> <span data-ttu-id="50490-141">Podrobné vysvětlení mechanismu továrny hostitele služby naleznete v tématu [Rozšíření hostingu pomocí ServiceHostFactory.](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)</span><span class="sxs-lookup"><span data-stu-id="50490-141">For a detailed explanation of the service host factory mechanism, see the [Extending Hosting Using ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50490-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="50490-142">See also</span></span>

- [<span data-ttu-id="50490-143">Vytváření služeb WCF pro ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="50490-143">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [<span data-ttu-id="50490-144">Postupy: Migrace webových služeb ASP.NET s podporou AJAXu na službu WCF</span><span class="sxs-lookup"><span data-stu-id="50490-144">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
