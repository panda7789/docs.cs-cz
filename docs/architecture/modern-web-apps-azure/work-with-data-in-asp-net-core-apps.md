---
title: Práce s daty v aplikacích ASP.NET Core
description: Architekt moderních webových aplikací pomocí ASP.NET Core a Azure | Práce s daty v aplikacích ASP.NET Core
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: 5a38ca94b6df676858e7cb058272e450aaf1572e
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2020
ms.locfileid: "78241036"
---
# <a name="working-with-data-in-aspnet-core-apps"></a>Práce s daty v aplikacích ASP.NET Core

> "Data jsou úžasné a budou naposledy delší než systémy samotné."
>
> Tim Berners-Novák

Přístup k datům je důležitou součástí téměř libovolné softwarové aplikace. ASP.NET Core podporuje celou řadu možností přístupu k datům, včetně Entity Framework Core (a také Entity Framework 6), a může fungovat s libovolným rozhraním .NET Data Access Framework. Volba rozhraní pro přístup k datům, která se má použít, závisí na potřebách aplikace. Díky abstrakci těchto voleb z projektů ApplicationCore a uživatelských rozhraní a zapouzdřování podrobností o implementaci v infrastruktuře vám pomůže vydávat volně spojený testovatelné software.

## <a name="entity-framework-core-for-relational-databases"></a>Entity Framework Core (pro relační databáze)

Pokud vytváříte novou ASP.NET Core aplikaci, která potřebuje pracovat s relačními daty, je doporučeným způsobem, jak vaše aplikace přistupuje k datům, je Entity Framework Core (EF Core). EF Core je objektově-relační Mapovač (O/RM), který umožňuje vývojářům v rozhraní .NET zachovat objekty do a ze zdroje dat. Eliminuje nutnost, že většina vývojářů kódu pro přístup k datům obvykle vyžaduje zápis. Podobně jako u ASP.NET Core se EF Core od základu přepsala pro podporu modulárních aplikací pro více platforem. Přidáte ho do vaší aplikace jako balíček NuGet, nakonfigurujete ho při spuštění a vyžádáte ho přes vkládání závislostí všude, kde ho potřebujete.

Pokud chcete použít EF Core s databází SQL Server, spusťte následující příkaz dotnet CLI:

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
```

Přidání podpory pro zdroj dat pro nedostatek paměti pro testování:

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore.InMemory
```

### <a name="the-dbcontext"></a>DbContext

Chcete-li pracovat s EF Core, potřebujete podtřídu <xref:Microsoft.EntityFrameworkCore.DbContext>. Tato třída uchovává vlastnosti představující kolekce entit, se kterými bude aplikace pracovat. Ukázka eShopOnWeb zahrnuje CatalogContext s kolekcemi pro položky, značky a typy:

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

Vaše DbContext musí mít konstruktor, který přijímá DbContextOptions a předávat tento argument základnímu konstruktoru DbContext. Máte-li ve své aplikaci pouze jeden DbContext, můžete předat instanci DbContextOptions, ale pokud máte více než jeden, musíte použít > typu Generic DbContextOptions\<T a předat jako obecný parametr typ DbContext.

### <a name="configuring-ef-core"></a>Konfigurace EF Core

Ve vaší aplikaci ASP.NET Core obvykle ve své metodě ConfigureServices nakonfigurujete EF Core. EF Core používá DbContextOptionsBuilder, který podporuje několik užitečných metod rozšíření pro zjednodušení konfigurace. Chcete-li nakonfigurovat CatalogContext pro použití databáze SQL Server s připojovacím řetězcem definovaným v konfiguraci, přidejte do ConfigureServices následující kód:

```csharp
services.AddDbContext<CatalogContext>(options => options.UseSqlServer (Configuration.GetConnectionString("DefaultConnection")));
```

Použití databáze v paměti:

```csharp
services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```

Jakmile nainstalujete EF Core, vytvoříte podřízený typ DbContext a nakonfigurujete ho v ConfigureServices, jste připraveni použít EF Core. Můžete požádat o instanci DbContext typu v jakékoli službě, která ji potřebuje, a začít pracovat s trvalými entitami pomocí LINQ, jako kdyby byly jednoduše v kolekci. EF Core provádí překlad výrazů LINQ do dotazů SQL a ukládá a načítá vaše data.

