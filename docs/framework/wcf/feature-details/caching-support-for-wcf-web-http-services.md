---
title: "Podpora ukládání dat do mezipaměti pro webové HTTP služby WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7f8078e0-00d9-415c-b8ba-c1b6d5c31799
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a4dd96f444d6405022a0a812a55a92cec1052fbb
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="caching-support-for-wcf-web-http-services"></a><span data-ttu-id="4dce7-102">Podpora ukládání dat do mezipaměti pro webové HTTP služby WCF</span><span class="sxs-lookup"><span data-stu-id="4dce7-102">Caching Support for WCF Web HTTP Services</span></span>
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="4dce7-103">umožňuje používat deklarativní ukládání do mezipaměti mechanismus, který je již k dispozici v technologii ASP.NET v službách WCF Web HTTP.</span><span class="sxs-lookup"><span data-stu-id="4dce7-103"> enables you to use the declarative caching mechanism already available in ASP.NET in your WCF Web HTTP services.</span></span> <span data-ttu-id="4dce7-104">To vám umožní do mezipaměti odpovědi z vaší operací služby WCF Web HTTP.</span><span class="sxs-lookup"><span data-stu-id="4dce7-104">This allows you to cache responses from your WCF Web HTTP service operations.</span></span> <span data-ttu-id="4dce7-105">Když uživatel odešle do služby, který je nakonfigurován pro ukládání do mezipaměti GET protokolu HTTP, ASP.NET zašle zpět odpověď uložená v mezipaměti a není volána metoda služby.</span><span class="sxs-lookup"><span data-stu-id="4dce7-105">When a user sends an HTTP GET to your service that is configured for caching, ASP.NET sends back the cached response and the service method is not called.</span></span> <span data-ttu-id="4dce7-106">Když vyprší platnost mezipaměti, při příštím uživatel odešle HTTP GET, se nazývá metodu služby a ještě jednou do mezipaměti odpovědi.</span><span class="sxs-lookup"><span data-stu-id="4dce7-106">When the cache expires, the next time a user sends an HTTP GET, your service method is called and the response is once again cached.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="4dce7-107">Ukládání do mezipaměti, ASP.NET, najdete v části [přehled ukládání do mezipaměti technologie ASP.NET](http://go.microsoft.com/fwlink/?LinkId=152534)</span><span class="sxs-lookup"><span data-stu-id="4dce7-107"> ASP.NET caching, see [ASP.NET Caching Overview](http://go.microsoft.com/fwlink/?LinkId=152534)</span></span>  
  
## <a name="basic-web-http-service-caching"></a><span data-ttu-id="4dce7-108">Základní webové služby HTTP ukládání do mezipaměti</span><span class="sxs-lookup"><span data-stu-id="4dce7-108">Basic Web HTTP Service Caching</span></span>  
 <span data-ttu-id="4dce7-109">Povolit HTTP webové služby ukládání do mezipaměti je třeba nejprve povolit režim kompatibility ASP.NET použitím <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> na nastavení služby <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> k <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> nebo <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>.</span><span class="sxs-lookup"><span data-stu-id="4dce7-109">To enable WEB HTTP service caching you must first enable ASP.NET compatibility by applying the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> to the service setting <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> to <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> or <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>.</span></span>  
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)]<span data-ttu-id="4dce7-110">zavádí nový atribut názvem <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> , můžete zadat název profilu mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="4dce7-110"> introduces a new attribute called <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> that allows you to specify a cache profile name.</span></span> <span data-ttu-id="4dce7-111">Tento atribut se používá pro operaci služby.</span><span class="sxs-lookup"><span data-stu-id="4dce7-111">This attribute is applied to a service operation.</span></span> <span data-ttu-id="4dce7-112">Následující příklad se vztahuje <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> službě povolit režim kompatibility ASP.NET a nakonfiguruje `GetCustomer` operace pro ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="4dce7-112">The following example applies the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> to a service to enable ASP.NET compatibility and configures the `GetCustomer` operation for caching.</span></span> <span data-ttu-id="4dce7-113"><!--zz<xref:System.ServiceModel.Activation.AspNetCacheProfileAttribute>--> `System.ServiceModel.Activation.AspNetCacheProfileAttribute` Atribut určuje profil mezipaměti, který obsahuje nastavení mezipaměti, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="4dce7-113">The <!--zz<xref:System.ServiceModel.Activation.AspNetCacheProfileAttribute>--> `System.ServiceModel.Activation.AspNetCacheProfileAttribute` attribute specifies a cache profile that contains the cache settings to be used.</span></span>  
  
