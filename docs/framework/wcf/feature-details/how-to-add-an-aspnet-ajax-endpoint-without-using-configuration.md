---
title: "Postupy: Přidání koncového bodu ASP.NET AJAX bez použití konfiguračního souboru"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7b90ecd94f439472c89d0c075c8b7486abeacf38
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a><span data-ttu-id="56a25-102">Postupy: Přidání koncového bodu ASP.NET AJAX bez použití konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="56a25-102">How to: Add an ASP.NET AJAX Endpoint Without Using Configuration</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="56a25-103">Umožňuje vytvořit službu, která zveřejňuje koncový bod podporou technologie ASP.NET AJAX, který lze volat z jazyka JavaScript na webovém serveru klienta.</span><span class="sxs-lookup"><span data-stu-id="56a25-103"> allows you to create a service that exposes an ASP.NET AJAX-enabled endpoint that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="56a25-104">Pokud chcete vytvořit takové koncový bod, můžete pomocí konfiguračního souboru, stejně jako u všech dalších koncových bodů WCF nebo použít metodu, která nevyžaduje, aby všechny konfigurace – elementy.</span><span class="sxs-lookup"><span data-stu-id="56a25-104">To create such an endpoint, you can either use a configuration file, as with all other WCF endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="56a25-105">Toto téma popisuje druhý přístup.</span><span class="sxs-lookup"><span data-stu-id="56a25-105">This topic demonstrates the second approach.</span></span>  
  
 <span data-ttu-id="56a25-106">Vytvoření služby pomocí koncových bodů prvku ASP.NET AJAX bez konfigurace, musí být služby hostované Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="56a25-106">To create services with ASP.NET AJAX endpoints without configuration, the services must be hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="56a25-107">Pokud chcete aktivovat tento přístup pomocí prvku ASP.NET AJAX koncový bod, zadejte <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> jako parametr objekt pro vytváření v [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) direktivy v souboru .svc.</span><span class="sxs-lookup"><span data-stu-id="56a25-107">To activate an ASP.NET AJAX endpoint using this approach, specify the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> as the Factory parameter in the [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive in the .svc file.</span></span> <span data-ttu-id="56a25-108">Tento vlastní objekt pro vytváření je součást, který automaticky nakonfiguruje koncového bodu ASP.NET AJAX tak, aby může být volána z jazyka JavaScript na webovém serveru klienta.</span><span class="sxs-lookup"><span data-stu-id="56a25-108">This custom factory is the component that automatically configures an ASP.NET AJAX endpoint so that it can be called from JavaScript on a client Web site.</span></span>  
  
 <span data-ttu-id="56a25-109">Příklad pracovní najdete v tématu [služba AJAX bez konfigurace](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="56a25-109">For a working example, see the [AJAX Service Without Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span></span>  
  
 <span data-ttu-id="56a25-110">Přehled konfigurace koncového bodu ASP.NET AJAX pomocí konfigurace – elementy, najdete v části [postupy: použití konfigurace k přidání koncového bodu ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).</span><span class="sxs-lookup"><span data-stu-id="56a25-110">For an outline of how to configure an ASP.NET AJAX endpoint using configuration elements, see [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md).</span></span>  
  
### <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="56a25-111">Chcete-li vytvořit základní služby WCF</span><span class="sxs-lookup"><span data-stu-id="56a25-111">To create a basic WCF service</span></span>  
  
1.  <span data-ttu-id="56a25-112">Zadejte základní [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kontrakt služby s rozhraním označené jako <xref:System.ServiceModel.ServiceContractAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="56a25-112">Define a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="56a25-113">Označit každou operaci s <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="56a25-113">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="56a25-114">Nastavte <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="56a25-114">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
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
  
2.  <span data-ttu-id="56a25-115">Implementace `ICalculator` kontrakt služby s `CalculatorService`.</span><span class="sxs-lookup"><span data-stu-id="56a25-115">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```csharp  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3.  <span data-ttu-id="56a25-116">Zadejte obor názvů pro `ICalculator` a `CalculatorService` implementace podle jejich zabalení v bloku oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="56a25-116">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a><span data-ttu-id="56a25-117">K hostování služby v Internetové informační službě bez konfigurace</span><span class="sxs-lookup"><span data-stu-id="56a25-117">To host the service in Internet Information Services without configuration</span></span>  
  
1.  <span data-ttu-id="56a25-118">Vytvořte nový soubor s názvem služby s příponou .svc v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="56a25-118">Create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="56a25-119">Tento soubor upravit přidáním odpovídající [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) direktivy informace pro službu.</span><span class="sxs-lookup"><span data-stu-id="56a25-119">Edit this file by adding the appropriate [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="56a25-120">Určit, že <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> má být použita v [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) směrnice pro automatickou konfiguraci koncového bodu ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="56a25-120">Specify that the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is to be used in the [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive to automatically configure an ASP.NET AJAX endpoint.</span></span>  
  
    ```  
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2.  <span data-ttu-id="56a25-121">Sestavte službu a volání z klienta.</span><span class="sxs-lookup"><span data-stu-id="56a25-121">Build the service and call it from the client.</span></span> <span data-ttu-id="56a25-122">Internetové informační služby (IIS) aktivuje službu při volání.</span><span class="sxs-lookup"><span data-stu-id="56a25-122">Internet Information Services (IIS) activates the service when called.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="56a25-123">hostování ve službě IIS, najdete v části [postupy: hostování služby WCF ve službě IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span><span class="sxs-lookup"><span data-stu-id="56a25-123"> hosting in IIS, see [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
### <a name="to-call-the-service"></a><span data-ttu-id="56a25-124">Pro volání služby</span><span class="sxs-lookup"><span data-stu-id="56a25-124">To call the service</span></span>  
  
1.  <span data-ttu-id="56a25-125">Koncový bod je konfigurována na prázdnou adresu relativně k souboru .svc tak, aby služba je nyní k dispozici a může vyvolat odesílání požadavků na service.svc/\<operaci > – například service.svc/Add pro `Add` operaci.</span><span class="sxs-lookup"><span data-stu-id="56a25-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="56a25-126">Můžete ji tak, že zadáte adresu URL služby do kolekce skripty ovládacího prvku ASP.NET AJAX skript správce.</span><span class="sxs-lookup"><span data-stu-id="56a25-126">You can use it by entering the service URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="56a25-127">Příklad, naleznete v části [služba AJAX bez konfigurace](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="56a25-127">For an example, see the [AJAX Service Without Configuration](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="56a25-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="56a25-128">Example</span></span>  
  
 <span data-ttu-id="56a25-129">Koncový bod automaticky nakonfiguruje se vytvoří na prázdnou adresu relativně k základní adresu URL.</span><span class="sxs-lookup"><span data-stu-id="56a25-129">The automatically-configured endpoint is created at an empty address relative to the base URL.</span></span> <span data-ttu-id="56a25-130">Konfigurační soubor můžete taky přidat a používat s tímto přístupem.</span><span class="sxs-lookup"><span data-stu-id="56a25-130">A configuration file can also be added and used with this approach.</span></span> <span data-ttu-id="56a25-131">Pokud konfigurační soubor obsahuje definice koncových bodů, tyto koncové body se přidají do koncového bodu automaticky nakonfigurované.</span><span class="sxs-lookup"><span data-stu-id="56a25-131">If the configuration file contains endpoint definitions, these endpoints are added to the automatically-configured endpoint.</span></span>  
  
 <span data-ttu-id="56a25-132">Například používá service.svc <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> a adresář služby obsahuje soubor Web.config, který definuje koncový bod pro stejné služby pomocí <xref:System.ServiceModel.BasicHttpBinding> na adrese relativní "soap".</span><span class="sxs-lookup"><span data-stu-id="56a25-132">For example, service.svc uses the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> and the service directory contains a Web.config file that defines an endpoint for the same service using the <xref:System.ServiceModel.BasicHttpBinding> at the "soap" relative address.</span></span> <span data-ttu-id="56a25-133">V takovém případě služba obsahuje dva koncové body: jeden po service.svc (který reaguje na požadavky ASP.NET AJAX) a jiné na service.svc/soap (který reaguje na požadavky protokolu SOAP).</span><span class="sxs-lookup"><span data-stu-id="56a25-133">In this case, the service contains two endpoints: one at service.svc (which responds to ASP.NET AJAX requests) and another at service.svc/soap (which responds to SOAP requests).</span></span>  
  
 <span data-ttu-id="56a25-134">Pokud konfigurační soubor definuje koncový bod na prázdnou adresu relativní a <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> se používá, je vyvolána výjimka, a službu nepodaří spustit.</span><span class="sxs-lookup"><span data-stu-id="56a25-134">If the configuration file defines an endpoint at an empty relative address and the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used, an exception is thrown and the service fails to start.</span></span>  
  
 <span data-ttu-id="56a25-135">Konfigurace nelze použít k úpravě nastavení pro koncový bod automaticky nakonfigurované.</span><span class="sxs-lookup"><span data-stu-id="56a25-135">You cannot use configuration to modify settings on the automatically-configured endpoint.</span></span> <span data-ttu-id="56a25-136">Pokud žádné nastavení (například čtečky kvótu) musí být změněna, nesmí používat přístup bez konfigurace odebráním <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> ze souboru .svc a vytvořením položky konfigurace pro koncový bod.</span><span class="sxs-lookup"><span data-stu-id="56a25-136">If any setting (such as a reader quota) must be modified, you must not use the configuration-free approach by removing the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> from the .svc file and creating a configuration entry for the endpoint.</span></span>  
  
 <span data-ttu-id="56a25-137">Pokud vaše služba vyžaduje režim kompatibility ASP.NET – například pokud se používá <xref:System.Web.HttpContext> třídu nebo mechanismy ověřování ASP.NET – konfigurační soubor je stále vyžadují k zapnutí v tomto režimu.</span><span class="sxs-lookup"><span data-stu-id="56a25-137">If your service requires ASP.NET Compatibility Mode - for example, if it uses the <xref:System.Web.HttpContext> class or ASP.NET authorization mechanisms - a configuration file is still required to turn on this mode.</span></span> <span data-ttu-id="56a25-138">Konfigurační element požadované je [ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) element, který musí být přidán následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="56a25-138">The configuration element required is the [\<serviceHostingEnvironment>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md) element, which must be added as follows.</span></span>  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="56a25-139">[služby WCF a ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="56a25-139"> the [WCF Services and ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md) topic.</span></span>  
  
 <span data-ttu-id="56a25-140"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> Třída je třídu odvozenou z <xref:System.ServiceModel.Activation.ServiceHostFactory>.</span><span class="sxs-lookup"><span data-stu-id="56a25-140">The <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> class is a derived class of <xref:System.ServiceModel.Activation.ServiceHostFactory>.</span></span> <span data-ttu-id="56a25-141">Podrobné vysvětlení mechanismus objekt pro vytváření hostitele služby, najdete v článku [rozšíření hostování pomocí třídy ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="56a25-141">For a detailed explanation of the service host factory mechanism, see the [Extending Hosting Using ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md) topic.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56a25-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="56a25-142">See Also</span></span>  
 [<span data-ttu-id="56a25-143">Vytváření služeb WCF pro ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="56a25-143">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [<span data-ttu-id="56a25-144">Postupy: Migrace webových služeb ASP.NET s podporou AJAX na WCF</span><span class="sxs-lookup"><span data-stu-id="56a25-144">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
