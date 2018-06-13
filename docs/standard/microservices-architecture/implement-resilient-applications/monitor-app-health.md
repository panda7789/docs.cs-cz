---
title: Monitorování stavu
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Monitorování stavu
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: 81c4fc7662212bb3c6586a590d87e731220b7b7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33578869"
---
# <a name="health-monitoring"></a>Monitorování stavu

Sledování stavu můžete povolit téměř v reálném čase informací o stavu kontejnery a mikroslužeb. Sledování stavu je pro několik aspektů operačního mikroslužeb a je zvlášť důležité při orchestrators částečné aplikace upgrady provádět v fází, jak je popsáno později.

Aplikace založené na Mikroslužeb často používají prezenčních signálů nebo stavu ověří jejich monitorování výkonu, plánovače a orchestrators ke sledování velkého množství services povolit. Pokud služby nelze odeslat nějaká "Jsem zachování" signálu na vyžádání nebo podle plánu, může aplikace čelí rizika při nasazení aktualizací, nebo může být jednoduše příliš pozdní rozpoznala chyby a není možné zastavit kaskádových chyb, které se můžou skončit ve hlavní výpadků.

V typické modelu služby odesílat zprávy o jejich stavu a zobrazují se tyto informace k poskytování celkový přehled o stavu stavu aplikace. Pokud používáte orchestrator, zajistíte tak, aby cluster může fungovat odpovídajícím způsobem informace o stavu vaší orchestrator clusteru. Pokud jste investovat do vysoce kvalitní stavu vytváření sestav, které je přizpůsobené pro vaši aplikaci, můžete zjistit a opravit problémy mnohem snadněji pro běžící aplikaci.

## <a name="implementing-health-checks-in-aspnet-core-services"></a>Implementace stavu změnami ASP.NET Core services

