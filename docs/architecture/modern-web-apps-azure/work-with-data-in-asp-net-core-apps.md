---
title: Práce s daty v ASP.NET základních aplikacích
description: Architekt moderní webové aplikace s ASP.NET core a Azure | Práce s daty v aplikacích ASP.NET Core
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: 5a38ca94b6df676858e7cb058272e450aaf1572e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78241036"
---
# <a name="working-with-data-in-aspnet-core-apps"></a>Práce s daty v základních aplikacích ASP.NET

> "Data jsou vzácná věc a vydrží déle než samotné systémy."
>
> Tim Berners-Lee

Přístup k datům je důležitou součástí téměř každé softwarové aplikace. ASP.NET Core podporuje celou řadu možností přístupu k datům, včetně entity framework core (a entity Framework 6 také) a může pracovat s libovolným rozhraním pro přístup k datům .NET. Volba, které rozhraní pro přístup k datům použít, závisí na potřebách aplikace. Abstrakce těchto možností z projektů ApplicationCore a UI a zapouzdření podrobností implementace v infrastruktuře pomáhá vytvářet volně vázaný, testovatelný software.

## <a name="entity-framework-core-for-relational-databases"></a>Core rámce entity (pro relační databáze)

Pokud píšete novou ASP.NET základní aplikace, která potřebuje pracovat s relačními daty, pak entity framework core (EF Core) je doporučený způsob, jak pro vaši aplikaci přístup k datům. EF Core je objektrelační mapovač (O/RM), který umožňuje vývojářům rozhraní .NET uchovávat objekty do a ze zdroje dat. Eliminuje potřebu pro většinu vývojáři kódu přístupu k datům by obvykle nutné psát. Stejně jako ASP.NET Core, EF Core byl přepsán od základu pro podporu modulárních aplikací pro více platforem. Přidáte ji do aplikace jako balíček NuGet, nakonfigurujte jej při spuštění a požádejte o něj prostřednictvím vkládání závislostí, kdekoli ji potřebujete.

Chcete-li použít ef core s databází serveru SQL Server, spusťte následující příkaz dotnet CLI:

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
```

Chcete-li přidat podporu pro zdroj dat InMemory, pro testování:

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore.InMemory
```

### <a name="the-dbcontext"></a>Kontextu db

Chcete-li pracovat s EF Core, <xref:Microsoft.EntityFrameworkCore.DbContext>potřebujete podtřídu . Tato třída obsahuje vlastnosti představující kolekce entit, se kterými bude aplikace pracovat. Ukázka eShopOnWeb obsahuje Kontext katalogu s kolekcemi pro položky, značky a typy:

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

DbContext musí mít konstruktor, který přijímá DbContextOptions a předat tento argument základní dbContext konstruktoru. Pokud máte pouze jeden DbContext ve vaší aplikaci, můžete předat instanci DbContextOptions, ale pokud\<máte více než jeden, musíte použít obecný DbContextOptions T> typu, předávání typu DbContext jako obecný parametr.

### <a name="configuring-ef-core"></a>Konfigurace jádra EF

Ve vaší aplikaci ASP.NET Core obvykle nakonfigurujete EF Core v metodě ConfigureServices. EF Core používá DbContextOptionsBuilder, který podporuje několik užitečných metod rozšíření pro zjednodušení jeho konfigurace. Chcete-li nakonfigurovat CatalogContext pro použití databáze serveru SQL Server s připojovacím řetězcem definovaným v konfiguraci, přidejte do služby ConfigureServices následující kód:

```csharp
services.AddDbContext<CatalogContext>(options => options.UseSqlServer (Configuration.GetConnectionString("DefaultConnection")));
```

Použití databáze v paměti:

```csharp
services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```

Po instalaci EF Core, vytvořil dbcontext podřízený typ a nakonfiguroval jej v ConfigureServices, jste připraveni k použití EF Core. Můžete požádat o instanci typu DbContext v libovolné službě, která ji potřebuje, a začít pracovat s trvalými entitami pomocí LINQ, jako by byly jednoduše v kolekci. EF Core provádí překlad výrazů LINQ do dotazů SQL pro uložení a načtení dat.

Můžete vidět dotazy EF Core je spuštěn a konfigurace protokolování a zajištění jeho úroveň je nastavena alespoň informace, jak je znázorněno na obrázku 8-1.

