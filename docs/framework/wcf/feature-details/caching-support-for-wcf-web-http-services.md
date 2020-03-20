---
title: Podpora ukládání dat do mezipaměti pro webové HTTP služby WCF
ms.date: 03/30/2017
ms.assetid: 7f8078e0-00d9-415c-b8ba-c1b6d5c31799
ms.openlocfilehash: 63c83cc1af9a3ccfdbdd79f8d0480e6c29eaf2f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185433"
---
# <a name="caching-support-for-wcf-web-http-services"></a><span data-ttu-id="27700-102">Podpora ukládání dat do mezipaměti pro webové HTTP služby WCF</span><span class="sxs-lookup"><span data-stu-id="27700-102">Caching Support for WCF Web HTTP Services</span></span>

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="27700-103">umožňuje použít deklarativní mechanismus ukládání do mezipaměti, který je již k dispozici v ASP.NET ve službách WCF Web HTTP.</span><span class="sxs-lookup"><span data-stu-id="27700-103">enables you to use the declarative caching mechanism already available in ASP.NET in your WCF Web HTTP services.</span></span> <span data-ttu-id="27700-104">To umožňuje ukládat odpovědi do mezipaměti z operací služby WCF Web HTTP.</span><span class="sxs-lookup"><span data-stu-id="27700-104">This allows you to cache responses from your WCF Web HTTP service operations.</span></span> <span data-ttu-id="27700-105">Když uživatel odešle http get do vaší služby, která je nakonfigurována pro ukládání do mezipaměti, ASP.NET odešle zpět odpověď uloženou v mezipaměti a metoda služby není volána.</span><span class="sxs-lookup"><span data-stu-id="27700-105">When a user sends an HTTP GET to your service that is configured for caching, ASP.NET sends back the cached response and the service method is not called.</span></span> <span data-ttu-id="27700-106">Po vypršení mezipaměti, při příštím uživatel odešle HTTP GET, je volána metoda služby a odpověď je opět uložena do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="27700-106">When the cache expires, the next time a user sends an HTTP GET, your service method is called and the response is once again cached.</span></span> <span data-ttu-id="27700-107">Další informace o ukládání do mezipaměti ASP.NET naleznete [v tématu ASP.NET Přehled ukládání do mezipaměti](https://docs.microsoft.com/previous-versions/aspnet/ms178597(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="27700-107">For more information about ASP.NET caching, see [ASP.NET Caching Overview](https://docs.microsoft.com/previous-versions/aspnet/ms178597(v=vs.100)).</span></span>  
  
## <a name="basic-web-http-service-caching"></a><span data-ttu-id="27700-108">Ukládání do mezipaměti základní webové služby HTTP</span><span class="sxs-lookup"><span data-stu-id="27700-108">Basic Web HTTP Service Caching</span></span>  

  <span data-ttu-id="27700-109">Chcete-li povolit ukládání do mezipaměti služby WEB <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> HTTP, <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> musíte <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>nejprve povolit ASP.NET kompatibilitu použitím nastavení služby pro nebo .</span><span class="sxs-lookup"><span data-stu-id="27700-109">To enable WEB HTTP service caching, you must first enable ASP.NET compatibility by applying the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> to the service setting <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> to <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> or <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>.</span></span>  
  
 <span data-ttu-id="27700-110">Rozhraní .NET Framework 4 zavádí <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> nový atribut s názvem, který umožňuje zadat název profilu mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="27700-110">.NET Framework 4 introduces a new attribute called <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> that allows you to specify a cache profile name.</span></span> <span data-ttu-id="27700-111">Tento atribut je použit pro operaci služby.</span><span class="sxs-lookup"><span data-stu-id="27700-111">This attribute is applied to a service operation.</span></span> <span data-ttu-id="27700-112">Následující příklad použije <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> službu, která umožňuje kompatibilitu `GetCustomer` ASP.NET a konfiguruje operaci pro ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="27700-112">The following example applies the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> to a service to enable ASP.NET compatibility and configures the `GetCustomer` operation for caching.</span></span> <span data-ttu-id="27700-113">Atribut <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> určuje profil mezipaměti, který obsahuje nastavení mezipaměti, které má být použito.</span><span class="sxs-lookup"><span data-stu-id="27700-113">The <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> attribute specifies a cache profile that contains the cache settings to be used.</span></span>  
  
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
  
<span data-ttu-id="27700-114">Zapněte také ASP.NET režimkompatibility v souboru Web.config, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="27700-114">Also turn on ASP.NET compatibility mode in the Web.config file as shown in the following example.</span></span>  
  
```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```
  
> [!WARNING]
> <span data-ttu-id="27700-115">Pokud ASP.NET režim kompatibility není <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> zapnuta a je použita výjimka je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="27700-115">If ASP.NET compatibility mode is not turned on and the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> is used an exception is thrown.</span></span>  
  
 <span data-ttu-id="27700-116">Název profilu mezipaměti <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> určený profilem mezipaměti, který je přidán do konfiguračního souboru Web.config.</span><span class="sxs-lookup"><span data-stu-id="27700-116">The cache profile name specified by the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> identifies a cache profile that is added to your Web.config configuration file.</span></span> <span data-ttu-id="27700-117">Profil mezipaměti je definován `outputCacheSetting` v <> prvku, jak je znázorněno v následujícím příkladu konfigurace.</span><span class="sxs-lookup"><span data-stu-id="27700-117">The cache profile is defined with in a <`outputCacheSetting`> element as shown in the following configuration example.</span></span>  
  
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
  
 <span data-ttu-id="27700-118">Jedná se o stejný konfigurační prvek, který je k dispozici pro ASP.NET aplikace.</span><span class="sxs-lookup"><span data-stu-id="27700-118">This is the same configuration element that is available to ASP.NET applications.</span></span> <span data-ttu-id="27700-119">Další informace o ASP.NET profilech mezipaměti naleznete v tématu <xref:System.Web.Configuration.OutputCacheProfile>.</span><span class="sxs-lookup"><span data-stu-id="27700-119">For more information about ASP.NET cache profiles, see <xref:System.Web.Configuration.OutputCacheProfile>.</span></span> <span data-ttu-id="27700-120">Pro webové služby HTTP jsou nejdůležitějšími atributy `cacheDuration` `varyByParam`v profilu mezipaměti: a .</span><span class="sxs-lookup"><span data-stu-id="27700-120">For Web HTTP services, the most important attributes in the cache profile are: `cacheDuration` and `varyByParam`.</span></span> <span data-ttu-id="27700-121">Oba tyto atributy jsou povinné.</span><span class="sxs-lookup"><span data-stu-id="27700-121">Both of these attributes are required.</span></span> <span data-ttu-id="27700-122">`cacheDuration`nastaví dobu, po kterou má být odpověď uložena do mezipaměti v sekundách.</span><span class="sxs-lookup"><span data-stu-id="27700-122">`cacheDuration` sets the amount of time a response should be cached in seconds.</span></span> <span data-ttu-id="27700-123">`varyByParam`umožňuje zadat parametr řetězce dotazu, který se používá k ukládání odpovědí do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="27700-123">`varyByParam` allows you to specify a query string parameter that is used to cache responses.</span></span> <span data-ttu-id="27700-124">Všechny požadavky provedené s různými hodnotami parametrů řetězce dotazu jsou ukládány do mezipaměti samostatně.</span><span class="sxs-lookup"><span data-stu-id="27700-124">All requests made with different query string parameter values are cached separately.</span></span> <span data-ttu-id="27700-125">Například po počáteční požadavek `http://MyServer/MyHttpService/MyOperation?param=10`na , všechny následné požadavky provedené se stejným URI by být vrácena odpověď uložené v mezipaměti (tak dlouho, dokud trvání mezipaměti neuplynula).</span><span class="sxs-lookup"><span data-stu-id="27700-125">For example, once an initial request is made to `http://MyServer/MyHttpService/MyOperation?param=10`, all subsequent requests made with the same URI would be returned the cached response (so long as the cache duration has not elapsed).</span></span> <span data-ttu-id="27700-126">Odpovědi pro podobný požadavek, který je stejný, ale má jinou hodnotu parametru řetězce dotazu parametru jsou ukládány do mezipaměti samostatně.</span><span class="sxs-lookup"><span data-stu-id="27700-126">Responses for a similar request that is the same but has a different value for the parameter query string parameter are cached separately.</span></span> <span data-ttu-id="27700-127">Pokud nechcete, aby toto samostatné `varyByParam` ukládání do mezipaměti chování, nastavte na "none".</span><span class="sxs-lookup"><span data-stu-id="27700-127">If you do not want this separate caching behavior, set `varyByParam` to "none".</span></span>  
  
## <a name="sql-cache-dependency"></a><span data-ttu-id="27700-128">Závislost mezipaměti SQL</span><span class="sxs-lookup"><span data-stu-id="27700-128">SQL Cache Dependency</span></span>  

  <span data-ttu-id="27700-129">Odpovědi webové služby HTTP lze také uložit do mezipaměti se závislostí mezipaměti SQL.</span><span class="sxs-lookup"><span data-stu-id="27700-129">Web HTTP service responses can also be cached with a SQL cache dependency.</span></span> <span data-ttu-id="27700-130">Pokud vaše webová služba HTTP WCF závisí na datech uložených v databázi SQL, můžete chtít uložit odpověď služby do mezipaměti a zrušit platnost odpovědi uložené v mezipaměti při změně dat v databázové tabulce SQL.</span><span class="sxs-lookup"><span data-stu-id="27700-130">If your WCF Web HTTP service depends on data stored in a SQL database, you may want to cache the service's response and invalidate the cached response when data in the SQL database table changes.</span></span> <span data-ttu-id="27700-131">Toto chování je zcela nakonfigurováno v souboru Web.config.</span><span class="sxs-lookup"><span data-stu-id="27700-131">This behavior is configured completely within the Web.config file.</span></span> <span data-ttu-id="27700-132">Nejprve definujte připojovací řetězec v prvku <`connectionStrings`>.</span><span class="sxs-lookup"><span data-stu-id="27700-132">First, define a connection string in the <`connectionStrings`> element.</span></span>  
  
```xml
<connectionStrings>
  <add name="connectString"
       connectionString="Data Source=MyService;Initial Catalog=MyTestDatabase;Integrated Security=True"
       providerName="System.Data.SqlClient" />
</connectionStrings>
```  
  
 <span data-ttu-id="27700-133">Potom je nutné povolit závislost `caching` mezipaměti SQL `system.web` v rámci <> prvek v rámci <> prvek, jak je znázorněno v následujícím příkladu konfigurace.</span><span class="sxs-lookup"><span data-stu-id="27700-133">Then you must enable SQL cache dependency within a <`caching`> element within the <`system.web`> element as shown in the following config example.</span></span>  
  
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
  
 <span data-ttu-id="27700-134">Zde je povolena závislost mezipaměti SQL a je nastavena doba dotazování 1000 milisekund.</span><span class="sxs-lookup"><span data-stu-id="27700-134">Here SQL cache dependency is enabled and a polling time of 1000 milliseconds is set.</span></span> <span data-ttu-id="27700-135">Pokaždé, když čas dotazování uplyne, je databáze tabulka zkontrolována aktualizace.</span><span class="sxs-lookup"><span data-stu-id="27700-135">Each time the polling time elapses the database table is checked for updates.</span></span> <span data-ttu-id="27700-136">Pokud jsou zjištěny změny, obsah mezipaměti jsou odebrány a při příštím spuštění operace služby je nová odpověď uložena do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="27700-136">If changes are detected the contents of the cache are removed and the next time the service operation is invoked a new response is cached.</span></span> <span data-ttu-id="27700-137">V rámci `sqlCacheDependency` <> elementu přidejte databáze a `databases` odkazna připojovací řetězce v rámci <> prvek, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="27700-137">Within the <`sqlCacheDependency`> element add the databases and reference the connection strings within the <`databases`> element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="27700-138">Dále je nutné nakonfigurovat nastavení `caching` výstupní mezipaměti v rámci <> prvku, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="27700-138">Next you must configure the output cache settings within the <`caching`> element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="27700-139">Zde je doba trvání mezipaměti `varyByParam` nastavena na 60 sekund, je nastavena na žádnou a `sqlDependency` je nastavena na seznam dvojic názvů/tabulek oddělených středníkem oddělených dvojtečkami.</span><span class="sxs-lookup"><span data-stu-id="27700-139">Here the cache duration is set to 60 seconds, `varyByParam` is set to none, and `sqlDependency` is set to a semicolon-delimited list of database name/table pairs separated by colons.</span></span> <span data-ttu-id="27700-140">Při změně `MyTable` dat v je odebrána odpověď uložené v mezipaměti pro operaci služby a při vyvolání operace je generována nová odpověď (voláním operace služby), uloženy do mezipaměti a vráceny klientovi.</span><span class="sxs-lookup"><span data-stu-id="27700-140">When data in `MyTable` is changed the cached response for the service operation is removed and when the operation is invoked a new response is generated (by calling the service operation), cached, and returned to the client.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="27700-141">Chcete-li ASP.NET získat přístup k databázi SQL, je nutné použít [nástroj ASP.NET sql server registration tool](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms229862(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="27700-141">For ASP.NET to access a SQL database, you must use the [ASP.NET SQL Server Registration Tool](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms229862(v=vs.90)).</span></span> <span data-ttu-id="27700-142">Kromě toho musíte povolit přístup příslušného uživatelského účtu k databázi a tabulce.</span><span class="sxs-lookup"><span data-stu-id="27700-142">In addition you must allow the appropriate user account access to the database and table.</span></span> <span data-ttu-id="27700-143">Další informace naleznete [v tématu Přístup k serveru SQL Server z webové aplikace](https://docs.microsoft.com/previous-versions/aspnet/ht43wsex(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="27700-143">For more information, see [Accessing SQL Server from a Web Application](https://docs.microsoft.com/previous-versions/aspnet/ht43wsex(v=vs.100)).</span></span>  
  
## <a name="conditional-http-get-based-caching"></a><span data-ttu-id="27700-144">Podmíněné ukládání do mezipaměti založené na protokolu HTTP GET</span><span class="sxs-lookup"><span data-stu-id="27700-144">Conditional HTTP GET Based Caching</span></span>  

  <span data-ttu-id="27700-145">Ve scénářích http webu je podmíněné HTTP GET často používáno službami k implementaci inteligentního ukládání do mezipaměti HTTP, jak je popsáno ve [specifikaci HTTP](https://www.w3.org/Protocols/rfc2616/rfc2616.html).</span><span class="sxs-lookup"><span data-stu-id="27700-145">In Web HTTP scenarios a conditional HTTP GET is often used by services to implement intelligent HTTP caching as described in the [HTTP Specification](https://www.w3.org/Protocols/rfc2616/rfc2616.html).</span></span> <span data-ttu-id="27700-146">Chcete-li to provést, musí služba nastavit hodnotu hlavičky ETag v odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="27700-146">To do this, the service must set the value of the ETag header in the HTTP response.</span></span> <span data-ttu-id="27700-147">Musí také zkontrolovat hlavičku If-None-Match v požadavku HTTP, aby se zjistilo, zda některý z zadaných eTag odpovídá aktuálnímu eTagu.</span><span class="sxs-lookup"><span data-stu-id="27700-147">It also must check the If-None-Match header in the HTTP request to see whether any of the ETag specified matches the current ETag.</span></span>  
  
 <span data-ttu-id="27700-148">Pro požadavky GET a <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> HEAD přebírá hodnotu ETag a kontroluje ji proti if-None-Match záhlaví požadavku.</span><span class="sxs-lookup"><span data-stu-id="27700-148">For GET and HEAD requests, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> takes an ETag value and checks it against the If-None-Match header of the request.</span></span> <span data-ttu-id="27700-149">Pokud záhlaví je k dispozici a <xref:System.ServiceModel.Web.WebFaultException> je shoda, a se stavovým kódem HTTP 304 (Nezměněno) je vyvolána a záhlaví ETag je přidán do odpovědi s odpovídající ETag.</span><span class="sxs-lookup"><span data-stu-id="27700-149">If the header is present and there is a match, a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 304 (Not Modified) is thrown and an ETag header is added to the response with the matching ETag.</span></span>  
  
 <span data-ttu-id="27700-150">Jedno přetížení <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> metody trvá datum poslední změny a zkontroluje proti If-Modified-Since záhlaví požadavku.</span><span class="sxs-lookup"><span data-stu-id="27700-150">One overload of the <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> method takes a last modified date and checks it against the If-Modified-Since header of the request.</span></span> <span data-ttu-id="27700-151">Pokud záhlaví je k dispozici a prostředek nebyl <xref:System.ServiceModel.Web.WebFaultException> změněn od, a se stavovým kódem HTTP 304 (Nezměněno) je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="27700-151">If the header is present and the resource has not been modified since, a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 304 (Not Modified) is thrown.</span></span>  
  
 <span data-ttu-id="27700-152">Pro požadavky PUT, POST a <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> DELETE přebírá aktuální hodnotu ETag prostředku.</span><span class="sxs-lookup"><span data-stu-id="27700-152">For PUT, POST, and DELETE requests, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> takes the current ETag value of a resource.</span></span> <span data-ttu-id="27700-153">Pokud je aktuální hodnota ETag null, metoda zkontroluje, zda má hlavička If-None- Match hodnotu "\*".</span><span class="sxs-lookup"><span data-stu-id="27700-153">If the current ETag value is null, the method checks that the If-None- Match header has a value of "\*".</span></span>  <span data-ttu-id="27700-154">Pokud aktuální hodnota ETag není výchozí hodnota, pak metoda zkontroluje aktuální hodnotu ETag proti if-match záhlaví požadavku.</span><span class="sxs-lookup"><span data-stu-id="27700-154">If the current ETag value is not a default value, then the method checks the current ETag value against the If- Match header of the request.</span></span> <span data-ttu-id="27700-155">V obou případech metoda vyvolá <xref:System.ServiceModel.Web.WebFaultException> se stavovým kódem HTTP 412 (Podmínka se nezdařila), pokud očekávaná hlavička není k dispozici v požadavku nebo jeho hodnota nesplňuje podmíněnou kontrolu a nastaví hlavičku ETag odpovědi na aktuální hodnotu ETag.</span><span class="sxs-lookup"><span data-stu-id="27700-155">In either case, the method throws a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 412 (Precondition Failed) if the expected header is not present in the request or its value does not satisfy the conditional check and sets the ETag header of the response to the current ETag value.</span></span>  
  
 <span data-ttu-id="27700-156">`CheckConditional` Metody i <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> metoda zajišťují, že hodnota ETag nastavená v hlavičce odpovědi je platný eTag podle specifikace HTTP.</span><span class="sxs-lookup"><span data-stu-id="27700-156">Both the `CheckConditional` methods and the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> method ensures that the ETag value set on the response header is a valid ETag according to the HTTP specification.</span></span> <span data-ttu-id="27700-157">To zahrnuje okolní ETag hodnotu v uvozovkách, pokud již nejsou k dispozici a správně unikat všechny vnitřní dvojité uvozovky znaky.</span><span class="sxs-lookup"><span data-stu-id="27700-157">This includes surrounding the ETag value in double quotes if they are not already present and properly escaping any internal double quote characters.</span></span> <span data-ttu-id="27700-158">Slabé porovnání ETag není podporováno.</span><span class="sxs-lookup"><span data-stu-id="27700-158">Weak ETag comparison is not supported.</span></span>  
  
 <span data-ttu-id="27700-159">Následující příklad ukazuje, jak používat tyto metody.</span><span class="sxs-lookup"><span data-stu-id="27700-159">The following example shows how to use these methods.</span></span>  
  
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
  
## <a name="security-considerations"></a><span data-ttu-id="27700-160">Aspekty zabezpečení</span><span class="sxs-lookup"><span data-stu-id="27700-160">Security Considerations</span></span>  
 <span data-ttu-id="27700-161">Požadavky, které vyžadují autorizaci, by neměly mít své odpovědi uložené v mezipaměti, protože autorizace není provedena, když je odpověď obsluhována z mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="27700-161">Requests that require authorization should not have their responses cached, because the authorization is not performed when the response is served from the cache.</span></span>  <span data-ttu-id="27700-162">Ukládání takových odpovědí do mezipaměti by zavádělo vážnou chybu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="27700-162">Caching such responses would introduce a serious security vulnerability.</span></span>  <span data-ttu-id="27700-163">Požadavky, které vyžadují autorizaci, obvykle poskytují data specifická pro uživatele, a proto ukládání do mezipaměti na straně serveru není ani výhodné.</span><span class="sxs-lookup"><span data-stu-id="27700-163">Usually, requests that require authorization provide user-specific data and therefore server-side caching is not even beneficial.</span></span>  <span data-ttu-id="27700-164">V takových situacích bude vhodnější ukládání do mezipaměti na straně klienta nebo prostě ne ukládání do mezipaměti vůbec.</span><span class="sxs-lookup"><span data-stu-id="27700-164">In such situations, client-side caching or simply not caching at all will be more appropriate.</span></span>
