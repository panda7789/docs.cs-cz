---
title: Monitorování stavu
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Monitorování stavu
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: 35f6d773d714878f56a5e9151320072ebcd51e06
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53145972"
---
# <a name="health-monitoring"></a>Monitorování stavu

Monitorování stavu umožňuje téměř v reálném čase informace o stavu kontejnerů a mikroslužeb. Monitorování stavu je zásadní pro několik aspektů provoz mikroslužeb a je zvlášť důležité při orchestrátorů provést upgrady částečné použití argumentů ve fázích, jak je popsáno později.

Aplikace založená na Mikroslužbách často používají prezenční signály nebo povolit jejich sledování výkonu, plánovače a orchestrátory můžete sledovat různé služby, doplněk pro kontroly stavu. Pokud služby nelze odeslat nějaký druh "Jsem aktivní" signálu na vyžádání nebo podle plánu, může vaše aplikace musí rizika při nasazení aktualizací, nebo může být příliš pozdě. stačí zjišťování chyb a nebylo možné zastavit kaskádové chyby, ke kterým může ukládaly do hlavní výpadků.

V typické modelu služby odesílat zprávy o stavu a zobrazují se tyto informace poskytnout celkový přehled o stavu stavu aplikace. Pokud používáte orchestrator, můžete zadat informace o stavu vaší orchestrator clusteru tak, aby cluster můžete příslušně na ně reagovat. Pokud Investujete do sestav stavu vysoce kvalitní, který je přizpůsobený pro vaši aplikaci, můžete zjistit a opravit problémy pro běžící aplikaci mnohem snadněji.

## <a name="implementing-health-checks-in-aspnet-core-services"></a>Implementace stavu kontroluje služby ASP.NET Core

