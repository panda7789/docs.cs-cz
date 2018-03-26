---
title: Podpora ukládání dat do mezipaměti pro webové HTTP služby WCF
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f8078e0-00d9-415c-b8ba-c1b6d5c31799
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 723f485ab45cbe127bfd337c2d428d38d5f27232
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2018
---
# <a name="caching-support-for-wcf-web-http-services"></a>Podpora ukládání dat do mezipaměti pro webové HTTP služby WCF
[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] umožňuje používat deklarativní ukládání do mezipaměti mechanismus, který je již k dispozici v technologii ASP.NET v službách WCF Web HTTP. To vám umožní do mezipaměti odpovědi z vaší operací služby WCF Web HTTP. Když uživatel odešle do služby, který je nakonfigurován pro ukládání do mezipaměti GET protokolu HTTP, ASP.NET zašle zpět odpověď uložená v mezipaměti a není volána metoda služby. Když vyprší platnost mezipaměti, při příštím uživatel odešle HTTP GET, se nazývá metodu služby a ještě jednou do mezipaměti odpovědi. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] Ukládání do mezipaměti, ASP.NET, najdete v části [přehled ukládání do mezipaměti technologie ASP.NET](http://go.microsoft.com/fwlink/?LinkId=152534)  
  
## <a name="basic-web-http-service-caching"></a>Základní webové služby HTTP ukládání do mezipaměti  
 Povolit HTTP webové služby ukládání do mezipaměti je třeba nejprve povolit režim kompatibility ASP.NET použitím <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> na nastavení služby <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute.RequirementsMode%2A> k <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Allowed> nebo <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsMode.Required>.  
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)] zavádí nový atribut názvem <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> , můžete zadat název profilu mezipaměti. Tento atribut se používá pro operaci služby. Následující příklad se vztahuje <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> službě povolit režim kompatibility ASP.NET a nakonfiguruje `GetCustomer` operace pro ukládání do mezipaměti. <!--zz<xref:System.ServiceModel.Activation.AspNetCacheProfileAttribute>--> `System.ServiceModel.Activation.AspNetCacheProfileAttribute` Atribut určuje profil mezipaměti, který obsahuje nastavení mezipaměti, který se má použít.  
  
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
  
 Také je potřeba zapnout režim kompatibility ASP.NET v souboru Web.config, jak je znázorněno v následujícím příkladu.  
  
```xml
<system.serviceModel>
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
</system.serviceModel>
```
  
> [!WARNING]
>  Pokud není zapnutý režim kompatibility ASP.NET a <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> se používá k výjimce.  
  
 Název profilu mezipaměti určeného <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> identifikuje profil mezipaměti, který je přidán do konfiguračního souboru Web.config. Profil mezipaměti je definován s v <`outputCacheSetting`> elementu, jak je znázorněno v následujícím příkladu konfigurace.  
  
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
  
 Toto je stejný element konfigurace, který je k dispozici pro aplikace ASP.NET. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] Profilech mezipaměti ASP.NET, najdete v tématu <xref:System.Web.Configuration.OutputCacheProfile>. Webové služby HTTP jsou nejdůležitější atributy v mezipaměti profilu: `cacheDuration` a `varyByParam`. Obě tyto atributy se vyžadují. `cacheDuration` Nastaví množství času, které do mezipaměti odpovědi v sekundách. `varyByParam` Umožňuje zadat parametr řetězce dotazu, který se používá k odpovědi v mezipaměti. Všechny požadavky vytvořené s hodnotami parametrů řetězce dotazu jsou samostatně do mezipaměti. Například po počáteční žádosti http://MyServer/MyHttpService/MyOperation?param=10 všechny následné žádosti se stejným identifikátorem URI by vrátit odpověď uložená v mezipaměti (tak dlouho, dokud není uplynul doba uložení do mezipaměti). V odpovědi na podobné požadavek, který je stejný, ale má jinou hodnotu pro parametr řetězce dotazu parametr samostatně mezipaměti. Pokud nechcete, aby tento samostatné chování ukládání do mezipaměti, nastavte `varyByParam` na "žádný".  
  
## <a name="sql-cache-dependency"></a>Závislost SQL mezipaměti  
 Webové HTTP služby odezvy také do mezipaměti se závislostí mezipaměti SQL. Pokud vaše webové služby WCF HTTP závisí na data uložená v databázi SQL, můžete ukládat do mezipaměti odpovědi služby a zrušit platnost odpověď uložená v mezipaměti, když data v SQL databázi změny tabulky. Toto chování je úplně nakonfigurován v souboru Web.config. Nejdřív je nutné definovat připojovací řetězec <`connectionStrings`> elementu.  
  