Můžete zobrazit dotazy EF Core spouštíte konfigurací protokolovacího nástroje a zajištěním jeho úrovně na alespoň informace, jak je znázorněno na obrázku 8-1.

![Protokolování dotazů EF Core do konzoly](./media/image8-1.png)

**Obrázek 8-1**. Protokolování dotazů EF Core do konzoly

### <a name="fetching-and-storing-data"></a>Načítají se a ukládají se data.

Chcete-li načíst data z EF Core, přistupujete k příslušné vlastnosti a pomocí LINQ můžete filtrovat výsledek. Můžete také použít LINQ k provedení projekce a transformovat výsledek z jednoho typu na jiný. Následující příklad by načetl CatalogBrands seřazený podle názvu, vyfiltroval podle jejich povolených vlastností a propnul na SelectListItem typ:

```csharp
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem {
        Value = b.Id, Text = b.Name })
    .ToListAsync();
```

Ve výše uvedeném příkladu je důležité přidat volání do ToListAsync, aby se dotaz spustil okamžitě. V opačném případě příkaz přiřadí rozhraní IQueryable\<SelectListItem > k brandItems, které nebude provedeno, dokud není vyhodnocena. Existují specialisté a nevýhody vrácení výsledků IQueryable z metod. Umožňuje, aby byl dotaz EF Core dále upravován, ale může také vést k chybám, ke kterým dochází pouze za běhu, pokud jsou do dotazu přidány operace, které EF Core nelze přeložit. Obecně je bezpečnější předat jakékoli filtry do metody, která provádí přístup k datům, a vrátit zpět kolekci v paměti (například seznam\<T >) jako výsledek.

EF Core sleduje změny entit, které načítá z Persistence. Chcete-li uložit změny ve sledované entitě, stačí zavolat metodu SaveChanges na DbContext, čímž se zajistí, že se jedná o stejnou instanci DbContext, která byla použita k načtení entity. Přidávání a odebírání entit je přímo provedeno na příslušné vlastnosti Negenerickými a volání metody SaveChanges ke spuštění databázových příkazů. Následující příklad ukazuje přidávání, aktualizování a odebírání entit z Persistence.

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

EF Core podporuje synchronní i asynchronní metody pro načítání a ukládání. Ve webových aplikacích se doporučuje použít vzor Async/await s asynchronními metodami, aby se vlákna webového serveru neblokovala při čekání na dokončení operací přístupu k datům.

### <a name="fetching-related-data"></a>Načítají se související data.

Když EF Core načítá entity, naplní všechny vlastnosti, které jsou uloženy přímo s touto entitou v databázi. Navigační vlastnosti, jako jsou například seznamy souvisejících entit, nejsou naplněny a mohou mít hodnotu nastavenou na hodnotu null. Tím se zajistí, že EF Core nenačítá víc dat, než je potřeba, což je zvláště důležité pro webové aplikace, které musí rychle zpracovávat požadavky a vracet odpovědi účinným způsobem. Chcete-li zahrnout relace s entitou pomocí _Eager načítání_, zadejte vlastnost pomocí metody include Extension na dotaz, jak je znázorněno níže:

```csharp
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```

Můžete zahrnout více relací a můžete také zahrnout podrelace pomocí ThenInclude. EF Core spustí jeden dotaz, který načte výslednou sadu entit. Alternativně můžete zahrnout navigační vlastnosti navigačních vlastností předáním ".". -řetězec oddělený řetězcem metody rozšíření `.Include()`, například:

```csharp
    .Include(“Items.Products”)
```

Kromě zapouzdření logiky filtrování může specifikace určit tvar dat, která mají být vrácena, včetně vlastností, které mají být naplněny. Ukázka eShopOnWeb obsahuje několik specifikací, které ukazují, jak zapouzdřit Eager načítání informací v rámci specifikace. To, jak se specifikace používá jako součást dotazu, vidíte tady:

```csharp
// Includes all expression-based includes
query = specification.Includes.Aggregate(query,
            (current, include) => current.Include(include));

// Include any string-based include statements
query = specification.IncludeStrings.Aggregate(query,
            (current, include) => current.Include(include));
```