![Protokolování dotazů EF Core do konzoly](./media/image8-1.png)

**Obrázek 8-1**. Protokolování dotazů EF Core do konzoly

### <a name="fetching-and-storing-data"></a>Načítání a ukládání dat

Chcete-li načíst data z EF Core, přístup k příslušné vlastnosti a pomocí LINQ filtrovat výsledek. Můžete také použít LINQ k provedení projekce, transformovat výsledek z jednoho typu do druhého. Následující příklad by načetl CatalogBrands, seřazené podle názvu, filtrované podle jejich Vlastnost IPoa a promítnuté do typu SelectListItem:

```csharp
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem {
        Value = b.Id, Text = b.Name })
    .ToListAsync();
```

Ve výše uvedeném příkladu je důležité přidat volání toListAsync, aby bylo možné okamžitě spustit dotaz. V opačném případě příkaz přiřadí\<IQueryable SelectListItem> brandItems, které nebudou provedeny, dokud nebude uveden výčet. Existují klady a zápory k vrácení IQueryable výsledky z metod. Umožňuje dotaz EF Core bude konstrukce dále upravit, ale může také způsobit chyby, které dochází pouze za běhu, pokud operace jsou přidány do dotazu, který EF Core nelze přeložit. Obecně je bezpečnější předat všechny filtry do metody provádějící přístup k datům a vrátit\<zpět kolekci v paměti (například Seznam T>) jako výsledek.

EF Core sleduje změny na entity, které načte z trvalosti. Chcete-li uložit změny sledované entity, stačí zavolat SaveChanges metoda na DbContext, ujistěte se, že je to stejné DbContext instance, která byla použita k načtení entity. Přidání a odebrání entit se provádí přímo na příslušné DbSet vlastnost, opět s voláním SaveChanges ke spuštění příkazů databáze. Následující příklad ukazuje přidání, aktualizaci a odebrání entit z trvalosti.

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

EF Core podporuje synchronní i asynchronní metody pro načítání a ukládání. Ve webových aplikacích se doporučuje použít vzor async/await s asynchronními metodami, aby vlákna webového serveru nebyla blokována při čekání na dokončení operací přístupu k datům.

### <a name="fetching-related-data"></a>Načítání souvisejících dat

Když EF Core načte entity, naplní všechny vlastnosti, které jsou uloženy přímo s tuto entitu v databázi. Navigační vlastnosti, jako jsou seznamy souvisejících entit, nejsou naplněny a mohou mít jejich hodnotu nastavenou na hodnotu null. Tím je zajištěno, že EF Core nenačítá více dat, než je potřeba, což je obzvláště důležité pro webové aplikace, které musí rychle zpracovat požadavky a vrátit odpovědi efektivním způsobem. Chcete-li zahrnout vztahy s entitou pomocí _eager loading_, zadejte vlastnost pomocí metody Include extension v dotazu, jak je znázorněno:

```csharp
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```

Můžete zahrnout více relací a můžete také zahrnout podvztahy pomocí ThenInclude. EF Core spustí jeden dotaz k načtení výsledné sady entit. Alternativně můžete zahrnout navigační vlastnosti navigačnívlastnosti předáním '.. -oddělený řetězec `.Include()` k metodě rozšíření, například takto:

```csharp
    .Include(“Items.Products”)
```

Kromě logiky zapouzdření filtrování může specifikace určit tvar dat, která mají být vrácena, včetně vlastností, které mají být naplněny. Ukázka eShopOnWeb obsahuje několik specifikací, které demonstrují zapouzdření dychtivých informací o načítání v rámci specifikace. Můžete vidět, jak se specifikace používá jako součást dotazu zde:

```csharp
// Includes all expression-based includes
query = specification.Includes.Aggregate(query,
            (current, include) => current.Include(include));

// Include any string-based include statements
query = specification.IncludeStrings.Aggregate(query,
            (current, include) => current.Include(include));
```

Další možností pro načítání souvisejících dat je použití _explicitního načítání_. Explicitní načítání umožňuje načíst další data do entity, která již byla načtena. Vzhledem k tomu, že se jedná o samostatný požadavek do databáze, není doporučeno pro webové aplikace, což by mělo minimalizovat počet databázových zpátečních cest provedených na požadavek.

