---
title: Podpora ukládání dat do mezipaměti pro webové HTTP služby WCF
ms.date: 03/30/2017
ms.assetid: 7f8078e0-00d9-415c-b8ba-c1b6d5c31799
ms.openlocfilehash: 25b564235b5d2b3b26b5d657f3e5f0bd5d594125
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45972985"
---
# <a name="caching-support-for-wcf-web-http-services"></a>Podpora ukládání dat do mezipaměti pro webové HTTP služby WCF
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] umožňuje používat deklarativní mechanizmus ukládání do mezipaměti, aktuálně k dispozici v ASP.NET ve vašich službách WCF Web HTTP. To vám umožní do mezipaměti odpovědi z servisní operace webových služeb HTTP WCF. Když uživatel odešle do služby, který je nakonfigurovaný pro ukládání do mezipaměti HTTP GET, ASP.NET, odešle zpět odpověď uložená v mezipaměti a není volána metoda služby. Když vyprší platnost mezipaměti, při příštím uživatel odešle HTTP GET, je volána metoda vaše služby a znovu do mezipaměti odpovědi. Další informace o ukládání do mezipaměti ASP.NET najdete v tématu [přehled ukládání do mezipaměti ASP.NET](https://go.microsoft.com/fwlink/?LinkId=152534)  
  
## <a name="basic-web-http-service-caching"></a>Základní webové služby HTTP ukládání do mezipaměti  
 Povolit webových služeb HTTP služby ukládání do mezipaměti je třeba nejprve povolit režim kompatibility ASP.NET použitím <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> nastavení služby <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> k <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> nebo <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>.  
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] zavádí nový atribut volá <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> , který umožňuje určit název profilu mezipaměti. Tento atribut je použit na operaci služby. Následující příklad se vztahuje <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> na službu a povolte režim kompatibility ASP.NET a nakonfiguruje `GetCustomer` operace pro ukládání do mezipaměti. <!--zz<xref:System.ServiceModel.Activation.AspNetCacheProfileAttribute>--> `System.ServiceModel.Activation.AspNetCacheProfileAttribute` Atribut určuje, který obsahuje nastavení mezipaměti pro použití profilu mezipaměti.  
  
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
  
 Musíte také zapnout režim kompatibility ASP.NET v souboru Web.config, jak je znázorněno v následujícím příkladu.  
  
```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```
  
> [!WARNING]
>  Pokud není zapnutý režim kompatibility ASP.NET a <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> slouží k výjimce.  
  
 Název profilu mezipaměti určené <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> identifikuje profilu mezipaměti, který je přidán do konfiguračního souboru Web.config. Profil mezipaměti je definována s v <`outputCacheSetting`> element, jak je znázorněno v následujícím příkladu konfigurace.  
  
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
  
 Toto je stejný prvek konfigurace, který je k dispozici pro aplikace ASP.NET. Další informace o profilech mezipaměti ASP.NET najdete v tématu <xref:System.Web.Configuration.OutputCacheProfile>. Webové služby HTTP jsou nejdůležitější atributy v profilu mezipaměti: `cacheDuration` a `varyByParam`. Tyto atributy jsou potřeba. `cacheDuration` Nastaví množství času, které do mezipaměti odpovědi v řádu sekund. `varyByParam` Umožňuje zadat parametr řetězce dotazu, který slouží k mezipaměti odpovědí. Všechny požadavky provedené s hodnotami parametrů řetězce dotazu jsou zvlášť v mezipaměti. Například po provedení počáteční žádosti http://MyServer/MyHttpService/MyOperation?param=10 všechny následné požadavky provedené přes stejný identifikátor URI by vrátila odpověď uložená v mezipaměti (tak dlouho, dokud nebyla uplynula doba uložení do mezipaměti). Odpovědi na podobné žádosti, která je stejná, ale má jinou hodnotu pro parametr parametru řetězce dotazu jsou zvlášť do mezipaměti. Pokud nechcete, aby tento zvláštní chování ukládání do mezipaměti, nastavte `varyByParam` na "žádný".  
  
## <a name="sql-cache-dependency"></a>Závislosti mezipaměti SQL  
 Odpovědi na webu HTTP služby můžete také uložit do mezipaměti závislosti mezipaměti SQL. Pokud vaše webové služby WCF HTTP závisí na data uložená ve službě SQL database, můžete ukládat do mezipaměti odpovědi služby a zneplatnit odpověď uložená v mezipaměti, když data v SQL databázi tabulku změn. Toto chování je zcela nastaven v souboru Web.config. Nejdřív je nutné definovat připojovacího řetězce v <`connectionStrings`> element.  
  