Při vývoji aplikace ASP.NET Core mikroslužbu nebo webové aplikace, můžete použít out-of-band knihovny (není oficiální jako součást ASP.NETCore) s názvem `HealthChecks` od týmu ASP.NET. Je k dispozici v této [úložiště GitHub](https://github.com/dotnet-architecture/HealthChecks).

Tato knihovna je snadno použitelný a poskytuje funkce, která umožňují, které jste ověřte, že žádné konkrétní externí prostředek pro vaši aplikaci (například databáze systému SQL Server nebo rozhraní API pro vzdálené) správně funguje. Při použití této knihovny, můžete také určit, co znamená, že je prostředek v pořádku, protože objasníme později.

Chcete-li použít tuto knihovnu, musíte nejprve použít knihovnu v vaší mikroslužeb. Druhý musíte aplikace front-endu, který se dotazuje pro sestavy stavu. Který front-endu aplikace může být vlastní vytváření sestav aplikace, nebo může být orchestrator sám sebe, který můžete odpovídajícím způsobem reagovat na stav.

### <a name="using-the-healthchecks-library-in-your-back-end-aspnet-microservices"></a>Použití knihovny HealthChecks v back-end vašeho mikroslužeb ASP.NET

Uvidíte použití knihovny HealthChecks v eShopOnContainers ukázkovou aplikaci. Pokud chcete začít, musíte definovat, co se považuje za dobrý stav pro každý mikroslužby. V ukázkové aplikace jsou v pořádku, pokud mikroslužbu rozhraní API je přístupná prostřednictvím protokolu HTTP a jeho souvisejících databáze systému SQL Server je také k dispozici mikroslužeb.

V budoucnu nebudete moct instalovat knihovně HealthChecks jako balíčku NuGet. Ale v době psaní tohoto textu, budete muset stáhnout a zkompilovat kód v rámci vašeho řešení. Zkopírujte kód, který je k dispozici na https://github.com/dotnet-architecture/HealthChecks a zkopírujte do řešení pro následující složky:

  - src/společné
  - src/Microsoft.AspNetCore.HealthChecks
  - src/Microsoft.Extensions.HealthChecks
  - src/Microsoft.Extensions.HealthChecks.SqlServer

Můžete také použít další kontroly, jako jsou pro Azure (Microsoft.Extensions.HealthChecks.AzureStorage), ale vzhledem k tomu, že tato verze eShopOnContainers nemá žádné závislosti na platformě Azure, není nutné. Není nutné kontroly stavu ASP.NET, protože eShopOnContainers je založena na ASP.NET Core.

Obrázek 10-6 ukazuje knihovně HealthChecks v sadě Visual Studio, budete moct používat jako stavební blok ve všech mikroslužeb.

![](./media/image6.png)

**Obrázek 10-6**. ASP.NET Core HealthChecks knihovny zdrojový kód v řešení sady Visual Studio

Zavádí dříve, je první věc, kterou chcete provést v jednotlivých projektů mikroslužbu se přidat odkaz na tři HealthChecks knihovny. Potom přidáte akce kontroly stavu, které chcete provést v této mikroslužby. Tyto akce jsou v podstatě závislosti na jiných mikroslužeb (HttpUrlCheck) nebo databáze (aktuálně SqlCheck\* databází systému SQL Server). Můžete přidat akce v rámci třídy spuštění každé mikroslužbu ASP.NET nebo webové aplikace ASP.NET.

Každá služba nebo webové aplikace musí být nakonfigurovaný tak, že přidáte všechny jeho závislosti protokolu HTTP nebo databáze jako jednu metodu AddHealthCheck. Například webové aplikace MVC z eShopOnContainers závisí na mnoha službách, proto má několik metod AddCheck přidány do kontroly stavu.

Následující kód například uvidíte jak mikroslužbu katalogu přidá závislost na svou databázi systému SQL Server.

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

Webová aplikace MVC z eShopOnContainers však má více závislostí na zbytek mikroslužeb. Proto volá metodu jeden AddUrlCheck pro každý mikroslužbu, jak je znázorněno v následujícím příkladu:

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

Mikroslužbu proto nebude poskytovat "v pořádku" stav, dokud všechny jeho kontroly jsou také v pořádku.

Pokud mikroslužbu nemá závislost na službě, nebo na serveru SQL Server, měli byste přidat jenom kontrolu Healthy("Ok"). Následující kód je z mikroslužbu basket.api eShopOnContainers. (Nákupní košík mikroslužbu používá mezipaměť Redis, ale knihovny ještě nezahrnuje poskytovatele Kontrola stavu Redis.)

```csharp
services.AddHealthChecks(checks =>
{
    checks.AddValueTaskCheck("HTTP Endpoint", () => new
        ValueTask<IHealthCheckResult>(HealthCheckResult.Healthy("Ok")));
});
```

Pro službu nebo webovou aplikaci vystavit koncový bod kontrolu stavu, je povolit UseHealthChecks (\[*url\_pro\_stavu\_kontroluje*\]) rozšíření Metoda. Tato metoda přejde na WebHostBuilder úrovni v metodě hlavní třídy Program ASP.NET Core služby nebo webové aplikace, hned po UseKestrel, jak je znázorněno v následujícím kódu.

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

Probíhá proces takto: každý mikroslužbu zpřístupní HC koncový bod. Vytvoří tohoto koncového bodu se HealthChecks knihovny ASP.NET Core middleware. Po vyvolání tohoto koncového bodu spustí všechny kontroly stavu, které jsou nakonfigurované v metodě AddHealthChecks ve třídě spuštění.

Metoda UseHealthChecks očekává, že port nebo cestu. Tento port nebo cesta je koncový bod pomocí zkontrolovat stav služby. Mikroslužbu katalogu pro instanci používá HC cestu.

### <a name="caching-health-check-responses"></a>Ukládání do mezipaměti odpovědi kontroly stavu

Vzhledem k tomu, že nechcete způsobit odepření služby (DoS) v službách nebo jednoduše není chcete dopad na výkon služby kontrolou prostředky příliš často, můžete se vrátí do mezipaměti a nakonfigurovat trvání mezipaměti pro každý kontrolu stavu.

Ve výchozím nastavení Doba uložení do mezipaměti interně nastavena na 5 minut, ale můžete změnit dobu trvání této mezipaměti na každou kontrolou stavu, jako v následujícím kódu:

```csharp
checks.AddUrlCheck(Configuration["CatalogUrl"],1); // 1 min as cache duration
```

### <a name="querying-your-microservices-to-report-about-their-health-status"></a>Dotazování vaší mikroslužeb na zprávu o jejich stav

Pokud jste nakonfigurovali kontroly stavu podle postupu popsaného tady, jakmile mikroslužbu běží v Docker, můžete přímo zkontrolovat z prohlížeče pokud je v pořádku. (To vyžadovat, že publikujete port kontejneru mimo Docker hostitele, dostanete kontejneru prostřednictvím místního hostitele nebo externí IP hostitelů Docker.) Obrázek 10-7 zobrazuje v prohlížeči a odpovídající reakce žádost.

![](./media/image7.png)

**Obrázek 10-7**. Kontroluje stav služby jednoho z prohlížeče

V testu uvidíte, že je v pořádku, mikroslužbu catalog.api (spuštěn na portu 5101) vrací informace o stavu a stav protokolu HTTP 200 ve formátu JSON. Také znamená, že interně službu také zkontrolovat stav jeho závislost databáze systému SQL Server a že kontrola stavu se samo označuje jako v pořádku.

## <a name="using-watchdogs"></a>Pomocí watchdogs

Sledovací zařízení je samostatný služba, která může sledovat stav a zatížení v rámci služeb a stavu sestavy o mikroslužeb dotazováním s knihovnou HealthChecks zavedená dříve. To může pomoct zabránit chybám, které by se na základě zobrazení jedné služby. Watchdogs jsou také vhodné místo pro hostitele kód, který můžete provést nápravné akce pro známé podmínky bez zásahu uživatele.

Ukázka eShopOnContainers obsahuje webové stránky, která zobrazuje vzorové sestavy kontrolu stavu, jak ukazuje obrázek 10-8. Toto je nejjednodušší sledovací zařízení můžete mít, protože všechny dělá jsou ukazuje stav mikroslužeb a webové aplikace v eShopOnContainers. Sledovací zařízení obvykle také provede akce, když zjistí stavy není v pořádku.

![](./media/image8.png)

**Obrázek 10-8**. Ukázková sestava kontroly stavu v eShopOnContainers

V souhrnu poskytuje middleware ASP.NET knihovny ASP.NET Core HealthChecks kontrola koncový bod jednoho stavu pro každý mikroslužby. Tato akce provést kontroly stavu definované v něm a vrátit celkového přehledu o stavu v závislosti na všechny tyto kontroly.

Knihovna HealthChecks je rozšiřitelný prostřednictvím nové kontroly stavu budoucí externích zdrojů. Například Očekáváme, že v budoucnosti knihovny bude mít kontroly stavu pro Redis cache a pro jiné databáze. Knihovny umožňuje stavu hlášení více závislostí služby nebo aplikace, a můžete pak proveďte akce založené na těchto kontroly stavu.

## <a name="health-checks-when-using-orchestrators"></a>Kontroly stavu při použití orchestrators

Ke sledování dostupnosti vaší mikroslužeb, orchestrators jako Docker Swarm, Kubernetes a Service Fabric pravidelně provádět kontroly stavu pomocí zasílání požadavků na test mikroslužeb. Když orchestrator zjistí, že služba nebo kontejner není v pořádku, že zastaví směrování požadavků do této instance. Také obvykle vytvoří novou instanci tohoto kontejneru.

Většina orchestrators pro instanci, můžete použít kontroly stavu pro správu nasazení nula. výpadků. Pouze v případě, že bude stav kontejneru služby nebo změny pořádku orchestrator spustit směrování provozu do kontejneru služby nebo instancí.

Sledování stavu je obzvláště důležité, když orchestrator provádí upgrade aplikace. Některé orchestrators (např. Azure Service Fabric) aktualizujte služby v fáze – například může aktualizovat jeden pátý povrchu clusteru pro každý upgradu aplikace. Sada uzlů, která se upgraduje současně se označuje jako *upgradovací doméně*. Po každé upgradované domény byl upgradován a je k dispozici pro uživatele, že upgradovací doméně musí projít kontroly stavu, než nasazení přikročí k další upgradovací doméně.

Další aspekt stav služby je generování sestav metriky ze služby. Toto je jednou z upřesňujících možností stavu modelu některé orchestrators, jako je Service Fabric. Metriky jsou důležité při použití orchestrator, protože se používají k vyrovnávání využití prostředků. Metriky taky může být indikátor stavu systému. Například můžete mít aplikace, která má mnoho mikroslužeb a každá instance sestavy metrika požadavků za sekundu (RPS). Pokud se jedna služba používá více prostředků (paměť, procesor atd.) než jiné službě, orchestrator může pohyb instance služby v clusteru, a pokuste se udržovat i využití prostředků.

Všimněte si, že pokud používáte Azure Service Fabric, poskytuje svou vlastní [sledování stavu modelu](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction), což je pokročilejší než kontroly stavu jednoduché.

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a>Rozšířené monitorování: vizualizace, analýzu a výstrahy

Poslední část monitorování je vizualizace proudu událostí, zprávy o výkonu služby a výstrahy, když se zjistí problém. Různá řešení můžete použít pro tento aspekt monitorování.

Můžete použít jednoduchý vlastních aplikací zobrazující stavu vašich služeb, jako jsou vlastní stránky jsme vám ukázal, když jsme vysvětlené [ASP.NET Core HealthChecks](https://github.com/aspnet/HealthChecks). Nebo můžete použít pokročilejší nástroje, například Azure Application Insights a Operations Management Suite budou generovány výstrahy založené na události datového proudu.

Nakonec pokud byly ukládání všech datových proudů událostí, můžete Microsoft Power BI nebo řešení třetí strany, jako je Kibana nebo Splunk můžete znázorňovat data.

## <a name="additional-resources"></a>Další zdroje

-   **ASP.NET Core HealthChecks** (předběžnou verzi) [*https://github.com/aspnet/HealthChecks/*](https://github.com/aspnet/HealthChecks/)

-   **Úvod do monitorování stavu Service Fabric**
    [*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)

-   **Azure Application Insights**
    [*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)

-   **Microsoft Operations Management Suite**
    [*https://www.microsoft.com/en-us/cloud-platform/operations-management-suite*](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)

>[!div class="step-by-step"]
[Předchozí] (implementace okruh dělení pattern.md) [Další] (.. /Secure-NET-microservices-Web-Applications/index.MD)