Při vytváření mikroslužeb nebo webové aplikace ASP.NET Core, můžete použít knihovnu out-of-band (ne official je přínosné jako součást ASP.NETCore) s názvem `HealthChecks` od týmu služby ASP.NET. Je k dispozici na tomto [úložiště GitHub se vzorovými](https://github.com/dotnet-architecture/HealthChecks).

Tato knihovna se snadno používá a nabízí funkce, které umožňují, ověřte, že žádné konkrétní externího zdroje potřebné pro vaši aplikaci (například databáze systému SQL Server nebo vzdálené rozhraní API) správně funguje. Při použití této knihovny, můžete také rozhodnout, co znamená to, jestli prostředek je v pořádku, protože vám vysvětlíme, později.

Chcete-li použít tuto knihovnu, budete muset nejdřív použít knihovnu v mikroslužby. Za druhé budete potřebovat front-endové aplikace, který se dotazuje sestavy o stavu. Který aplikace front-endu může být vlastní aplikace pro vytváření sestav, nebo to může být orchestrátor samotného, můžete odpovídajícím způsobem reagovat na stav.

### <a name="using-the-healthchecks-library-in-your-back-end-aspnet-microservices"></a>Použití knihovny HealthChecks v back-endu ASP.NET mikroslužeb

Uvidíte jak knihovny HealthChecks slouží v aplikaci eShopOnContainers ukázkovou aplikaci. Pokud chcete začít, musíte definovat, co se považuje za bezproblémového stavu u jednotlivých mikroslužeb. V ukázkové aplikaci mikroslužby jsou v pořádku, pokud mikroslužeb rozhraní API jsou přístupná přes protokol HTTP a pokud jeho související databáze systému SQL Server je také k dispozici.

V budoucnu bude možné ji nainstalovat HealthChecks jako balíček NuGet. Ale v době psaní tohoto návodu budete muset stáhnout a kompilaci kódu jako součást vašeho řešení. Klonování kódu, které jsou k dispozici na https://github.com/dotnet-architecture/HealthChecks a zkopírujte následující složky do vašeho řešení:

  - src/common
  - src/Microsoft.AspNetCore.HealthChecks
  - src/Microsoft.Extensions.HealthChecks
  - src/Microsoft.Extensions.HealthChecks.SqlServer

Můžete také použít další kontroly, jako jsou pro Azure (Microsoft.Extensions.HealthChecks.AzureStorage), ale vzhledem k tomu, že tato verze aplikaci eShopOnContainers nemá závislost na Azure, není nutné. Není nutné ASP.NET kontroly stavu, protože aplikaci eShopOnContainers je založena na technologii ASP.NET Core.

Obrázek 10 až 6 ukazuje HealthChecks knihovny v sadě Visual Studio, můžete využívat jako stavební blok všechny mikroslužby.

![](./media/image6.png)

**Obrázek 10 až 6**. Zdrojový kód knihovny ASP.NET Core HealthChecks v řešení sady Visual Studio

První věc, kterou provedete v každém projektu mikroslužeb zavedeném dříve, je přidejte odkaz na tři HealthChecks knihovny. Potom přidáte stav vrácení akce, které chcete provést v tomto mikroslužeb. Tyto akce jsou v podstatě závislosti na jiných mikroslužby (HttpUrlCheck) nebo databází (aktuálně SqlCheck\* databází systému SQL Server). Můžete přidat akce v rámci třídy spuštění jednotlivých mikroslužeb technologie ASP.NET nebo webové aplikace ASP.NET.

Každá služba nebo webové aplikace musí být nakonfigurovaný tak, že přidáte všechny její závislosti protokolu HTTP nebo databází jako jednu metodu AddHealthCheck. Například webové aplikace MVC v aplikaci eShopOnContainers závisí na mnoha službách, proto má několik metod AddCheck přidán na kontroly stavu.

V následujícím kódu, uvidíte jak mikroslužeb katalogu přidá závislost na jeho databáze systému SQL Server.

```csharp
// Startup.cs from Catalog.api microservice
//
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        // Add framework services
        services.AddHealthChecks(checks =>
        {
            checks.AddSqlCheck("CatalogDb", Configuration["ConnectionString"]);
        });
        // Other services
    }
}
```

Webovou aplikaci MVC aplikaci eShopOnContainers má ale více závislostí na zbývajících mikroslužby. Proto volání metod AddUrlCheck u jednotlivých mikroslužeb, jak je znázorněno v následujícím příkladu:

```csharp
// Startup.cs from the MVC web app
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();
        services.Configure<AppSettings>(Configuration);
        services.AddHealthChecks(checks =>
        {
            checks.AddUrlCheck(Configuration["CatalogUrl"]);
            checks.AddUrlCheck(Configuration["OrderingUrl"]);
            checks.AddUrlCheck(Configuration["BasketUrl"]);
            checks.AddUrlCheck(Configuration["IdentityUrl"]);
        });
    }
}
```

Mikroslužby proto neposkytne "v pořádku" stav, dokud všechny jeho kontroly jsou také v pořádku.

Pokud mikroslužbách nemá závislost na službě nebo na serveru SQL Server, měli byste přidat jenom kontrolu Healthy("Ok"). Následující kód se z mikroslužeb basket.api aplikaci eShopOnContainers. (Nákupní košík mikroslužeb používá mezipaměť Redis, ale knihovny zatím nezahrnuje zprostředkovatele Redis stav kontroly.)

```csharp
services.AddHealthChecks(checks =>
{
    checks.AddValueTaskCheck("HTTP Endpoint", () => new
        ValueTask<IHealthCheckResult>(HealthCheckResult.Healthy("Ok")));
});
```

Služby nebo webové aplikace zveřejněte koncový bod kontroly stavu, je třeba povolit UseHealthChecks (\[*url\_pro\_stavu\_kontroluje*\]) rozšíření Metoda. Tato metoda přejde na WebHostBuilder úrovně v hlavní metodě třídy aplikace ASP.NET Core service nebo webové aplikace, hned po UseKestrel, jak je znázorněno v následujícím kódu.

```csharp
namespace Microsoft.eShopOnContainers.WebMVC
{
    public class Program
    {
        public static void Main(string[] args)
        {
            var host = new WebHostBuilder()
                .UseKestrel()
                .UseHealthChecks("/hc")
                .UseContentRoot(Directory.GetCurrentDirectory())
                .UseIISIntegration()
                .UseStartup<Startup>()
                .Build();
            host.Run();
        }
    }
}
```

Tento proces funguje takto: jednotlivých mikroslužeb poskytuje HC koncový bod. Tento koncový bod se vytvořil HealthChecks knihovna middlewarových ASP.NET Core. Při vyvolání tohoto koncového bodu, spustí všechny kontroly stavu, které jsou nakonfigurované v metodě AddHealthChecks ve třídě spuštění.

Metoda UseHealthChecks očekává, že port nebo cestu. Tento port nebo cesta jsou koncový bod, který slouží ke kontrole stavu služby. Například mikroslužeb katalogu používá HC cestu.

### <a name="caching-health-check-responses"></a>Ukládání do mezipaměti odpovědi na kontrolu stavu

Vzhledem k tomu, že nechcete způsobit odepření služby (DoS) ve vašich službách nebo jednoduše nechcete dopad na výkon služby tak, že zkontrolujete prostředky příliš často, můžete vrátí do mezipaměti a nakonfigurovat doba mezipaměti pro každou kontrolu stavu.

Ve výchozím nastavení Doba uložení do mezipaměti interně nastavena na 5 minut, ale můžete změnit této mezipaměti na každé kontrolu stavu, stejně jako v následujícím kódu:

```csharp
checks.AddUrlCheck(Configuration["CatalogUrl"],1); // 1 min as cache duration
```

### <a name="querying-your-microservices-to-report-about-their-health-status"></a>Dotazování na mikroslužby na zprávu o jejich stavu

Kontroly stavu jste nakonfigurovali podle postupu popsaného tady, jakmile je spuštěna mikroslužby v Dockeru, můžete přímo zkontrolovat z prohlížeče pokud je v pořádku. (To vyžaduje, že publikujete port kontejneru Dockeru hostitele, tak prostřednictvím místního hostitele nebo externí IP adresa hostitele Docker můžete přístup ke kontejneru.) Obrázek 10-7 ukazuje požadavek v prohlížeči a odpovídající odpověď.

![](./media/image7.png)

**Obrázek 10-7**. Kontroluje se stav jedinou službou v prohlížeči

V testu uvidíte, že je v pořádku, mikroslužbách catalog.api (spuštěné na portu 5101) vrací stav protokolu HTTP 200 a informace o stavu ve formátu JSON. To také znamená, že interně služba zkontrolovány také stav jeho závislost databáze systému SQL Server a, kontrola stavu samotné byl nahlášen jako v pořádku.

## <a name="using-watchdogs"></a>Pomocí watchdogs

Sledovacího zařízení je samostatná služba, která může sledovat stav a zatížení napříč službami a stavu sestavy o mikroslužby pomocí dotazu s knihovnou HealthChecks zavedené dříve. To může pomoci zabránit chybám, které nebudou zjištěny založené na zobrazení jedné služby. Watchdogs je také vhodné místo pro hostování kódu, který může provádět nápravné akce pro známé podmínky bez zásahu uživatele.

Ukázkové aplikaci eShopOnContainers obsahuje webovou stránku, která zobrazí ukázkové sestavy stavu zaškrtnutí, jak ukazuje obrázek 10-8. Toto je nejjednodušší sledovacího zařízení může mít, protože celá jeho se zobrazují stav mikroslužbách a webových aplikací v aplikaci eShopOnContainers. Obvykle sledovacího zařízení také provede akce při zjišťuje stavy není v pořádku.

![](./media/image8.png)

**Obrázek 10-8**. Ukázková sestava kontroly stavu v aplikaci eShopOnContainers

Stručně řečeno middleware ASP.NET knihovny ASP.NET Core HealthChecks poskytuje koncový bod jednoho stavu zaškrtnutí u jednotlivých mikroslužeb. To spustí všechny kontroly stavu, v něm definovanou a vrátit celkového přehledu o stavu v závislosti na těchto kontrol.

Knihovna HealthChecks je rozšiřitelný prostřednictvím nové kontroly stavu budoucí externích prostředků. Například Očekáváme, že v budoucnu knihovny bude mít kontroly stavu pro mezipaměť Redis a pro ostatní databáze. Knihovny umožňuje zdraví, vytváření sestav ve více závislostí služby nebo aplikace, a pak můžete provádět akce založené na tyto kontroly stavu.

## <a name="health-checks-when-using-orchestrators"></a>Kontroly stavu při použití orchestrátorů

Pokud chcete monitorovat dostupnost mikroslužby, orchestrátorů, jako je Docker Swarm, Kubernetes a Service Fabric pravidelně provádět kontroly stavu pomocí zasílání požadavků na test mikroslužby. Když orchestrátor zjistí, že služby/kontejneru není v pořádku, že zastaví směrování požadavků do této instance. Také obvykle vytvoří novou instanci kontejneru.

Většina orchestrátorů, můžete použít kontroly stavu pro správu nasazení s nulovými výpadky. Pouze v případě, že bude stav kontejneru služby/změny v pořádku orchestrátoru start směrování provozu do služby a container instances.

Monitorování stavu je obzvláště důležité, když orchestrátor provádí upgrade aplikace. Některé zvolené orchestrátory (jako je Azure Service Fabric) aktualizovat služby ve fázích – například může aktualizovat jeden pátého povrchu clusteru pro každý upgrade aplikace. Sada uzlů, který se upgraduje ve stejnou dobu se označuje jako *upgradovací doména*. Po každé upgradovací doména byl upgradován a je k dispozici pro uživatele, že upgradovací doména musí uplynout kontroly stavu nasazení přejde k další upgradovací doméně.

Dalším aspektem služby service health je generování sestav metrik ze služby. Toto je rozšířená možnost modelu stavu některé zvolené orchestrátory, jako je Service Fabric. Metriky jsou důležité při použití orchestrator, protože se používají k vyrovnávání využití prostředků. Metriky taky může být indikátor stavu systému. Například může mít aplikaci, která má mnoho mikroslužeb a každá instance sestav metriky požadavků za sekundu (předávajících stran). Pokud jedna služba používá další prostředky (paměť, procesor, atd.) než jiné službě, orchestrator může pohybovat instance služby v clusteru se pokouší spravovat i využití prostředků.

Všimněte si, že pokud používáte Azure Service Fabric, poskytuje vlastní [monitorování stavu modelu](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction), což je složitější než kontroly stavu jednoduché.

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a>Rozšířené monitorování: vizualizace, analýzy a upozornění

Poslední část monitorování je vizualizace datového proudu událostí, vytváření sestav o výkonu služby a upozorní při zjištění problému. Můžete použít různá řešení pro tento aspekt monitorování.

Můžete použít jednoduchý vlastní aplikace zobrazuje stav služeb, stejně jako vlastní stránku jsme ukázali, když jsme vysvětlení [ASP.NET Core HealthChecks](https://github.com/aspnet/HealthChecks). Nebo můžete použít rozšířené nástroje, jako je Azure Application Insights a Operations Management Suite budou generovány výstrahy založené na události datového proudu.

Nakonec pokud byly ukládání všech datových proudů událostí, můžete použít Microsoft Power BI nebo řešení třetí strany, jako je Kibana nebo Splunk k vizualizaci dat.

## <a name="additional-resources"></a>Další zdroje

-   **ASP.NET Core HealthChecks** (dřívější verze) [*https://github.com/aspnet/HealthChecks/*](https://github.com/aspnet/HealthChecks/)

-   **Úvod do monitorování stavu Service Fabric**
    [*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)

-   **Azure Application Insights**
    [*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)

-   **Microsoft Operations Management Suite**
    [*https://www.microsoft.com/en-us/cloud-platform/operations-management-suite*](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)

>[!div class="step-by-step"]
>[Předchozí](implement-circuit-breaker-pattern.md)
>[další](../secure-net-microservices-web-applications/index.md)