```csharp
[ServiceContract] AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]
public class Service
{
    [WebGet(UriTemplate = "{id}")]
    [AspNetCacheProfile("CacheFor60Seconds")]
    public Customer GetCustomer(string id)
    {
        // ...
    }
}
```  
  
 <span data-ttu-id="4dce7-114">Také je potřeba zapnout režim kompatibility ASP.NET v souboru Web.config, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="4dce7-114">You must also turn on ASP.NET compatibility mode in the Web.config file as shown in the following example.</span></span>  
  
```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```
  
> [!WARNING]
>  <span data-ttu-id="4dce7-115">Pokud není zapnutý režim kompatibility ASP.NET a <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> se používá k výjimce.</span><span class="sxs-lookup"><span data-stu-id="4dce7-115">If ASP.NET compatibility mode is not turned on and the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> is used an exception is thrown.</span></span>  
  
 <span data-ttu-id="4dce7-116">Název profilu mezipaměti určeného <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> identifikuje profil mezipaměti, který je přidán do konfiguračního souboru Web.config.</span><span class="sxs-lookup"><span data-stu-id="4dce7-116">The cache profile name specified by the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> identifies a cache profile that is added to your Web.config configuration file.</span></span> <span data-ttu-id="4dce7-117">Profil mezipaměti je definován s v <`outputCacheSetting`> elementu, jak je znázorněno v následujícím příkladu konfigurace.</span><span class="sxs-lookup"><span data-stu-id="4dce7-117">The cache profile is defined with in a <`outputCacheSetting`> element as shown in the following configuration example.</span></span>  
  
```xml
<!-- ...  -->
<system.web>  
   <caching>  
      <outputCacheSettings>  
         <outputCacheProfiles>  
            <add name="CacheFor60Seconds" duration="60" varyByParam="none" sqlDependency="MyTestDatabase:MyTable"/>  
         </outputCacheProfiles>  
      </outputCacheSettings>  
   </caching>  
   <!-- ... -->  
</system.web>  
```  
  
 <span data-ttu-id="4dce7-118">Toto je stejný element konfigurace, který je k dispozici pro aplikace ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="4dce7-118">This is the same configuration element that is available to ASP.NET applications.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="4dce7-119">Profilech mezipaměti ASP.NET, najdete v tématu <xref:System.Web.Configuration.OutputCacheProfile>.</span><span class="sxs-lookup"><span data-stu-id="4dce7-119"> ASP.NET cache profiles, see <xref:System.Web.Configuration.OutputCacheProfile>.</span></span> <span data-ttu-id="4dce7-120">Webové služby HTTP jsou nejdůležitější atributy v mezipaměti profilu: `cacheDuration` a `varyByParam`.</span><span class="sxs-lookup"><span data-stu-id="4dce7-120">For Web HTTP services, the most important attributes in the cache profile are: `cacheDuration` and `varyByParam`.</span></span> <span data-ttu-id="4dce7-121">Obě tyto atributy se vyžadují.</span><span class="sxs-lookup"><span data-stu-id="4dce7-121">Both of these attributes are required.</span></span> <span data-ttu-id="4dce7-122">`cacheDuration`Nastaví množství času, které do mezipaměti odpovědi v sekundách.</span><span class="sxs-lookup"><span data-stu-id="4dce7-122">`cacheDuration` sets the amount of time a response should be cached in seconds.</span></span> <span data-ttu-id="4dce7-123">`varyByParam`Umožňuje zadat parametr řetězce dotazu, který se používá k odpovědi v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="4dce7-123">`varyByParam` allows you to specify a query string parameter that is used to cache responses.</span></span> <span data-ttu-id="4dce7-124">Všechny požadavky vytvořené s hodnotami parametrů řetězce dotazu jsou samostatně do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="4dce7-124">All requests made with different query string parameter values are cached separately.</span></span> <span data-ttu-id="4dce7-125">Například po počáteční žádosti http://MyServer/MyHttpService/MyOperation?param=10 všechny následné žádosti se stejným identifikátorem URI by vrátit odpověď uložená v mezipaměti (tak dlouho, dokud není uplynul doba uložení do mezipaměti).</span><span class="sxs-lookup"><span data-stu-id="4dce7-125">For example, once an initial request is made to http://MyServer/MyHttpService/MyOperation?param=10 all subsequent requests made with the same URI would be returned the cached response (so long as the cache duration has not elapsed).</span></span> <span data-ttu-id="4dce7-126">V odpovědi na podobné požadavek, který je stejný, ale má jinou hodnotu pro parametr řetězce dotazu parametr samostatně mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="4dce7-126">Responses for a similar request that is the same but has a different value for the parameter query string parameter are cached separately.</span></span> <span data-ttu-id="4dce7-127">Pokud nechcete, aby tento samostatné chování ukládání do mezipaměti, nastavte `varyByParam` na "žádný".</span><span class="sxs-lookup"><span data-stu-id="4dce7-127">If you do not want this separate caching behavior, set `varyByParam` to "none".</span></span>  
  