```xml
<connectionStrings>
  <add name="connectString"
       connectionString="Data Source=MyService;Initial Catalog=MyTestDatabase;Integrated Security=True"
       providerName="System.Data.SqlClient" />
</connectionStrings>
```  
  
 Pak musíte povolit mezipaměť závislost SQL v rámci <`caching`> v rámci <`system.web`> elementu, jak je znázorněno v následujícím příkladu konfigurace.  
  
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
  
 Zde je povolené závislost SQL mezipaměti a čas dotazování na 1000 milisekund se nastavuje. Pokaždé, když uplyne časový dotazování tabulky databáze je kontrola aktualizací. Pokud byly zjištěny změny obsahu mezipaměti, se odeberou a další čas, kdy operace služby je volána novou odpověď se uloží do mezipaměti. V rámci <`sqlCacheDependency`> elementu přidejte databáze a odkazovat na připojovací řetězce v rámci <`databases`> elementu, jak je znázorněno v následujícím příkladu.  
  
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
  
 Dále musíte nakonfigurovat nastavení výstupní mezipaměti v rámci <`caching`> elementu, jak je znázorněno v následujícím příkladu.  
  
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
  
 Zde je doba uložení do mezipaměti nastavena na 60 sekund, `varyByParam` je nastaven na hodnotu none a `sqlDependency` nastavena na seznam oddělený středníky páry název/tabulky databáze oddělené dvojtečkou. Pokud data v `MyTable` změní odpovědi v mezipaměti pro operaci služby se odebere a po vyvolání operace novou odpověď je generována (voláním operace služby), do mezipaměti a vrátí klientovi.  
  
> [!IMPORTANT]
>  Pro technologii ASP.NET pro přístup k databázi SQL, je nutné použít [nástroj registrace serveru SQL Server ASP.NET](http://go.microsoft.com/fwlink/?LinkId=152536). Kromě toho musíte povolit odpovídající uživatelskému účtu přístup do databáze a tabulky. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Přístup k systému SQL Server z webové aplikace](http://go.microsoft.com/fwlink/?LinkId=178988).  
  
## <a name="conditional-http-get-based-caching"></a>Podmíněné HTTP GET na základě ukládání do mezipaměti  
 Ve scénářích Web HTTP podmíněného GET protokolu HTTP se často používá služby k implementaci inteligentního ukládání do mezipaměti protokolu HTTP, jak je popsáno v [specifikace protokolu HTTP](http://go.microsoft.com/fwlink/?LinkId=165800). K tomu službu nutné nastavit hodnotu hlavičky značky ETag v odpovědi HTTP. Je také nutné zkontrolovat hlavičku If-None-Match v požadavku HTTP, zda všechny zadané značky ETag odpovídá aktuální značka ETag.  
  
 Pro požadavky GET a HEAD <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> přebírá hodnotu ETag a ověří proti hlavičku If-None-Match požadavku. Pokud je k dispozici hlavičku a je nalezena shoda, <xref:System.ServiceModel.Web.WebFaultException> s protokolem HTTP je vyvolána stavový kód 304 (upraveno) a hlavičku ETag se přidá do odpovědi s odpovídající značky ETag.  
  
 Jedním přetížením <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> metoda přebírá datum poslední změny a ověří proti hlavičku If-upravit-Since požadavku. Pokud je k dispozici záhlaví a prostředek nebyl upraven od, <xref:System.ServiceModel.Web.WebFaultException> pomocí protokolu HTTP je vyvolána stavový kód 304 (upraveno).  
  
 Pro požadavky PUT, POST a odstranění <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> načítá aktuální hodnotu ETag prostředku. Pokud je aktuální hodnota ETag hodnotu null, metoda kontroluje, zda záhlaví If-None-Match má hodnotu "*".  Pokud je aktuální hodnota ETag není výchozí hodnotu, zkontroluje tato metoda aktuální hodnota ETag proti hlavičku If - Match požadavku. V obou případech vyvolá metoda <xref:System.ServiceModel.Web.WebFaultException> se stavem HTTP code 412 (nezdařil se předběžnou podmínku), pokud očekávaný hlavičky není přítomné v žádosti nebo nevyhovuje podmíněného zkontrolujte jeho hodnotu a nastaví hlavičku ETag odpovědi na aktuální značka ETag hodnota.  
  
 Obě `CheckConditional` metody a <xref:System.ServiceModel.Web.OutgoingWebResponseContext.SetETag%2A> metoda zajišťuje, že značka ETag nastavenou na hlavičku odpovědi na platnou značku ETag podle specifikace protokolu HTTP. To zahrnuje, které obaluje ETag hodnotu do dvojitých uvozovek, pokud již nejsou přítomny a správně uvozovací znaky znaky interní dvojitých uvozovek. Slabé porovnání značka ETag není podporována.  
  
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
 Požadavky, které vyžadují autorizace by neměl mít jejich odpovědi v mezipaměti, protože autorizaci se neprovede, pokud je odpověď obsluhovat z mezipaměti.  Ukládání do mezipaměti tyto odpovědi by vznikla chyba závažné zabezpečení.  Obvykle požadavky, které vyžadují autorizace poskytují uživatelská data a proto není i výhodné ukládání do mezipaměti na straně serveru.  V takových situacích ukládání do mezipaměti na straně klienta nebo jednoduše není ukládání do mezipaměti na všech bude vhodnější.
