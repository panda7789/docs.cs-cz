---
title: 'Postupy: Přidání koncového bodu ASP.NET AJAX bez použití konfiguračního souboru'
ms.date: 03/30/2017
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
ms.openlocfilehash: 4a7ff48e529ab58c8744edea22d52ad12a4d7b96
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70895078"
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a><span data-ttu-id="b65a6-102">Postupy: Přidání koncového bodu ASP.NET AJAX bez použití konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="b65a6-102">How to: Add an ASP.NET AJAX Endpoint Without Using Configuration</span></span>
<span data-ttu-id="b65a6-103">Windows Communication Foundation (WCF) umožňuje vytvořit službu, která zveřejňuje koncový bod s povoleným ASP.NET AJAX, který se dá volat z JavaScriptu na klientském webu.</span><span class="sxs-lookup"><span data-stu-id="b65a6-103">Windows Communication Foundation (WCF) allows you to create a service that exposes an ASP.NET AJAX-enabled endpoint that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="b65a6-104">Chcete-li vytvořit takový koncový bod, můžete buď použít konfigurační soubor, stejně jako všechny ostatní koncové body WCF, nebo použít metodu, která nevyžaduje žádné konfigurační prvky.</span><span class="sxs-lookup"><span data-stu-id="b65a6-104">To create such an endpoint, you can either use a configuration file, as with all other WCF endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="b65a6-105">Toto téma ukazuje druhý přístup.</span><span class="sxs-lookup"><span data-stu-id="b65a6-105">This topic demonstrates the second approach.</span></span>  
  
 <span data-ttu-id="b65a6-106">Chcete-li vytvořit služby s koncovými body ASP.NET AJAX bez konfigurace, musí být služby hostovány Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="b65a6-106">To create services with ASP.NET AJAX endpoints without configuration, the services must be hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="b65a6-107">Chcete-li aktivovat koncový bod ASP.NET AJAX pomocí tohoto přístupu, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> zadejte jako parametr Factory [ \@](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) v direktivě ServiceHost v souboru. svc.</span><span class="sxs-lookup"><span data-stu-id="b65a6-107">To activate an ASP.NET AJAX endpoint using this approach, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> as the Factory parameter in the [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive in the .svc file.</span></span> <span data-ttu-id="b65a6-108">Tato vlastní továrna je komponenta, která automaticky konfiguruje koncový bod ASP.NET AJAX tak, aby jej bylo možné volat z JavaScriptu na klientském webu.</span><span class="sxs-lookup"><span data-stu-id="b65a6-108">This custom factory is the component that automatically configures an ASP.NET AJAX endpoint so that it can be called from JavaScript on a client Web site.</span></span>  
  
 <span data-ttu-id="b65a6-109">Pracovní příklad naleznete v tématu [Služba AJAX bez konfigurace](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="b65a6-109">For a working example, see the [AJAX Service Without Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span></span>  
  
 <span data-ttu-id="b65a6-110">Osnova, jak nakonfigurovat koncový bod ASP.NET AJAX pomocí elementů konfigurace, naleznete v [tématu How to: Pomocí konfigurace přidejte koncový bod](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="b65a6-110">For an outline of how to configure an ASP.NET AJAX endpoint using configuration elements, see [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).</span></span>  
  
### <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="b65a6-111">Vytvoření základní služby WCF</span><span class="sxs-lookup"><span data-stu-id="b65a6-111">To create a basic WCF service</span></span>  
  
1. <span data-ttu-id="b65a6-112">Definujte základní kontrakt služby WCF s rozhraním označeným <xref:System.ServiceModel.ServiceContractAttribute> atributem.</span><span class="sxs-lookup"><span data-stu-id="b65a6-112">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="b65a6-113">Označte každou operaci pomocí <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="b65a6-113">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="b65a6-114">Nezapomeňte nastavit <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b65a6-114">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
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
  
2. <span data-ttu-id="b65a6-115">Implementujte kontrakt `CalculatorService`služby s. `ICalculator`</span><span class="sxs-lookup"><span data-stu-id="b65a6-115">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```csharp  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3. <span data-ttu-id="b65a6-116">Definujte obor názvů pro `ICalculator` implementace a `CalculatorService` jejich zabalením do bloku oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b65a6-116">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a><span data-ttu-id="b65a6-117">Hostování služby v Internetová informační služba bez konfigurace</span><span class="sxs-lookup"><span data-stu-id="b65a6-117">To host the service in Internet Information Services without configuration</span></span>  
  
1. <span data-ttu-id="b65a6-118">V aplikaci vytvořte nový soubor s názvem služba s příponou. svc.</span><span class="sxs-lookup"><span data-stu-id="b65a6-118">Create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="b65a6-119">Upravte tento soubor přidáním příslušné [ \@](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) informace o direktivě ServiceHost pro službu.</span><span class="sxs-lookup"><span data-stu-id="b65a6-119">Edit this file by adding the appropriate [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="b65a6-120">Určete, že <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> se má použít [ \@](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) v direktivě ServiceHost k automatické konfiguraci koncového bodu ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="b65a6-120">Specify that the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is to be used in the [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive to automatically configure an ASP.NET AJAX endpoint.</span></span>  
  
    ```text
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2. <span data-ttu-id="b65a6-121">Sestavte službu a zavolejte ji z klienta.</span><span class="sxs-lookup"><span data-stu-id="b65a6-121">Build the service and call it from the client.</span></span> <span data-ttu-id="b65a6-122">Internetová informační služba (IIS) aktivuje službu při volání.</span><span class="sxs-lookup"><span data-stu-id="b65a6-122">Internet Information Services (IIS) activates the service when called.</span></span> <span data-ttu-id="b65a6-123">Další informace o hostování ve službě IIS najdete v [tématu How to: Hostování služby WCF ve službě IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span><span class="sxs-lookup"><span data-stu-id="b65a6-123">For more information about hosting in IIS, see [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
### <a name="to-call-the-service"></a><span data-ttu-id="b65a6-124">Volání služby</span><span class="sxs-lookup"><span data-stu-id="b65a6-124">To call the service</span></span>  
  
1. <span data-ttu-id="b65a6-125">Koncový bod je nakonfigurován na prázdné adrese relativní vzhledem k souboru. svc, takže služba je nyní k dispozici a je možné ji vyvolat odesláním žádostí do služby. svc\</Operation > – například Service. svc/Add `Add` pro operaci.</span><span class="sxs-lookup"><span data-stu-id="b65a6-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="b65a6-126">Můžete ji použít tak, že zadáte adresu URL služby do kolekce Scripts ovládacího prvku Správce skriptů ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="b65a6-126">You can use it by entering the service URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="b65a6-127">Příklad naleznete v tématu [Služba AJAX bez konfigurace](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="b65a6-127">For an example, see the [AJAX Service Without Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b65a6-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="b65a6-128">Example</span></span>  
  
 <span data-ttu-id="b65a6-129">Automaticky konfigurovaný koncový bod se vytvoří na prázdné adrese relativní vzhledem k základní adrese URL.</span><span class="sxs-lookup"><span data-stu-id="b65a6-129">The automatically-configured endpoint is created at an empty address relative to the base URL.</span></span> <span data-ttu-id="b65a6-130">S tímto přístupem je možné taky přidat konfigurační soubor a použít ho.</span><span class="sxs-lookup"><span data-stu-id="b65a6-130">A configuration file can also be added and used with this approach.</span></span> <span data-ttu-id="b65a6-131">Pokud konfigurační soubor obsahuje definice koncových bodů, tyto koncové body se přidají do automaticky konfigurovaného koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="b65a6-131">If the configuration file contains endpoint definitions, these endpoints are added to the automatically-configured endpoint.</span></span>  
  
 <span data-ttu-id="b65a6-132">Například služba. svc používá <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> a adresář služby obsahuje soubor Web. config, který definuje koncový bod pro stejnou službu pomocí na <xref:System.ServiceModel.BasicHttpBinding> relativní adrese "SOAP".</span><span class="sxs-lookup"><span data-stu-id="b65a6-132">For example, service.svc uses the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> and the service directory contains a Web.config file that defines an endpoint for the same service using the <xref:System.ServiceModel.BasicHttpBinding> at the "soap" relative address.</span></span> <span data-ttu-id="b65a6-133">V tomto případě služba obsahuje dva koncové body: jeden na Service. svc (který reaguje na požadavky ASP.NET AJAX) a druhý v Service. svc/SOAP (který reaguje na žádosti SOAP).</span><span class="sxs-lookup"><span data-stu-id="b65a6-133">In this case, the service contains two endpoints: one at service.svc (which responds to ASP.NET AJAX requests) and another at service.svc/soap (which responds to SOAP requests).</span></span>  
  
 <span data-ttu-id="b65a6-134">Pokud konfigurační soubor definuje koncový bod na prázdné relativní adrese a <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> použije se, vyvolá se výjimka a služba se nespustí.</span><span class="sxs-lookup"><span data-stu-id="b65a6-134">If the configuration file defines an endpoint at an empty relative address and the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used, an exception is thrown and the service fails to start.</span></span>  
  
 <span data-ttu-id="b65a6-135">Konfiguraci nelze použít pro úpravu nastavení automaticky konfigurovaného koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="b65a6-135">You cannot use configuration to modify settings on the automatically-configured endpoint.</span></span> <span data-ttu-id="b65a6-136">Pokud je nutné změnit jakékoli nastavení (například kvótu čtenářů), nepoužívejte přístup k nebezplatné konfiguraci odebráním <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> ze souboru. svc a vytvořením položky konfigurace pro koncový bod.</span><span class="sxs-lookup"><span data-stu-id="b65a6-136">If any setting (such as a reader quota) must be modified, you must not use the configuration-free approach by removing the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> from the .svc file and creating a configuration entry for the endpoint.</span></span>  
  
 <span data-ttu-id="b65a6-137">Pokud vaše služba vyžaduje režim kompatibility ASP.NET, například pokud používá <xref:System.Web.HttpContext> autorizační mechanismy třídy nebo ASP.NET, je pro zapnutí tohoto režimu stále nutný konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="b65a6-137">If your service requires ASP.NET Compatibility Mode - for example, if it uses the <xref:System.Web.HttpContext> class or ASP.NET authorization mechanisms - a configuration file is still required to turn on this mode.</span></span> <span data-ttu-id="b65a6-138">Požadovaný prvek konfigurace je [ \<element serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) , který musí být přidán následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="b65a6-138">The configuration element required is the [\<serviceHostingEnvironment>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) element, which must be added as follows.</span></span>  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 <span data-ttu-id="b65a6-139">Další informace najdete v tématu [služby WCF a ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) .</span><span class="sxs-lookup"><span data-stu-id="b65a6-139">For more information, see the [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) topic.</span></span>  
  
 <span data-ttu-id="b65a6-140">Třída je odvozenou <xref:System.ServiceModel.Activation.ServiceHostFactory>třídou třídy. <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory></span><span class="sxs-lookup"><span data-stu-id="b65a6-140">The <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> class is a derived class of <xref:System.ServiceModel.Activation.ServiceHostFactory>.</span></span> <span data-ttu-id="b65a6-141">Podrobné vysvětlení mechanismu výrobního hostitele služby najdete v tématu [rozšíření hostování pomocí ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) .</span><span class="sxs-lookup"><span data-stu-id="b65a6-141">For a detailed explanation of the service host factory mechanism, see the [Extending Hosting Using ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b65a6-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b65a6-142">See also</span></span>

- [<span data-ttu-id="b65a6-143">Vytváření služeb WCF pro ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="b65a6-143">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [<span data-ttu-id="b65a6-144">Postupy: Migrace webových služeb ASP.NET s podporou jazyka AJAX do WCF</span><span class="sxs-lookup"><span data-stu-id="b65a6-144">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