Další možností načítání souvisejících dat je použití _explicitního načítání_. Explicitní načítání umožňuje načíst další data do entity, která již byla načtena. Vzhledem k tomu, že se jedná o samostatný požadavek na databázi, není doporučeno používat webové aplikace, což by mělo minimalizovat počet přenosů databáze odeslaných na požadavek.

_Opožděné načítání_ je funkce, která automaticky načte související data, která jsou odkazována aplikací. EF Core přidaná podpora pro opožděné načítání ve verzi 2,1. Opožděné načítání není ve výchozím nastavení povolené a vyžaduje instalaci `Microsoft.EntityFrameworkCore.Proxies`. Stejně jako u explicitního načítání by se obvykle mělo pro webové aplikace zakázat opožděné načítání, protože jeho použití bude mít za následek další databázové dotazy v rámci každé webové žádosti. Režijní náklady spojené s opožděným načtením se bohužel často neúčtují v době vývoje, pokud je latence malá a často jsou datové sady používané pro testování malé. Nicméně v produkčním prostředí s více uživateli, více daty a větší latencí můžou další požadavky databáze často způsobit špatný výkon webových aplikací, které využívají opožděné načítání.

[Vyhnout se entitám opožděného načítání ve webových aplikacích](https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications)

### <a name="encapsulating-data"></a>Zapouzdření dat

EF Core podporuje několik funkcí, které umožní vašemu modelu správně zapouzdřit svůj stav. Běžným problémem v doménových modelech je to, že zveřejňují vlastnosti navigace v kolekci jako veřejně přístupné typy seznamů. To umožňuje všem spolupracovníkům manipulovat s obsahem těchto typů kolekcí, což může obejít důležité obchodní pravidla související s kolekcí, což může opustit objekt v neplatném stavu. Řešením je vystavit přístup jen pro čtení k souvisejícím kolekcím a explicitně poskytnout metody definující způsoby, kterými je můžou klienti manipulovat, jako v tomto příkladu:

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

Tento typ entity nevystavuje vlastnost Public `List` nebo `ICollection`, ale místo toho zpřístupňuje typ `IReadOnlyCollection`, který zabalí základní typ seznamu. Při použití tohoto modelu můžete určit, že se má Entity Framework Core použít pole pro zálohování, například:

```csharp
private void ConfigureBasket(EntityTypeBuilder<Basket> builder)
{
    var navigation = builder.Metadata.FindNavigation(nameof(Basket.Items));

    navigation.SetPropertyAccessMode(PropertyAccessMode.Field);
}
```

Dalším způsobem, jak můžete zlepšit model domény, je použití objektů hodnot pro typy, které postrádají identitu a jsou rozlišeny jenom jejich vlastnostmi. Použití takových typů jako vlastností vašich entit může pomoci udržet logiku specifickou pro objekt hodnoty, kde patří, a může zabránit duplicitní logice mezi několika entitami, které používají stejný pojem. V Entity Framework Core můžete zachovat objekty hodnot ve stejné tabulce jako jejich vlastnící entita nakonfigurováním typu jako vlastněné entity, například takto:

```csharp
private void ConfigureOrder(EntityTypeBuilder<Order> builder)
{
    builder.OwnsOne(o => o.ShipToAddress);
}
```

V tomto příkladu je vlastnost `ShipToAddress` typu `Address`. `Address` je objekt hodnoty s několika vlastnostmi, například `Street` a `City`. EF Core mapuje objekt `Order` na jeho tabulku s jedním sloupcem na `Address` vlastnost, přičemž prefixuje název každého sloupce s názvem vlastnosti. V tomto příkladu by tabulka `Order` zahrnovala sloupce jako `ShipToAddress_Street` a `ShipToAddress_City`. V případě potřeby je také možné uložit vlastněné typy v samostatných tabulkách.

Přečtěte si další informace o podpoře vlastněných [entit v EF Core](/ef/core/modeling/owned-entities).

### <a name="resilient-connections"></a>Odolná připojení

