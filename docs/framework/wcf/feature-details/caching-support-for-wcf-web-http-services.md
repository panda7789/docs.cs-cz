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
# <a name="caching-support-for-wcf-web-http-services"></a>Podpora ukládání dat do mezipaměti pro webové HTTP služby WCF

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]umožňuje použít deklarativní mechanismus ukládání do mezipaměti, který je již k dispozici v ASP.NET ve službách WCF Web HTTP. To umožňuje ukládat odpovědi do mezipaměti z operací služby WCF Web HTTP. Když uživatel odešle http get do vaší služby, která je nakonfigurována pro ukládání do mezipaměti, ASP.NET odešle zpět odpověď uloženou v mezipaměti a metoda služby není volána. Po vypršení mezipaměti, při příštím uživatel odešle HTTP GET, je volána metoda služby a odpověď je opět uložena do mezipaměti. Další informace o ukládání do mezipaměti ASP.NET naleznete [v tématu ASP.NET Přehled ukládání do mezipaměti](https://docs.microsoft.com/previous-versions/aspnet/ms178597(v=vs.100)).  
  
## <a name="basic-web-http-service-caching"></a>Ukládání do mezipaměti základní webové služby HTTP  

  Chcete-li povolit ukládání do mezipaměti služby WEB <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> HTTP, <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> musíte <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>nejprve povolit ASP.NET kompatibilitu použitím nastavení služby pro nebo .  
  
 Rozhraní .NET Framework 4 zavádí <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> nový atribut s názvem, který umožňuje zadat název profilu mezipaměti. Tento atribut je použit pro operaci služby. Následující příklad použije <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> službu, která umožňuje kompatibilitu `GetCustomer` ASP.NET a konfiguruje operaci pro ukládání do mezipaměti. Atribut <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> určuje profil mezipaměti, který obsahuje nastavení mezipaměti, které má být použito.  
  
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
  
Zapněte také ASP.NET režimkompatibility v souboru Web.config, jak je znázorněno v následujícím příkladu.  
  
```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```
  
> [!WARNING]
> Pokud ASP.NET režim kompatibility není <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> zapnuta a je použita výjimka je vyvolána.  
  
 Název profilu mezipaměti <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> určený profilem mezipaměti, který je přidán do konfiguračního souboru Web.config. Profil mezipaměti je definován `outputCacheSetting` v <> prvku, jak je znázorněno v následujícím příkladu konfigurace.  
  
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
  
 Jedná se o stejný konfigurační prvek, který je k dispozici pro ASP.NET aplikace. Další informace o ASP.NET profilech mezipaměti naleznete v tématu <xref:System.Web.Configuration.OutputCacheProfile>. Pro webové služby HTTP jsou nejdůležitějšími atributy `cacheDuration` `varyByParam`v profilu mezipaměti: a . Oba tyto atributy jsou povinné. `cacheDuration`nastaví dobu, po kterou má být odpověď uložena do mezipaměti v sekundách. `varyByParam`umožňuje zadat parametr řetězce dotazu, který se používá k ukládání odpovědí do mezipaměti. Všechny požadavky provedené s různými hodnotami parametrů řetězce dotazu jsou ukládány do mezipaměti samostatně. Například po počáteční požadavek `http://MyServer/MyHttpService/MyOperation?param=10`na , všechny následné požadavky provedené se stejným URI by být vrácena odpověď uložené v mezipaměti (tak dlouho, dokud trvání mezipaměti neuplynula). Odpovědi pro podobný požadavek, který je stejný, ale má jinou hodnotu parametru řetězce dotazu parametru jsou ukládány do mezipaměti samostatně. Pokud nechcete, aby toto samostatné `varyByParam` ukládání do mezipaměti chování, nastavte na "none".  
  
## <a name="sql-cache-dependency"></a>Závislost mezipaměti SQL  

  Odpovědi webové služby HTTP lze také uložit do mezipaměti se závislostí mezipaměti SQL. Pokud vaše webová služba HTTP WCF závisí na datech uložených v databázi SQL, můžete chtít uložit odpověď služby do mezipaměti a zrušit platnost odpovědi uložené v mezipaměti při změně dat v databázové tabulce SQL. Toto chování je zcela nakonfigurováno v souboru Web.config. Nejprve definujte připojovací řetězec v prvku <`connectionStrings`>.  
  
```xml
<connectionStrings>
  <add name="connectString"
       connectionString="Data Source=MyService;Initial Catalog=MyTestDatabase;Integrated Security=True"
       providerName="System.Data.SqlClient" />
</connectionStrings>
```  
  
 Potom je nutné povolit závislost `caching` mezipaměti SQL `system.web` v rámci <> prvek v rámci <> prvek, jak je znázorněno v následujícím příkladu konfigurace.  
  
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
  
 Zde je povolena závislost mezipaměti SQL a je nastavena doba dotazování 1000 milisekund. Pokaždé, když čas dotazování uplyne, je databáze tabulka zkontrolována aktualizace. Pokud jsou zjištěny změny, obsah mezipaměti jsou odebrány a při příštím spuštění operace služby je nová odpověď uložena do mezipaměti. V rámci `sqlCacheDependency` <> elementu přidejte databáze a `databases` odkazna připojovací řetězce v rámci <> prvek, jak je znázorněno v následujícím příkladu.  
  
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
  
 Dále je nutné nakonfigurovat nastavení `caching` výstupní mezipaměti v rámci <> prvku, jak je znázorněno v následujícím příkladu.  
  
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
  
 Zde je doba trvání mezipaměti `varyByParam` nastavena na 60 sekund, je nastavena na žádnou a `sqlDependency` je nastavena na seznam dvojic názvů/tabulek oddělených středníkem oddělených dvojtečkami. Při změně `MyTable` dat v je odebrána odpověď uložené v mezipaměti pro operaci služby a při vyvolání operace je generována nová odpověď (voláním operace služby), uloženy do mezipaměti a vráceny klientovi.  
  
> [!IMPORTANT]
> Chcete-li ASP.NET získat přístup k databázi SQL, je nutné použít [nástroj ASP.NET sql server registration tool](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms229862(v=vs.90)). Kromě toho musíte povolit přístup příslušného uživatelského účtu k databázi a tabulce. Další informace naleznete [v tématu Přístup k serveru SQL Server z webové aplikace](https://docs.microsoft.com/previous-versions/aspnet/ht43wsex(v=vs.100)).  
  
## <a name="conditional-http-get-based-caching"></a>Podmíněné ukládání do mezipaměti založené na protokolu HTTP GET  

  Ve scénářích http webu je podmíněné HTTP GET často používáno službami k implementaci inteligentního ukládání do mezipaměti HTTP, jak je popsáno ve [specifikaci HTTP](https://www.w3.org/Protocols/rfc2616/rfc2616.html). Chcete-li to provést, musí služba nastavit hodnotu hlavičky ETag v odpovědi HTTP. Musí také zkontrolovat hlavičku If-None-Match v požadavku HTTP, aby se zjistilo, zda některý z zadaných eTag odpovídá aktuálnímu eTagu.  
  
 Pro požadavky GET a <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> HEAD přebírá hodnotu ETag a kontroluje ji proti if-None-Match záhlaví požadavku. Pokud záhlaví je k dispozici a <xref:System.ServiceModel.Web.WebFaultException> je shoda, a se stavovým kódem HTTP 304 (Nezměněno) je vyvolána a záhlaví ETag je přidán do odpovědi s odpovídající ETag.  
  
 Jedno přetížení <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> metody trvá datum poslední změny a zkontroluje proti If-Modified-Since záhlaví požadavku. Pokud záhlaví je k dispozici a prostředek nebyl <xref:System.ServiceModel.Web.WebFaultException> změněn od, a se stavovým kódem HTTP 304 (Nezměněno) je vyvolána.  
  
 Pro požadavky PUT, POST a <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> DELETE přebírá aktuální hodnotu ETag prostředku. Pokud je aktuální hodnota ETag null, metoda zkontroluje, zda má hlavička If-None- Match hodnotu "*".  Pokud aktuální hodnota ETag není výchozí hodnota, pak metoda zkontroluje aktuální hodnotu ETag proti if-match záhlaví požadavku. V obou případech metoda vyvolá <xref:System.ServiceModel.Web.WebFaultException> se stavovým kódem HTTP 412 (Podmínka se nezdařila), pokud očekávaná hlavička není k dispozici v požadavku nebo jeho hodnota nesplňuje podmíněnou kontrolu a nastaví hlavičku ETag odpovědi na aktuální hodnotu ETag.  
  
 `CheckConditional` Metody i <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> metoda zajišťují, že hodnota ETag nastavená v hlavičce odpovědi je platný eTag podle specifikace HTTP. To zahrnuje okolní ETag hodnotu v uvozovkách, pokud již nejsou k dispozici a správně unikat všechny vnitřní dvojité uvozovky znaky. Slabé porovnání ETag není podporováno.  
  
 Následující příklad ukazuje, jak používat tyto metody.  
  
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
  
## <a name="security-considerations"></a>Aspekty zabezpečení  
 Požadavky, které vyžadují autorizaci, by neměly mít své odpovědi uložené v mezipaměti, protože autorizace není provedena, když je odpověď obsluhována z mezipaměti.  Ukládání takových odpovědí do mezipaměti by zavádělo vážnou chybu zabezpečení.  Požadavky, které vyžadují autorizaci, obvykle poskytují data specifická pro uživatele, a proto ukládání do mezipaměti na straně serveru není ani výhodné.  V takových situacích bude vhodnější ukládání do mezipaměti na straně klienta nebo prostě ne ukládání do mezipaměti vůbec.