## <a name="sql-cache-dependency"></a><span data-ttu-id="4dce7-128">Závislost SQL mezipaměti</span><span class="sxs-lookup"><span data-stu-id="4dce7-128">SQL Cache Dependency</span></span>  
 <span data-ttu-id="4dce7-129">Webové HTTP služby odezvy také do mezipaměti se závislostí mezipaměti SQL.</span><span class="sxs-lookup"><span data-stu-id="4dce7-129">Web HTTP service responses can also be cached with a SQL cache dependency.</span></span> <span data-ttu-id="4dce7-130">Pokud vaše webové služby WCF HTTP závisí na data uložená v databázi SQL, můžete ukládat do mezipaměti odpovědi služby a zrušit platnost odpověď uložená v mezipaměti, když data v SQL databázi změny tabulky.</span><span class="sxs-lookup"><span data-stu-id="4dce7-130">If your WCF Web HTTP service depends on data stored in a SQL database, you may want to cache the service's response and invalidate the cached response when data in the SQL database table changes.</span></span> <span data-ttu-id="4dce7-131">Toto chování je úplně nakonfigurován v souboru Web.config.</span><span class="sxs-lookup"><span data-stu-id="4dce7-131">This behavior is configured completely within the Web.config file.</span></span> <span data-ttu-id="4dce7-132">Nejdřív je nutné definovat připojovací řetězec <`connectionStrings`> elementu.</span><span class="sxs-lookup"><span data-stu-id="4dce7-132">You must first define a connection string in the <`connectionStrings`> element.</span></span>  
  
```xml
<connectionStrings>
  <add name="connectString"
       connectionString="Data Source=MyService;Initial Catalog=MyTestDatabase;Integrated Security=True"
       providerName="System.Data.SqlClient" />
</connectionStrings>
```  
  
 <span data-ttu-id="4dce7-133">Pak musíte povolit mezipaměť závislost SQL v rámci <`caching`> v rámci <`system.web`> elementu, jak je znázorněno v následujícím příkladu konfigurace.</span><span class="sxs-lookup"><span data-stu-id="4dce7-133">Then you must enable SQL cache dependency within a <`caching`> element within the <`system.web`> element as shown in the following config example.</span></span>  
  
