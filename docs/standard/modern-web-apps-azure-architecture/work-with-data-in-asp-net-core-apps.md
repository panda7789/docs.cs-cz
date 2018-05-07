---
title: Práce s daty v aplikacích ASP.NET Core
description: Architektury moderních webových aplikací pomocí ASP.NET Core a Azure | Práce s daty v asp
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.openlocfilehash: 89df46c8e04e1826c84058e5d2a92d089eb96098
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="working-with-data-in-aspnet-core-apps"></a>Práce s daty v aplikacích ASP.NET Core

> "Data drahocenný jedinou a bude trvat déle, než systémy sami."

TIM Berners-Lee

## <a name="summary"></a>Souhrn

Přístup k datům je důležitou součástí téměř jakoukoli softwarová aplikace. ASP.NET Core podporuje celou řadu možností přístupu data, včetně Entity Framework Core (a také Entity Framework 6) a mohou pracovat s žádné rozhraní .NET framework data access. Výběr z nich přístup k datům framework použít závisí na potřebám aplikace. Poskytuje abstrakci tyto volby z projektů ApplicationCore a uživatelského rozhraní a zapouzdření podrobnosti implementace v infrastruktuře, pomáhá vytvářet volně párované, možností intenzivního testování softwaru.

## <a name="entity-framework-core-for-relational-databases"></a>Entity Framework Core (pro relační databáze)

Pokud píšete novou aplikaci ASP.NET Core, která musí pracovat s relačních dat, základní Entity Framework (EF jader) je doporučeným způsobem pro vaši aplikaci pro přístup k jeho data. Základní EF je objekt relační mapper (O/RM), která umožňuje zachovat objekty do a ze zdroje dat vývojáři v rozhraní .NET. Eliminuje potřebu většinu kódu přístup dat, které vývojáři obvykle potřebovat k zápisu. Jako ASP.NET Core jsou přepsána EF základní od základu podporuje modulární multiplatformní aplikace. Přidat do vaší aplikace jako balíčku NuGet, jeho konfiguraci v spuštění a žádostí pomocí vkládání závislostí, bez ohledu na to potřebujete.

Použití jádra EF s databázi systému SQL Server, spusťte následující příkaz dotnet rozhraní příkazového řádku:

Přidejte balíček Microsoft.EntityFrameworkCore.SqlServer DotNet.

Chcete-li přidat podporu pro zdroj dat InMemory pro testování:

Přidejte balíček Microsoft.EntityFrameworkCore.InMemory DotNet.

### <a name="the-dbcontext"></a>DbContext

Chcete-li pracovat s EF jádra, je třeba podtřídou třídy DbContext. Tato třída obsahuje vlastnosti představující kolekce entit, které vaše aplikace bude fungovat s. Ukázka eShopOnWeb zahrnuje CatalogContext s kolekcí pro položky, značky a typy:

```csharp
public class CatalogContext : DbContext
{
    public CatalogContext(DbContextOptions<CatalogContext> options) : base(options)
    {

    }

    public DbSet<CatalogItem> CatalogItems { get; set; }

    public DbSet<CatalogBrand> CatalogBrands { get; set; }

    public DbSet<CatalogType> CatalogTypes { get; set; }
}
```

Vaše DbContext musí mít konstruktor, který přijímá DbContextOptions a předat tento argument základní konstruktor DbContext. Všimněte si, že pokud máte pouze jeden DbContext v aplikaci, můžete předat instanci DbContextOptions, ale pokud máte více než jeden musíte použít obecné DbContextOptions<T> předávání v vašeho typu DbContext jako obecný parametr typu.

### <a name="configuring-ef-core"></a>Konfigurace EF jádra

V aplikaci ASP.NET Core obvykle nakonfigurujete EF základní ve své metodě ConfigureServices. Základní EF používá DbContextOptionsBuilder, která podporuje několik užitečné rozšiřující metody pro zjednodušit konfiguraci. Pokud chcete nakonfigurovat CatalogContext používat databázi systému SQL Server s připojovacím řetězcem definované v konfiguraci, by přidejte následující kód do ConfigureServices:

```csharp
services.AddDbContext<CatalogContext>(options => options.UseSqlServer (Configuration.GetConnectionString("DefaultConnection")));
```

Chcete použít databázi v paměti:

```csharp
services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```

Po instalaci základní EF, vytvořili podřízené typ DbContext a nakonfigurovat v ConfigureServices, budete chtít použít EF jádra. Můžete požádat o instanci typu DbContext v jakoukoli službu, která jej potřebuje a začít pracovat s trvalou pomocí LINQ, jako kdyby byly jednoduše v kolekci entit. Základní EF funguje překladu vaší LINQ – výrazy do dotazů SQL pro ukládání a načítání vaše data.

Můžete zobrazit dotazy EF základní provádí konfiguraci protokoly a zajištění jeho úroveň je nastavena alespoň na informace, jak ukazuje obrázek 8-1.

![](./media/image8-1.png)

Obrázek 8-1 protokolování EF základní dotazy do konzoly nástroje

### <a name="fetching-and-storing-data"></a>Načítání a ukládání dat

K načtení dat z EF jádra, přístup k příslušné vlastnosti a pomocí LINQ filtrovat výsledek. LINQ můžete použít také k provedení projekce, transformace jeden typ výsledku. V následujícím příkladu by načíst CatalogBrands, seřazené podle názvu, filtrovaná podle jejich vlastnost povoleno a promítnuta na typ SelectListItem:

```csharp
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem {
        Value = b.Id, Text = b.Name })
    .ToListAsync();
```

Je důležité v předchozím příkladu a přidejte volání do ToListAsync okamžitě provádění dotazu. Příkaz, jinak hodnota přiřadí položku IQueryable<SelectListItem> k brandItems, který nebude provedeno, dokud je ve výčtu. Existují výhody a nevýhody vrací IQueryable výsledky z metod. Umožňuje na dotaz, který EF základní vytvoří další upravovat, ale může taky vést chyb vzniklých pouze za běhu, pokud operace jsou přidány do dotazu, který nemůže překládat EF jádra. Obecně je bezpečnější k předání všechny filtry do metoda provádí přístup k datům a vraťte se zpět kolekci v paměti (například seznam<T>) jako výsledek.

Základní EF sleduje změny u entit, který je načte z trvalost. Pokud chcete uložit změny do sledované entity, stačí zavolat metodu SaveChanges pro dbcontext, ujistěte se, že je stejné instanci DbContext, která byla použita k načtení entity. Přidávání a odebírání entity je přímo na příslušnou vlastnost DbSet, znovu s volání SaveChanges příkazy databáze. Následující příklad ukazuje, přidání, aktualizace a odstranění entity z trvalost.

```csharp
// create
var newBrand = new CatalogBrand() { Brand = "Acme" };
_context.Add(newBrand);
await _context.SaveChangesAsync();

// read and update
var existingBrand = _context.CatalogBrands.Find(1);
existingBrand.Brand = "Updated Brand";
await _context.SaveChangesAsync();

// read and delete (alternate Find syntax)
var brandToDelete = _context.Find<CatalogBrand>(2);
_context.CatalogBrands.Remove(brandToDelete);
await _context.SaveChangesAsync();
```

Jádro EF podporuje i synchronní a asynchronní metody pro načítání a ukládání. V webových aplikací se doporučuje použití vzoru async/await s asynchronní metody, tak, aby webový server vláken nejsou blokované při čekání na dokončení operací přístupu pro data.

### <a name="fetching-related-data"></a>Načítají se související Data

Když EF základní načte entity, naplní všechny vlastnosti, které jsou uloženy přímo s dané entity v databázi. Navigační vlastnosti, jako je například seznam entit v relaci, nejsou naplněny a může mít jejich nastavená na hodnotu null. Tím se zajistí, že EF jádra není načítání více dat, než je potřeba, který je obzvláště důležité pro webové aplikace, které musí rychle zpracovávat požadavky a odpovědi vrátit účinným způsobem. Zahrnout relace se entitu s využitím *přes načítání*, určete vlastnost použití metody rozšíření zahrnout v dotazu, jak je znázorněno:

```csharp
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```