Externí prostředky, jako jsou databáze SQL, mohou být občas nedostupné. V případech dočasné nedostupnosti mohou aplikace použít logiku opakování, aby nedošlo k vyvolání výjimky. Tato technika se běžně označuje jako _odolnost připojení_. Můžete implementovat [vlastní opakování pomocí exponenciální omezení rychlosti](https://docs.microsoft.com/azure/architecture/patterns/retry) techniky tím, že zkusíte opakovat pokus s exponenciálním zvýšením čekací doby, dokud nedosáhnete maximálního počtu opakování. Tato technika zahrnuje skutečnost, že prostředky cloudu můžou být občas nedostupné po krátkou dobu, což vede k selhání některých požadavků.

Pro Azure SQL DB už Entity Framework Core k dispozici odolnost interního připojení k databázi a logiku opakování. Pro každé připojení DbContext ale musíte povolit strategii spouštění Entity Framework, pokud chcete mít odolná EF Core připojení.

Například následující kód na úrovni připojení EF Core umožňuje odolné připojení SQL, které se opakuje, pokud se připojení nepovede.

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

Když jsou v EF Core připojení povolené opakované pokusy, každá operace, kterou provádíte pomocí EF Core, se stal svou vlastní opakovanou operací. Každý dotaz a každé volání metody SaveChanges se bude opakovat jako jednotka, pokud dojde k přechodnému selhání.

Nicméně pokud váš kód inicializuje transakci pomocí BeginTransaction, definujete vlastní skupinu operací, které je třeba považovat za jednotku. vše uvnitř transakce se musí vrátit zpátky, pokud dojde k selhání. Pokud se pokusíte provést tuto transakci při použití strategie provádění EF (opakování zásad) a zahrnete do něj několik DbContexts, zobrazí se výjimka podobná následující.

System. InvalidOperationException: nakonfigurovaná strategie provádění SqlServerRetryingExecutionStrategy nepodporuje transakce iniciované uživatelem. K provedení všech operací v transakci jako opakované jednotky použijte strategii spuštění vrácenou funkcí DbContext. Database. CreateExecutionStrategy ().

Řešením je ruční vyvolání strategie provádění EF s delegátem, který představuje všechno, co je třeba provést. Pokud dojde k přechodnému selhání, strategie provádění znovu vyvolá delegáta. Následující kód ukazuje, jak implementovat tento přístup:

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

První DbContext je \_catalogContext a druhá DbContext je v objektu \_integrationEventLogService. Nakonec se akce potvrzení provede více DbContexts a použije se strategie provádění EF.

> ### <a name="references--entity-framework-core"></a>Odkazy – Entity Framework Core
>
> - **EF Core Docs**
>   <https://docs.microsoft.com/ef/>
> - **EF Core: související
>   dat** <https://docs.microsoft.com/ef/core/querying/related-data>
> - **Vyhněte se entitám opožděného načítání v aplikacích ASPNET**
>   <https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications>

## <a name="ef-core-or-micro-orm"></a>EF Core nebo mikroorm?

I když je EF Core skvělou volbou pro správu trvalosti a většina z nich zapouzdřuje podrobnosti databáze od vývojářů aplikací, není jedinou volbou. Další oblíbenou alternativou Open Source je [dapperem](https://github.com/StackExchange/Dapper), což se říká mikroorm. Mikroorm je odlehčený a méně plnohodnotný nástroj pro mapování objektů na datové struktury. V případě Dapperem se záměr jejich návrhu zaměřuje na výkon, místo úplného zapouzdření základních dotazů, které používá k načtení a aktualizaci dat. Vzhledem k tomu, že se nejedná o abstraktní SQL z vývojářů, Dapperem je "blíže k metalu" a vývojářům umožňuje psát přesné dotazy, které chtějí použít pro danou operaci přístupu k datům.

EF Core má dvě důležité funkce, které nabízí oddělení IT od Dapperem, ale také přidávají k jeho režijnímu výkonu. První je převod z výrazů LINQ do jazyka SQL. Tyto překlady jsou ukládány do mezipaměti, ale i tak, aby při prvním spuštění bylo režie. Druhým je sledování změn u entit (aby bylo možné vygenerovat efektivní příkazy aktualizace). Toto chování je možné vypnout pro konkrétní dotazy pomocí rozšíření AsNotTracking. EF Core také generuje dotazy SQL, které jsou obvykle velice efektivní a v jakémkoliv případě zcela přijatelné z hlediska výkonu, ale pokud potřebujete lepší kontrolu nad přesným dotazem, který se má provést, můžete předat vlastní SQL (nebo spustit uloženou proceduru) pomocí EF. Jádro. V takovém případě Dapperem stále vykonává EF Core, ale jenom mírně. Julie Lerman prezentuje údaje o výkonu v jeho 2016 článku na webu MSDN [dapperem, Entity Framework a hybridních aplikacích](https://docs.microsoft.com/archive/msdn-magazine/2016/may/data-points-dapper-entity-framework-and-hybrid-apps). Další data srovnávacích testů výkonu pro celou řadu metod přístupu k datům najdete na [webu dapperem](https://github.com/StackExchange/Dapper).

Chcete-li zjistit, jak se syntaxe Dapperem liší od EF Core, zvažte tyto dvě verze stejné metody pro načtení seznamu položek:

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

Pokud potřebujete vytvořit složitější grafy objektů pomocí Dapperem, je potřeba napsat přidružené dotazy sami (na rozdíl od přidání zahrnutí jako při EF Core). To je podporováno prostřednictvím nejrůznějších syntaxí, včetně funkce s názvem vícenásobné mapování, které umožňuje mapovat jednotlivé řádky na více mapovaných objektů. Například vzhledem k tomu, že daný příspěvek třídy se vlastníkem vlastnosti typu uživatel, vrátí následující SQL všechna potřebná data:

```sql
select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id
```

Každý vrácený řádek obsahuje data uživatelů i post. Vzhledem k tomu, že data uživatelů by měla být připojena k post data prostřednictvím její vlastnosti Owner, je použita následující funkce:

```csharp
(post, user) => { post.Owner = user; return post; }
```

Úplný výpis kódu, který vrátí kolekci příspěvků s vlastností Owner naplněnou s přidruženými uživatelskými daty, by byl:

```csharp
var sql = @"select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id";
var data = connection.Query<Post, User, Post>(sql,
(post, user) => { post.Owner = user; return post;});
```

Vzhledem k tomu, že nabízí méně zapouzdření, Dapperem vyžaduje, aby si vývojáři dozvěděli více o tom, jak jsou jejich data uložená, jak je efektivně dotazovat, a zapsali další kód pro jeho načtení. Při změně modelu místo pouhého vytvoření nové migrace (jiné funkce EF Core) a aktualizace informací o mapování na jednom místě v DbContext musí být všechny ovlivněné dotazy aktualizované. Tyto dotazy nemají žádné záruky v době kompilace, takže můžou v reakci na změny modelu nebo databáze přerušit za běhu. díky tomu je obtížné detekovat chyby rychleji. V systému Exchange pro tyto kompromisy nabízí Dapperem extrémně vysoký výkon.

Pro většinu aplikací a pro většinu částí téměř všech aplikací nabízí EF Core přijatelný výkon. Proto se přínosy pro produktivitu vývojářů můžou snížit na výkon. V případě dotazů, které mohou využívat ukládání do mezipaměti, může být samotný dotaz proveden pouze v malém procentu času, což vede k poměrně malým rozdílům ve výkonu dotazů moot.

## <a name="sql-or-nosql"></a>SQL nebo NoSQL

Tradičně jsou relační databáze, jako je SQL Server, na webu Marketplace pro trvalé úložiště dat, ale nejedná se o jediné dostupné řešení. Databáze NoSQL, jako je [MongoDB](https://www.mongodb.com/what-is-mongodb) , nabízejí odlišný přístup k ukládání objektů. Místo mapování objektů na tabulky a řádky je další možností serializace celého grafu objektů a uložení výsledku. Nejnižšími výhodami tohoto přístupu je jednoduchost a výkon. Je jednodušší uložit jeden serializovaný objekt s klíčem, než aby bylo možné objekt rozložit na mnoho tabulek se vztahy a aktualizacemi a řádky, které se mohly změnit od posledního načtení objektu z databáze. Podobně načítání a deserializace jednoho objektu z úložiště založeného na klíčích je obvykle mnohem rychlejší a jednodušší než složitá spojení nebo více databázových dotazů, které jsou nutné k úplnému vytvoření stejného objektu z relační databáze. Chybějící zámky nebo transakce nebo pevné schéma také zpřístupňuje NoSQL databází snadněji škálování napříč mnoha počítači a podporují velmi velké datové sady.

Na druhé straně databáze NoSQL (jak jsou obvykle volány) mají své nevýhody. Relační databáze používají normalizaci k vymáhání konzistence a vyhnout se duplikaci dat. Tím se zmenší celková velikost databáze a zajistí, že aktualizace sdílených dat budou k dispozici okamžitě v rámci databáze. V relační databázi může tabulka adres odkazovat na tabulku zemí podle ID, takže pokud se změnil název země nebo oblasti, budou se záznamy adres těžit z této aktualizace, aniž by bylo nutné je aktualizovat. V databázi NoSQL se ale adresa a přidružená země můžou serializovat jako součást mnoha uložených objektů. Aktualizace názvu země nebo oblasti by vyžadovala aktualizaci všech takových objektů, nikoli jednoho řádku. Relační databáze mohou také zajistit relační integritu vynucením pravidel, jako jsou cizí klíče. Databáze NoSQL obvykle nenabízejí taková omezení pro svá data.

Jiné databáze složitosti NoSQL musí řešit správu verzí. Když se změní vlastnosti objektu, nemusí být možné deserializovat z minulých verzí, které byly uloženy. Proto musí být všechny existující objekty, které mají serializovanou (předchozí) verzi objektu, aktualizovány tak, aby odpovídaly novému schématu. Nejedná se o koncepční rozdíl od relační databáze, kde změny schématu někdy vyžadují skripty aktualizace nebo aktualizace mapování. Počet položek, které je třeba upravit, je však často mnohem větší v přístupu NoSQL, protože existuje více duplicit dat.

Je možné, že databáze NoSQL ukládá více verzí objektů, ale některé pevné relační databáze schémat obvykle nepodporují. Nicméně v tomto případě bude kód vaší aplikace muset brát v úvahu existenci předchozích verzí objektů a přidává další složitost.

Databáze NoSQL obvykle vynutily [kyselinu](https://en.wikipedia.org/wiki/ACID), což znamená, že výhody výkonu i škálovatelnosti oproti relačním databázím. Jsou vhodné pro extrémně velké datové sady a objekty, které nejsou vhodné pro úložiště v normalizovaných strukturách tabulek. Neexistuje žádný důvod, proč jediná aplikace nemůže využívat relační i NoSQL databáze, a to s využitím každého z nich, kde se nejlépe hodí.

## <a name="azure-cosmos-db"></a>Databáze Azure Cosmos

Azure Cosmos DB je plně spravovaná databázová služba NoSQL, která nabízí cloudové úložiště dat bez schématu. Azure Cosmos DB je postavená na zajištění rychlého a předvídatelného výkonu, vysoké dostupnosti, elastického škálování a globální distribuce. I když se jedná o databázi NoSQL, můžou vývojáři používat pro data JSON bohatou a známou schopnost dotazů SQL. Všechny prostředky v Azure Cosmos DB jsou uloženy jako dokumenty JSON. Prostředky se spravují jako _položky_, což jsou dokumenty obsahující metadata a _kanály_, které jsou kolekcemi položek. Obrázek 8-2 ukazuje vztah mezi různými prostředky Azure Cosmos DB.

![Hierarchický vztah mezi prostředky v Azure Cosmos DB databáze JSON NoSQL](./media/image8-2.png)

**Obrázek 8-2.** Azure Cosmos DB organizace prostředků.

Dotazovací jazyk Azure Cosmos DB je jednoduché, ale výkonné rozhraní pro dotazování dokumentů JSON. Tento jazyk podporuje podmnožinu gramatiky ANSI SQL a přidává těsnou integraci s javascriptovými objekty, poli, vytvářením objektů a voláním funkcí.

**Odkazy – Azure Cosmos DB**

- Azure Cosmos DB Úvod <https://docs.microsoft.com/azure/cosmos-db/introduction>

## <a name="other-persistence-options"></a>Další možnosti trvalosti

Kromě možností relačního a NoSQL úložiště mohou aplikace ASP.NET Core používat Azure Storage k ukládání nejrůznějších formátů dat a souborů v cloudovém škálovatelném způsobem. Azure Storage je široce škálovatelná, takže můžete začít ukládat malé objemy dat a škálovat je tak, aby se ukládaly stovky nebo terabajty, pokud je vaše aplikace vyžaduje. Azure Storage podporuje čtyři druhy dat:

- Blob Storage nestrukturovaných textových nebo binárních úložišť, označovaných také jako úložiště objektů.

- Table Storage strukturovaných datových sad, které jsou přístupné prostřednictvím klíčů řádků.

- Queue Storage pro spolehlivé zasílání zpráv na základě fronty.

- File Storage pro přístup ke sdíleným souborům mezi virtuálními počítači Azure a místními aplikacemi.

**Odkazy – Azure Storage**

- Azure Storage Úvod <https://docs.microsoft.com/azure/storage/storage-introduction>

## <a name="caching"></a>Ukládání do mezipaměti

V případě webových aplikací by měly být jednotlivé webové žádosti dokončeny v nejkratší možné době. Toho můžete dosáhnout tak, že omezíte počet externích volání, které server musí provést, aby se žádost dokončila. Ukládání do mezipaměti zahrnuje ukládání kopie dat na server (nebo jiné úložiště dat, které je snazší dotazovat se na zdroj dat). Webové aplikace a zejména tradiční webové aplikace bez ověřování hesla potřebují pro každý požadavek sestavit celé uživatelské rozhraní. To často znamená, že mnoho stejných databázových dotazů opakovaně vychází z jednoho požadavku uživatele na další. Ve většině případů se tato data mění zřídka, proto existuje málo důvodů, jak ji z databáze trvale vyžádat. ASP.NET Core podporuje ukládání odpovědí do mezipaměti, pro ukládání celých stránek do mezipaměti a ukládání dat do mezipaměti, které podporuje podrobnější chování ukládání do mezipaměti.

Při implementaci ukládání do mezipaměti je důležité mít na paměti oddělení obav. Vyhněte se implementaci logiky ukládání do mezipaměti v logice přístupu k datům nebo v uživatelském rozhraní. Místo toho zapouzdřujte ukládání do mezipaměti ve vlastních třídách a pomocí konfigurace spravujte jeho chování. Postupuje podle otevřených/uzavřených a jednoduchých zodpovědností a usnadňuje vám správu způsobu ukládání do mezipaměti ve vaší aplikaci během rozšiřování.

### <a name="aspnet-core-response-caching"></a>Ukládání odpovědí do mezipaměti ASP.NET Core

ASP.NET Core podporuje dvě úrovně ukládání odpovědí do mezipaměti. První úroveň neukládá do mezipaměti cokoli na serveru, ale přidává hlavičky HTTP, které instruují klienty a proxy servery k ukládání odpovědí do mezipaměti. To je implementováno přidáním atributu ResponseCache na jednotlivé řadiče nebo akce:

```csharp
[ResponseCache(Duration = 60)]
public IActionResult Contact()
{
    ViewData["Message"] = "Your contact page.";
    return View();
}
```

V předchozím příkladu bude k odpovědi přidáno následující záhlaví, které dává klientům pokyn, aby výsledky do mezipaměti po dobu až 60 sekund.

Cache-Control: Public, Max-Age = 60

Aby bylo možné do aplikace přidat ukládání do mezipaměti na straně serveru, musíte odkazovat na balíček NuGet Microsoft. AspNetCore. ResponseCaching a pak přidat middleware pro ukládání odpovědí do mezipaměti. Tento middleware je nakonfigurovaný jak v ConfigureServices, tak v konfiguraci při spuštění:

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

Middleware pro ukládání odpovědí do mezipaměti bude automaticky ukládat odpovědi na základě sady podmínek, které můžete přizpůsobit. Ve výchozím nastavení se do mezipaměti ukládají pouze odpovědi 200 (OK) požadované prostřednictvím metody GET nebo HEAD. Kromě toho musí mít požadavky odpověď s hlavičkou Cache-Control: Public header a nesmí obsahovat hlavičky pro Authorization nebo Set-cookie. Podívejte se na [úplný seznam podmínek ukládání do mezipaměti, které používá middleware pro ukládání odpovědí do mezipaměti](/aspnet/core/performance/caching/middleware#conditions-for-caching).

### <a name="data-caching"></a>Ukládání dat do mezipaměti

Místo (nebo kromě) ukládání úplných webových odpovědí do mezipaměti můžete ukládat výsledky jednotlivých dotazů na data. V takovém případě můžete použít v ukládání do mezipaměti na webovém serveru nebo použít [distribuovanou mezipaměť](/aspnet/core/performance/caching/distributed). V této části se dozvíte, jak implementovat v mezipaměti paměti.

Přidáte podporu pro ukládání do mezipaměti (nebo distribuované) do mezipaměti v ConfigureServices:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMemoryCache();
    services.AddMvc();
}
```

Nezapomeňte přidat také balíček NuGet Microsoft. Extensions. Caching. Memory.

Po přidání služby si vyžádáte IMemoryCache prostřednictvím injektáže závislosti, kdykoli budete potřebovat přístup do mezipaměti. V tomto příkladu používá CachedCatalogService vzor návrhu proxy (nebo dekoratér) tím, že poskytuje alternativní implementaci ICatalogService, která řídí přístup k základní implementaci CatalogService (nebo k tomu přidává chování).

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

Chcete-li nakonfigurovat aplikaci tak, aby používala verzi služby uloženou v mezipaměti, ale stále umožňuje službě získat v jejím konstruktoru instanci CatalogService, kterou potřebuje, přidejte do ConfigureServices následující:

```csharp
services.AddMemoryCache();
services.AddScoped<ICatalogService, CachedCatalogService>();
services.AddScoped<CatalogService>();
```

V takovém případě se databáze volá do načtení dat katalogu pouze jednou za minutu, nikoli u všech požadavků. V závislosti na provozu na lokalitu to může mít výrazný vliv na počet dotazů provedených v databázi a na průměrnou dobu načítání stránky pro domovskou stránku, která v současné době závisí na všech třech dotazech vystavených touto službou.

K problému, který nastane při implementaci ukládání do mezipaměti, je _zastaralá data_ – to znamená, že data, která se změnila ve zdroji, ale zastaralá verze, zůstanou v mezipaměti. Jednoduchým způsobem, jak tento problém zmírnit, je použití malých mezipamětí, protože u zaneprázdněné aplikace je k rozšíření dat délky v mezipaměti omezená další výhoda. Představte si například stránku, která vytváří jeden databázový dotaz a je požadována desetkrát za sekundu. Pokud se tato stránka ukládá do mezipaměti po dobu jedné minuty, bude se počet dotazů databáze za minutu odpustit z 600 na 1, což snižuje 99,8%. Pokud místo toho jste udělali dobu trvání mezipaměti, celkové snížení by bylo 99,997%, ale teď je pravděpodobnost výrazně větší i potenciální stáří zastaralých dat.

Další možností je proaktivně odebrat položky mezipaměti, když jsou data, která obsahují, aktualizována. Jednotlivé položky lze odebrat, pokud je její klíč znám:

```csharp
_cache.Remove(cacheKey);
```

Pokud vaše aplikace zpřístupňuje funkce pro aktualizaci záznamů, které ukládá do mezipaměti, můžete odebrat odpovídající položky mezipaměti v kódu, který provádí aktualizace. V některých případech se může jednat o mnoho různých položek závislých na konkrétní sadě dat. V takovém případě může být užitečné vytvořit závislosti mezi položkami mezipaměti pomocí CancellationChangeToken. S CancellationChangeToken můžete vypršet platnost několika záznamů v mezipaměti tím, že token zrušíte.

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

Ukládání do mezipaměti může výrazně zlepšit výkon webových stránek, které opakovaně vyžádají stejné hodnoty z databáze. Nezapomeňte změřit přístup k datům a výkon stránky před použitím ukládání do mezipaměti a použít ukládání do mezipaměti jenom v případě, že je potřeba zlepšení. Ukládání do mezipaměti spotřebovává prostředky paměti webového serveru a zvyšuje složitost aplikace, takže je důležité, abyste s touto technikou nemuseli předčasně optimalizovat.

>[!div class="step-by-step"]
>[Předchozí](develop-asp-net-core-mvc-apps.md)
>[Další](test-asp-net-core-mvc-apps.md)