_Opožděné načtení_ je funkce, která automaticky načte související data, jak je odkazováno aplikací. EF Core přidal podporu pro opožděné načítání ve verzi 2.1. Opožděné načtení není ve výchozím `Microsoft.EntityFrameworkCore.Proxies`nastavení povoleno a vyžaduje instalaci rozhraní . Stejně jako u explicitní načítání opožděné načítání by měla být obvykle zakázána pro webové aplikace, protože jeho použití bude mít za následek další databázové dotazy v rámci každého webového požadavku. Bohužel režie vzniklé opožděné načítání často bez povšimnutí v době vývoje, kdy latence je malý a často datové sady používané pro testování jsou malé. V produkčním prostředí s více uživateli, více dat a více latence, další požadavky na databázi může často vést ke snížení výkonu pro webové aplikace, které využívají náročné načítání.

[Vyhněte se opožděné načítání entit ve webových aplikacích](https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications)

### <a name="encapsulating-data"></a>Zapouzdření dat

EF Core podporuje několik funkcí, které umožňují modelu správně zapouzdřit jeho stav. Běžným problémem v modelech domény je, že zveřejňují navigační vlastnosti kolekce jako veřejně přístupné typy seznamů. To umožňuje všechny spolupracovníky manipulovat s obsahem těchto typů kolekce, které mohou obejít důležitá obchodní pravidla související s kolekcí, případně ponechat objekt v neplatném stavu. Řešením je vystavit přístup jen pro čtení k související kolekce a explicitně poskytnout metody definující způsoby, ve kterém klienti mohou manipulovat s nimi, jako v tomto příkladu:

```csharp
public class Basket : BaseEntity
{
    public string BuyerId { get; set; }
    private readonly List<BasketItem> _items = new List<BasketItem>();
    public IReadOnlyCollection<BasketItem> Items => _items.AsReadOnly();

    public void AddItem(int catalogItemId, decimal unitPrice, int quantity = 1)
    {
        if (!Items.Any(i => i.CatalogItemId == catalogItemId))
        {
            _items.Add(new BasketItem()
            {
                CatalogItemId = catalogItemId,
                Quantity = quantity,
                UnitPrice = unitPrice
            });
            return;
        }
        var existingItem = Items.FirstOrDefault(i => i.CatalogItemId == catalogItemId);
        existingItem.Quantity += quantity;
    }
}
```

Tento typ entity nezveřejňuje `List` veřejné `ICollection` nebo vlastnosti, `IReadOnlyCollection` ale místo toho zveřejňuje typ, který obtéká základní typ seznamu. Při použití tohoto vzoru můžete na jádro entity frameworku určit, že se má použít záložní pole takto:

```csharp
private void ConfigureBasket(EntityTypeBuilder<Basket> builder)
{
    var navigation = builder.Metadata.FindNavigation(nameof(Basket.Items));

    navigation.SetPropertyAccessMode(PropertyAccessMode.Field);
}
```

Dalším způsobem, ve kterém můžete zlepšit model domény je pomocí hodnotových objektů pro typy, které postrádají identitu a jsou rozlišeny pouze jejich vlastnosti. Použití takových typů, jako jsou vlastnosti entit, může pomoci zachovat logiku specifickou pro objekt hodnoty, kam patří, a vyhnout se duplicitní logice mezi více entitami, které používají stejný koncept. V jádru entity frameworku můžete zachovat hodnotové objekty ve stejné tabulce jako jejich vlastnící entitu konfigurací typu jako vlastněné entity, například takto:

```csharp
private void ConfigureOrder(EntityTypeBuilder<Order> builder)
{
    builder.OwnsOne(o => o.ShipToAddress);
}
```

V tomto příkladu `ShipToAddress` je `Address`vlastnost typu . `Address`je objekt s několika vlastnostmi, například `Street` a `City`. EF Core `Order` mapuje objekt na jeho `Address` tabulku s jedním sloupcem na vlastnost, předponou každý název sloupce s názvem vlastnosti. V tomto příkladu by tabulka `Order` `ShipToAddress_Street` obsahovala sloupce, jako jsou a `ShipToAddress_City`. Je také možné v případě potřeby ukládat vlastněné typy v samostatných tabulkách.

Další informace o [podpoře vlastněných entit v EF Core](/ef/core/modeling/owned-entities).