Může obsahovat více vztahů, a může zahrnovat i dílčí relace pomocí ThenInclude. Základní EF provede jeden dotaz pro načtení výslednou sadu entit.

Další možností pro načítání související data se má používat *explicitní načítání*. Explicitní načítání umožňuje načíst další data do entity, která již byla načtena. Vzhledem k tomu, že to zahrnuje samostatné žádosti do databáze, se nedoporučuje pro webové aplikace, které by měl minimalizovat počet databáze odezev provedené na základě požadavku.

*Opožděného načítání* je funkce, která automaticky načte související data, protože odkazuje na aplikaci. Není aktuálně podporována EF jádra, ale jako s explicitní načítání je obvykle třeba zakázat pro webové aplikace.

### <a name="resilient-connections"></a>Odolné připojení

Příležitostně externím prostředkům, jako jsou databáze SQL pravděpodobně není k dispozici. V případě dočasné nedostupnosti aplikace, můžete použít logika opakovaných pokusů předejdete vyvolání k výjimce. Tento postup se obvykle označuje jako *odolnost připojení*. Můžete implementovat vaše [vlastní znova s exponenciálního omezení rychlosti](https://docs.microsoft.com/azure/architecture/patterns/retry) technika pokusem o rety s exponenciálně roste doba čekání, až maximální počet opakování byl dosažen. Tento postup zahrnuje fakt, že cloudové prostředky občas je pravděpodobně není k dispozici na krátkou dobu, což vede k selhání některých požadavků.

Pro databáze SQL Azure Entity Framework Core již poskytuje interní databáze připojení odolnost proti chybám a zkuste to znovu logiku. Ale musíte povolit strategii provádění Entity Framework pro každé připojení DbContext, pokud chcete mít odolné EF základní připojení.

Například následující kód na úrovni připojení EF základní umožňuje odolné připojení SQL, které jsou opakovat, pokud se nepovede připojit.

```csharp
// Startup.cs from any ASP.NET Core Web API
public class Startup
{
    public IServiceProvider ConfigureServices(IServiceCollection services)
    {
        //...
        services.AddDbContext<OrderingContext>(options =>
        {
            options.UseSqlServer(Configuration["ConnectionString"],
            sqlServerOptionsAction: sqlOptions =>
        {
            sqlOptions.EnableRetryOnFailure(
            maxRetryCount: 5,
            maxRetryDelay: TimeSpan.FromSeconds(30), 
            errorNumbersToAdd: null); 
        });
    });
}
//...
```

  #### <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a>Strategie provádění a pomocí zahájení transakce a více DbContexts explicitních transakcí 
  
  Když opakování jsou povolena v připojení EF jádra, stane jednotlivých operací, které můžete provádět pomocí EF základní vlastní dá se zkusit znovu operaci. Každý dotaz a každé volání SaveChanges bude zopakován jako jednotku, pokud dojde k přechodné chybě.
  
  Ale pokud kódu inicializuje transakci pomocí zahájení transakce, definujete vlastní skupiny operací, které musí být považovány za jednotku – všechno uvnitř transakce se vrátila zpět v případě, že dojde k chybě. Pokud se pokusíte provést tuto transakci, při použití EF strategii provádění (zásady opakování) a zahrnují několik SaveChanges z více DbContexts v něm uvidíte výjimku podobně jako tento.

System.InvalidOperationException: V nakonfigurované strategii provádění 'SqlServerRetryingExecutionStrategy' nepodporuje transakce inicializované uživatelem. Použijte strategii provádění vrácený 'DbContext.Database.CreateExecutionStrategy()' provádět všechny operace v rámci transakce jako nevyřeší jednotku.

Řešení je ručně vyvolání strategie provádění EF s představující všechno delegáta, který je třeba provést. Pokud dojde k přechodné chybě, bude strategii provádění znovu vyvolání delegáta. Následující kód ukazuje, jak implementovat tohoto přístupu:

```csharp
// Use of an EF Core resiliency strategy when using multiple DbContexts
// within an explicit transaction
// See:
// https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency
var strategy = _catalogContext.Database.CreateExecutionStrategy(); 
await strategy.ExecuteAsync(async () =>
{
    // Achieving atomicity between original Catalog database operation and the
    // IntegrationEventLog thanks to a local transaction
    using (var transaction = _catalogContext.Database.BeginTransaction())
    {
        _catalogContext.CatalogItems.Update(catalogItem);
        await _catalogContext.SaveChangesAsync();
        
        // Save to EventLog only if product price changed
        if (raiseProductPriceChangedEvent)
        await _integrationEventLogService.SaveEventAsync(priceChangedEvent);
        transaction.Commit();
    }
});
```

Je první DbContext \_catalogContext a druhý je DbContext v rámci \_integrationEventLogService objektu. Nakonec potvrzení akce bude provedena více DbContexts a pomocí strategii provádění EF.

> ### <a name="references--entity-framework-core"></a>Odkazy – základní Entity Framework
> - **EF základní dokumentace**  
> <https://docs.microsoft.com/ef/>
> - **EF jádra: Související Data**  
> <https://docs.microsoft.com/ef/core/querying/related-data>
> - **Vyhněte se opožděného načítání entity v aplikacích ASPNET**  
> <https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications>

## <a name="ef-core-or-micro-orm"></a>Základní EF nebo micro ORM?

Při EF základní je je služba skvělou volbou pro správu trvalosti a ve většině případů zapouzdří podrobnosti databáze z vývojáři aplikace, není pouze volbu. Další alternativou populární open source je [Dapper](https://github.com/StackExchange/Dapper), takzvané micro ORM. Micro-ORM je lightweight, méně plnohodnotný nástroj pro mapování objektů na datové struktury. V případě Dapper návrh cíle soustředit na výkon, nikoli plně zapouzdřením základní dotazy používá načíst a aktualizovat data. Vzhledem k tomu, že ji nebude abstraktní SQL od vývojáře, Dapper "blíže počítač" a umožňuje vývojářům zápisu přesný operace přístupu k dotazy, které chtějí používat pro daná data.

Základní EF má dvě důležité funkce poskytuje které oddělení od Dapper, ale také přidat do jeho nároky na výkon. První je překlad z LINQ – výrazy do SQL. Tyto překlady jsou uložené v mezipaměti, ale i tak je zatížení při provádění je poprvé. Druhá je sledování změn na entity (tak, aby příkazy efektivní aktualizace může být generována). Toto chování může být vypnuto pro konkrétní dotazy pomocí AsNotTracking rozšíření. Základní EF vytvoří také dotazy SQL, které obvykle jsou velmi efektivně a v každém případě zcela přijatelné z hlediska výkonu, ale pokud je třeba přesně řídit provedení přesné dotazu, abyste mohli předávat vlastní SQL (nebo provedení uložené procedury) pomocí EF Příliš základní. V takovém případě Dapper stále překonává výkonem EF jádra, ale pouze mírně. Uvede Julie Lerman některé údaje o výkonu v její může článku na webu MSDN 2016 [Dapper Entity Framework a hybridní aplikace](https://msdn.microsoft.com/magazine/mt703432.aspx). Další srovnávací test data o výkonu pro celou řadu metod přístupu dat můžete najít na [webu Dapper](https://github.com/StackExchange/Dapper).

Pokud chcete zobrazit, jak se liší od EF základní syntaxe Dapper, vezměte v úvahu tyto dvě verze stejné metodu pro načtení seznamu položek:

```csharp
// EF Core
private readonly CatalogContext _context;
public async Task<IEnumerable<CatalogType>> GetCatalogTypes()
{
    return await _context.CatalogTypes.ToListAsync();
}

// Dapper
private readonly SqlConnection _conn;
public async Task<IEnumerable<CatalogType>> GetCatalogTypesWithDapper()
{
    return await _conn.QueryAsync<CatalogType>("SELECT * FROM CatalogType");
}
```

Pokud potřebujete k vytváření složitějších objekt grafy s Dapper, budete muset zápisu přidružené dotazy (na rozdíl od přidání zahrnutí, stejně jako v základní EF). Tato možnost je podporována prostřednictvím řady různých syntaxe, včetně funkci více mapování, která umožňuje mapování jednotlivých řádků na více objektů namapované. Například danou třídu Post s vlastností vlastníka typu uživatele, následující příkaz SQL vrátí všechna potřebná data:

```sql
select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id
```

Každý vrácený řádek obsahuje data uživatele a Post. Vzhledem k tomu, že data uživatele by měl být připojen následná data přes vlastnost jeho vlastníka, se používá následující funkce:

```csharp
(post, user) => { post.Owner = user; return post; }
```

Výpis úplného kódu mají vracet kolekci příspěvcích s jejich vlastnost Owner naplněný daty uživatele by byl:

```csharp
var sql = @"select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id";
var data = connection.Query<Post, User, Post>(sql,
(post, user) => { post.Owner = user; return post;});
```

Protože nabízí menší zapouzdření, Dapper vyžaduje vývojáři vědět více o tom, jak mají uložená data, jak efektivní dotazování a napsat další kód se jej načíst. Když se změní model, místo jednoduše vytváření nové migrace (jiné EF základní funkce), a aktualizovat informace o mapování na jednom místě v konstruktoru DbContext každý dotaz, který je ovlivněno musí aktualizovat. Tyto dotazy mají není kompilace čas záruky, takže se může zalomit za běhu v reakci na změny do modelu nebo databáze, což chyby obtížné rychle zjistit. Za těchto kompromisy Dapper nabízí velmi vysoký výkon.

Pro většinu aplikací a většina částí téměř všechny aplikace nabízí základní EF přijatelný výkon. Proto se jeho výhody produktivitu vývojářů pravděpodobně převáží nad jeho nároky na výkon. Pro dotazy, které můžete využít ukládání do mezipaměti, skutečný dotaz může spustit pouze malá velikost procento doby, což poměrně malý dotaz moot rozdíly výkonu.

## <a name="sql-or-nosql"></a>SQL nebo NoSQL

Obvyklým relační databáze jako SQL Server mají potřebná hlavně marketplace pro úložiště dat, ale nejsou k dispozici pouze řešení. Databáze NoSQL, jako [MongoDB](https://www.mongodb.com/what-is-mongodb) nabízejí jiný přístup k ukládání objektů. Další možností je místo mapování objektů na tabulky a řádky, serializaci celý objekt grafu a uložit výsledek. Výhody tohoto přístupu alespoň na začátku jsou jednoduchost a výkonu. Je určitě jednodušší pro uložení jedné serializovaný objekt s klíčem, než se rozložit na mnoho tabulky se vztahy objektu a aktualizací a řádky, které může se změnily od posledního objekt načíst z databáze. Podobně načítání a deserializaci jeden objekt z úložiště na základě klíčů je obvykle mnohem rychlejší a snadnější než komplexní spojení nebo více dotazů databáze, které jsou potřeba plně tvoří stejný objekt z relační databáze. Nedostatek zámky nebo transakce nebo pevného schématu také díky databáze NoSQL velmi přenášejí škálování mezi mnoho počítačů, podpora velmi rozsáhlých datových sad.

Na druhé straně databáze NoSQL (jako jsou obvykle nazývá) mít svoje nevýhody. Relační databáze pomocí normalizaci zajistit konzistenci a zamezit tak duplicitních dat. To snižuje celkové velikosti databáze a zajistí, že aktualizace sdílených dat jsou k dispozici okamžitě celé databáze. V relační databázi může tabulky adres referenční tabulku země podle ID, tak, že pokud se změnily název země, záznamy adres by využívat aktualizace bez sami nutnosti ho aktualizovat. Ale v databázi NoSQL, adresa a její přidružené země může serializovat v rámci uložené objektů. Aktualizace název země by vyžadovaly všechny tyto objekty k aktualizaci, místo jednoho řádku. Relační databáze můžete také zajistit relační integritu vynucením pravidla, jako jsou cizí klíče. Databáze NoSQL obvykle nenabízejí takové omezení na svá data.

Další složitost NoSQL databáze musí řešit je správa verzí. Při změně vlastnosti objektu, nemusí být možné deserializovat od minulých verzí, které jste uložili. Proto musí být aktualizovány všechny existující objekty, které mají serializovaných (předchozí) verze objektu, tak, aby odpovídala nové schématem. Toto není koncepčně liší od relační databázi, kde je někdy změní schéma vyžadují skriptů pro aktualizaci nebo mapování aktualizace. Počet položek, které se musí upravit, je však často mnohem větší v přístupu NoSQL, protože existuje více duplicitních dat.

Je možné v databáze NoSQL uložit více verzí objektů, něco pevného schématu relačních databází obvykle nepodporují. Ale v tomto případě kód aplikace potřeba účet existenci předchozích verzích objektů a přidávání dalších složitost.

Databáze NoSQL obvykle Nevynucovat [kyseliny](https://en.wikipedia.org/wiki/ACID), což znamená, že mají výkon a škálovatelnost výhody nad relačních databází. Jsou vhodné řešení pro velmi rozsáhlých datových sad a objektů, které nejsou vhodné řešení pro úložiště v struktury normalizovaný tabulky. Neexistuje žádný důvod, proč jednu aplikaci nelze využít výhod obě relační a vhodné databáze NoSQL, každý pomocí, kde je nejvhodnější.

## <a name="azure-documentdb"></a>Azure DocumentDB

Azure DocumentDB je plně spravovaná služba databáze NoSQL, která nabízí úložiště založené na cloudu data bez schémat. DocumentDB je vytvořené pro vysoký a předvídatelný výkon, vysokou dostupnost, elastické škálování a globální distribuční. Přestože jsou databáze NoSQL, vývojáři mohou použít bohatý a známých možnosti dotazů SQL na JSON data. Všechny prostředky v DocumentDB jsou ukládány jako dokumenty JSON. Prostředky se spravují jako *položky*, které jsou dokumenty obsahující metadata, a *kanály*, které jsou kolekce položek. Obrázek 8-2 ukazuje vztah mezi různými prostředky DocumentDB.


![Hierarchický vztah mezi prostředky v DocumentDB, databázi NoSQL JSON](./media/image8-2.png)

**Obrázek 8-2.** DocumentDB prostředků organizace.

Dotazovací jazyk DocumentDB je jednoduché, ale výkonné rozhraní pro dotazování dokumentů JSON. Jazyk podporuje podmnožinu gramatiky ANSI SQL a přidává těsnou integraci objekt jazyka JavaScript, pole, vytvářením objektů a volání funkce.

**Odkazy – DocumentDB**

-   DocumentDB Introduction\
    <https://docs.microsoft.com/azure/documentdb/documentdb-introduction>

## <a name="other-persistence-options"></a>Další možnosti trvalost

Také na relační a možnosti úložiště typu NoSQL aplikace ASP.NET Core slouží k uložení různých formátů data a soubory způsobem Cloudová, škálovatelná Azure Storage. Azure Storage je nesmírně škálovatelná služba, abyste mohli začít se ukládání malé množství dat a škálování až ukládání stovkami nebo terabajtů, pokud vaše aplikace vyžaduje, aby ho. Úložiště Azure podporuje čtyři typy dat:

-   Pro nestrukturovaná text nebo binární úložiště, které jsou také označovány jako úložiště objektů úložiště objektů BLOB.

-   Úložiště Table pro strukturované datové sady, přístupné přes řádek klíče.

-   Fronty úložiště pro zasílání zpráv spolehlivého na základě fronty.

-   Úložiště souborů pro přístup ke sdílenému souboru mezi virtuálními počítači Azure a místními aplikacemi.

**Odkazy – úložiště Azure**

-   Introduction\ úložiště Azure
    <https://docs.microsoft.com/azure/storage/storage-introduction>

## <a name="caching"></a>Ukládání do mezipaměti

Ve webových aplikacích každý webový požadavek by se měly dokončit v možná nejkratší době. Jedním ze způsobů jak toho docílit je omezit počet externí volání, které server musíte provést žádost dokončit. Ukládání do mezipaměti zahrnuje ukládání kopii dat na serveru (nebo jiného úložiště dat, který je více než zdroj dat snadno dotaz). Webové aplikace a hlavně-zabezpečené ověřování HESLA tradiční webových aplikací, potřebujete k vytvoření celé uživatelské rozhraní s každou žádostí. To často zahrnuje, vytvoření řadu stejné databázové dotazy opakovaně z jednoho uživatele požadavku na další. Ve většině případů tato data změní zřídka, takže je málo důvod neustále požádat o z databáze. ASP.NET Core podporuje ukládání odpovědí do mezipaměti, pro ukládání do mezipaměti celé stránky a ukládání do mezipaměti dat, která podporuje podrobnější chování ukládání do mezipaměti.

Při implementaci ukládání do mezipaměti, je důležité mít na paměti oddělené oblasti zájmu. Vyhněte se implementace logiky ukládaní do mezipaměti v logika data přístup, nebo v uživatelském rozhraní. Místo toho zapouzdření ukládání do mezipaměti v jeho vlastní třídy a konfiguraci použít ke správě své chování. To odpovídá otevřete/uzavřeno a jeden odpovědnost zásady a bude jednodušší pro správu, jak používat ukládání do mezipaměti v aplikaci jako roste.

### <a name="aspnet-core-response-caching"></a>Ukládání odpovědí do mezipaměti ASP.NET Core

Jádro ASP.NET podporuje dvě úrovně ukládání odpovědí do mezipaměti. První úroveň neukládá do mezipaměti nic na serveru, ale přidá hlavičky HTTP, které dáte pokyn, klienty a proxy servery do mezipaměti odpovědi. Tato možnost je implementovaná přidáním atribut ResponseCache pro jednotlivé řadiče nebo akce:

```csharp
    [ResponseCache(Duration = 60)]
    public IActionResult Contact()
    { }
    
    ViewData["Message"] = "Your contact page.";
    return View();
}

The above example will result in the following header being added to the response, instructing clients to cache the result for up to 60 seconds.

Cache-Control: public,max-age=60

In order to add server-side in-memory caching to the application, you must reference the Microsoft.AspNetCore.ResponseCaching NuGet package, and then add the Response Caching middleware. This middleware is configured in both ConfigureServices and Configure in Startup:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddResponseCaching();
}

public void Configure(IApplicationBuilder app)
{
    app.UseResponseCaching();
}
```

Middleware ukládání do mezipaměti odpovědi bude automaticky ukládat do mezipaměti odpovědi na základě sady podmínek, které můžete přizpůsobit. Ve výchozím nastavení jsou do mezipaměti pouze 200 (OK) odpovědí požadovaný prostřednictvím metody GET nebo HEAD. Kromě toho požadavky musí mít odpověď se Cache-Control: veřejné záhlaví a nesmí obsahovat záhlaví pro autorizaci nebo Set-Cookie. V tématu [úplný seznam ukládání do mezipaměti podmínky používané odpovědi ukládání do mezipaměti middleware](https://docs.microsoft.com/aspnet/core/performance/caching/middleware#conditions-for-caching).

### <a name="data-caching"></a>Ukládání dat

Místo (nebo kromě) ukládání do mezipaměti úplné webové odezvy, mezipaměti můžete ukládat výsledky jednotlivých dat dotazů. V takovém případě můžete použít v ukládání do mezipaměti na webovém serveru nebo pomocí [distribuované mezipaměti](https://docs.microsoft.com/aspnet/core/performance/caching/distributed). Tato část popisuje, jak implementovat v ukládání do mezipaměti.

Přidání podpory pro paměti (nebo distribuované) ukládání do mezipaměti v ConfigureServices:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMemoryCache();
    services.AddMvc();
}
```

Je nutné přidat balíček Microsoft.Extensions.Caching.Memory NuGet.

Jakmile přidáte službu, můžete požádat o IMemoryCache pomocí vkládání závislostí vždy, když potřebujete pro přístup do mezipaměti. V tomto příkladu je CachedCatalogService pomocí vzoru návrhu Proxy (nebo Dekoratéra), tím, že poskytuje alternativní implementace ICatalogService, která řídí přístup k (nebo ho přidá chování) základní implementaci CatalogService.

```csharp
public class CachedCatalogService : ICatalogService
{
    private readonly IMemoryCache _cache;
    private readonly CatalogService _catalogService;
    private static readonly string _brandsKey = "brands";
    private static readonly string _typesKey = "types";
    private static readonly string _itemsKeyTemplate = "items-{0}-{1}-{2}-{3}";
    private static readonly TimeSpan _defaultCacheDuration = TimeSpan.FromSeconds(30);
    public CachedCatalogService(IMemoryCache cache,
    CatalogService catalogService)
    {
        _cache = cache;
        _catalogService = catalogService;
    }
    
    public async Task<IEnumerable<SelectListItem>> GetBrands()
    {
        return await _cache.GetOrCreateAsync(_brandsKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetBrands();
        });
    }
    
    public async Task<Catalog> GetCatalogItems(int pageIndex, int itemsPage, int? brandID, int? typeId)
    {
        string cacheKey = String.Format(_itemsKeyTemplate, pageIndex, itemsPage, brandID, typeId);
        return await _cache.GetOrCreateAsync(cacheKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetCatalogItems(pageIndex, itemsPage, brandID, typeId);
        });
    }
    
    public async Task<IEnumerable<SelectListItem>> GetTypes()
    {
        return await _cache.GetOrCreateAsync(_typesKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetTypes();
        });
    }
}
```

Chcete-li konfigurovat aplikaci používat v mezipaměti verzi služby, ale stále povolit služby pro získání instance CatalogService musí v jeho konstruktoru, by přidejte následující do ConfigureServices:

```csharp
services.AddMemoryCache();
services.AddScoped<ICatalogService, CachedCatalogService>();
services.AddScoped<CatalogService>();
```

S tímto zavedené volání databáze načíst data katalogu se provádí pouze jednou za minutu, nikoli na každou žádost. V závislosti na provoz na web to může mít velmi významný dopad na počet dotazů provedené v databázi a čas načítání stránky průměrná pro domovskou stránku, který aktuálně závisí na všechny tři dotazů vystavené touto službou.

Potíže, které mohou nastat, pokud se implementuje ukládání do mezipaměti je *zastaralých dat* – to znamená, data, která se změnila na zdroji, ale aktuální verze zůstává v mezipaměti. Jednoduchý způsob, jak zmírnit tento problém je použití malých doby trvání mezipaměti, protože pro zaneprázdněnou aplikaci je omezená další výhody rozšíření délku, kterou data se uloží do mezipaměti. Představte si třeba stránky, který umožňuje dotazu jedné databáze, a vyžaduje 10krát za sekundu. Pokud tato stránka se uloží do mezipaměti pro jednu minutu, bude výsledkem počet dotazů na databázi vyřadit z 600 na 1, snížení 99.8 % provedené za minutu. Pokud místo toho doba uložení do mezipaměti byly provedeny jednu hodinu, celkové snížení by 99.997 %, ale teď pravděpodobnost a potenciální stáří zastaralá data jsou obě zvětšit výrazně.

Další možností je aktivně odebrat položky mezipaměti při aktualizaci dat, která obsahují. Všechny jednotlivé položky lze odebrat, pokud je znám svůj klíč:

```csharp
_cache.Remove(cacheKey);
```

Pokud vaše aplikace poskytuje funkce pro aktualizaci položky, které se ukládá do mezipaměti, můžete odebrat odpovídající položky mezipaměti ve vašem kódu, který provádí aktualizaci. V některých případech může být mnoho různé položky, které závisí na konkrétní sadu dat. V takovém případě může být užitečné k vytvoření závislosti mezi položky mezipaměti pomocí CancellationChangeToken. S CancellationChangeToken můžete najednou vyprší více položek mezipaměti pomocí tokenu zrušení.

```csharp
// configure CancellationToken and add entry to cache
var cts = new CancellationTokenSource();
_cache.Set("cts", cts);
_cache.Set(cacheKey,
itemToCache,
new CancellationChangeToken(cts.Token));

// elsewhere, expire the cache by cancelling the token\
_cache.Get<CancellationTokenSource>("cts").Cancel();
```

>[!div class="step-by-step"]
[Předchozí] (develop-asp-net-core-mvc-apps.md) [Další] (test-asp-net-core-mvc-apps.md)
