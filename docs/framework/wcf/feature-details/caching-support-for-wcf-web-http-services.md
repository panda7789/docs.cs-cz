---
title: Podpora ukládání dat do mezipaměti pro webové HTTP služby WCF
ms.date: 03/30/2017
ms.assetid: 7f8078e0-00d9-415c-b8ba-c1b6d5c31799
ms.openlocfilehash: 25b564235b5d2b3b26b5d657f3e5f0bd5d594125
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43798596"
---
# <a name="caching-support-for-wcf-web-http-services"></a><span data-ttu-id="30c10-102">Podpora ukládání dat do mezipaměti pro webové HTTP služby WCF</span><span class="sxs-lookup"><span data-stu-id="30c10-102">Caching Support for WCF Web HTTP Services</span></span>
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="30c10-103"> umožňuje používat deklarativní mechanizmus ukládání do mezipaměti, aktuálně k dispozici v ASP.NET ve vašich službách WCF Web HTTP.</span><span class="sxs-lookup"><span data-stu-id="30c10-103"> enables you to use the declarative caching mechanism already available in ASP.NET in your WCF Web HTTP services.</span></span> <span data-ttu-id="30c10-104">To vám umožní do mezipaměti odpovědi z servisní operace webových služeb HTTP WCF.</span><span class="sxs-lookup"><span data-stu-id="30c10-104">This allows you to cache responses from your WCF Web HTTP service operations.</span></span> <span data-ttu-id="30c10-105">Když uživatel odešle do služby, který je nakonfigurovaný pro ukládání do mezipaměti HTTP GET, ASP.NET, odešle zpět odpověď uložená v mezipaměti a není volána metoda služby.</span><span class="sxs-lookup"><span data-stu-id="30c10-105">When a user sends an HTTP GET to your service that is configured for caching, ASP.NET sends back the cached response and the service method is not called.</span></span> <span data-ttu-id="30c10-106">Když vyprší platnost mezipaměti, při příštím uživatel odešle HTTP GET, je volána metoda vaše služby a znovu do mezipaměti odpovědi.</span><span class="sxs-lookup"><span data-stu-id="30c10-106">When the cache expires, the next time a user sends an HTTP GET, your service method is called and the response is once again cached.</span></span> <span data-ttu-id="30c10-107">Další informace o ukládání do mezipaměti ASP.NET najdete v tématu [přehled ukládání do mezipaměti ASP.NET](https://go.microsoft.com/fwlink/?LinkId=152534)</span><span class="sxs-lookup"><span data-stu-id="30c10-107">For more information about ASP.NET caching, see [ASP.NET Caching Overview](https://go.microsoft.com/fwlink/?LinkId=152534)</span></span>  
  
## <a name="basic-web-http-service-caching"></a><span data-ttu-id="30c10-108">Základní webové služby HTTP ukládání do mezipaměti</span><span class="sxs-lookup"><span data-stu-id="30c10-108">Basic Web HTTP Service Caching</span></span>  
 <span data-ttu-id="30c10-109">Povolit webových služeb HTTP služby ukládání do mezipaměti je třeba nejprve povolit režim kompatibility ASP.NET použitím <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> nastavení služby <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> k <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> nebo <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>.</span><span class="sxs-lookup"><span data-stu-id="30c10-109">To enable WEB HTTP service caching you must first enable ASP.NET compatibility by applying the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> to the service setting <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> to <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> or <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>.</span></span>  
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)]<span data-ttu-id="30c10-110"> zavádí nový atribut volá <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> , který umožňuje určit název profilu mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="30c10-110"> introduces a new attribute called <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> that allows you to specify a cache profile name.</span></span> <span data-ttu-id="30c10-111">Tento atribut je použit na operaci služby.</span><span class="sxs-lookup"><span data-stu-id="30c10-111">This attribute is applied to a service operation.</span></span> <span data-ttu-id="30c10-112">Následující příklad se vztahuje <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> na službu a povolte režim kompatibility ASP.NET a nakonfiguruje `GetCustomer` operace pro ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="30c10-112">The following example applies the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> to a service to enable ASP.NET compatibility and configures the `GetCustomer` operation for caching.</span></span> <span data-ttu-id="30c10-113"><!--zz<xref:System.ServiceModel.Activation.AspNetCacheProfileAttribute>--> `System.ServiceModel.Activation.AspNetCacheProfileAttribute` Atribut určuje, který obsahuje nastavení mezipaměti pro použití profilu mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="30c10-113">The <!--zz<xref:System.ServiceModel.Activation.AspNetCacheProfileAttribute>--> `System.ServiceModel.Activation.AspNetCacheProfileAttribute` attribute specifies a cache profile that contains the cache settings to be used.</span></span>  
  
