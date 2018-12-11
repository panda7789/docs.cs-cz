---
title: Práce s daty v aplikace v ASP.NET Core
description: Navrhování moderních webových aplikací pomocí ASP.NET Core a Azure | Práce s daty v aplikacích ASP.NET Core
author: ardalis
ms.author: wiwagn
ms.date: 06/28/2018
ms.openlocfilehash: efadf3a0d216197b05d6cd4cfe94ee3eb24bb18e
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147171"
---
# <a name="working-with-data-in-aspnet-core-apps"></a>Práce s daty v aplikacích ASP.NET Core

> "Dat je cenný věc a bude trvat déle než systémy sami."
>
> TIM Berners-Lee

Přístup k datům je důležitou součástí téměř všechny softwarové aplikace. ASP.NET Core podporuje širokou škálu možnosti přístupu k datům, včetně Entity Framework Core (a také Entity Framework 6) a může fungovat s jakékoli rozhraní .NET framework data access. Volba, které přístup k datům framework použít závisí na potřebách vaší aplikace. Poskytuje abstrakci tyto možnosti z projektů ApplicationCore a uživatelského rozhraní a zapouzdření podrobností o implementaci v infrastruktuře, pomáhá vytvářet volně propojených, možností intenzivního testování softwaru.

## <a name="entity-framework-core-for-relational-databases"></a>Entity Framework Core (pro relační databáze)

Pokud píšete nové aplikace ASP.NET Core, kterou je potřeba práci s relačními daty, Entity Framework Core (jádro EF) je doporučený postup pro vaši aplikaci pro přístup k jeho datům. EF Core je objektově relační Mapovač (O/RM), který umožňuje vývojářům .NET k uchování objektů do a z datového zdroje. To eliminuje potřebu většinu kód přístupu k datům, které obvykle byste museli vývojáři napsat. Jako je ASP.NET Core EF Core přepsali jsme od základů podporuje modulární multiplatformní aplikace. Přidat do vaší aplikace jako balíček NuGet, jeho konfiguraci v při spuštění a žádosti pomocí vkládání závislostí, bez ohledu na to budete potřebovat.

EF Core pomocí databáze SQL serveru, spusťte následující příkaz rozhraní příkazového řádku dotnet:

příkaz DotNet add package Microsoft.EntityFrameworkCore.SqlServer

Přidání podpory pro zdroj dat InMemory, pro účely testování:

příkaz DotNet add package Microsoft.EntityFrameworkCore.InMemory

### <a name="the-dbcontext"></a>Uvolněn objekt DbContext

Pro práci s EF Core, je třeba podtřída <xref:Microsoft.EntityFrameworkCore.DbContext>. Tato třída obsahuje vlastnosti představující kolekce entit, které vaše aplikace bude fungovat s. Ukázka eShopOnWeb zahrnuje CatalogContext s kolekcí položek, značky a typy:

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

Vaše DbContext musí mít konstruktor, který přijímá DbContextOptions a předat tento argument pro konstruktor základní třídy DbContext. Poznámka: Pokud máte pouze jeden DbContext v aplikaci, můžete předat instanci DbContextOptions, ale pokud máte více než jeden je nutné použít obecný DbContextOptions<T> typ, předejte typ DbContext jako na generický parametr.

### <a name="configuring-ef-core"></a>Konfigurace EF Core

V aplikaci ASP.NET Core obvykle nakonfigurujete EF Core ve své metodě ConfigureServices. EF Core používá DbContextOptionsBuilder, která podporuje několik užitečných rozšiřující metody pro usnadnit jeho konfiguraci. Pokud chcete nakonfigurovat CatalogContext pro použití jiné databáze systému SQL Server pomocí připojovacího řetězce definované v konfiguraci, by přidejte následující kód k ConfigureServices:

```csharp
services.AddDbContext<CatalogContext>(options => options.UseSqlServer (Configuration.GetConnectionString("DefaultConnection")));
```

Použití databáze v paměti:

```csharp
services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```

Po EF Core vytvořili podřízený typ DbContext, nainstalované a nakonfigurované v ConfigureServices, jste připraveni používat EF Core. Můžete požádat o instanci typu DbContext v jakékoli služby, která potřebuje a začít pracovat s trvalou entit pomocí LINQ, jako by byly jednoduše v kolekci. EF Core funguje překlad výrazech LINQ na dotazy SQL pro ukládání a načítání dat.