```xml  
<system.web>
  <caching>
    <sqlCacheDependency enabled="true" pollTime="1000">
      <databases>
        <add name="MyTestDatabase" connectionStringName="connectString" />
      </databases>
    </sqlCacheDependency>
    <!-- ... -->
  </caching>
  <!-- ... -->
</system.web>
```  
  
 <span data-ttu-id="4dce7-134">Zde je povolené závislost SQL mezipaměti a čas dotazování na 1000 milisekund se nastavuje.</span><span class="sxs-lookup"><span data-stu-id="4dce7-134">Here SQL cache dependency is enabled and a polling time of 1000 milliseconds is set.</span></span> <span data-ttu-id="4dce7-135">Pokaždé, když uplyne časový dotazování tabulky databáze je kontrola aktualizací.</span><span class="sxs-lookup"><span data-stu-id="4dce7-135">Each time the polling time elapses the database table is checked for updates.</span></span> <span data-ttu-id="4dce7-136">Pokud byly zjištěny změny obsahu mezipaměti, se odeberou a další čas, kdy operace služby je volána novou odpověď se uloží do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="4dce7-136">If changes are detected the contents of the cache are removed and the next time the service operation is invoked a new response is cached.</span></span> <span data-ttu-id="4dce7-137">V rámci <`sqlCacheDependency`> elementu přidejte databáze a odkazovat na připojovací řetězce v rámci <`databases`> elementu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="4dce7-137">Within the <`sqlCacheDependency`> element add the databases and reference the connection strings within the <`databases`> element as shown in the following example.</span></span>  
  
```xml  
<system.web>
  <caching>
    <sqlCacheDependency enabled="true" pollTime="1000">
      <databases>
        <add name="MyTestDatabase" connectionStringName="connectString" />
      </databases>  
    </sqlCacheDependency>  
    <!-- ... -->  
  </caching>  
  <!-- ... -->  
</system.web>  
```  
  
 <span data-ttu-id="4dce7-138">Dále musíte nakonfigurovat nastavení výstupní mezipaměti v rámci <`caching`> elementu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="4dce7-138">Next you must configure the output cache settings within the <`caching`> element as shown in the following example.</span></span>  
  
```xml
<system.web>
  <caching>  
    <!-- ...  -->
    <outputCacheSettings>
      <outputCacheProfiles>
        <add name="CacheFor60Seconds" duration="60" varyByParam="none" sqlDependency="MyTestDatabase:MyTable" />
      </outputCacheProfiles>
    </outputCacheSettings>
  </caching>
  <!-- ... -->
</system.web>
```  
  
 <span data-ttu-id="4dce7-139">Zde je doba uložení do mezipaměti nastavena na 60 sekund, `varyByParam` je nastaven na hodnotu none a `sqlDependency` nastavena na seznam oddělený středníky páry název/tabulky databáze oddělené dvojtečkou.</span><span class="sxs-lookup"><span data-stu-id="4dce7-139">Here the cache duration is set to 60 seconds, `varyByParam` is set to none and `sqlDependency` is set to a semicolon delimited list of database name/table pairs separated by colons.</span></span> <span data-ttu-id="4dce7-140">Pokud data v `MyTable` změní odpovědi v mezipaměti pro operaci služby se odebere a po vyvolání operace novou odpověď je generována (voláním operace služby), do mezipaměti a vrátí klientovi.</span><span class="sxs-lookup"><span data-stu-id="4dce7-140">When data in `MyTable` is changed the cached response for the service operation is removed and when the operation is invoked a new response is generated (by calling the service operation), cached, and returned to the client.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4dce7-141">Pro technologii ASP.NET pro přístup k databázi SQL, je nutné použít [nástroj registrace serveru SQL Server ASP.NET](http://go.microsoft.com/fwlink/?LinkId=152536).</span><span class="sxs-lookup"><span data-stu-id="4dce7-141">For ASP.NET to access a SQL database, you must use the [ASP.NET SQL Server Registration Tool](http://go.microsoft.com/fwlink/?LinkId=152536).</span></span> <span data-ttu-id="4dce7-142">Kromě toho musíte povolit odpovídající uživatelskému účtu přístup do databáze a tabulky.</span><span class="sxs-lookup"><span data-stu-id="4dce7-142">In addition you must allow the appropriate user account access to the database and table.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="4dce7-143">[Přístup k systému SQL Server z webové aplikace](http://go.microsoft.com/fwlink/?LinkId=178988).</span><span class="sxs-lookup"><span data-stu-id="4dce7-143"> [Accessing SQL Server from a Web Application](http://go.microsoft.com/fwlink/?LinkId=178988).</span></span>  
  
