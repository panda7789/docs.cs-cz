---
title: 'Postupy: Volba mezi žádostmi HTTP POST a HTTP GET u koncových bodů ASP.NET AJAX'
ms.date: 03/30/2017
ms.assetid: b47de82a-4c92-4af6-bceb-a5cb8bb8ede9
ms.openlocfilehash: 6de32c798e7d0db5ad2d8f6666d6c5d1714250d5
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991569"
---
# <a name="how-to-choose-between-http-post-and-http-get-requests-for-aspnet-ajax-endpoints"></a><span data-ttu-id="1dea7-102">Postupy: Volba mezi žádostmi HTTP POST a HTTP GET u koncových bodů ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="1dea7-102">How to: Choose between HTTP POST and HTTP GET requests for ASP.NET AJAX Endpoints</span></span>

<span data-ttu-id="1dea7-103">Windows Communication Foundation (WCF) umožňuje vytvořit službu, která zveřejňuje koncový bod s povoleným ASP.NET AJAX, který se dá volat z JavaScriptu na klientském webu.</span><span class="sxs-lookup"><span data-stu-id="1dea7-103">Windows Communication Foundation (WCF) allows you to create a service that exposes an ASP.NET AJAX-enabled endpoint that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="1dea7-104">Základní postupy pro vytváření takových služeb jsou popsány [v tématu Postupy: Pomocí konfigurace přidejte koncový bod](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) ASP.NET AJAX a [postup: Přidejte koncový bod ASP.NET AJAX bez použití konfigurace](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="1dea7-104">The basic procedures for building such services is discussed in [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) and [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
 <span data-ttu-id="1dea7-105">ASP.NET AJAX podporuje operace, které používají příkazy HTTP POST a HTTP GET, přičemž HTTP POST je výchozí.</span><span class="sxs-lookup"><span data-stu-id="1dea7-105">ASP.NET AJAX supports operations that use the HTTP POST and HTTP GET verbs, with HTTP POST being the default.</span></span> <span data-ttu-id="1dea7-106">Při vytváření operace, která nemá žádné vedlejší účinky, a vrátí data, která se zřídka nebo nikdy nemění, použijte místo toho HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="1dea7-106">When creating an operation that has no side effects and returns data that rarely or never changes, use HTTP GET instead.</span></span> <span data-ttu-id="1dea7-107">Výsledky operací GET lze ukládat do mezipaměti, což znamená, že více volání stejné operace může mít za následek pouze jeden požadavek na vaši službu.</span><span class="sxs-lookup"><span data-stu-id="1dea7-107">Results of GET operations can be cached, which means that multiple calls to the same operation may result in only one request to your service.</span></span> <span data-ttu-id="1dea7-108">Služba WCF neprovádí ukládání do mezipaměti, ale může probíhat na libovolné úrovni (v prohlížeči uživatele, na proxy server a na jiných úrovních.) Ukládání do mezipaměti je výhodné, pokud chcete zvýšit výkon služby, ale nemusí být přijatelné, pokud se data často mění nebo pokud operace provádí určitou akci.</span><span class="sxs-lookup"><span data-stu-id="1dea7-108">The caching is not done by WCF but can take place at any level (in a user's browser, on a proxy server, and other levels.) Caching is advantageous if you want to increase service performance, but may not be acceptable if data changes frequently or if the operation performs some action.</span></span>  
  
 <span data-ttu-id="1dea7-109">Například pokud navrhujete službu pro správu hudební knihovny uživatele, operace, která vyhledá interpreta v závislosti na názvu alba, je výhodná pro použití GET, ale operace, která přidá album do osobní kolekce uživatele, musí používat POST.</span><span class="sxs-lookup"><span data-stu-id="1dea7-109">For example, if you are designing service to manage a user's music library, an operation that looks up the artist based on an album's title benefits from using GET, but an operation that adds an album to the user's personal collection must use POST.</span></span>  
  
 <span data-ttu-id="1dea7-110">Chcete-li řídit dobu života mezipaměti, použijte <xref:System.ServiceModel.Web.OutgoingWebResponseContext> typ.</span><span class="sxs-lookup"><span data-stu-id="1dea7-110">To control the lifetime of the cache, use the <xref:System.ServiceModel.Web.OutgoingWebResponseContext> type.</span></span> <span data-ttu-id="1dea7-111">Například při navrhování služby, která vrátí každou hodinu aktualizovanou předpověď počasí, byste měli použít možnost získat, ale omezit dobu trvání mezipaměti na hodinu nebo méně, aby uživatelé služby nemohli přistupovat k zastaralým datům.</span><span class="sxs-lookup"><span data-stu-id="1dea7-111">For example, when designing a service that returns weather forecasts updated hourly, you would use GET but limit the cache duration to an hour or less to prevent the users of the service from accessing stale data.</span></span>  
  
 <span data-ttu-id="1dea7-112">Při používání služeb ze stránky ASP.NET AJAX, která používá ovládací prvek Správce skriptů, neprovede žádný rozdíl bez ohledu na to, zda operace používá funkci GET nebo POST – mechanismus správce skriptu zajišťuje, aby byl vydán správný typ žádosti.</span><span class="sxs-lookup"><span data-stu-id="1dea7-112">When using services from an ASP.NET AJAX page that use the Script Manager control, it makes no difference whether the operation uses GET or POST - the script manager mechanism ensures that the correct request type is issued.</span></span>  
  
 <span data-ttu-id="1dea7-113">Operace HTTP GET používají všechny vstupní parametry, které podporuje operace POST, včetně složitých typů kontraktů dat.</span><span class="sxs-lookup"><span data-stu-id="1dea7-113">HTTP GET operations use any input parameters supported by POST operations, including complex data contract types.</span></span> <span data-ttu-id="1dea7-114">Ve většině případů se ale doporučuje vyhnout se příliš mnoha parametrům nebo parametrům, které jsou příliš složité v operacích GET, protože se snižuje efektivita ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="1dea7-114">However, in most cases it is recommended to avoid too many parameters or parameters that are too complex in GET operations because it reduces caching efficiency.</span></span>  
  
 <span data-ttu-id="1dea7-115">Toto téma ukazuje, jak vybrat mezi GET a post přidáním <xref:System.ServiceModel.Web.WebGetAttribute> atributů nebo <xref:System.ServiceModel.Web.WebInvokeAttribute> do relevantních operací v kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="1dea7-115">This topic demonstrates how to select between GET and POST by adding the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes to the relevant operations in the service contract.</span></span> <span data-ttu-id="1dea7-116">Ostatní kroky (k implementaci, konfiguraci a hostování služby), které jsou potřeba k tomu, aby služba běžela, jsou podobné těm, které používá služba ASP.NET AJAX ve službě WCF.</span><span class="sxs-lookup"><span data-stu-id="1dea7-116">The other steps (to implement, configure and host the service) that are required to get the service running are similar to those used by any ASP.NET AJAX service in WCF.</span></span>  
  
 <span data-ttu-id="1dea7-117">Operace označená pomocí <xref:System.ServiceModel.Web.WebGetAttribute> vždy používá požadavek GET.</span><span class="sxs-lookup"><span data-stu-id="1dea7-117">An operation marked with the <xref:System.ServiceModel.Web.WebGetAttribute> always uses a GET request.</span></span> <span data-ttu-id="1dea7-118">Operace označená pomocí <xref:System.ServiceModel.Web.WebInvokeAttribute>, nebo není označená žádným z těchto dvou atributů, používá požadavek POST.</span><span class="sxs-lookup"><span data-stu-id="1dea7-118">An operation marked with the <xref:System.ServiceModel.Web.WebInvokeAttribute>, or not marked with any of the two attributes, uses a POST request.</span></span> <span data-ttu-id="1dea7-119">Umožňuje použít jiné příkazy HTTP, než Get a post (například PUT a Delete) <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> prostřednictvím vlastnosti. <xref:System.ServiceModel.Web.WebInvokeAttribute></span><span class="sxs-lookup"><span data-stu-id="1dea7-119">The <xref:System.ServiceModel.Web.WebInvokeAttribute> allows the use of other HTTP verbs, other than GET and POST (such as PUT and DELETE) through the <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> property.</span></span> <span data-ttu-id="1dea7-120">Nicméně ASP.NET AJAX nepodporuje tyto příkazy.</span><span class="sxs-lookup"><span data-stu-id="1dea7-120">However, these verbs are not supported by ASP.NET AJAX.</span></span> <span data-ttu-id="1dea7-121">Pokud máte v úmyslu používat službu ze stránek ASP.NET pomocí ovládacího prvku Správce skriptů, nepoužívejte <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1dea7-121">If you intend to use the service from ASP.NET pages using the Script Manager control, do not use the <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> property.</span></span>  
  
 <span data-ttu-id="1dea7-122">Pracovní příklad přepínání na získání najdete v ukázce [základní služby AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md) .</span><span class="sxs-lookup"><span data-stu-id="1dea7-122">For a working example of switching to GET, see the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>  
  
 <span data-ttu-id="1dea7-123">Ukázku, která používá POST, najdete v ukázce [služby AJAX pomocí protokolu HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) .</span><span class="sxs-lookup"><span data-stu-id="1dea7-123">For a sample that uses POST, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) sample.</span></span>  
  
## <a name="to-create-a-wcf-service-that-responds-to-http-get-or-http-post-requests"></a><span data-ttu-id="1dea7-124">Vytvoření služby WCF, která reaguje na požadavky HTTP GET nebo HTTP POST</span><span class="sxs-lookup"><span data-stu-id="1dea7-124">To create a WCF service that responds to HTTP GET or HTTP POST requests</span></span>
  
1. <span data-ttu-id="1dea7-125">Definujte základní kontrakt služby WCF s rozhraním označeným <xref:System.ServiceModel.ServiceContractAttribute> atributem.</span><span class="sxs-lookup"><span data-stu-id="1dea7-125">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="1dea7-126">Označte každou operaci pomocí <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="1dea7-126">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="1dea7-127"><xref:System.ServiceModel.Web.WebGetAttribute> Přidejte atribut, který stanoví, že operace by měla reagovat na požadavky HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="1dea7-127">Add the <xref:System.ServiceModel.Web.WebGetAttribute> attribute to stipulate that an operation should respond to HTTP GET requests.</span></span> <span data-ttu-id="1dea7-128">Můžete také přidat <xref:System.ServiceModel.Web.WebInvokeAttribute> atribut pro explicitní určení http post nebo Neurčovat atribut, který má výchozí hodnotu http post.</span><span class="sxs-lookup"><span data-stu-id="1dea7-128">You can also add the <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute to explicitly specify HTTP POST, or not specify an attribute, which defaults to HTTP POST.</span></span>
  
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
  
2. <span data-ttu-id="1dea7-129">Implementujte kontrakt `MusicService`služby s. `IMusicService`</span><span class="sxs-lookup"><span data-stu-id="1dea7-129">Implement the `IMusicService` service contract with a `MusicService`.</span></span>
  
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
  
3. <span data-ttu-id="1dea7-130">V aplikaci vytvořte nový soubor s názvem služba s příponou. svc.</span><span class="sxs-lookup"><span data-stu-id="1dea7-130">Create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="1dea7-131">Upravte tento soubor přidáním příslušné [ \@](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) informace o direktivě ServiceHost pro službu.</span><span class="sxs-lookup"><span data-stu-id="1dea7-131">Edit this file by adding the appropriate [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="1dea7-132">Určete, že <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> se má použít [ \@](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) v direktivě ServiceHost k automatické konfiguraci koncového bodu ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="1dea7-132">Specify that the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is to be used in the [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive to automatically configure an ASP.NET AJAX endpoint.</span></span>  
  
    ```
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.MusicService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
## <a name="to-call-the-service"></a><span data-ttu-id="1dea7-133">Volání služby</span><span class="sxs-lookup"><span data-stu-id="1dea7-133">To call the service</span></span>  
  
1. <span data-ttu-id="1dea7-134">Pomocí prohlížeče můžete testovat operace GET vaší služby bez jakéhokoli klientského kódu.</span><span class="sxs-lookup"><span data-stu-id="1dea7-134">You can test your service's GET operations without any client code, by using the browser.</span></span> <span data-ttu-id="1dea7-135">Například pokud je vaše služba nakonfigurovaná na `http://example.com/service.svc` adrese, pak se zadáním `http://example.com/service.svc/LookUpArtist?album=SomeAlbum` do panelu Adresa prohlížeče vyvolá služba a dojde ke stažení nebo zobrazení odpovědi.</span><span class="sxs-lookup"><span data-stu-id="1dea7-135">For example, if your service is configured at the `http://example.com/service.svc` address, then typing `http://example.com/service.svc/LookUpArtist?album=SomeAlbum` into the browser address bar invokes the service and causes the response to be downloaded or displayed.</span></span>
  
2. <span data-ttu-id="1dea7-136">Služby s operacemi GET můžete používat stejným způsobem jako jakékoli jiné ASP.NET služby AJAX – zadáním adresy URL služby do kolekce Scripts v ovládacím prvku Správce skriptů ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="1dea7-136">You can use services with GET operations in the same way as any other ASP.NET AJAX services - by entering the service URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="1dea7-137">Příklad naleznete v tématu [základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md).</span><span class="sxs-lookup"><span data-stu-id="1dea7-137">For an example, see the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1dea7-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1dea7-138">See also</span></span>

- [<span data-ttu-id="1dea7-139">Vytváření služeb WCF pro ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="1dea7-139">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [<span data-ttu-id="1dea7-140">Postupy: Migrace webových služeb ASP.NET s podporou jazyka AJAX do WCF</span><span class="sxs-lookup"><span data-stu-id="1dea7-140">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