Můžete zobrazit dotazy EF Core provádí konfigurací protokolovací nástroj a zajištění jeho úroveň je nastavené aspoň informace, jak ukazuje obrázek 8-1.

![](./media/image8-1.png)

Obrázek 8-1 protokolování EF Core dotazy do konzoly

### <a name="fetching-and-storing-data"></a>Načítání a ukládání dat

K načtení dat z EF Core, přístup k příslušné vlastnosti a zprostředkovatel LINQ slouží pro filtrování výsledků. LINQ můžete také použít k provedení projekce, transformaci výsledku z jednoho typu na jiný. V následujícím příkladu by načíst CatalogBrands, seřazené podle názvu, filtrovat podle jejich vlastnosti Enabled a plánovaných na typ SelectListItem:

```csharp
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem {
        Value = b.Id, Text = b.Name })
    .ToListAsync();
```

Je důležité v příkladu výše a přidejte volání do ToListAsync, aby bylo možné okamžitě spustit dotaz. V opačném případě bude příkaz Přiřadit položku IQueryable<SelectListItem> k brandItems, který nebude provedeno, dokud je ve výčtu. Existují výhody a nevýhody vrací typ IQueryable výsledky z metod. Umožňuje dotazu, které EF Core vytvoří dále upravit, ale můžete také za následek chyby, které se vztahuje pouze na za běhu, pokud operace jsou přidány do dotazu, který nelze přeložit EF Core. Obecně je bezpečnější pro předání nějaké filtry do metody provádí přístup k datům a vrátit zpět kolekce v paměti (například seznamu<T>) jako výsledek.

EF Core sleduje změny u entit, který načte z trvalého úložiště. Pokud chcete uložit změny do sledované entity, stačí zavolat metodu SaveChanges objekt dbcontext, ujistěte se, že se že jedná o stejnou instanci DbContext, který byl použit pro načtení entity. Přidávání a odebírání entity se provádí přímo na odpovídající vlastnosti DbSet, znovu s volání SaveChanges pro spuštění databázových příkazů. Následující příklad ukazuje přidání, aktualizace nebo odebrání entity z trvalého úložiště.

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

EF Core podporuje obě synchronní a asynchronní metody pro načítání a ukládání. Ve webových aplikacích doporučuje se použití vzoru async/await s asynchronními metodami, tak, aby při čekání na dokončení operací přístupu k data nejsou blokované vlákna webového serveru.

### <a name="fetching-related-data"></a>Načítání souvisejících dat

Když EF Core načte entity, naplní všechny vlastnosti, které jsou uloženy přímo s dané entitě v databázi. Navigační vlastnosti, jako je například seznam souvisejících entit nejsou naplněny a může mít nastavenou na hodnotu null. Tím se zajistí, že EF Core není načítání více dat, než je potřeba, což je obzvláště důležité pro webové aplikace, které musí rychle zpracovávají požadavky a vracet odpovědi efektivním způsobem. Zahrnout vztahy s entitu s využitím _předběžné načítání_, určete vlastnost pomocí metody rozšíření zahrnout u dotazu, jak je znázorněno:

```csharp
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```

Může obsahovat více vztahů a může také obsahovat dílčí vztahy pomocí ThenInclude. EF Core se spustit jeden dotaz pro načtení výslednou sadu entit.

Další možností pro načítání souvisejících dat je použití _explicitní načtení_. Explicitní načtení umožňuje načtení dalších dat do entity, která již byla načtena. Protože to vyžaduje samostatnou žádost do databáze, se nedoporučuje pro webové aplikace, které byste minimalizovat počet databáze má zpáteční převod vytvářejí pro jednotlivé žádosti.

_Opožděné načtení_ je funkce, která automaticky načte související data, jak se odkazuje aplikaci. EF Core má přidanou podporu pro opožděné načtení ve verzi 2.1. Opožděné načtení není ve výchozím nastavení povolené a vyžaduje instalaci `Microsoft.EntityFrameworkCore.Proxies`. Stejně jako u explicitní načtení opožděné načtení obvykle je třeba zakázat pro webové aplikace, protože její použití způsobí další databázových dotazů prováděných v rámci každého webového požadavku. Režie vzniklé opožděné načtení často přejde bohužel bez povšimnutí při vývoji, kdy latence je malý a často jsou malé datové sady, používá se pro testování. Ale v produkčním prostředí s více uživateli, víc dat a další latence požadavky další databáze můžete často za následek nízký výkon pro webové aplikace, které se hojně používají opožděné načtení.

