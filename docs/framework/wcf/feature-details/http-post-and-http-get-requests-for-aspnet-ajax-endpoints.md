---
title: "Postupy: výběr mezi HTTP POST a HTTP GET požadavky pro koncové body ASP.NET AJAX"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b47de82a-4c92-4af6-bceb-a5cb8bb8ede9
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9b9116cee8067ed3c7592413f30adc65379eb149
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-choose-between-http-post-and-http-get-requests-for-aspnet-ajax-endpoints"></a><span data-ttu-id="3da33-102">Postupy: výběr mezi HTTP POST a HTTP GET požadavky pro koncové body ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="3da33-102">How to: Choose between HTTP POST and HTTP GET requests for ASP.NET AJAX Endpoints</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="3da33-103">Umožňuje vytvořit službu, která zveřejňuje koncový bod podporou technologie ASP.NET AJAX, který lze volat z jazyka JavaScript na webovém serveru klienta.</span><span class="sxs-lookup"><span data-stu-id="3da33-103"> allows you to create a service that exposes an ASP.NET AJAX-enabled endpoint that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="3da33-104">Ale základní postupy pro vytváření těchto služeb je popsané v [postupy: použití konfigurace k přidání koncového bodu ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) a [postupy: Přidání aplikace ASP.NET AJAX konfigurace koncového bodu bez pomocí](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="3da33-104">The basic procedures for building such services is discussed in [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) and [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
 <span data-ttu-id="3da33-105">Technologie ASP.NET AJAX podporuje operace, které používají akce HTTP POST a HTTP GET s HTTP POST se výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="3da33-105">ASP.NET AJAX supports operations that use the HTTP POST and HTTP GET verbs, with HTTP POST being the default.</span></span> <span data-ttu-id="3da33-106">Při vytváření operace, která nemá žádné vedlejší účinky a vrátí data, která změní občas nebo vůbec, použijte GET protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="3da33-106">When creating an operation that has no side effects and returns data that rarely or never changes, use HTTP GET instead.</span></span> <span data-ttu-id="3da33-107">Výsledky operace GET do mezipaměti, což znamená, že několik volání do stejné operace může způsobit pouze jeden požadavek pro vaši službu.</span><span class="sxs-lookup"><span data-stu-id="3da33-107">Results of GET operations can be cached, which means that multiple calls to the same operation may result in only one request to your service.</span></span> <span data-ttu-id="3da33-108">Ukládání do mezipaměti není provádí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] , ale může probíhat na kterékoli úrovni (prohlížeč, na serveru proxy a jiných úrovních.) Ukládání do mezipaměti je výhodné, pokud chcete zvýšit výkon služby, ale nemusí být přijatelné, pokud často mění data, nebo pokud operace provede určitou akci.</span><span class="sxs-lookup"><span data-stu-id="3da33-108">The caching is not done by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] but can take place at any level (in a user's browser, on a proxy server, and other levels.) Caching is advantageous if you want to increase service performance, but may not be acceptable if data changes frequently or if the operation performs some action.</span></span>  
  
 <span data-ttu-id="3da33-109">Například pokud navrhujete služby ke správě uživatele Knihovna Hudba, operace, která vyhledává umělcem podle výhody title album pomocí GET, ale operace, která přidá album do vlastní kolekce uživatele musíte použít POST.</span><span class="sxs-lookup"><span data-stu-id="3da33-109">For example, if you are designing service to manage a user's music library, an operation that looks up the artist based on an album's title benefits from using GET, but an operation that adds an album to the user's personal collection must use POST.</span></span>  
  
 <span data-ttu-id="3da33-110">Chcete-li řídit Životnost mezipaměti, použijte <xref:System.ServiceModel.Web.OutgoingWebResponseContext> typu.</span><span class="sxs-lookup"><span data-stu-id="3da33-110">To control the lifetime of the cache, use the <xref:System.ServiceModel.Web.OutgoingWebResponseContext> type.</span></span> <span data-ttu-id="3da33-111">Při navrhování služby, která vrací předpovědi počasí aktualizovat každou hodinu, byste použili získat ale maximální doba uložení do mezipaměti na jednu hodinu nebo méně uživatelé služby zabránit v přístupu k zastaralá data.</span><span class="sxs-lookup"><span data-stu-id="3da33-111">For example, when designing a service that returns weather forecasts updated hourly, you would use GET but limit the cache duration to an hour or less to prevent the users of the service from accessing stale data.</span></span>  
  
 <span data-ttu-id="3da33-112">Při použití služeb ze stránky ASP.NET AJAX, které používají řízení správce skriptu, ať už používá operace GET nebo POST - mechanismus skript správce zajistí, že je typ správný požadavku vydané umožňuje žádný rozdíl.</span><span class="sxs-lookup"><span data-stu-id="3da33-112">When using services from an ASP.NET AJAX page that use the Script Manager control, it makes no difference whether the operation uses GET or POST - the script manager mechanism ensures that the correct request type is issued.</span></span>  
  
 <span data-ttu-id="3da33-113">Operace HTTP GET používají žádné vstupní parametry nepodporuje operace POST, včetně komplexními datovými typy kontrakt.</span><span class="sxs-lookup"><span data-stu-id="3da33-113">HTTP GET operations use any input parameters supported by POST operations, including complex data contract types.</span></span> <span data-ttu-id="3da33-114">Ve většině případů doporučujeme však vyhnout příliš mnoho parametrů nebo parametry, které jsou v operacích GET příliš složité, protože snižuje efektivitu ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="3da33-114">However, in most cases it is recommended to avoid too many parameters or parameters that are too complex in GET operations because it reduces caching efficiency.</span></span>  
  
 <span data-ttu-id="3da33-115">Toto téma ukazuje, jak můžete vybrat, jestli GET a POST pomocí přidání <xref:System.ServiceModel.Web.WebGetAttribute> nebo <xref:System.ServiceModel.Web.WebInvokeAttribute> atributy s příslušnými operacemi kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="3da33-115">This topic demonstrates how to select between GET and POST by adding the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes to the relevant operations in the service contract.</span></span> <span data-ttu-id="3da33-116">Další kroky (k implementaci, konfigurace a hostitelem služby), které je potřeba získat služba spuštěná jsou podobné těm, které používá služba žádné prvku ASP.NET AJAX v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3da33-116">The other steps (to implement, configure and host the service) that are required to get the service running are similar to those used by any ASP.NET AJAX service in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 <span data-ttu-id="3da33-117">Operace označené jako <xref:System.ServiceModel.Web.WebGetAttribute> vždy používá požadavek GET.</span><span class="sxs-lookup"><span data-stu-id="3da33-117">An operation marked with the <xref:System.ServiceModel.Web.WebGetAttribute> always uses a GET request.</span></span> <span data-ttu-id="3da33-118">Operace označené jako <xref:System.ServiceModel.Web.WebInvokeAttribute>, nebo není označena s žádným z těchto atributů, používá požadavek POST.</span><span class="sxs-lookup"><span data-stu-id="3da33-118">An operation marked with the <xref:System.ServiceModel.Web.WebInvokeAttribute>, or not marked with any of the two attributes, uses a POST request.</span></span> <span data-ttu-id="3da33-119"><xref:System.ServiceModel.Web.WebInvokeAttribute> Umožňuje použít další příkazy HTTP, jiné než GET a POST (například PUT a DELETE) prostřednictvím <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3da33-119">The <xref:System.ServiceModel.Web.WebInvokeAttribute> allows the use of other HTTP verbs, other than GET and POST (such as PUT and DELETE) through the <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> property.</span></span> <span data-ttu-id="3da33-120">Tyto příkazy však nepodporuje prvku ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="3da33-120">However, these verbs are not supported by ASP.NET AJAX.</span></span> <span data-ttu-id="3da33-121">Pokud máte v úmyslu používat službu ze stránky ASP.NET pomocí ovládacího prvku správce skriptu, nepoužívejte <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3da33-121">If you intend to use the service from ASP.NET pages using the Script Manager control, do not use the <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> property.</span></span>  
  
 <span data-ttu-id="3da33-122">Příklad pracovní přepínání GET, naleznete [základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="3da33-122">For a working example of switching to GET, see the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>  
  
 <span data-ttu-id="3da33-123">Příklad, který používá metodu POST, najdete v článku [AJAX služby pomocí HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="3da33-123">For a sample that uses POST, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) sample.</span></span>  
  
### <a name="to-create-a-wcf-service-that-responds-to-http-get-or-http-post-requests"></a><span data-ttu-id="3da33-124">Vytvoření služby WCF, odpoví na HTTP GET nebo POST protokolu HTTP požadavky</span><span class="sxs-lookup"><span data-stu-id="3da33-124">To create a WCF service that responds to HTTP GET or HTTP POST requests</span></span>  
  
1.  <span data-ttu-id="3da33-125">Zadejte základní [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kontrakt služby s rozhraním označené jako <xref:System.ServiceModel.ServiceContractAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="3da33-125">Define a basic [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="3da33-126">Označit každou operaci s <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="3da33-126">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="3da33-127">Přidat <xref:System.ServiceModel.Web.WebGetAttribute> atribut ke stanovení, zda operace by měla odpovídat na požadavky HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="3da33-127">Add the <xref:System.ServiceModel.Web.WebGetAttribute> attribute to stipulate that an operation should respond to HTTP GET requests.</span></span> <span data-ttu-id="3da33-128">Můžete také přidat <xref:System.ServiceModel.Web.WebInvokeAttribute> atribut k explicitnímu zadání HTTP POST, nebo není uveden atribut, který se standardně HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="3da33-128">You can also add the <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute to explicitly specify HTTP POST, or not specify an attribute, which defaults to HTTP POST.</span></span>  
  
    ```  
    [ServiceContract]  
    public interface IMusicService  
    {  
        //This operation uses a GET method.  
        [OperationContract]  
        [WebGet]  
        string LookUpArtist(string album);  
  
        //This operation will use a POST method.  
        [OperationContract]  
        [WebInvoke]  
        void AddAlbum(string user, string album);  
  
        //This operation will use POST method by default  
        //since nothing else is explicitly specified.  
        [OperationContract]  
        string[] GetAlbums(string user);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2.  <span data-ttu-id="3da33-129">Implementace `IMusicService` kontrakt služby s `MusicService`.</span><span class="sxs-lookup"><span data-stu-id="3da33-129">Implement the `IMusicService` service contract with a `MusicService`.</span></span>  
  
    ```  
    public class MusicService : IMusicService  
    {  
        public void AddAlbum(string user, string album)  
        {  
            //Add implementation here.  
        }  
  
         //Other operations omitted…  
    }  
    ```  
  
3.  <span data-ttu-id="3da33-130">Vytvořte nový soubor s názvem služby s příponou .svc v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3da33-130">Create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="3da33-131">Tento soubor upravit přidáním odpovídající [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) direktivy informace pro službu.</span><span class="sxs-lookup"><span data-stu-id="3da33-131">Edit this file by adding the appropriate [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="3da33-132">Určit, že <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> má být použita v [ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) směrnice pro automatickou konfiguraci koncového bodu ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="3da33-132">Specify that the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is to be used in the [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive to automatically configure an ASP.NET AJAX endpoint.</span></span>  
  
    ```  
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.MusicService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
### <a name="to-call-the-service"></a><span data-ttu-id="3da33-133">Pro volání služby</span><span class="sxs-lookup"><span data-stu-id="3da33-133">To call the service</span></span>  
  
1.  <span data-ttu-id="3da33-134">Operace GET vaší služby bez žádný kód klienta, můžete otestovat pomocí prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="3da33-134">You can test your service's GET operations without any client code, by using the browser.</span></span> <span data-ttu-id="3da33-135">Například pokud vaše služba je nakonfigurována na adrese "http://example.com/service.svc", do panelu Adresa prohlížeče zadáním příkazu "http://example.com/service.svc/LookUpArtist?album=SomeAlbum" vyvolá službu a způsobí, že odpověď na být stáhnout nebo zobrazit.</span><span class="sxs-lookup"><span data-stu-id="3da33-135">For example, if your service is configured at the "http://example.com/service.svc" address, then typing "http://example.com/service.svc/LookUpArtist?album=SomeAlbum" into the browser address bar invokes the service and causes the response to be downloaded or displayed.</span></span>  
  
2.  <span data-ttu-id="3da33-136">Služby můžete použít s operacemi GET stejným způsobem jako jiné služby prvku ASP.NET AJAX – zadáním službu Řízení adresu URL do kolekce skripty správce skript AJAX technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="3da33-136">You can use services with GET operations in the same way as any other ASP.NET AJAX services - by entering the service URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="3da33-137">Příklad, naleznete v části [základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md).</span><span class="sxs-lookup"><span data-stu-id="3da33-137">For an example, see the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3da33-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="3da33-138">See Also</span></span>  
 [<span data-ttu-id="3da33-139">Vytváření služeb WCF pro ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="3da33-139">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [<span data-ttu-id="3da33-140">Postupy: migrace technologie AJAX webových služeb ASP.NET na WCF</span><span class="sxs-lookup"><span data-stu-id="3da33-140">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
