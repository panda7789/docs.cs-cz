---
title: Podpora ukládání dat do mezipaměti pro webové HTTP služby WCF
ms.date: 03/30/2017
ms.assetid: 7f8078e0-00d9-415c-b8ba-c1b6d5c31799
ms.openlocfilehash: 7c60deab635c29785398a1b50f9cf14c0f688420
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141784"
---
# <a name="caching-support-for-wcf-web-http-services"></a><span data-ttu-id="00485-102">Podpora ukládání dat do mezipaměti pro webové HTTP služby WCF</span><span class="sxs-lookup"><span data-stu-id="00485-102">Caching Support for WCF Web HTTP Services</span></span>
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] <span data-ttu-id="00485-103">umožňuje použít deklarativní mechanizmus ukládání do mezipaměti, který je již k dispozici v ASP.NET ve webových službách HTTP služby WCF.</span><span class="sxs-lookup"><span data-stu-id="00485-103">enables you to use the declarative caching mechanism already available in ASP.NET in your WCF Web HTTP services.</span></span> <span data-ttu-id="00485-104">To vám umožní ukládat odpovědi z operací služby HTTP webu WCF do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="00485-104">This allows you to cache responses from your WCF Web HTTP service operations.</span></span> <span data-ttu-id="00485-105">Když uživatel odešle službě požadavek HTTP GET, která je nakonfigurovaná pro ukládání do mezipaměti, ASP.NET odešle zpět odpověď uloženou v mezipaměti a metoda služby se nevolá.</span><span class="sxs-lookup"><span data-stu-id="00485-105">When a user sends an HTTP GET to your service that is configured for caching, ASP.NET sends back the cached response and the service method is not called.</span></span> <span data-ttu-id="00485-106">Až mezipaměť vyprší, při příštím odeslání HTTP GET se vaše metoda služby zavolá a odpověď se znovu uloží do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="00485-106">When the cache expires, the next time a user sends an HTTP GET, your service method is called and the response is once again cached.</span></span> <span data-ttu-id="00485-107">Další informace o ukládání do mezipaměti ASP.NET najdete v tématu [Přehled ukládání do mezipaměti ASP.NET](https://go.microsoft.com/fwlink/?LinkId=152534) .</span><span class="sxs-lookup"><span data-stu-id="00485-107">For more information about ASP.NET caching, see [ASP.NET Caching Overview](https://go.microsoft.com/fwlink/?LinkId=152534)</span></span>  
  
## <a name="basic-web-http-service-caching"></a><span data-ttu-id="00485-108">Mezipaměť základní webové služby HTTP</span><span class="sxs-lookup"><span data-stu-id="00485-108">Basic Web HTTP Service Caching</span></span>  
 <span data-ttu-id="00485-109">Pokud chcete povolit ukládání webové služby HTTP do mezipaměti, musíte nejdřív povolit kompatibilitu s ASP.NET, a to tak, že použijete <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> pro nastavení služby <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> na <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> nebo <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>.</span><span class="sxs-lookup"><span data-stu-id="00485-109">To enable WEB HTTP service caching you must first enable ASP.NET compatibility by applying the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> to the service setting <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> to <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> or <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>.</span></span>  
  
 <span data-ttu-id="00485-110">.NET Framework 4 zavádí nový atribut nazvaný <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, který umožňuje zadat název profilu mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="00485-110">.NET Framework 4 introduces a new attribute called <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> that allows you to specify a cache profile name.</span></span> <span data-ttu-id="00485-111">Tento atribut se aplikuje na operaci služby.</span><span class="sxs-lookup"><span data-stu-id="00485-111">This attribute is applied to a service operation.</span></span> <span data-ttu-id="00485-112">Následující příklad aplikuje <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> na službu, aby povolovala kompatibilitu ASP.NET a nakonfiguruje operaci `GetCustomer` pro ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="00485-112">The following example applies the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> to a service to enable ASP.NET compatibility and configures the `GetCustomer` operation for caching.</span></span> <span data-ttu-id="00485-113">Atribut <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> určuje profil mezipaměti, který obsahuje nastavení mezipaměti, která se mají použít.</span><span class="sxs-lookup"><span data-stu-id="00485-113">The <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> attribute specifies a cache profile that contains the cache settings to be used.</span></span>  
  
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
  
 <span data-ttu-id="00485-114">Také je nutné zapnout režim kompatibility ASP.NET v souboru Web. config, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="00485-114">You must also turn on ASP.NET compatibility mode in the Web.config file as shown in the following example.</span></span>  
  
```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```
  
> [!WARNING]
> <span data-ttu-id="00485-115">Pokud není zapnutý režim kompatibility ASP.NET a <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> se používá výjimka, je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="00485-115">If ASP.NET compatibility mode is not turned on and the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> is used an exception is thrown.</span></span>  
  
 <span data-ttu-id="00485-116">Název profilu mezipaměti určený <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> identifikuje profil mezipaměti, který je přidán do konfiguračního souboru Web. config.</span><span class="sxs-lookup"><span data-stu-id="00485-116">The cache profile name specified by the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> identifies a cache profile that is added to your Web.config configuration file.</span></span> <span data-ttu-id="00485-117">Profil mezipaměti je definován v <`outputCacheSetting`> prvku, jak je znázorněno v následujícím příkladu konfigurace.</span><span class="sxs-lookup"><span data-stu-id="00485-117">The cache profile is defined with in a <`outputCacheSetting`> element as shown in the following configuration example.</span></span>  
  
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
  
 <span data-ttu-id="00485-118">Jedná se o stejný prvek konfigurace, který je k dispozici pro ASP.NET aplikace.</span><span class="sxs-lookup"><span data-stu-id="00485-118">This is the same configuration element that is available to ASP.NET applications.</span></span> <span data-ttu-id="00485-119">Další informace o profilech mezipaměti ASP.NET najdete v tématu <xref:System.Web.Configuration.OutputCacheProfile>.</span><span class="sxs-lookup"><span data-stu-id="00485-119">For more information about ASP.NET cache profiles, see <xref:System.Web.Configuration.OutputCacheProfile>.</span></span> <span data-ttu-id="00485-120">U webových služeb HTTP jsou nejdůležitější atributy v profilu mezipaměti: `cacheDuration` a `varyByParam`.</span><span class="sxs-lookup"><span data-stu-id="00485-120">For Web HTTP services, the most important attributes in the cache profile are: `cacheDuration` and `varyByParam`.</span></span> <span data-ttu-id="00485-121">Oba tyto atributy jsou povinné.</span><span class="sxs-lookup"><span data-stu-id="00485-121">Both of these attributes are required.</span></span> <span data-ttu-id="00485-122">`cacheDuration` nastaví množství času, po který by měla být odpověď uložená v mezipaměti v sekundách.</span><span class="sxs-lookup"><span data-stu-id="00485-122">`cacheDuration` sets the amount of time a response should be cached in seconds.</span></span> <span data-ttu-id="00485-123">`varyByParam` umožňuje zadat parametr řetězce dotazu, který se používá k ukládání odpovědí do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="00485-123">`varyByParam` allows you to specify a query string parameter that is used to cache responses.</span></span> <span data-ttu-id="00485-124">Všechny požadavky vytvořené pomocí různých hodnot parametrů řetězce dotazu jsou ukládány do mezipaměti odděleně.</span><span class="sxs-lookup"><span data-stu-id="00485-124">All requests made with different query string parameter values are cached separately.</span></span> <span data-ttu-id="00485-125">Například po provedení prvotní žádosti o `http://MyServer/MyHttpService/MyOperation?param=10`všechny následné požadavky se stejným identifikátorem URI vrátí odpověď uloženou v mezipaměti (Pokud doba trvání mezipaměti neuplynula).</span><span class="sxs-lookup"><span data-stu-id="00485-125">For example, once an initial request is made to `http://MyServer/MyHttpService/MyOperation?param=10`, all subsequent requests made with the same URI would be returned the cached response (so long as the cache duration has not elapsed).</span></span> <span data-ttu-id="00485-126">Odpovědi na podobný požadavek, který je stejný, ale má jinou hodnotu parametru řetězce dotazu parametru, jsou ukládány do mezipaměti odděleně.</span><span class="sxs-lookup"><span data-stu-id="00485-126">Responses for a similar request that is the same but has a different value for the parameter query string parameter are cached separately.</span></span> <span data-ttu-id="00485-127">Pokud nechcete toto samostatné chování ukládání do mezipaměti, nastavte `varyByParam` na "žádný".</span><span class="sxs-lookup"><span data-stu-id="00485-127">If you do not want this separate caching behavior, set `varyByParam` to "none".</span></span>  
  
## <a name="sql-cache-dependency"></a><span data-ttu-id="00485-128">Závislost mezipaměti SQL</span><span class="sxs-lookup"><span data-stu-id="00485-128">SQL Cache Dependency</span></span>  
 <span data-ttu-id="00485-129">Odpovědi na webové HTTP služby můžou být také uloženy v mezipaměti se závislostí mezipaměti SQL.</span><span class="sxs-lookup"><span data-stu-id="00485-129">Web HTTP service responses can also be cached with a SQL cache dependency.</span></span> <span data-ttu-id="00485-130">Je-li služba WCF Web HTTP závislá na datech uložených v databázi SQL, může být vhodné uložit odpověď služby do mezipaměti a zrušit platnost odpovědi uložené v mezipaměti, když dojde ke změně dat v tabulce databáze SQL.</span><span class="sxs-lookup"><span data-stu-id="00485-130">If your WCF Web HTTP service depends on data stored in a SQL database, you may want to cache the service's response and invalidate the cached response when data in the SQL database table changes.</span></span> <span data-ttu-id="00485-131">Toto chování je zcela nakonfigurované v souboru Web. config.</span><span class="sxs-lookup"><span data-stu-id="00485-131">This behavior is configured completely within the Web.config file.</span></span> <span data-ttu-id="00485-132">Je nutné nejprve definovat připojovací řetězec v prvku <`connectionStrings`>.</span><span class="sxs-lookup"><span data-stu-id="00485-132">You must first define a connection string in the <`connectionStrings`> element.</span></span>  
  
```xml
<connectionStrings>
  <add name="connectString"
       connectionString="Data Source=MyService;Initial Catalog=MyTestDatabase;Integrated Security=True"
       providerName="System.Data.SqlClient" />
</connectionStrings>
```  
  
 <span data-ttu-id="00485-133">Pak je nutné povolit funkci závislosti mezipaměti SQL v rámci <`caching`> elementu v rámci <`system.web`> elementu, jak je znázorněno v následujícím příkladu konfigurace.</span><span class="sxs-lookup"><span data-stu-id="00485-133">Then you must enable SQL cache dependency within a <`caching`> element within the <`system.web`> element as shown in the following config example.</span></span>  
  
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
  
 <span data-ttu-id="00485-134">V tomto případě je povolena závislost mezipaměti SQL a je nastavena doba cyklického dotazování 1000 milisekund.</span><span class="sxs-lookup"><span data-stu-id="00485-134">Here SQL cache dependency is enabled and a polling time of 1000 milliseconds is set.</span></span> <span data-ttu-id="00485-135">Pokaždé, když uplyne doba dotazování v tabulce databáze, bude kontrolována aktualizace.</span><span class="sxs-lookup"><span data-stu-id="00485-135">Each time the polling time elapses the database table is checked for updates.</span></span> <span data-ttu-id="00485-136">Pokud se zjistí změny, obsah mezipaměti se odstraní a při příštím vyvolání operace služby se nová odpověď uloží do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="00485-136">If changes are detected the contents of the cache are removed and the next time the service operation is invoked a new response is cached.</span></span> <span data-ttu-id="00485-137">V rámci <`sqlCacheDependency`> elementu přidejte databáze a odkazujte na připojovací řetězce v rámci <`databases`> elementu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="00485-137">Within the <`sqlCacheDependency`> element add the databases and reference the connection strings within the <`databases`> element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="00485-138">Dále je nutné nakonfigurovat nastavení výstupní mezipaměti v rámci <`caching`> prvku, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="00485-138">Next you must configure the output cache settings within the <`caching`> element as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="00485-139">V tomto případě je doba trvání mezipaměti nastavená na 60 sekund, `varyByParam` je nastavená na hodnotu None a `sqlDependency` je nastavená na seznam dvojic název databáze/tabulka oddělený středníkem.</span><span class="sxs-lookup"><span data-stu-id="00485-139">Here the cache duration is set to 60 seconds, `varyByParam` is set to none and `sqlDependency` is set to a semicolon delimited list of database name/table pairs separated by colons.</span></span> <span data-ttu-id="00485-140">Při změně dat v `MyTable` je odpověď uložená v mezipaměti pro operaci služby odebrána a když je operace vyvolána, je vygenerována nová odpověď (voláním operace služby), uloženou v mezipaměti a vrácena klientovi.</span><span class="sxs-lookup"><span data-stu-id="00485-140">When data in `MyTable` is changed the cached response for the service operation is removed and when the operation is invoked a new response is generated (by calling the service operation), cached, and returned to the client.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="00485-141">Aby ASP.NET mohl získat přístup ke službě SQL Database, je nutné použít [Nástroj pro registraci nástroje ASP.NET SQL Server](https://go.microsoft.com/fwlink/?LinkId=152536).</span><span class="sxs-lookup"><span data-stu-id="00485-141">For ASP.NET to access a SQL database, you must use the [ASP.NET SQL Server Registration Tool](https://go.microsoft.com/fwlink/?LinkId=152536).</span></span> <span data-ttu-id="00485-142">Kromě toho je nutné, aby měl příslušný uživatelský účet přístup k databázi a tabulce.</span><span class="sxs-lookup"><span data-stu-id="00485-142">In addition you must allow the appropriate user account access to the database and table.</span></span> <span data-ttu-id="00485-143">Další informace najdete v tématu [přístup k SQL Server z webové aplikace](https://go.microsoft.com/fwlink/?LinkId=178988).</span><span class="sxs-lookup"><span data-stu-id="00485-143">For more information, see [Accessing SQL Server from a Web Application](https://go.microsoft.com/fwlink/?LinkId=178988).</span></span>  
  
## <a name="conditional-http-get-based-caching"></a><span data-ttu-id="00485-144">Podmíněné ukládání do mezipaměti založené na protokolu HTTP</span><span class="sxs-lookup"><span data-stu-id="00485-144">Conditional HTTP GET Based Caching</span></span>  
 <span data-ttu-id="00485-145">Ve scénářích webového protokolu HTTP často využívají podmíněné HTTP GET služby k implementaci inteligentního ukládání do mezipaměti protokolu HTTP, jak je popsáno ve [specifikaci http](https://go.microsoft.com/fwlink/?LinkId=165800).</span><span class="sxs-lookup"><span data-stu-id="00485-145">In Web HTTP scenarios a conditional HTTP GET is often used by services to implement intelligent HTTP caching as described in the [HTTP Specification](https://go.microsoft.com/fwlink/?LinkId=165800).</span></span> <span data-ttu-id="00485-146">Aby bylo možné tuto službu provést, musí být v odpovědi HTTP nastavena hodnota hlavičky ETag.</span><span class="sxs-lookup"><span data-stu-id="00485-146">To do this the service must set the value of the ETag header in the HTTP response.</span></span> <span data-ttu-id="00485-147">Také musí v požadavku HTTP zaškrtnout hlavičku If-None-Match, aby bylo možné zjistit, zda některý ze zadaných značek ETag odpovídá aktuálnímu ETag.</span><span class="sxs-lookup"><span data-stu-id="00485-147">It also must check the If-None-Match header in the HTTP request to see whether any of the ETag specified matches the current ETag.</span></span>  
  
 <span data-ttu-id="00485-148">V případě požadavků GET a HEAD <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> přebírá hodnotu ETag a kontroluje ji v hlavičce If-None-Match žádosti.</span><span class="sxs-lookup"><span data-stu-id="00485-148">For GET and HEAD requests, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> takes an ETag value and checks it against the If-None-Match header of the request.</span></span> <span data-ttu-id="00485-149">Pokud je hlavička přítomna a existuje shoda, je vyvolána <xref:System.ServiceModel.Web.WebFaultException> se stavovým kódem HTTP 304 (nezměněno) a hlavička ETag je přidána do odpovědi s odpovídající značkou ETag.</span><span class="sxs-lookup"><span data-stu-id="00485-149">If the header is present and there is a match, a <xref:System.ServiceModel.Web.WebFaultException> with a HTTP status code 304 (Not Modified) is thrown and an ETag header is added to the response with the matching ETag.</span></span>  
  
 <span data-ttu-id="00485-150">Jedno přetížení metody <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> přijímá datum poslední změny a kontroluje je proti hlavičce Request-Modified-od hlavičky žádosti.</span><span class="sxs-lookup"><span data-stu-id="00485-150">One overload of the <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> method takes a last modified date and checks it against the If-Modified-Since header of the request.</span></span> <span data-ttu-id="00485-151">Pokud se hlavička nachází a prostředek se od chvíle nezměnil, je vyvolána <xref:System.ServiceModel.Web.WebFaultException> se stavovým kódem HTTP 304 (nezměněno).</span><span class="sxs-lookup"><span data-stu-id="00485-151">If the header is present and the resource has not been modified since, a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 304 (Not Modified) is thrown.</span></span>  
  
 <span data-ttu-id="00485-152">U žádostí o vložení, odeslání a odstranění <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> převezme aktuální hodnotu ETag prostředku.</span><span class="sxs-lookup"><span data-stu-id="00485-152">For PUT, POST, and DELETE requests, <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> takes the current ETag value of a resource.</span></span> <span data-ttu-id="00485-153">Pokud je aktuální hodnota ETag null, metoda zkontroluje, zda má hlavička If-None-Match hodnotu "\*".</span><span class="sxs-lookup"><span data-stu-id="00485-153">If the current ETag value is null, the method checks that the If-None- Match header has a value of "\*".</span></span>  <span data-ttu-id="00485-154">Pokud aktuální hodnota ETag není výchozí hodnotou, pak metoda zkontroluje aktuální hodnotu ETag v hlavičce If-Match žádosti.</span><span class="sxs-lookup"><span data-stu-id="00485-154">If the current ETag value is not a default value, then the method checks the current ETag value against the If- Match header of the request.</span></span> <span data-ttu-id="00485-155">V obou případech metoda vyvolá <xref:System.ServiceModel.Web.WebFaultException> se stavovým kódem HTTP 412 (Předběžná podmínka se nezdařila), pokud očekávaná hlavička není v požadavku k dispozici, nebo její hodnota nevyhovuje podmíněné kontrole a nastavuje hlavičku ETag odpovědi na aktuální hodnotu ETag.</span><span class="sxs-lookup"><span data-stu-id="00485-155">In either case, the method throws a <xref:System.ServiceModel.Web.WebFaultException> with an HTTP status code 412 (Precondition Failed) if the expected header is not present in the request or its value does not satisfy the conditional check and sets the ETag header of the response to the current ETag value.</span></span>  
  
 <span data-ttu-id="00485-156">Jak metody `CheckConditional`, tak metoda <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> zajistí, že hodnota ETag nastavená v hlavičce Response je platná značka ETag podle specifikace HTTP.</span><span class="sxs-lookup"><span data-stu-id="00485-156">Both the `CheckConditional` methods and the <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> method ensures that the ETag value set on the response header is a valid ETag according to the HTTP specification.</span></span> <span data-ttu-id="00485-157">To zahrnuje okolí hodnoty ETag v dvojitých uvozovkách, pokud již nejsou přítomny, a správně uvozovací znaky všech vnitřních dvojitých uvozovek.</span><span class="sxs-lookup"><span data-stu-id="00485-157">This includes surrounding the ETag value in double quotes if they are not already present and properly escaping any internal double quote characters.</span></span> <span data-ttu-id="00485-158">Slabé porovnání ETag není podporováno.</span><span class="sxs-lookup"><span data-stu-id="00485-158">Weak ETag comparison is not supported.</span></span>  
  
 <span data-ttu-id="00485-159">Následující příklad ukazuje, jak použít tyto metody.</span><span class="sxs-lookup"><span data-stu-id="00485-159">The following example shows how to use these methods.</span></span>  
  
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
  
## <a name="security-considerations"></a><span data-ttu-id="00485-160">Důležité informace o zabezpečení</span><span class="sxs-lookup"><span data-stu-id="00485-160">Security Considerations</span></span>  
 <span data-ttu-id="00485-161">Žádosti, které vyžadují autorizaci, by neměly mít své odpovědi uložené v mezipaměti, protože autorizace se neprovádí, pokud je odpověď obsluhována z mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="00485-161">Requests that require authorization should not have their responses cached, because the authorization is not performed when the response is served from the cache.</span></span>  <span data-ttu-id="00485-162">Ukládání takových odpovědí do mezipaměti by vedlo k závažné chybě zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="00485-162">Caching such responses would introduce a serious security vulnerability.</span></span>  <span data-ttu-id="00485-163">Obvykle požadavky vyžadující autorizaci poskytují data specifická pro uživatele, a proto ukládání do mezipaměti na straně serveru není ještě výhodné.</span><span class="sxs-lookup"><span data-stu-id="00485-163">Usually, requests that require authorization provide user-specific data and therefore server-side caching is not even beneficial.</span></span>  <span data-ttu-id="00485-164">V takových situacích bude vhodné ukládat do mezipaměti na straně klienta nebo jednoduše ukládat do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="00485-164">In such situations, client-side caching or simply not caching at all will be more appropriate.</span></span>