### <a name="resilient-connections"></a>Odolná připojení

Externí prostředky, jako jsou databáze SQL, mohou být občas nedostupné. V případech dočasné nedostupnosti aplikace můžete použít logiku opakování, aby se zabránilo vyvolání výjimky. Tato technika se běžně označuje jako _odolnost proti chybám připojení_. Můžete implementovat [vlastní opakování s exponenciální backoff](https://docs.microsoft.com/azure/architecture/patterns/retry) technika pokusem o opakování s exponenciálně zvyšuje čekací doby, dokud není dosaženo maximální počet opakování bylo dosaženo. Tato technika zahrnuje skutečnost, že cloudové prostředky může být občas k dispozici pro krátké časové období, což má za následek selhání některých požadavků.

Pro Azure SQL DB, Entity Framework Core již poskytuje odolnost proti interní muškát připojení databáze a logiku opakování. Ale musíte povolit strategii provádění entity framework pro každé připojení DbContext, pokud chcete mít odolné připojení EF Core.

Například následující kód na úrovni připojení EF Core umožňuje odolná připojení SQL, která jsou opakována, pokud se připojení nezdaří.

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

Pokud jsou v připojeních EF Core povoleny opakované pokusy, každá operace, kterou provedete pomocí EF Core, se stane vlastní opakovatelnou operací. Každý dotaz a každé volání SaveChanges bude opakován jako celek, pokud dojde k přechodné selhání.

Pokud však váš kód iniciuje transakci pomocí BeginTransaction, definujete vlastní skupinu operací, které je třeba považovat za jednotku; vše uvnitř transakce musí být vrácena zpět, pokud dojde k selhání. Zobrazí se výjimka, jako je následující, pokud se pokusíte provést tuto transakci při použití strategie provádění EF (zásady opakování) a zahrnout několik SaveChanges z více DbContexts v něm.

System.InvalidOperationException: Nakonfigurovaná strategie spuštění SqlServerRetryingExecutionStrategy nepodporuje transakce iniciované uživatelem. Pomocí strategie provádění vrácené 'DbContext.Database.CreateExecutionStrategy()' provést všechny operace v transakci jako opakovatelné jednotky.

Řešením je ručně vyvolat strategii provádění EF s delegátem představující vše, co je třeba provést. Pokud dojde k přechodnému selhání, strategie provádění znovu vyvolá delegáta. Následující kód ukazuje, jak implementovat tento přístup:

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

První DbContext je \_catalogContext a druhý DbContext \_je v rámci integrationEventLogService objektu. Nakonec potvrzení akce by být provedena více DbContexts a pomocí strategie provádění EF.

> ### <a name="references--entity-framework-core"></a>Odkazy – jádro rámce entity
>
> - **Základní dokumenty EF**
>   <https://docs.microsoft.com/ef/>
> - **EF Core: Související údaje**
>   <https://docs.microsoft.com/ef/core/querying/related-data>
> - **Vyhněte se opožděným načítáním entit v aplikacích ASPNET**
>   <https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications>

## <a name="ef-core-or-micro-orm"></a>EF Core nebo mikro-ORM?

Zatímco EF Core je skvělou volbou pro správu trvalosti a z větší části zapouzdřuje podrobnosti o databázi od vývojářů aplikací, není to jediná volba. Další populární open-source alternativou je [Dapper](https://github.com/StackExchange/Dapper), takzvaný mikro-ORM. Mikro-ORM je lehký, méně plnohodnotný nástroj pro mapování objektů na datové struktury. V případě Dapper, jeho cíle návrhu se zaměřují na výkon, spíše než plně zapouzdření základní dotazy, které používá k načtení a aktualizaci dat. Vzhledem k tomu, že není abstraktní SQL od vývojáře, Dapper je "blíže ke kovu" a umožňuje vývojářům psát přesné dotazy, které chtějí použít pro danou operaci přístupu k datům.

EF Core má dvě významné funkce, které poskytuje, které ji oddělují od Dapper, ale také přidat k jeho výkonu režie. První je překlad z výrazů LINQ do SQL. Tyto překlady jsou uloženy do mezipaměti, ale i tak je režie při jejich provádění poprvé. Druhým je sledování změn na entity (tak, aby efektivní příkazy aktualizace mohou být generovány). Toto chování lze vypnout pro konkrétní dotazy pomocí rozšíření AsNotTracking. EF Core také generuje SQL dotazy, které jsou obvykle velmi efektivní a v každém případě dokonale přijatelné z hlediska výkonu, ale pokud potřebujete jemnou kontrolu nad přesnýdotaz, který má být proveden, můžete předat vlastní SQL (nebo spustit uloženou proceduru) pomocí EF Jádro taky. V tomto případě Dapper stále překonává EF Core, ale jen mírně. Julie Lerman představuje některé údaje o výkonu ve svém článku MSDN z května 2016 [Dapper, Entity Framework a Hybridní aplikace](https://docs.microsoft.com/archive/msdn-magazine/2016/may/data-points-dapper-entity-framework-and-hybrid-apps). Další srovnávací údaje o výkonnosti pro různé metody přístupu k datům lze nalézt na [webu Dapper](https://github.com/StackExchange/Dapper).

Chcete-li zjistit, jak se syntaxe pro Dapper liší od EF Core, zvažte tyto dvě verze stejné metody pro načítání seznamu položek:

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

Pokud potřebujete vytvořit složitější objektové grafy s Dapper, musíte napsat přidružené dotazy sami (na rozdíl od přidání Include jako v EF Core). To je podporováno prostřednictvím různých syntaxí, včetně funkce s názvem Vícenásobné mapování, která umožňuje mapovat jednotlivé řádky na více mapovaných objektů. Například vzhledem k tomu, třídy Post s vlastností Vlastník typu Uživatel, následující SQL vrátí všechna potřebná data:

```sql
select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id
```

Každý vrácený řádek obsahuje data uživatele i příspěvku. Vzhledem k tomu, že uživatelská data by měla být připojena k datům Příspěvku prostřednictvím vlastnosti Owner, používá se následující funkce:

```csharp
(post, user) => { post.Owner = user; return post; }
```

Úplný výpis kódu pro vrácení kolekce příspěvků s jejich owner vlastností naplněnou přidruženými uživatelskými daty by byl:

```csharp
var sql = @"select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id";
var data = connection.Query<Post, User, Post>(sql,
(post, user) => { post.Owner = user; return post;});
```

Vzhledem k tomu, že nabízí méně zapouzdření, Dapper vyžaduje, aby vývojáři věděli více o tom, jak jsou jejich data uložena, jak je efektivně dotazovat a psát další kód pro jejich načtení. Při změně modelu, namísto jednoduše vytvoření nové migrace (jiné funkce EF Core) a/nebo aktualizace informací o mapování na jednom místě v DbContext, každý dotaz, který je ovlivněn, musí být aktualizovány. Tyto dotazy nemají žádné záruky kompilace, takže může přerušit za běhu v reakci na změny modelu nebo databáze, takže chyby obtížnější zjistit rychle. Výměnou za tyto kompromisy, Dapper nabízí extrémně rychlý výkon.

Pro většinu aplikací a většinu částí téměř všech aplikací nabízí EF Core přijatelný výkon. Výhody produktivity vývojářů tedy pravděpodobně převáží nad režií výkonu. U dotazů, které mohou těžit z ukládání do mezipaměti, skutečný dotaz může být proveden pouze malé procento času, takže relativně malé rozdíly výkonu dotazu diskutabilní.

## <a name="sql-or-nosql"></a>SQL nebo NoSQL

Relační databáze jako SQL Server tradičně dominují trhu pro trvalé ukládání dat, ale nejsou jediným dostupným řešením. NoSQL databáze jako [MongoDB](https://www.mongodb.com/what-is-mongodb) nabízejí jiný přístup k ukládání objektů. Spíše než mapování objektů na tabulky a řádky, další možností je serializovat celý objekt grafu a uložit výsledek. Výhody tohoto přístupu, alespoň zpočátku, jsou jednoduchost a výkon. Je jednodušší uložit jeden serializovaný objekt s klíčem než rozložit objekt do mnoha tabulek s relacemi a aktualizace a řádky, které se mohly změnit od posledního načtení objektu z databáze. Podobně načítání a deserializace jednoho objektu z úložiště založeného na klíči je obvykle mnohem rychlejší a jednodušší než komplexní spojení nebo více databázových dotazů potřebných k úplnému vytvoření stejného objektu z relační databáze. Nedostatek zámků nebo transakcí nebo pevné schéma také umožňuje NoSQL databáze přístupné škálování napříč mnoha počítači, podporující velmi velké datové sady.

Na druhou stranu, NoSQL databáze (jak se obvykle nazývají) mají své nevýhody. Relační databáze používají normalizaci k vynucení konzistence a zabránění duplikaci dat. Tím se zmenší celková velikost databáze a zajistí, že aktualizace sdílených dat jsou k dispozici okamžitě v celé databázi. V relační databázi může tabulka Adresa odkazovat na tabulku Země podle ID, takže pokud by byl změněn název země nebo oblasti, záznamy adres by měly prospěch z aktualizace, aniž by musely být aktualizovány. V databázi NoSQL však může být adresa a přidružená země serializována jako součást mnoha uložených objektů. Aktualizace názvu země nebo oblasti by vyžadovala, aby byly aktualizovány všechny tyto objekty, nikoli jeden řádek. Relační databáze mohou také zajistit relační integritu vynucením pravidel, jako jsou cizí klíče. NoSQL databáze obvykle nenabízejí taková omezení na jejich data.

Další složitost NoSQL databáze musí řešit, je správa verzí. Při změně vlastností objektu nemusí být možné rekonstruovat z minulých verzí, které byly uloženy. Proto všechny existující objekty, které mají serializované (předchozí) verze objektu musí být aktualizovány tak, aby odpovídaly jeho nové schéma. To se koncepčně neliší od relační databáze, kde změny schématu někdy vyžadují aktualizace skriptů nebo aktualizace mapování. Počet položek, které musí být změněny, je však často mnohem větší v přístupu NoSQL, protože je více duplikace dat.

Je možné v nosql databázích ukládat více verzí objektů, něco pevné schéma relační databáze obvykle nepodporují. V tomto případě však kód aplikace bude muset účet pro existenci předchozíverze objektů, přidání další složitosti.

NoSQL databáze obvykle nevynucují [ACID](https://en.wikipedia.org/wiki/ACID), což znamená, že mají výhody výkonu i škálovatelnosti oproti relačním databázím. Jsou vhodné pro extrémně velké datové sady a objekty, které nejsou vhodné pro ukládání v normalizovaných strukturách tabulek. Neexistuje žádný důvod, proč jedna aplikace nemůže využít relační a NoSQL databáze, pomocí každého, kde je nejvhodnější.

## <a name="azure-cosmos-db"></a>Azure Cosmos DB

Azure Cosmos DB je plně spravovaná databázová služba NoSQL, která nabízí cloudové úložiště dat bez schématu. Azure Cosmos DB je vybudován pro rychlý a předvídatelný výkon, vysokou dostupnost, elastické škálování a globální distribuci. Přesto, že je databáze NoSQL, mohou vývojáři používat bohaté a známé funkce DOTAZŮ SQL na datech JSON. Všechny prostředky v Azure Cosmos DB jsou uloženy jako dokumenty JSON. Prostředky jsou _spravovány_jako položky , což jsou dokumenty obsahující metadata a _informační kanály_, což jsou kolekce položek. Obrázek 8-2 znázorňuje vztah mezi různými prostředky Azure Cosmos DB.

![Hierarchický vztah mezi prostředky v Azure Cosmos DB, databázi NoSQL JSON](./media/image8-2.png)

**Obrázek 8-2.** Organizace prostředků Azure Cosmos DB.

Dotazovací jazyk Azure Cosmos DB je jednoduché, ale výkonné rozhraní pro dotazování dokumentů JSON. Tento jazyk podporuje podmnožinu gramatiky ANSI SQL a přidává těsnou integraci s javascriptovými objekty, poli, vytvářením objektů a voláním funkcí.

**Reference – Azure Cosmos DB**

- Úvod do Azure Cosmos DB<https://docs.microsoft.com/azure/cosmos-db/introduction>

## <a name="other-persistence-options"></a>Další možnosti trvalosti

Kromě možností relačního úložiště a úložiště NoSQL můžou aplikace ASP.NET Core používat Azure Storage k ukládání různých formátů dat a souborů cloudovým a škálovatelným způsobem. Azure Storage je masivně škálovatelné, takže můžete začít ukládat malá množství dat a škálovat až na ukládání stovek nebo terabajtů, pokud to vaše aplikace vyžaduje. Azure Storage podporuje čtyři druhy dat:

- Úložiště objektů blob pro nestrukturovaný text nebo binární úložiště, označované také jako úložiště objektů.

- Úložiště tabulek pro strukturované datové sady, přístupné pomocí klíčů řádků.

- Úložiště fronty pro spolehlivé zasílání zpráv založené na frontách.

- Úložiště souborů pro sdílený přístup k souborům mezi virtuálními počítači Azure a místními aplikacemi.

**Reference – Azure Storage**

- Úvod k úložišti Azure<https://docs.microsoft.com/azure/storage/storage-introduction>

## <a name="caching"></a>Ukládání do mezipaměti

Ve webových aplikacích by měl být každý webový požadavek dokončen v co nejkratším možném čase. Jedním ze způsobů, jak toho dosáhnout, je omezit počet externích volání, která musí server provést k dokončení požadavku. Ukládání do mezipaměti zahrnuje ukládání kopie dat na server (nebo jiné úložiště dat, které je snadněji dotazován než zdroj dat). Webové aplikace, a zejména non-SPA tradiční webové aplikace, je třeba vytvořit celé uživatelské rozhraní s každým požadavkem. To často zahrnuje provádění mnoho stejných databázových dotazů opakovaně z jednoho požadavku uživatele na další. Ve většině případů se tato data mění zřídka, takže je malý důvod neustále požadovat z databáze. ASP.NET Core podporuje ukládání do mezipaměti odpovědí, ukládání do mezipaměti celých stránek a ukládání dat do mezipaměti, které podporuje podrobnější chování ukládání do mezipaměti.

Při implementaci ukládání do mezipaměti je důležité mít na paměti oddělení obav. Vyhněte se implementaci logiky ukládání do mezipaměti v logice přístupu k datům nebo v uživatelském rozhraní. Místo toho zapouzdřte ukládání do mezipaměti ve vlastních třídách a použijte konfiguraci ke správě jeho chování. To se řídí otevřenými/uzavřenými a jednotnými zásadami odpovědnosti a usnadňuje vám správu způsobu používání ukládání do mezipaměti v aplikaci podle jeho růstu.

### <a name="aspnet-core-response-caching"></a>ASP.NET ukládání do mezipaměti odpovědi jádra

ASP.NET Core podporuje dvě úrovně ukládání do mezipaměti odezvy. První úroveň neukládá na server nic do mezipaměti, ale přidává hlavičky HTTP, které instruují klienty a proxy servery k ukládání odpovědí do mezipaměti. To je implementováno přidáním atributu ResponseCache k jednotlivým řadičům nebo akcím:

```csharp
[ResponseCache(Duration = 60)]
public IActionResult Contact()
{
    ViewData["Message"] = "Your contact page.";
    return View();
}
```

V předchozím příkladu bude mít za následek následující záhlaví, které jsou přidány do odpovědi, pokyn klientům do mezipaměti výsledek po dobu až 60 sekund.

Cache-Control: veřejná,max-age=60

Chcete-li do aplikace přidat ukládání do mezipaměti na straně serveru v paměti, musíte odkazovat na balíček NuGet služby Microsoft.AspNetCore.ResponseCaching a potom přidat middleware pro ukládání do mezipaměti odpovědi. Tento middleware je konfigurován v configureservices a konfigurovat při spuštění:

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

Middleware pro ukládání do mezipaměti odpovědi bude automaticky ukládány do mezipaměti na základě sady podmínek, které můžete přizpůsobit. Ve výchozím nastavení pouze 200 (OK) odpovědi požadované prostřednictvím GET nebo HEAD metody jsou uloženy do mezipaměti. Kromě toho musí mít požadavky odpověď s ovládacím prvkem cache: veřejné záhlaví a nesmí obsahovat záhlaví pro autorizaci nebo set-cookie. Podívejte se na [úplný seznam podmínek ukládání do mezipaměti používaných middleware pro ukládání do mezipaměti odpovědi](/aspnet/core/performance/caching/middleware#conditions-for-caching).

### <a name="data-caching"></a>Ukládání dat do mezipaměti

Spíše než (nebo kromě) ukládání úplných webových odpovědí do mezipaměti můžete ukládat výsledky jednotlivých datových dotazů do mezipaměti. K tomu můžete použít ukládání do mezipaměti paměti na webovém serveru nebo [použít distribuovanou mezipaměť](/aspnet/core/performance/caching/distributed). Tato část ukáže, jak implementovat do mezipaměti paměti.

Podporu ukládání do mezipaměti paměti (nebo distribuovaného) ukládání do mezipaměti v programu ConfigureServices přidáte:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMemoryCache();
    services.AddMvc();
}
```

Nezapomeňte také přidat balíček Microsoft.Extensions.Caching.Memory NuGet.

Po přidání služby požádáte IMemoryCache prostřednictvím vkládání závislostí všude tam, kde potřebujete přístup k mezipaměti. V tomto příkladu CachedCatalogService používá proxy (nebo decorator) návrhový vzor tím, že poskytuje alternativní implementaci ICatalogService, která řídí přístup (nebo přidá chování) základní implementace CatalogService.

```csharp
public class CachedCatalogService : ICatalogService
{
    private readonly IMemoryCache _cache;
    private readonly CatalogService _catalogService;
    private static readonly string _brandsKey = "brands";
    private static readonly string _typesKey = "types";
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
        string cacheKey = $"items-{pageIndex}-{itemsPage}-{brandID}-{typeId}";
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

Chcete-li nakonfigurovat aplikaci tak, aby používala verzi služby uloženou v mezipaměti, ale přesto povolit službě získat instanci služby CatalogService, kterou potřebuje ve svém konstruktoru, byste do služby ConfigureServices přidali následující:

```csharp
services.AddMemoryCache();
services.AddScoped<ICatalogService, CachedCatalogService>();
services.AddScoped<CatalogService>();
```

S tímto na místě volání databáze načíst data katalogu bude provedena pouze jednou za minutu, nikoli na každém požadavku. V závislosti na provozu na webu to může mít významný vliv na počet dotazů provedených v databázi a průměrnou dobu načítání stránky pro domovskou stránku, která aktuálně závisí na všech třech dotazech vystavených touto službou.

Problém, který vzniká při implementaci ukládání do mezipaměti, jsou _zastaralá data_ – to znamená data, která se změnila u zdroje, ale v mezipaměti zůstává zastaralá verze. Jednoduchý způsob, jak zmírnit tento problém je použití malé mezipaměti trvání, protože pro zaneprázdněné aplikace je omezená další výhoda rozšíření délky dat je uložena v mezipaměti. Zvažte například stránku, která vytvoří dotaz na jednu databázi a je požadována 10krát za sekundu. Pokud je tato stránka uložena do mezipaměti po dobu jedné minuty, bude mít za následek počet dotazů databáze provedených za minutu, aby klesly z 600 na 1, což je snížení o 99,8 %. Pokud místo toho trvání mezipaměti byly provedeny jednu hodinu, celkové snížení by bylo 99,997%, ale nyní pravděpodobnost a potenciální stáří zastaralých dat jsou oba dramaticky zvýšily.

Dalším přístupem je proaktivní odebrání položek mezipaměti při aktualizaci dat, která obsahují. Každá jednotlivá položka může být odebrána, pokud je znám její klíč:

```csharp
_cache.Remove(cacheKey);
```

Pokud aplikace zveřejňuje funkce pro aktualizaci položek, které ukládá do mezipaměti, můžete odebrat odpovídající položky mezipaměti v kódu, který provádí aktualizace. Někdy může existovat mnoho různých položek, které závisí na konkrétní sadu dat. V takovém případě může být užitečné vytvořit závislosti mezi položkami mezipaměti pomocí CancellationChangeToken. S CancellationChangeToken můžete vypršet více položek mezipaměti najednou zrušením tokenu.

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

Ukládání do mezipaměti může výrazně zlepšit výkon webových stránek, které opakovaně požadují stejné hodnoty z databáze. Před použitím ukládání do mezipaměti nezapomeňte měřit přístup k datům a výkon stránky a používat ukládání do mezipaměti pouze tam, kde je potřeba zlepšení. Ukládání do mezipaměti spotřebovává prostředky paměti webového serveru a zvyšuje složitost aplikace, takže je důležité, abyste předčasně optimalizovat pomocí této techniky.

>[!div class="step-by-step"]
>[Předchozí](develop-asp-net-core-mvc-apps.md)
>[další](test-asp-net-core-mvc-apps.md)
