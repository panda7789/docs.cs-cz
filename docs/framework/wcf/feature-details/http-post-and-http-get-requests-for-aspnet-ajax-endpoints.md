---
title: 'Postupy: Volba mezi žádostmi HTTP POST a HTTP GET u koncových bodů ASP.NET AJAX'
ms.date: 03/30/2017
ms.assetid: b47de82a-4c92-4af6-bceb-a5cb8bb8ede9
ms.openlocfilehash: 33763a77d1ab1c82af9b9e1fb9c42d72392f8798
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59091275"
---
# <a name="how-to-choose-between-http-post-and-http-get-requests-for-aspnet-ajax-endpoints"></a><span data-ttu-id="e5594-102">Postupy: Volba mezi žádostmi HTTP POST a HTTP GET u koncových bodů ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="e5594-102">How to: Choose between HTTP POST and HTTP GET requests for ASP.NET AJAX Endpoints</span></span>

<span data-ttu-id="e5594-103">Windows Communication Foundation (WCF) umožňuje vytvořit službu, která zpřístupňuje koncový bod s podporou technologie ASP.NET AJAX, který může být volána z jazyka JavaScript na webové stránce klienta.</span><span class="sxs-lookup"><span data-stu-id="e5594-103">Windows Communication Foundation (WCF) allows you to create a service that exposes an ASP.NET AJAX-enabled endpoint that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="e5594-104">Základní postupy pro vytváření těchto služeb je podrobněji popsána [jak: Použití konfigurace k přidání koncového bodu ASP.NET AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) a [jak: Přidání koncového bodu ASP.NET AJAX bez použití konfiguračního](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="e5594-104">The basic procedures for building such services is discussed in [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) and [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
 <span data-ttu-id="e5594-105">ASP.NET AJAX podporuje operace, které používají operace HTTP POST a HTTP GET, pomocí HTTP POST, je výchozí hodnota.</span><span class="sxs-lookup"><span data-stu-id="e5594-105">ASP.NET AJAX supports operations that use the HTTP POST and HTTP GET verbs, with HTTP POST being the default.</span></span> <span data-ttu-id="e5594-106">Při vytváření operace, která nemá žádné vedlejší účinky a vrací data, která se mění jen zřídka nebo vůbec, použijte GET protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="e5594-106">When creating an operation that has no side effects and returns data that rarely or never changes, use HTTP GET instead.</span></span> <span data-ttu-id="e5594-107">Výsledky operací GET můžete uložit do mezipaměti, což znamená, že několik volání do stejné operace mohou způsobit pouze jeden požadavek na vaši službu.</span><span class="sxs-lookup"><span data-stu-id="e5594-107">Results of GET operations can be cached, which means that multiple calls to the same operation may result in only one request to your service.</span></span> <span data-ttu-id="e5594-108">Ukládání do mezipaměti se provádí WCF, ale může probíhat na libovolné úrovni (do prohlížeče uživatele, na proxy server a další úrovně.) Ukládání do mezipaměti je výhodné, pokud chcete zvýšit výkon služby, ale nemusí být akceptovatelné Pokud, data se často mění, nebo pokud operace provede určitou akci.</span><span class="sxs-lookup"><span data-stu-id="e5594-108">The caching is not done by WCF but can take place at any level (in a user's browser, on a proxy server, and other levels.) Caching is advantageous if you want to increase service performance, but may not be acceptable if data changes frequently or if the operation performs some action.</span></span>  
  
 <span data-ttu-id="e5594-109">Například pokud navrhujete služby ke správě uživatele hudební knihovnu, operace, která vyhledá interpreta podle výhody alba název pomocí GET, ale operaci, která přidá alba do vlastní kolekce uživatele musíte použít příspěvku.</span><span class="sxs-lookup"><span data-stu-id="e5594-109">For example, if you are designing service to manage a user's music library, an operation that looks up the artist based on an album's title benefits from using GET, but an operation that adds an album to the user's personal collection must use POST.</span></span>  
  
 <span data-ttu-id="e5594-110">Pokud chcete řídit dobu životnosti mezipaměti, použijte <xref:System.ServiceModel.Web.OutgoingWebResponseContext> typu.</span><span class="sxs-lookup"><span data-stu-id="e5594-110">To control the lifetime of the cache, use the <xref:System.ServiceModel.Web.OutgoingWebResponseContext> type.</span></span> <span data-ttu-id="e5594-111">Při návrhu služby, která vrací předpověď počasí aktualizován po hodinách, můžete využít získat ale omezit dobu uložení do mezipaměti na jednu hodinu nebo méně zabránit v přístupu k zastaralých dat uživatelům této služby.</span><span class="sxs-lookup"><span data-stu-id="e5594-111">For example, when designing a service that returns weather forecasts updated hourly, you would use GET but limit the cache duration to an hour or less to prevent the users of the service from accessing stale data.</span></span>  
  
 <span data-ttu-id="e5594-112">Při použití služby ze stránky technologie ASP.NET AJAX využívající ovládací prvek správce skriptů, už nezáleží, jestli používá operace GET nebo POST - mechanismus skript správce zajišťuje, že typ správnou žádost vydává.</span><span class="sxs-lookup"><span data-stu-id="e5594-112">When using services from an ASP.NET AJAX page that use the Script Manager control, it makes no difference whether the operation uses GET or POST - the script manager mechanism ensures that the correct request type is issued.</span></span>  
  
 <span data-ttu-id="e5594-113">Operace GET protokolu HTTP používají vstupní parametry. podporované operace POST, včetně komplexních datových typů kontraktu.</span><span class="sxs-lookup"><span data-stu-id="e5594-113">HTTP GET operations use any input parameters supported by POST operations, including complex data contract types.</span></span> <span data-ttu-id="e5594-114">Ve většině případů doporučujeme ale příliš mnoha parametry ani parametry, které jsou příliš složité v operace GET, protože snižuje efektivita ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="e5594-114">However, in most cases it is recommended to avoid too many parameters or parameters that are too complex in GET operations because it reduces caching efficiency.</span></span>  
  
 <span data-ttu-id="e5594-115">Toto téma ukazuje, jak vybrat mezi GET a POST přidáním <xref:System.ServiceModel.Web.WebGetAttribute> nebo <xref:System.ServiceModel.Web.WebInvokeAttribute> atributy do příslušné operace v kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="e5594-115">This topic demonstrates how to select between GET and POST by adding the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes to the relevant operations in the service contract.</span></span> <span data-ttu-id="e5594-116">Další kroky (k implementaci, konfiguraci a hostitelem služby), které jsou požadovány pro spuštění služby jsou podobné těm, které používá služba všechny technologie ASP.NET AJAX ve službě WCF.</span><span class="sxs-lookup"><span data-stu-id="e5594-116">The other steps (to implement, configure and host the service) that are required to get the service running are similar to those used by any ASP.NET AJAX service in WCF.</span></span>  
  
 <span data-ttu-id="e5594-117">Operace označené <xref:System.ServiceModel.Web.WebGetAttribute> vždy používá požadavek GET.</span><span class="sxs-lookup"><span data-stu-id="e5594-117">An operation marked with the <xref:System.ServiceModel.Web.WebGetAttribute> always uses a GET request.</span></span> <span data-ttu-id="e5594-118">Operace označené <xref:System.ServiceModel.Web.WebInvokeAttribute>, nebo není označená pomocí některé z těchto atributů, používá požadavek POST.</span><span class="sxs-lookup"><span data-stu-id="e5594-118">An operation marked with the <xref:System.ServiceModel.Web.WebInvokeAttribute>, or not marked with any of the two attributes, uses a POST request.</span></span> <span data-ttu-id="e5594-119"><xref:System.ServiceModel.Web.WebInvokeAttribute> Umožňuje používat další příkazy HTTP, jiné než GET a POST (například PUT a DELETE) prostřednictvím <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e5594-119">The <xref:System.ServiceModel.Web.WebInvokeAttribute> allows the use of other HTTP verbs, other than GET and POST (such as PUT and DELETE) through the <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> property.</span></span> <span data-ttu-id="e5594-120">Tyto příkazy však nepodporuje technologie ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="e5594-120">However, these verbs are not supported by ASP.NET AJAX.</span></span> <span data-ttu-id="e5594-121">Pokud máte v úmyslu používat službu ze stránky ASP.NET s využitím ovládací prvek správce skriptů, nepoužívejte <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e5594-121">If you intend to use the service from ASP.NET pages using the Script Manager control, do not use the <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> property.</span></span>  
  
 <span data-ttu-id="e5594-122">Funkční příklad přepínání GET, najdete v článku [základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="e5594-122">For a working example of switching to GET, see the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>  
  
 <span data-ttu-id="e5594-123">Příklad, který používá metodu POST, najdete v článku [AJAX služba využívající HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="e5594-123">For a sample that uses POST, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) sample.</span></span>  
  
## <a name="to-create-a-wcf-service-that-responds-to-http-get-or-http-post-requests"></a><span data-ttu-id="e5594-124">Vytvoření služby WCF, který reaguje na HTTP GET nebo POST protokolu HTTP žádosti</span><span class="sxs-lookup"><span data-stu-id="e5594-124">To create a WCF service that responds to HTTP GET or HTTP POST requests</span></span>
  
1. <span data-ttu-id="e5594-125">Definování základní kontraktu služby WCF s rozhraním označené <xref:System.ServiceModel.ServiceContractAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="e5594-125">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="e5594-126">Označit každou operaci s <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="e5594-126">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="e5594-127">Přidat <xref:System.ServiceModel.Web.WebGetAttribute> atribut stanoví, že operace by měla reagovat na požadavky HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="e5594-127">Add the <xref:System.ServiceModel.Web.WebGetAttribute> attribute to stipulate that an operation should respond to HTTP GET requests.</span></span> <span data-ttu-id="e5594-128">Můžete také přidat <xref:System.ServiceModel.Web.WebInvokeAttribute> atribut s ohledem na HTTP POST, nebo není zadán atribut výchozí nastavení je HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="e5594-128">You can also add the <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute to explicitly specify HTTP POST, or not specify an attribute, which defaults to HTTP POST.</span></span>
  
    ```csharp
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
  
2. <span data-ttu-id="e5594-129">Implementace `IMusicService` kontrakt služby s `MusicService`.</span><span class="sxs-lookup"><span data-stu-id="e5594-129">Implement the `IMusicService` service contract with a `MusicService`.</span></span>
  
    ```csharp
    public class MusicService : IMusicService  
    {  
        public void AddAlbum(string user, string album)  
        {  
            //Add implementation here.  
        }  
  
         //Other operations omitted…  
    }  
    ```  
  
3. <span data-ttu-id="e5594-130">Vytvořte nový soubor s názvem služby s příponou .svc v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e5594-130">Create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="e5594-131">Tento soubor upravit tak, že přidáte odpovídající [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) direktiv informace pro službu.</span><span class="sxs-lookup"><span data-stu-id="e5594-131">Edit this file by adding the appropriate [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="e5594-132">Určit, že <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> se použije [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) směrnice pro automatickou konfiguraci koncového bodu ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="e5594-132">Specify that the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is to be used in the [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive to automatically configure an ASP.NET AJAX endpoint.</span></span>  
  
    ```  
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.MusicService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
## <a name="to-call-the-service"></a><span data-ttu-id="e5594-133">Volání služby</span><span class="sxs-lookup"><span data-stu-id="e5594-133">To call the service</span></span>  
  
1. <span data-ttu-id="e5594-134">Operace GET vaší služby bez žádný kód klienta, můžete otestovat pomocí prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="e5594-134">You can test your service's GET operations without any client code, by using the browser.</span></span> <span data-ttu-id="e5594-135">Například, pokud vaše služba je nakonfigurována na `http://example.com/service.svc` adresu zadáním `http://example.com/service.svc/LookUpArtist?album=SomeAlbum` do prohlížeče adresa vyvolá službu a způsobí, že odpověď na stažení nebo zobrazení.</span><span class="sxs-lookup"><span data-stu-id="e5594-135">For example, if your service is configured at the `http://example.com/service.svc` address, then typing `http://example.com/service.svc/LookUpArtist?album=SomeAlbum` into the browser address bar invokes the service and causes the response to be downloaded or displayed.</span></span>
  
2. <span data-ttu-id="e5594-136">Služby můžete použít s operacemi GET stejným způsobem jako jiné služby technologie ASP.NET AJAX – tak, že zadáte službu ovládací prvek adresy URL do kolekce skriptů správce skriptů AJAX technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e5594-136">You can use services with GET operations in the same way as any other ASP.NET AJAX services - by entering the service URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="e5594-137">Příklad najdete v tématu [základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md).</span><span class="sxs-lookup"><span data-stu-id="e5594-137">For an example, see the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e5594-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e5594-138">See also</span></span>

- [<span data-ttu-id="e5594-139">Vytváření služeb WCF pro ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="e5594-139">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [<span data-ttu-id="e5594-140">Postupy: Migrace s povoleným AJAX webových služeb ASP.NET na WCF</span><span class="sxs-lookup"><span data-stu-id="e5594-140">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
