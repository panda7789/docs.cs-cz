---
title: 'Postupy: Volba mezi žádostmi HTTP POST a HTTP GET u koncových bodů ASP.NET AJAX'
ms.date: 03/30/2017
ms.assetid: b47de82a-4c92-4af6-bceb-a5cb8bb8ede9
ms.openlocfilehash: 0f7a221d1fd14b4a978683f008858e35cbd2df19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184759"
---
# <a name="how-to-choose-between-http-post-and-http-get-requests-for-aspnet-ajax-endpoints"></a><span data-ttu-id="a3db5-102">Postupy: Volba mezi žádostmi HTTP POST a HTTP GET u koncových bodů ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="a3db5-102">How to: Choose between HTTP POST and HTTP GET requests for ASP.NET AJAX Endpoints</span></span>

<span data-ttu-id="a3db5-103">Windows Communication Foundation (WCF) umožňuje vytvořit službu, která zveřejňuje koncový bod s podporou ASP.NET AJAX, který lze volat z Jazyka JavaScript na klientském webu.</span><span class="sxs-lookup"><span data-stu-id="a3db5-103">Windows Communication Foundation (WCF) allows you to create a service that exposes an ASP.NET AJAX-enabled endpoint that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="a3db5-104">Základní postupy pro vytváření těchto služeb je popsána v [Postup: Použití konfigurace přidat ASP.NET koncový bod AJAX](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) a [jak: Přidat ASP.NET koncový bod AJAX bez použití konfigurace](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="a3db5-104">The basic procedures for building such services is discussed in [How to: Use Configuration to Add an ASP.NET AJAX Endpoint](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md) and [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
 <span data-ttu-id="a3db5-105">ASP.NET AJAX podporuje operace, které používají http post a HTTP GET slovesa, s HTTP POST je výchozí.</span><span class="sxs-lookup"><span data-stu-id="a3db5-105">ASP.NET AJAX supports operations that use the HTTP POST and HTTP GET verbs, with HTTP POST being the default.</span></span> <span data-ttu-id="a3db5-106">Při vytváření operace, která nemá žádné vedlejší účinky a vrátí data, která zřídka nebo nikdy nezmění, použijte HTTP GET místo.</span><span class="sxs-lookup"><span data-stu-id="a3db5-106">When creating an operation that has no side effects and returns data that rarely or never changes, use HTTP GET instead.</span></span> <span data-ttu-id="a3db5-107">Výsledky operací GET lze uložit do mezipaměti, což znamená, že více volání stejné operace může mít za následek pouze jeden požadavek na vaši službu.</span><span class="sxs-lookup"><span data-stu-id="a3db5-107">Results of GET operations can be cached, which means that multiple calls to the same operation may result in only one request to your service.</span></span> <span data-ttu-id="a3db5-108">Ukládání do mezipaměti není provedeno WCF, ale může probíhat na libovolné úrovni (v prohlížeči uživatele, na proxy serveru a na jiných úrovních.) Ukládání do mezipaměti je výhodné, pokud chcete zvýšit výkon služby, ale nemusí být přijatelné, pokud se data často mění nebo pokud operace provede nějakou akci.</span><span class="sxs-lookup"><span data-stu-id="a3db5-108">The caching is not done by WCF but can take place at any level (in a user's browser, on a proxy server, and other levels.) Caching is advantageous if you want to increase service performance, but may not be acceptable if data changes frequently or if the operation performs some action.</span></span>  
  
 <span data-ttu-id="a3db5-109">Například pokud navrhujete službu pro správu hudební knihovny uživatele, operace, která vyhledá umělce na základě názvu alba výhody z použití GET, ale operace, která přidá album do osobní kolekce uživatele musí používat POST.</span><span class="sxs-lookup"><span data-stu-id="a3db5-109">For example, if you are designing service to manage a user's music library, an operation that looks up the artist based on an album's title benefits from using GET, but an operation that adds an album to the user's personal collection must use POST.</span></span>  
  
 <span data-ttu-id="a3db5-110">Chcete-li řídit životnost mezipaměti, použijte <xref:System.ServiceModel.Web.OutgoingWebResponseContext> typ.</span><span class="sxs-lookup"><span data-stu-id="a3db5-110">To control the lifetime of the cache, use the <xref:System.ServiceModel.Web.OutgoingWebResponseContext> type.</span></span> <span data-ttu-id="a3db5-111">Například při navrhování služby, která vrací předpovědi počasí aktualizovány každou hodinu, byste použít GET, ale omezit dobu trvání mezipaměti na hodinu nebo méně, aby se zabránilo uživatelům služby v přístupu k zastaralým datům.</span><span class="sxs-lookup"><span data-stu-id="a3db5-111">For example, when designing a service that returns weather forecasts updated hourly, you would use GET but limit the cache duration to an hour or less to prevent the users of the service from accessing stale data.</span></span>  
  
 <span data-ttu-id="a3db5-112">Při použití služeb ze stránky ASP.NET AJAX, které používají ovládací prvek Správce skriptů, je jedno, zda operace používá GET nebo POST - mechanismus správce skriptů zajišťuje, že je vydán správný typ požadavku.</span><span class="sxs-lookup"><span data-stu-id="a3db5-112">When using services from an ASP.NET AJAX page that use the Script Manager control, it makes no difference whether the operation uses GET or POST - the script manager mechanism ensures that the correct request type is issued.</span></span>  
  
 <span data-ttu-id="a3db5-113">Operace HTTP GET používají všechny vstupní parametry podporované operacemi POST, včetně typů složitých datových kontraktů.</span><span class="sxs-lookup"><span data-stu-id="a3db5-113">HTTP GET operations use any input parameters supported by POST operations, including complex data contract types.</span></span> <span data-ttu-id="a3db5-114">Ve většině případů se však doporučuje vyhnout se příliš mnoha parametrům nebo parametrům, které jsou v operacích GET příliš složité, protože snižují efektivitu ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="a3db5-114">However, in most cases it is recommended to avoid too many parameters or parameters that are too complex in GET operations because it reduces caching efficiency.</span></span>  
  
 <span data-ttu-id="a3db5-115">Toto téma ukazuje, jak vybrat mezi <xref:System.ServiceModel.Web.WebGetAttribute> GET <xref:System.ServiceModel.Web.WebInvokeAttribute> a POST přidáním atributů nebo do příslušných operací v servisní smlouvě.</span><span class="sxs-lookup"><span data-stu-id="a3db5-115">This topic demonstrates how to select between GET and POST by adding the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes to the relevant operations in the service contract.</span></span> <span data-ttu-id="a3db5-116">Další kroky (k implementaci, konfiguraci a hostování služby), které jsou nutné k získání služby běží jsou podobné těm, které používají všechny ASP.NET služby AJAX v WCF.</span><span class="sxs-lookup"><span data-stu-id="a3db5-116">The other steps (to implement, configure and host the service) that are required to get the service running are similar to those used by any ASP.NET AJAX service in WCF.</span></span>  
  
 <span data-ttu-id="a3db5-117">Operace označená <xref:System.ServiceModel.Web.WebGetAttribute> vždy používá požadavek GET.</span><span class="sxs-lookup"><span data-stu-id="a3db5-117">An operation marked with the <xref:System.ServiceModel.Web.WebGetAttribute> always uses a GET request.</span></span> <span data-ttu-id="a3db5-118">Operace označená <xref:System.ServiceModel.Web.WebInvokeAttribute>nebo neoznačená žádným ze dvou atributů používá požadavek POST.</span><span class="sxs-lookup"><span data-stu-id="a3db5-118">An operation marked with the <xref:System.ServiceModel.Web.WebInvokeAttribute>, or not marked with any of the two attributes, uses a POST request.</span></span> <span data-ttu-id="a3db5-119">Umožňuje <xref:System.ServiceModel.Web.WebInvokeAttribute> použití jiných http slovesa, jiné než GET a POST (například PUT a DELETE) prostřednictvím vlastnosti. <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A></span><span class="sxs-lookup"><span data-stu-id="a3db5-119">The <xref:System.ServiceModel.Web.WebInvokeAttribute> allows the use of other HTTP verbs, other than GET and POST (such as PUT and DELETE) through the <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> property.</span></span> <span data-ttu-id="a3db5-120">Tato slovesa však nejsou podporovány ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="a3db5-120">However, these verbs are not supported by ASP.NET AJAX.</span></span> <span data-ttu-id="a3db5-121">Pokud máte v úmyslu použít službu z ASP.NET stránek pomocí <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> ovládacího prvku Správce skriptů, nepoužívejte vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a3db5-121">If you intend to use the service from ASP.NET pages using the Script Manager control, do not use the <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> property.</span></span>  
  
 <span data-ttu-id="a3db5-122">Pracovní příklad přechodu na GET, naleznete základní [AJAX service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="a3db5-122">For a working example of switching to GET, see the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>  
  
 <span data-ttu-id="a3db5-123">Ukázka, která používá POST, naleznete [v ajax služby pomocí http post](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) ukázku.</span><span class="sxs-lookup"><span data-stu-id="a3db5-123">For a sample that uses POST, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) sample.</span></span>  
  
## <a name="to-create-a-wcf-service-that-responds-to-http-get-or-http-post-requests"></a><span data-ttu-id="a3db5-124">Vytvoření služby WCF, která reaguje na požadavky HTTP GET nebo HTTP POST</span><span class="sxs-lookup"><span data-stu-id="a3db5-124">To create a WCF service that responds to HTTP GET or HTTP POST requests</span></span>
  
1. <span data-ttu-id="a3db5-125">Definujte základní servisní smlouvu WCF <xref:System.ServiceModel.ServiceContractAttribute> s rozhraním označeným atributem.</span><span class="sxs-lookup"><span data-stu-id="a3db5-125">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="a3db5-126">Každou operaci označte pomocí <xref:System.ServiceModel.OperationContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="a3db5-126">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="a3db5-127">Přidejte <xref:System.ServiceModel.Web.WebGetAttribute> atribut a stanovte, že operace by měla odpovídat na požadavky HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="a3db5-127">Add the <xref:System.ServiceModel.Web.WebGetAttribute> attribute to stipulate that an operation should respond to HTTP GET requests.</span></span> <span data-ttu-id="a3db5-128">Můžete také přidat <xref:System.ServiceModel.Web.WebInvokeAttribute> atribut explicitně určit HTTP POST, nebo ne zadat atribut, který výchozí http post.</span><span class="sxs-lookup"><span data-stu-id="a3db5-128">You can also add the <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute to explicitly specify HTTP POST, or not specify an attribute, which defaults to HTTP POST.</span></span>
  
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
  
2. <span data-ttu-id="a3db5-129">Dokončujte `IMusicService` `MusicService`servisní smlouvu s .</span><span class="sxs-lookup"><span data-stu-id="a3db5-129">Implement the `IMusicService` service contract with a `MusicService`.</span></span>
  
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
  
3. <span data-ttu-id="a3db5-130">Vytvořte nový soubor s názvem služby s příponou SVC v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a3db5-130">Create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="a3db5-131">Upravte tento soubor [ \@](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) přidáním příslušných informací směrnice ServiceHost pro službu.</span><span class="sxs-lookup"><span data-stu-id="a3db5-131">Edit this file by adding the appropriate [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="a3db5-132">Určete, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> že má být použit v [ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) směrnice automaticky konfigurovat koncový bod ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="a3db5-132">Specify that the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is to be used in the [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive to automatically configure an ASP.NET AJAX endpoint.</span></span>  
  
    ```
    <%@ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Ajax.Samples.MusicService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
## <a name="to-call-the-service"></a><span data-ttu-id="a3db5-133">Chcete-li volat službu</span><span class="sxs-lookup"><span data-stu-id="a3db5-133">To call the service</span></span>  
  
1. <span data-ttu-id="a3db5-134">Pomocí prohlížeče můžete otestovat operace GET vaší služby bez kódu klienta.</span><span class="sxs-lookup"><span data-stu-id="a3db5-134">You can test your service's GET operations without any client code, by using the browser.</span></span> <span data-ttu-id="a3db5-135">Pokud je například vaše služba `http://example.com/service.svc` nakonfigurována `http://example.com/service.svc/LookUpArtist?album=SomeAlbum` na adrese, potom zadáním do adresního řádku prohlížeče vyvolá službu a způsobí, že odpověď bude stažena nebo zobrazena.</span><span class="sxs-lookup"><span data-stu-id="a3db5-135">For example, if your service is configured at the `http://example.com/service.svc` address, then typing `http://example.com/service.svc/LookUpArtist?album=SomeAlbum` into the browser address bar invokes the service and causes the response to be downloaded or displayed.</span></span>
  
2. <span data-ttu-id="a3db5-136">Služby s operacemi GET můžete používat stejným způsobem jako všechny ostatní služby ASP.NET AJAX – zadáním adresy URL služby do kolekce Skripty ASP.NET ovládacího prvku AJAX Script Manager.</span><span class="sxs-lookup"><span data-stu-id="a3db5-136">You can use services with GET operations in the same way as any other ASP.NET AJAX services - by entering the service URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="a3db5-137">Příklad naleznete v části [Základní služba AJAX](../../../../docs/framework/wcf/samples/basic-ajax-service.md).</span><span class="sxs-lookup"><span data-stu-id="a3db5-137">For an example, see the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a3db5-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="a3db5-138">See also</span></span>

- [<span data-ttu-id="a3db5-139">Vytváření služeb WCF pro ASP.NET AJAX</span><span class="sxs-lookup"><span data-stu-id="a3db5-139">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [<span data-ttu-id="a3db5-140">Postupy: Migrace webových služeb ASP.NET s podporou AJAXu na službu WCF</span><span class="sxs-lookup"><span data-stu-id="a3db5-140">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