```xml
<connectionStrings>
  <add name="connectString"
       connectionString="Data Source=MyService;Initial Catalog=MyTestDatabase;Integrated Security=True"
       providerName="System.Data.SqlClient" />
</connectionStrings>
```  
  
 Pak je nutné povolit závislost mezipaměti SQL v rámci <`caching`> v elementu <`system.web`> element, jak je znázorněno v následujícím příkladu config.  
  
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
  
 Tady je povolené závislosti mezipaměti SQL a nastavte čas dotazování na 1000 milisekund. Pokaždé, když uplyne dotazování tabulky databáze je kontrola aktualizací. Pokud se zjistí změny obsahu mezipaměti se odeberou a při příštím operace služby je vyvolána nová odpověď do mezipaměti. V rámci <`sqlCacheDependency`> element přidejte databáze a odkazují na řetězce připojení v rámci <`databases`> element, jak je znázorněno v následujícím příkladu.  
  
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
  
 Dále musíte nakonfigurovat nastavení výstupní mezipaměti v rámci <`caching`> element, jak je znázorněno v následujícím příkladu.  
  
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
  
 Zde je na 60 sekund, nastavit dobu uložení do mezipaměti `varyByParam` je nastavena na hodnotu none a `sqlDependency` nastavena na středníkem oddělený seznam dvojic název/tabulky databáze odděleny dvojtečkami. Když data v `MyTable` změně odpověď uložená v mezipaměti pro operaci služby se odebere a po vyvolání operace nová odpověď vygenerovaných (podle volání operace služby) a vrácen do klienta do mezipaměti.  
  
> [!IMPORTANT]
>  Pro technologii ASP.NET pro přístup k databázi SQL, je nutné použít [nástroj registrace serveru SQL Server ASP.NET](https://go.microsoft.com/fwlink/?LinkId=152536). Kromě toho musí umožňovat odpovídající uživatelskému účtu přístup do databáze a tabulky. Další informace najdete v tématu [přístup k SQL serveru z webové aplikace](https://go.microsoft.com/fwlink/?LinkId=178988).  
  
## <a name="conditional-http-get-based-caching"></a>Podmíněné získat založený na HTTP ukládání do mezipaměti  
 Ve scénářích webových služeb HTTP podmíněné HTTP GET často dělají, když služby k implementaci inteligentního ukládání do mezipaměti HTTP, jak je popsáno v [specifikaci protokolu HTTP](https://go.microsoft.com/fwlink/?LinkId=165800). K tomu službu musí nastavit hodnotu hlavičky značky ETag do odpovědi HTTP. Také musíte zkontroluje hlavičky If-None-Match v požadavku HTTP, zda všechny zadané značky ETag odpovídá aktuální značku ETag.  
  
 Pro požadavky GET a HEAD <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> přebírá hodnotu značky ETag a ověří proti hlavičku If-None-Match požadavku. Pokud je k dispozici na záhlaví a pokud se zjistí shoda, <xref:System.ServiceModel.Web.WebFaultException> s HTTP se stavovým kódem 304 (Neupraveno) vyvolána a přidá hlavičku ETag do odpovědi s odpovídající značky ETag.  
  
 Jednomu přetížení <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> metoda přijímá datum poslední změny a ověří proti hlavičku If-Modified-Since požadavku. Pokud je k dispozici záhlaví a prostředek nebyl změněn od, <xref:System.ServiceModel.Web.WebFaultException> pomocí protokolu HTTP se stavovým kódem 304 (Neupraveno) vyvolána.  
  
 Pro požadavky PUT, POST a DELETE <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> trvá aktuální hodnotou ETag prostředku. Pokud aktuální značka ETag hodnota null, metoda zkontroluje, že hlavičku If-None-Match má hodnotu "*".  Pokud aktuální hodnotou ETag není výchozí hodnotu, metoda zkontroluje aktuální hodnotou ETag proti hlavičku If - Match požadavku. V obou případech se vyvolá metodu <xref:System.ServiceModel.Web.WebFaultException> se stavem HTTP kód 412 (Předběžná podmínka je neplatná), pokud není očekávaná hlavička v požadavku nebo jeho hodnota nevyhovuje podmíněnou kontrolu a nastaví hlavičku ETag do odpovědi na aktuální značku ETag hodnota.  
  
 Oba `CheckConditional` metody a <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> metoda zajišťuje, že hodnota ETag, nastavte v hlavičce odpovědi platná značka ETag podle specifikace protokolu HTTP. To zahrnuje hodnota ETag v dvojitých uvozovkách okolo, pokud již nejsou k dispozici a správně uvozovací znaky interní dvojité uvozovky. Porovnání slabou značku ETag není podporován.  
  
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
  
## <a name="security-considerations"></a>Důležité informace o zabezpečení  
 Požadavky, které vyžadují autorizace by neměly mít odpovědi v mezipaměti, protože autorizace se neprovede, pokud odpovědi se načítají z mezipaměti.  Ukládání do mezipaměti takové odpovědi by vznikla vážná chyba zabezpečení.  Obvykle požadavky, které vyžadují autorizace poskytují uživatelská data a proto není ještě výhodné ukládání do mezipaměti na straně serveru.  V takových situacích ukládání do mezipaměti na straně klienta nebo jednoduše ne ukládání do mezipaměti vůbec bude vhodnější.