```csharp
[ServiceContract] 
[AspNetCompatibilityRequirements(RequirementsMode=AspNetCompatibilityRequirementsMode.Allowed)]
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
  
 <span data-ttu-id="30c10-114">Musíte také zapnout režim kompatibility ASP.NET v souboru Web.config, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="30c10-114">You must also turn on ASP.NET compatibility mode in the Web.config file as shown in the following example.</span></span>  
  
```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```
  
> [!WARNING]
>  <span data-ttu-id="30c10-115">Pokud není zapnutý režim kompatibility ASP.NET a <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> slouží k výjimce.</span><span class="sxs-lookup"><span data-stu-id="30c10-115">If ASP.NET compatibility mode is not turned on and the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> is used an exception is thrown.</span></span>  
  
 <span data-ttu-id="30c10-116">Název profilu mezipaměti určené <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> identifikuje profilu mezipaměti, který je přidán do konfiguračního souboru Web.config.</span><span class="sxs-lookup"><span data-stu-id="30c10-116">The cache profile name specified by the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> identifies a cache profile that is added to your Web.config configuration file.</span></span> <span data-ttu-id="30c10-117">Profil mezipaměti je definována s v <`outputCacheSetting`> element, jak je znázorněno v následujícím příkladu konfigurace.</span><span class="sxs-lookup"><span data-stu-id="30c10-117">The cache profile is defined with in a <`outputCacheSetting`> element as shown in the following configuration example.</span></span>  
  
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
  
 <span data-ttu-id="30c10-118">Toto je stejný prvek konfigurace, který je k dispozici pro aplikace ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="30c10-118">This is the same configuration element that is available to ASP.NET applications.</span></span> <span data-ttu-id="30c10-119">Další informace o profilech mezipaměti ASP.NET najdete v tématu <xref:System.Web.Configuration.OutputCacheProfile>.</span><span class="sxs-lookup"><span data-stu-id="30c10-119">For more information about ASP.NET cache profiles, see <xref:System.Web.Configuration.OutputCacheProfile>.</span></span> <span data-ttu-id="30c10-120">Webové služby HTTP jsou nejdůležitější atributy v profilu mezipaměti: `cacheDuration` a `varyByParam`.</span><span class="sxs-lookup"><span data-stu-id="30c10-120">For Web HTTP services, the most important attributes in the cache profile are: `cacheDuration` and `varyByParam`.</span></span> <span data-ttu-id="30c10-121">Tyto atributy jsou potřeba.</span><span class="sxs-lookup"><span data-stu-id="30c10-121">Both of these attributes are required.</span></span> <span data-ttu-id="30c10-122">`cacheDuration` Nastaví množství času, které do mezipaměti odpovědi v řádu sekund.</span><span class="sxs-lookup"><span data-stu-id="30c10-122">`cacheDuration` sets the amount of time a response should be cached in seconds.</span></span> <span data-ttu-id="30c10-123">`varyByParam` Umožňuje zadat parametr řetězce dotazu, který slouží k mezipaměti odpovědí.</span><span class="sxs-lookup"><span data-stu-id="30c10-123">`varyByParam` allows you to specify a query string parameter that is used to cache responses.</span></span> <span data-ttu-id="30c10-124">Všechny požadavky provedené s hodnotami parametrů řetězce dotazu jsou zvlášť v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="30c10-124">All requests made with different query string parameter values are cached separately.</span></span> <span data-ttu-id="30c10-125">Například po provedení počáteční žádosti http://MyServer/MyHttpService/MyOperation?param=10 všechny následné požadavky provedené přes stejný identifikátor URI by vrátila odpověď uložená v mezipaměti (tak dlouho, dokud nebyla uplynula doba uložení do mezipaměti).</span><span class="sxs-lookup"><span data-stu-id="30c10-125">For example, once an initial request is made to http://MyServer/MyHttpService/MyOperation?param=10 all subsequent requests made with the same URI would be returned the cached response (so long as the cache duration has not elapsed).</span></span> <span data-ttu-id="30c10-126">Odpovědi na podobné žádosti, která je stejná, ale má jinou hodnotu pro parametr parametru řetězce dotazu jsou zvlášť do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="30c10-126">Responses for a similar request that is the same but has a different value for the parameter query string parameter are cached separately.</span></span> <span data-ttu-id="30c10-127">Pokud nechcete, aby tento zvláštní chování ukládání do mezipaměti, nastavte `varyByParam` na "žádný".</span><span class="sxs-lookup"><span data-stu-id="30c10-127">If you do not want this separate caching behavior, set `varyByParam` to "none".</span></span>  
  
## <a name="sql-cache-dependency"></a><span data-ttu-id="30c10-128">Závislosti mezipaměti SQL</span><span class="sxs-lookup"><span data-stu-id="30c10-128">SQL Cache Dependency</span></span>  
 <span data-ttu-id="30c10-129">Odpovědi na webu HTTP služby můžete také uložit do mezipaměti závislosti mezipaměti SQL.</span><span class="sxs-lookup"><span data-stu-id="30c10-129">Web HTTP service responses can also be cached with a SQL cache dependency.</span></span> <span data-ttu-id="30c10-130">Pokud vaše webové služby WCF HTTP závisí na data uložená ve službě SQL database, můžete ukládat do mezipaměti odpovědi služby a zneplatnit odpověď uložená v mezipaměti, když data v SQL databázi tabulku změn.</span><span class="sxs-lookup"><span data-stu-id="30c10-130">If your WCF Web HTTP service depends on data stored in a SQL database, you may want to cache the service's response and invalidate the cached response when data in the SQL database table changes.</span></span> <span data-ttu-id="30c10-131">Toto chování je zcela nastaven v souboru Web.config.</span><span class="sxs-lookup"><span data-stu-id="30c10-131">This behavior is configured completely within the Web.config file.</span></span> <span data-ttu-id="30c10-132">Nejdřív je nutné definovat připojovacího řetězce v <`connectionStrings`> element.</span><span class="sxs-lookup"><span data-stu-id="30c10-132">You must first define a connection string in the <`connectionStrings`> element.</span></span>  
  
```xml
<connectionStrings>
  <add name="connectString"
       connectionString="Data Source=MyService;Initial Catalog=MyTestDatabase;Integrated Security=True"
       providerName="System.Data.SqlClient" />