## <a name="conditional-http-get-based-caching"></a><span data-ttu-id="4dce7-144">Podmíněné HTTP GET na základě ukládání do mezipaměti</span><span class="sxs-lookup"><span data-stu-id="4dce7-144">Conditional HTTP GET Based Caching</span></span>  
 <span data-ttu-id="4dce7-145">Ve scénářích Web HTTP podmíněného GET protokolu HTTP se často používá služby k implementaci inteligentního ukládání do mezipaměti protokolu HTTP, jak je popsáno v [specifikace protokolu HTTP](http://go.microsoft.com/fwlink/?LinkId=165800).</span><span class="sxs-lookup"><span data-stu-id="4dce7-145">In Web HTTP scenarios a conditional HTTP GET is often used by services to implement intelligent HTTP caching as described in the [HTTP Specification](http://go.microsoft.com/fwlink/?LinkId=165800).</span></span> <span data-ttu-id="4dce7-146">K tomu službu nutné nastavit hodnotu hlavičky značky ETag v odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="4dce7-146">To do this the service must set the value of the ETag header in the HTTP response.</span></span> <span data-ttu-id="4dce7-147">Je také nutné zkontrolovat hlavičku If-None-Match v požadavku HTTP, zda všechny zadané značky ETag odpovídá aktuální značka ETag.</span><span class="sxs-lookup"><span data-stu-id="4dce7-147">It also must check the If-None-Match header in the HTTP request to see whether any of the ETag specified matches the current ETag.</span></span>  
  
 <span data-ttu-id="4dce7-148">Pro požadavky GET a HEAD <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> přebírá hodnotu ETag a ověří proti hlavičku If-None-Match požadavku.</span><span class="sxs-lookup"><span data-stu-id="4dce7-148">For GET and HEAD requests, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> takes an ETag value and checks it against the If-None-Match header of the request.</span></span> <span data-ttu-id="4dce7-149">Pokud je k dispozici hlavičku a je nalezena shoda, <xref:System.ServiceModel.Web.WebFaultException> s protokolem HTTP je vyvolána stavový kód 304 (upraveno) a hlavičku ETag se přidá do odpovědi s odpovídající značky ETag.</span><span class="sxs-lookup"><span data-stu-id="4dce7-149">If the header is present and there is a match, a <xref:System.ServiceModel.Web.WebFaultException> with a HTTP status code 304 (Not Modified) is thrown and an ETag header is added to the response with the matching ETag.</span></span>  
  
 <span data-ttu-id="4dce7-150">Jedním přetížením <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> metoda přebírá datum poslední změny a ověří proti hlavičku If-upravit-Since požadavku.</span><span class="sxs-lookup"><span data-stu-id="4dce7-150">One overload of the <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> method takes a last modified date and checks it against the If-Modified-Since header of the request.</span></span> <span data-ttu-id="4dce7-151">Pokud je k dispozici záhlaví a prostředek nebyl upraven od, <xref:System.ServiceModel.Web.WebFaultException> pomocí protokolu HTTP je vyvolána stavový kód 304 (upraveno).</span><span class="sxs-lookup"><span data-stu-id="4dce7-151">If the header is present and the resource has not been modified since, a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 304 (Not Modified) is thrown.</span></span>  
  
 <span data-ttu-id="4dce7-152">Pro požadavky PUT, POST a odstranění <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> načítá aktuální hodnotu ETag prostředku.</span><span class="sxs-lookup"><span data-stu-id="4dce7-152">For PUT, POST, and DELETE requests, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> takes the current ETag value of a resource.</span></span> <span data-ttu-id="4dce7-153">Pokud je aktuální hodnota ETag hodnotu null, metoda kontroluje, zda záhlaví If-None-Match má hodnotu "*".</span><span class="sxs-lookup"><span data-stu-id="4dce7-153">If the current ETag value is null, the method checks that the If-None- Match header has a value of "*".</span></span>  <span data-ttu-id="4dce7-154">Pokud je aktuální hodnota ETag není výchozí hodnotu, zkontroluje tato metoda aktuální hodnota ETag proti hlavičku If - Match požadavku.</span><span class="sxs-lookup"><span data-stu-id="4dce7-154">If the current ETag value is not a default value, then the method checks the current ETag value against the If- Match header of the request.</span></span> <span data-ttu-id="4dce7-155">V obou případech vyvolá metoda <xref:System.ServiceModel.Web.WebFaultException> se stavem HTTP code 412 (nezdařil se předběžnou podmínku), pokud očekávaný hlavičky není přítomné v žádosti nebo nevyhovuje podmíněného zkontrolujte jeho hodnotu a nastaví hlavičku ETag odpovědi na aktuální značka ETag hodnota.</span><span class="sxs-lookup"><span data-stu-id="4dce7-155">In either case, the method throws a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 412 (Precondition Failed) if the expected header is not present in the request or its value does not satisfy the conditional check and sets the ETag header of the response to the current ETag value.</span></span>  
  
 <span data-ttu-id="4dce7-156">Obě `CheckConditional` metody a <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> metoda zajišťuje, že značka ETag nastavenou na hlavičku odpovědi na platnou značku ETag podle specifikace protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="4dce7-156">Both the `CheckConditional` methods and the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> method ensures that the ETag value set on the response header is a valid ETag according to the HTTP specification.</span></span> <span data-ttu-id="4dce7-157">To zahrnuje, které obaluje ETag hodnotu do dvojitých uvozovek, pokud již nejsou přítomny a správně uvozovací znaky znaky interní dvojitých uvozovek.</span><span class="sxs-lookup"><span data-stu-id="4dce7-157">This includes surrounding the ETag value in double quotes if they are not already present and properly escaping any internal double quote characters.</span></span> <span data-ttu-id="4dce7-158">Slabé porovnání značka ETag není podporována.</span><span class="sxs-lookup"><span data-stu-id="4dce7-158">Weak ETag comparison is not supported.</span></span>  
  
 <span data-ttu-id="4dce7-159">Následující příklad ukazuje, jak používat tyto metody.</span><span class="sxs-lookup"><span data-stu-id="4dce7-159">The following example shows how to use these methods.</span></span>  
  
```csharp
[WebGet(UriTemplate = "{id}"), Description("Returns the specified customer from customers collection. Returns NotFound if there is no such customer. Supports conditional GET.")]
public Customer GetCustomer(string id)
{
    lock (writeLock)
    {
        // return NotFound if there is no item with the specified id.
        object itemEtag = customerEtags[id];
        if (itemEtag == null)
        {
            throw new WebFaultException(HttpStatusCode.NotFound);
        }
  
        // return NotModified if the client did a conditional GET and the customer item has not changed
        // since when the client last retrieved it
        WebOperationContext.Current.IncomingRequest.CheckConditionalRetrieve((long)itemEtag);
        Customer result = this.customers[id] as Customer;
        
        // set the customer etag before returning the result
        WebOperationContext.Current.OutgoingResponse.SetETag((long)itemEtag);
        return result;
    }
}
```  
  
## <a name="security-considerations"></a><span data-ttu-id="4dce7-160">Důležité informace o zabezpečení</span><span class="sxs-lookup"><span data-stu-id="4dce7-160">Security Considerations</span></span>  
 <span data-ttu-id="4dce7-161">Požadavky, které vyžadují autorizace by neměl mít jejich odpovědi v mezipaměti, protože autorizaci se neprovede, pokud je odpověď obsluhovat z mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="4dce7-161">Requests that require authorization should not have their responses cached, because the authorization is not performed when the response is served from the cache.</span></span>  <span data-ttu-id="4dce7-162">Ukládání do mezipaměti tyto odpovědi by vznikla chyba závažné zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4dce7-162">Caching such responses would introduce a serious security vulnerability.</span></span>  <span data-ttu-id="4dce7-163">Obvykle požadavky, které vyžadují autorizace poskytují uživatelská data a proto není i výhodné ukládání do mezipaměti na straně serveru.</span><span class="sxs-lookup"><span data-stu-id="4dce7-163">Usually, requests that require authorization provide user-specific data and therefore server-side caching is not even beneficial.</span></span>  <span data-ttu-id="4dce7-164">V takových situacích ukládání do mezipaměti na straně klienta nebo jednoduše není ukládání do mezipaměti na všech bude vhodnější.</span><span class="sxs-lookup"><span data-stu-id="4dce7-164">In such situations, client-side caching or simply not caching at all will be more appropriate.</span></span>