[Vyhněte se opožděné načtení entit ve webových aplikacích](https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications)

### <a name="resilient-connections"></a>Odolnost připojení

Externí prostředky, jako jsou databáze SQL může být čas od času není k dispozici. V případech dočasné nedostupnosti aplikací můžete logiku opakování vyhnuli vyvolání výjimky. Tato technika se obvykle označuje jako _odolnost připojení_. Můžete implementovat vaše [vlastní opakování pomocí exponenciálního omezení rychlosti](https://docs.microsoft.com/azure/architecture/patterns/retry) techniku pokusem o opakování s exponenciálně rostoucím času čekání, dokud nedosáhne maximální počet opakování. Tento postup poskytuje výkonný fakt, že cloudové prostředky přerušovaně pravděpodobně není k dispozici pro krátkou dobu, což vede k selhání některé požadavky.

Pro službu Azure SQL DB Entity Framework Core již poskytuje interní databáze připojení odolnost proti chybám a zkuste to znovu logiku. Ale je potřeba povolit strategie provádění Entity Framework pro každé připojení kontext databáze. Pokud chcete mít odolnost připojení EF Core.

Například následující kód na úrovni připojení EF Core umožňuje odolnost připojení SQL, které se zopakují, pokud se nepovede.

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

#### <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a>Strategie provádění a explicitní transakce pomocí BeginTransaction a více DbContexts

Pokud opakované pokusy jsou povolené v EF Core připojení, bude každé operace, které můžete provádět pomocí EF Core vyvolaly provozu. Každý dotaz a každé volání SaveChanges bude zopakován jako celek, pokud dojde k přechodnému selhání.

Ale pokud váš kód zahájí transakci pomocí BeginTransaction, definujete vlastní skupinu operací, které je potřeba za jednotku považuje – všechno, co je uvnitř transakce se vrátila zpět, pokud dojde k chybě. Pokud se pokusíte spustit transakci, při použití strategie provádění EF (zásady opakování) a v ní zahrnete několik SaveChanges z více DbContexts uvidíte výjimku vypadat asi takto.

System.InvalidOperationException: Strategie provádění nakonfigurované "SqlServerRetryingExecutionStrategy" nepodporuje transakce iniciované uživatelem. Použití strategie provádění vrácený "DbContext.Database.CreateExecutionStrategy()" provádět všechny operace v transakci jako vyvolaly jednotky.

Řešením je vyvolat strategie provádění EF s všechno, co představuje delegáta, který je nutné spustit ručně. Pokud dojde k přechodnému selhání, strategie provádění znovu vyvolá delegáta. Následující kód ukazuje implementaci tohoto přístupu:

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

Je první objekt DbContext \_catalogContext a druhý je DbContext v rámci \_integrationEventLogService objektu. Nakonec potvrzení bude akce provedena více DbContexts a použitím strategie provádění EF.

> ### <a name="references--entity-framework-core"></a>Odkazy – Entity Framework Core
>
> - **EF Core dokumentace**  
>   <https://docs.microsoft.com/ef/>
> - **EF Core: Související Data**  
>   <https://docs.microsoft.com/ef/core/querying/related-data>
> - **Vyhněte se opožděné načtení entit v aplikacích ASPNET**  
>   <https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications>

## <a name="ef-core-or-micro-orm"></a>EF Core nebo micro ORM?

EF Core je skvělou volbou pro správu trvalosti a ve většině případů zapouzdřuje databáze informace od vývojářů aplikací, není pouze podle výběru. Další oblíbené open source alternativou je [Dapperem](https://github.com/StackExchange/Dapper), takzvané ORM micro. Micro-ORM představuje jednoduché, méně plně funkční nástroj pro mapování objektů na datové struktury. V případě Dapperem jeho návrhu, které cíle soustředit na výkon, nikoli plně zapouzdření základní dotazy používá k načtení a aktualizovat data. Vzhledem k tomu, že SQL ji není abstraktní od vývojáře, Dapperem "nejblíže až na úroveň hardwaru" a umožňuje vývojářům psát přesné dotazy, které chtějí používat pro daný datový přístup k operaci.

EF Core má dvě důležité funkce poskytuje které oddělení od Dapperem, ale také přidat do své nároky na výkon. První je překlad z výrazů LINQ do SQL. Tyto převody jsou uložené v mezipaměti, ale i tak je režie při prvním spuštění. Druhým je sledování změn u entit (tak, aby je možné generovat příkazy efektivní aktualizace). Toto chování vypnete pro určité dotazy s použitím rozšíření AsNotTracking. EF Core také vygeneruje dotazy SQL, které jsou obvykle velmi efektivní a v každém případě nemusíte zajistit dokonalou přijatelné z hlediska výkonu, ale pokud potřebujete jemné kontrolu nad přesné provedení dotazu, můžete předat vlastní SQL (nebo provedení uložené procedury) pomocí EF Příliš jádro. V takovém případě Dapper stále lepší výkon než EF Core, ale jen mírně. Některá data o výkonu v její může článku na webu MSDN 2016 uvede Julie Lerman [Dapperem, Entity Framework a také hybridní aplikace](https://msdn.microsoft.com/magazine/mt703432.aspx). Dalších srovnávací test dat o výkonu pro celou řadu metod datového přístupu můžete najít na [Dapper lokality](https://github.com/StackExchange/Dapper).

Chcete-li zjistit, jak se liší od EF Core syntaxe Dapperem, zvažte tyto dvě verze stejné metody pro načtení seznamu položek:

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

Pokud budete muset vytvářet složitější grafů objektů s Dapperem, musíte napsat přidružené dotazy (na rozdíl od přidání do vloženého, stejně jako v EF Core). To je podporováno prostřednictvím různých syntaxí, včetně funkci s více mapování, která umožňuje mapovat na více objektů pro mapovanou jednotlivých řádků. Například vzhledem třídu příspěvek s vlastností vlastník typu uživatele následující příkaz SQL by vrátit všechna nezbytná data:

```sql
select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id
```

Každý vrácený řádek obsahuje data uživatelů a příspěvku. Protože data uživatele by měl být připojen následných dat prostřednictvím vlastnosti jeho vlastníka, se používá následující funkce:

```csharp
(post, user) => { post.Owner = user; return post; }
```

Výpis úplného kódu budou vráceny kolekci příspěvků s jejich vlastnost Owner naplněný daty přidruženého uživatele by byl:

```csharp
var sql = @"select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id";
var data = connection.Query<Post, User, Post>(sql,
(post, user) => { post.Owner = user; return post;});
```

Vzhledem k tomu, že nabízí méně zapouzdření, vyžaduje Dapperem vývojáři dozvědět víc o tom, jak jejich data uložená, jak efektivní dotazování a napsat další kód, který jej načíst. Když se změní model, místo jednoduše vytvářet novou migraci (Další EF Core funkcí) a/nebo aktualizace informací o mapování na jednom místě v DbContext, musí aktualizovat každý dotaz, který má vliv. Tyto dotazy obsahovat není záruky čas kompilace, tak se může přerušit za běhu v reakci na změny modelu nebo databáze, provádění obtížnější rychle detekovat chyby. Výměnou za tyto nevýhody Dapperem nabízí velmi rychlý výkon.

Pro většinu aplikací a většina součástí téměř všechny aplikace nabízí EF Core přijatelný výkon. Díky tomu se budou pravděpodobně nároky na výkon převažují nad jeho výhody produktivity pro vývojáře. Pro dotazy, které mohou těžit z ukládání do mezipaměti, samotný dotaz může spustit pouze velmi malé procento doby provádění poměrně málo početnému dotazování výkonu moot rozdíly.

## <a name="sql-or-nosql"></a>SQL a NoSQL

Tradičně relačních databází, jako je SQL Server mají ovládnutí úložiště trvalých dat na webu marketplace, ale nejsou k dispozici jenom řešení. Databáze NoSQL, jako jsou [MongoDB](https://www.mongodb.com/what-is-mongodb) nabízejí jiný přístup k ukládání objektů. Další možností je místo mapování objektů do tabulek a řádků, serializaci celý objekt grafu a uložit výsledek. Výhody tohoto přístupu alespoň ze začátku jsou jednoduchost a výkonu. Je určitě jednodušší pro uložení jedné serializované objekt s klíčem, než se rozloží na mnoho tabulky se vztahy objektu a aktualizací a řádky, které se možná změnily od posledního objekt načtených z databáze. Podobně načítání a deserializaci jednoho objektu z úložiště na základě klíčů je obvykle mnohem jednodušší a rychlejší než komplexním spojením nebo více databázových dotazů vyžaduje plně sestavení na stejný objekt z relační databáze. Nedostatek uzamčení nebo transakce nebo pevné schéma také díky databáze NoSQL velmi vydávání kompaktních škálování napříč velký počet počítačů, podpora velmi velkých datových sad.

Na druhé straně databáze NoSQL (obvykle se nazývá) mít svoje nevýhody. Relační databáze pomocí normalizace vynutit konzistenci a aby nedošlo k duplikaci data. Tím se sníží celkové velikosti databáze a zajistí, že jsou k dispozici okamžitě celé databáze aktualizace ke sdíleným datům. V relační databázi tabulku adres může odkazovat země tabulku podle ID, tak, že pokud byla změněna název v zemi, záznamy adres je výhodná aktualizace bez musejí být aktualizována. Ale v databázi NoSQL, adresa a její přidružené země může serializovat jako součást velký počet uložených objektů. Aktualizace názvu země by vyžadovaly všechny tyto objekty mají být aktualizovány, místo jednoho řádku. Relační databáze, můžete také zajistit relační integritu tím, že vynucuje pravidla, jako jsou cizí klíče. Databáze NoSQL není taková omezení na svá data obvykle nabízejí.

Další složitost NoSQL databáze musí čelit je správa verzí. Při změně vlastnosti objektu, nemusí být možné deserializovat rozdíl od minulých verzí, které byly uloženy. Díky tomu se musí aktualizovat všechny existující objekty, které mají serializovaná (předchozí) verzi objektu tak, aby odpovídal na jeho nové schéma. Toto není koncepčně liší od relační databáze, kde je někdy změní schéma vyžadují skripty pro aktualizaci nebo mapování aktualizace. Počet položek, které musí být upraveny je však často mnohem větší přístupu NoSQL, protože existuje více duplicitních dat.

Je možné v databázích NoSQL pro ukládání více verzí objektů, něco pevné schéma relačních databází obvykle nepodporují. Ale v tomto případě kódu aplikace potřebovat pro existenci předchozích verzích objekty, přidáte další složitosti.

Databáze NoSQL obvykle Nevynucovat [kyseliny](https://en.wikipedia.org/wiki/ACID), což znamená, že mají výhody výkonu a škálovatelnosti nad relačních databází. Jsou to skvěle se hodí k velmi velkých datových sad a objektů, které nejsou vhodné řešení pro úložiště ve strukturách normalizované tabulky. Neexistuje žádný důvod, proč si jednu aplikaci nemůžete využít výhod obou relační a vhodné databáze NoSQL, pomocí všech, kde je nejvhodnější.

## <a name="azure-documentdb"></a>Azure DocumentDB

Azure DocumentDB je plně spravovaná služba databáze NoSQL, která nabízí úložiště založené na cloudu data bez schémat. DocumentDB je vytvořená pro vysoký a předvídatelný výkon, vysokou dostupnost, elastické škálování a globální distribuci. Přestože jsou databáze NoSQL, vývojáři mohou pomocí bohaté a známé schopnosti příkazů jazyka SQL pro JSON data. Všechny prostředky v DocumentDB se ukládají jako dokumenty JSON. Prostředky se spravují jako _položky_, které jsou dokumenty obsahující metadata, a _informační kanály_, což jsou kolekce položek. Obrázek 8-2 je znázorněný vztah mezi různé prostředky DocumentDB.

![Hierarchický vztah mezi prostředky v DocumentDB, databázi NoSQL JSON](./media/image8-2.png)

**Obrázek 8-2.** Organizaci poskytující prostředky DocumentDB.

Dotazovací jazyk DocumentDB je jednoduché, ale výkonné rozhraní pro dotazování dokumentů JSON. Jazyk podporuje podmnožinu gramatiky ANSI SQL a přidává těsnou integraci s objektu jazyka JavaScript, pole, konstrukce objektu a volání funkce.

**Odkazy – DocumentDB**

- Úvod k DocumentDB  
  <https://docs.microsoft.com/azure/documentdb/documentdb-introduction>

## <a name="other-persistence-options"></a>Další možnosti trvalosti

Také do relační a možnosti úložiště NoSQL můžete použít aplikace ASP.NET Core služby Azure Storage k ukládání širokou škálu formátů data a soubory v podobě Cloudová, škálovatelná. Azure Storage je široce škálovatelné, takže můžete začít ukládat malá množství dat a škálování až na ukládání stovky nebo dokonce terabajtů, pokud ho vaše aplikace vyžaduje. Azure Storage podporuje čtyři typy dat:

- Úložiště objektů blob pro ukládání nestrukturovaných textových nebo binárních úložiště také označuje jako úložiště objektů.

- Table Storage pro strukturovaných datových sad, přístupné přes klíče řádku.

- Queue Storage pro spolehlivé na základě fronty zasílání zpráv.

- Úložiště souborů pro přístup ke sdílenému souboru mezi virtuální počítače Azure a místními aplikacemi.

**Odkazy – Azure Storage**

- Představení služby Azure Storage  
  <https://docs.microsoft.com/azure/storage/storage-introduction>

## <a name="caching"></a>Ukládání do mezipaměti

Ve webových aplikacích každý webový požadavek by měl dokončit v nejkratší možné době. Jedním ze způsobů, jak tohoto dosáhnout je omezit počet externích volání, které server musí provést k dokončení požadavku. Ukládání do mezipaměti zahrnuje ukládání kopie dat na serveru (nebo jiné datové úložiště, který je více než zdroj dat snadno dotazovat). Webové aplikace a hlavně-jednostránková aplikace tradiční webových aplikací, je potřeba sestavit celé uživatelské rozhraní při každé žádosti. To často zahrnuje provádění mnoha stejné databázové dotazy opakovaně z požadavku na jednoho uživatele na další. Ve většině případů tato data mění jen zřídka, tedy malou důvod, proč neustále žádosti z databáze. ASP.NET Core podporuje ukládání odpovědí do mezipaměti, pro ukládání do mezipaměti celé stránky a ukládání dat do mezipaměti, která podporuje podrobnější chování ukládání do mezipaměti.

Při implementaci ukládání do mezipaměti, je důležité udržovat v úvahu oddělení oblastí zájmu. Vyhněte se implementaci logiky ukládaní do mezipaměti v logikou přístupu dat nebo v uživatelském rozhraní. Místo toho zapouzdření ukládání do mezipaměti v jeho vlastní třídy a použití konfigurace k spravovat své chování. Následuje Open/uzavřeno a principy jednotnou zodpovědnost a usnadní správu, jak používat ukládání do mezipaměti ve vaší aplikaci, jak rostou.

### <a name="aspnet-core-response-caching"></a>Ukládání odpovědí do mezipaměti ASP.NET Core

ASP.NET Core podporuje dvě úrovně ukládání odpovědí do mezipaměti. První úroveň neukládá do mezipaměti nic na serveru, ale přidá hlavičky HTTP, které dáte pokyn, aby klienti a servery proxy do mezipaměti odpovědi. Tato možnost je implementovaná tak, že přidáte atribut ResponseCache individuální řadiče nebo provádět akce:

```csharp
    [ResponseCache(Duration = 60)]
    public IActionResult Contact()
    { }

    ViewData["Message"] = "Your contact page.";
    return View();
}
```

V předchozím příkladu bude výsledkem následující záhlaví se přidá do odpovědi, že klienti pro ukládání do mezipaměti výsledek až 60 sekund.

Cache-Control: veřejný, max-age = 60

Chcete-li přidat ukládání v mezipaměti na straně serveru k aplikaci, musíte odkázat na balíček Microsoft.AspNetCore.ResponseCaching NuGet a pak přidat ukládání odpovědí do mezipaměti middlewaru. Tento middleware je nakonfigurovaný v ConfigureServices a konfigurovat v po spuštění:

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

Middleware pro ukládání do mezipaměti odpovědi bude automaticky ukládat do mezipaměti odpovědi na základě sady podmínek, které si můžete přizpůsobit. Ve výchozím nastavení jsou uložené v mezipaměti jenom 200 (OK) odpovědi požadovaný prostřednictvím metody GET a HEAD. Kromě toho požadavky musí mít odpovědí s Cache-Control: veřejné záhlaví a nesmí obsahovat záhlaví pro povolení nebo Set-Cookie. Najdete v článku [úplný seznam ukládání do mezipaměti podmínky používané odpovědi ukládání do mezipaměti middleware](/aspnet/core/performance/caching/middleware#conditions-for-caching).

### <a name="data-caching"></a>Ukládání dat do mezipaměti

Místo (nebo kromě) ukládání do mezipaměti odpovědi na úplné webu, můžete ukládat do mezipaměti výsledky jednotlivých datových dotazů. V takovém případě můžete použít v paměti, ukládání do mezipaměti na webovém serveru, nebo použijte [distribuované mezipaměti](/aspnet/core/performance/caching/distributed). Tato část popisuje, jak implementovat v ukládání do mezipaměti.

Přidání podpory pro paměti (nebo distribuované) ukládání do mezipaměti v ConfigureServices:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMemoryCache();
    services.AddMvc();
}
```

Je potřeba přidat balíček Microsoft.Extensions.Caching.Memory NuGet.

Po přidání služby, můžete požádat o IMemoryCache pomocí vkládání závislostí bez ohledu na to budete potřebovat pro přístup do mezipaměti. V tomto příkladu je CachedCatalogService pomocí vzoru návrhu proxy serveru (nebo Dekoratér), tím, že poskytuje alternativní implementace ICatalogService, který určuje přístup do (nebo přidá chování) se základní implementací CatalogService.

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

Konfigurace aplikace pro použití verze uložené v mezipaměti služby, ale stále povolit službu pro získání instance CatalogService musí ve svých konstruktorech, přidáte následující v ConfigureServices:

```csharp
services.AddMemoryCache();
services.AddScoped<ICatalogService, CachedCatalogService>();
services.AddScoped<CatalogService>();
```

Díky tomu na místě volání databáze načíst data katalogu se provést pouze jednou za minutu, ne u každého požadavku. V závislosti na provoz do lokality to může mít velmi velký vliv na počet dotazů provedené v databázi a čas načítání stránky průměrné pro domovskou stránku, která aktuálně závisí na všech třech umístěních dotazů, které jsou vystavené touto službou.

Potíže, které mohou nastat, pokud se implementuje ukládání do mezipaměti je _zastaralých dat_ – to znamená, že data, která se změnila na zdroji, ale aktuální verze zůstává v mezipaměti. Použít malé mezipaměti doby trvání, protože zaneprázdněný aplikace je omezené výhody k prodloužení, které data uložená v mezipaměti je jednoduchý způsob, jak tento problém zmírnit. Představte si třeba stránku, která se zadá dotaz izolované databáze, a vyžaduje 10krát za sekundu. Pokud tato stránka je uložené v mezipaměti pro jednominutovým, způsobí počet provedených za minutu z 600 vyřazení na hodnotu 1, snížení 99,8 % databázové dotazy. Pokud místo toho dobu uložení do mezipaměti byly provedeny jednu hodinu, snížení celkové by 99.997 %, ale nyní pravděpodobnost a potenciální stáří zastaralých dat jsou obě výrazné zvýšení.

Další možností je aktivně odebrat položky mezipaměti, když dojde k aktualizaci dat, která obsahují. Všechny jednotlivé položky lze odebrat, pokud je jeho klíč je známý:

```csharp
_cache.Remove(cacheKey);
```

Pokud vaše aplikace zpřístupňuje funkce pro aktualizaci položky, které se ukládá do mezipaměti, můžete odebrat odpovídající položky v mezipaměti v kódu, který provádí aktualizace. V některých případech může být mnoho různých položek, které závisí na konkrétní sady dat. V takovém případě může být užitečné vytvořit závislosti mezi položky mezipaměti s využitím CancellationChangeToken. S CancellationChangeToken můžete ukončit platnost více položek mezipaměti najednou zrušením tokenu.

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

Ukládání do mezipaměti může výrazně zlepšit výkon webových stránek, které opakovaně požádat o stejné hodnoty z databáze. Je nutné měřit výkon přístupu a stránky dat před použitím ukládání do mezipaměti a ukládání do mezipaměti použít pouze pokud vznikne taková potřeba pro zlepšení. Ukládání do mezipaměti používá webové prostředky systémové paměti a zvyšují složitost aplikace, takže je důležité, že jste neoptimalizovat předčasně tímto způsobem.

>[!div class="step-by-step"]
>[Předchozí](develop-asp-net-core-mvc-apps.md)
>[další](test-asp-net-core-mvc-apps.md)