</connectionStrings>
```  
  
 <span data-ttu-id="30c10-133">Pak je nutné povolit závislost mezipaměti SQL v rámci <`caching`> v elementu <`system.web`> element, jak je znázorněno v následujícím příkladu config.</span><span class="sxs-lookup"><span data-stu-id="30c10-133">Then you must enable SQL cache dependency within a <`caching`> element within the <`system.web`> element as shown in the following config example.</span></span>  
  
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
  
 <span data-ttu-id="30c10-134">Tady je povolené závislosti mezipaměti SQL a nastavte čas dotazování na 1000 milisekund.</span><span class="sxs-lookup"><span data-stu-id="30c10-134">Here SQL cache dependency is enabled and a polling time of 1000 milliseconds is set.</span></span> <span data-ttu-id="30c10-135">Pokaždé, když uplyne dotazování tabulky databáze je kontrola aktualizací.</span><span class="sxs-lookup"><span data-stu-id="30c10-135">Each time the polling time elapses the database table is checked for updates.</span></span> <span data-ttu-id="30c10-136">Pokud se zjistí změny obsahu mezipaměti se odeberou a při příštím operace služby je vyvolána nová odpověď do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="30c10-136">If changes are detected the contents of the cache are removed and the next time the service operation is invoked a new response is cached.</span></span> <span data-ttu-id="30c10-137">V rámci <`sqlCacheDependency`> element přidejte databáze a odkazují na řetězce připojení v rámci <`databases`> element, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="30c10-137">Within the <`sqlCacheDependency`> element add the databases and reference the connection strings within the <`databases`> element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="30c10-138">Dále musíte nakonfigurovat nastavení výstupní mezipaměti v rámci <`caching`> element, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="30c10-138">Next you must configure the output cache settings within the <`caching`> element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="30c10-139">Zde je na 60 sekund, nastavit dobu uložení do mezipaměti `varyByParam` je nastavena na hodnotu none a `sqlDependency` nastavena na středníkem oddělený seznam dvojic název/tabulky databáze odděleny dvojtečkami.</span><span class="sxs-lookup"><span data-stu-id="30c10-139">Here the cache duration is set to 60 seconds, `varyByParam` is set to none and `sqlDependency` is set to a semicolon delimited list of database name/table pairs separated by colons.</span></span> <span data-ttu-id="30c10-140">Když data v `MyTable` změně odpověď uložená v mezipaměti pro operaci služby se odebere a po vyvolání operace nová odpověď vygenerovaných (podle volání operace služby) a vrácen do klienta do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="30c10-140">When data in `MyTable` is changed the cached response for the service operation is removed and when the operation is invoked a new response is generated (by calling the service operation), cached, and returned to the client.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="30c10-141">Pro technologii ASP.NET pro přístup k databázi SQL, je nutné použít [nástroj registrace serveru SQL Server ASP.NET](https://go.microsoft.com/fwlink/?LinkId=152536).</span><span class="sxs-lookup"><span data-stu-id="30c10-141">For ASP.NET to access a SQL database, you must use the [ASP.NET SQL Server Registration Tool](https://go.microsoft.com/fwlink/?LinkId=152536).</span></span> <span data-ttu-id="30c10-142">Kromě toho musí umožňovat odpovídající uživatelskému účtu přístup do databáze a tabulky.</span><span class="sxs-lookup"><span data-stu-id="30c10-142">In addition you must allow the appropriate user account access to the database and table.</span></span> <span data-ttu-id="30c10-143">Další informace najdete v tématu [přístup k SQL serveru z webové aplikace](https://go.microsoft.com/fwlink/?LinkId=178988).</span><span class="sxs-lookup"><span data-stu-id="30c10-143">For more information, see [Accessing SQL Server from a Web Application](https://go.microsoft.com/fwlink/?LinkId=178988).</span></span>  
  
## <a name="conditional-http-get-based-caching"></a><span data-ttu-id="30c10-144">Podmíněné získat založený na HTTP ukládání do mezipaměti</span><span class="sxs-lookup"><span data-stu-id="30c10-144">Conditional HTTP GET Based Caching</span></span>  
 <span data-ttu-id="30c10-145">Ve scénářích webových služeb HTTP podmíněné HTTP GET často dělají, když služby k implementaci inteligentního ukládání do mezipaměti HTTP, jak je popsáno v [specifikaci protokolu HTTP](https://go.microsoft.com/fwlink/?LinkId=165800).</span><span class="sxs-lookup"><span data-stu-id="30c10-145">In Web HTTP scenarios a conditional HTTP GET is often used by services to implement intelligent HTTP caching as described in the [HTTP Specification](https://go.microsoft.com/fwlink/?LinkId=165800).</span></span> <span data-ttu-id="30c10-146">K tomu službu musí nastavit hodnotu hlavičky značky ETag do odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="30c10-146">To do this the service must set the value of the ETag header in the HTTP response.</span></span> <span data-ttu-id="30c10-147">Také musíte zkontroluje hlavičky If-None-Match v požadavku HTTP, zda všechny zadané značky ETag odpovídá aktuální značku ETag.</span><span class="sxs-lookup"><span data-stu-id="30c10-147">It also must check the If-None-Match header in the HTTP request to see whether any of the ETag specified matches the current ETag.</span></span>  
  
 <span data-ttu-id="30c10-148">Pro požadavky GET a HEAD <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> přebírá hodnotu značky ETag a ověří proti hlavičku If-None-Match požadavku.</span><span class="sxs-lookup"><span data-stu-id="30c10-148">For GET and HEAD requests, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> takes an ETag value and checks it against the If-None-Match header of the request.</span></span> <span data-ttu-id="30c10-149">Pokud je k dispozici na záhlaví a pokud se zjistí shoda, <xref:System.ServiceModel.Web.WebFaultException> s HTTP se stavovým kódem 304 (Neupraveno) vyvolána a přidá hlavičku ETag do odpovědi s odpovídající značky ETag.</span><span class="sxs-lookup"><span data-stu-id="30c10-149">If the header is present and there is a match, a <xref:System.ServiceModel.Web.WebFaultException> with a HTTP status code 304 (Not Modified) is thrown and an ETag header is added to the response with the matching ETag.</span></span>  
  
 <span data-ttu-id="30c10-150">Jednomu přetížení <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> metoda přijímá datum poslední změny a ověří proti hlavičku If-Modified-Since požadavku.</span><span class="sxs-lookup"><span data-stu-id="30c10-150">One overload of the <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> method takes a last modified date and checks it against the If-Modified-Since header of the request.</span></span> <span data-ttu-id="30c10-151">Pokud je k dispozici záhlaví a prostředek nebyl změněn od, <xref:System.ServiceModel.Web.WebFaultException> pomocí protokolu HTTP se stavovým kódem 304 (Neupraveno) vyvolána.</span><span class="sxs-lookup"><span data-stu-id="30c10-151">If the header is present and the resource has not been modified since, a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 304 (Not Modified) is thrown.</span></span>  
  
 <span data-ttu-id="30c10-152">Pro požadavky PUT, POST a DELETE <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> trvá aktuální hodnotou ETag prostředku.</span><span class="sxs-lookup"><span data-stu-id="30c10-152">For PUT, POST, and DELETE requests, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> takes the current ETag value of a resource.</span></span> <span data-ttu-id="30c10-153">Pokud aktuální značka ETag hodnota null, metoda zkontroluje, že hlavičku If-None-Match má hodnotu "\*".</span><span class="sxs-lookup"><span data-stu-id="30c10-153">If the current ETag value is null, the method checks that the If-None- Match header has a value of "\*".</span></span>  <span data-ttu-id="30c10-154">Pokud aktuální hodnotou ETag není výchozí hodnotu, metoda zkontroluje aktuální hodnotou ETag proti hlavičku If - Match požadavku.</span><span class="sxs-lookup"><span data-stu-id="30c10-154">If the current ETag value is not a default value, then the method checks the current ETag value against the If- Match header of the request.</span></span> <span data-ttu-id="30c10-155">V obou případech se vyvolá metodu <xref:System.ServiceModel.Web.WebFaultException> se stavem HTTP kód 412 (Předběžná podmínka je neplatná), pokud není očekávaná hlavička v požadavku nebo jeho hodnota nevyhovuje podmíněnou kontrolu a nastaví hlavičku ETag do odpovědi na aktuální značku ETag hodnota.</span><span class="sxs-lookup"><span data-stu-id="30c10-155">In either case, the method throws a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 412 (Precondition Failed) if the expected header is not present in the request or its value does not satisfy the conditional check and sets the ETag header of the response to the current ETag value.</span></span>  
  
 <span data-ttu-id="30c10-156">Oba `CheckConditional` metody a <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> metoda zajišťuje, že hodnota ETag, nastavte v hlavičce odpovědi platná značka ETag podle specifikace protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="30c10-156">Both the `CheckConditional` methods and the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> method ensures that the ETag value set on the response header is a valid ETag according to the HTTP specification.</span></span> <span data-ttu-id="30c10-157">To zahrnuje hodnota ETag v dvojitých uvozovkách okolo, pokud již nejsou k dispozici a správně uvozovací znaky interní dvojité uvozovky.</span><span class="sxs-lookup"><span data-stu-id="30c10-157">This includes surrounding the ETag value in double quotes if they are not already present and properly escaping any internal double quote characters.</span></span> <span data-ttu-id="30c10-158">Porovnání slabou značku ETag není podporován.</span><span class="sxs-lookup"><span data-stu-id="30c10-158">Weak ETag comparison is not supported.</span></span>  
  
 <span data-ttu-id="30c10-159">Následující příklad ukazuje, jak používat tyto metody.</span><span class="sxs-lookup"><span data-stu-id="30c10-159">The following example shows how to use these methods.</span></span>  
  
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
  
## <a name="security-considerations"></a><span data-ttu-id="30c10-160">Důležité informace o zabezpečení</span><span class="sxs-lookup"><span data-stu-id="30c10-160">Security Considerations</span></span>  
 <span data-ttu-id="30c10-161">Požadavky, které vyžadují autorizace by neměly mít odpovědi v mezipaměti, protože autorizace se neprovede, pokud odpovědi se načítají z mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="30c10-161">Requests that require authorization should not have their responses cached, because the authorization is not performed when the response is served from the cache.</span></span>  <span data-ttu-id="30c10-162">Ukládání do mezipaměti takové odpovědi by vznikla vážná chyba zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="30c10-162">Caching such responses would introduce a serious security vulnerability.</span></span>  <span data-ttu-id="30c10-163">Obvykle požadavky, které vyžadují autorizace poskytují uživatelská data a proto není ještě výhodné ukládání do mezipaměti na straně serveru.</span><span class="sxs-lookup"><span data-stu-id="30c10-163">Usually, requests that require authorization provide user-specific data and therefore server-side caching is not even beneficial.</span></span>  <span data-ttu-id="30c10-164">V takových situacích ukládání do mezipaměti na straně klienta nebo jednoduše ne ukládání do mezipaměti vůbec bude vhodnější.</span><span class="sxs-lookup"><span data-stu-id="30c10-164">In such situations, client-side caching or simply not caching at all will be more appropriate.</span></span>
