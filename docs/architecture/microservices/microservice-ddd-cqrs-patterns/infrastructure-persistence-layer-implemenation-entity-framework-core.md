---
title: Implementace vrstvy trvalosti infrastruktury pomocí Entity Framework Core
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Prozkoumejte podrobnosti implementace vrstvy trvalé infrastruktury pomocí Entity Framework Core.
ms.date: 10/08/2018
ms.openlocfilehash: 7e3480999b115ac13f8d7ebcaed826b407aa7637
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295902"
---
# <a name="implement-the-infrastructure-persistence-layer-with-entity-framework-core"></a>Implementace vrstvy trvalosti infrastruktury s Entity Framework Core

Při použití relačních databází, jako jsou SQL Server, Oracle nebo PostgreSQL, je doporučený přístup implementovat vrstvu trvalosti založenou na Entity Framework (EF). EF podporuje LINQ a poskytuje objekty silného typu pro váš model a také zjednodušenou stálost databáze.

Entity Framework má jako součást .NET Framework dlouhou historii. Pokud používáte .NET Core, měli byste také použít Entity Framework Core, která běží v systému Windows nebo Linux stejným způsobem jako .NET Core. EF Core je úplný přepis Entity Framework implementovaný s mnohem menšími nároky a důležitými vylepšeními výkonu.

## <a name="introduction-to-entity-framework-core"></a>Úvod do Entity Framework Core

Jádro Entity Framework (EF) je odlehčená, rozšiřitelná a více platforem oblíbené technologie Entity Framework data pro přístup k datům. Byla představena s .NET Core v polovině až 2016.

Vzhledem k tomu, že Úvod do EF Core je již k dispozici v dokumentaci společnosti Microsoft, jednoduše poskytujeme odkazy na tyto informace.

### <a name="additional-resources"></a>Další zdroje

- **Entity Framework Core** \
  [https://docs.microsoft.com/ef/core/](/ef/core/)

- **Začínáme s ASP.NET Core a Entity Framework Core pomocí sady Visual Studio** \
  [https://docs.microsoft.com/aspnet/core/data/ef-mvc/](/aspnet/core/data/ef-mvc/)

- **DbContext – třída** \
  [https://docs.microsoft.com/dotnet/api/microsoft.entityframeworkcore.dbcontext](xref:Microsoft.EntityFrameworkCore.DbContext)

- **Compare EF Core & EF6. x** \
  [https://docs.microsoft.com/ef/efcore-and-ef6/index](/ef/efcore-and-ef6/index)

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a>Infrastruktura v Entity Framework Core z DDD perspektivy

Z bodu DDD je důležitou schopností EF použití doménových entit POCO, označovaných také v terminologii EF jako POCO *entity Code-First*. Pokud používáte doménové entity POCO, vaše třídy doménového modelu jsou ignorovány, a to po [ignorování perzistence](https://deviq.com/persistence-ignorance/) a principu [ignorování infrastruktury](https://ayende.com/blog/3137/infrastructure-ignorance) .

V případě vzorů na DDD byste měli zapouzdřit chování domény a pravidla v rámci samotné třídy entity, aby při přístupu k libovolné kolekci mohla řídit invariantní, ověřování a pravidla. Proto není dobrým zvykem v DDD, aby bylo možné získat veřejný přístup ke kolekcím podřízených entit nebo objektů hodnot. Místo toho chcete vystavit metody, které řídí, jak a kdy je možné aktualizovat vaše pole a kolekce vlastností a jaké chování a akce by měly nastat, pokud k tomu dojde.

Vzhledem k tomu, že EF Core 1,1 pro splnění těchto DDD požadavků, můžete místo veřejných vlastností použít ve svých entitách prostá pole. Pokud nechcete, aby pole entity bylo externě přístupné, můžete namísto vlastnosti vytvořit pouze atribut nebo pole. Lze také použít metody setter pro soukromé vlastnosti.

Podobným způsobem teď můžete mít k kolekcím přístup jen pro čtení pomocí veřejné vlastnosti zadané jako `IReadOnlyCollection<T>`, která je zajištěná členem soukromého pole pro kolekci ( `List<T>`jako) ve vaší entitě, která spoléhá na EF pro trvalost. Předchozí verze Entity Framework vyžadovaly podporu `ICollection<T>`vlastností kolekce, což znamenalo, že každý vývojář používající nadřazenou třídu entity může přidat nebo odebrat položky prostřednictvím svých kolekcí vlastností. Tato možnost by byla v porovnání s doporučenými vzory v DDD.

Můžete použít soukromou kolekci při vystavení objektu jen `IReadOnlyCollection<T>` pro čtení, jak je znázorněno v následujícím příkladu kódu:

```csharp
public class Order : Entity
{
    // Using private fields, allowed since EF Core 1.1
    private DateTime _orderDate;
    // Other fields ...

    private readonly List<OrderItem> _orderItems;
    public IReadOnlyCollection<OrderItem> OrderItems => _orderItems;

    protected Order() { }

    public Order(int buyerId, int paymentMethodId, Address address)
    {
        // Initializations ...
    }

    public void AddOrderItem(int productId, string productName,
                             decimal unitPrice, decimal discount,
                             string pictureUrl, int units = 1)
    {
        // Validation logic...

        var orderItem = new OrderItem(productId, productName,
                                      unitPrice, discount,
                                      pictureUrl, units);
        _orderItems.Add(orderItem);
    }
}
```

Všimněte si, `OrderItems` že vlastnost je přístupná jen pro čtení pomocí. `IReadOnlyCollection<OrderItem>` Tento typ je jen pro čtení, takže je chráněný před běžnými externími aktualizacemi.

EF Core poskytuje způsob mapování doménového modelu na fyzickou databázi bez "kontaminujících" doménového modelu. Je to čistě POCO kód .NET, protože akce mapování je implementovaná v perzistentní vrstvě. V této akci mapování je nutné nakonfigurovat mapování polí na databázi. V následujícím `OnModelCreating` příkladu metody z `OrderEntityTypeConfiguration` `OrderingContext` a třídy volá volání, aby `SetPropertyAccessMode` EF Core přístup `OrderItems` k vlastnosti prostřednictvím jejího pole.

```csharp
// At OrderingContext.cs from eShopOnContainers
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
   // ...
   modelBuilder.ApplyConfiguration(new OrderEntityTypeConfiguration());
   // Other entities’ configuration ...
}

// At OrderEntityTypeConfiguration.cs from eShopOnContainers
class OrderEntityTypeConfiguration : IEntityTypeConfiguration<Order>
{
    public void Configure(EntityTypeBuilder<Order> orderConfiguration)
    {
        orderConfiguration.ToTable("orders", OrderingContext.DEFAULT_SCHEMA);
        // Other configuration

        var navigation =
              orderConfiguration.Metadata.FindNavigation(nameof(Order.OrderItems));

        //EF access the OrderItem collection property through its backing field
        navigation.SetPropertyAccessMode(PropertyAccessMode.Field);

        // Other configuration
    }
}
```

Pokud použijete pole místo vlastností, `OrderItem` entita se uchová stejně, jako by `List<OrderItem>` měla vlastnost. Nicméně zpřístupňuje jeden přistupující objekt, `AddOrderItem` metodu pro přidání nových položek do objednávky. Výsledkem je, že chování a data jsou vzájemně propojeny a budou konzistentní v jakémkoli kódu aplikace, který používá doménový model.

## <a name="implement-custom-repositories-with-entity-framework-core"></a>Implementace vlastních úložišť pomocí Entity Framework Core

Na úrovni implementace je úložiště jednoduše třída, která má kód trvalosti dat koordinovaný podle pracovní jednotky (DBContext v EF Core) při provádění aktualizací, jak je znázorněno v následující třídě:

```csharp
// using statements...
namespace Microsoft.eShopOnContainers.Services.Ordering.Infrastructure.Repositories
{
    public class BuyerRepository : IBuyerRepository
    {
        private readonly OrderingContext _context;
        public IUnitOfWork UnitOfWork
        {
            get
            {
                return _context;
            }
        }

        public BuyerRepository(OrderingContext context)
        {
            _context = context ?? throw new ArgumentNullException(nameof(context));
        }

        public Buyer Add(Buyer buyer)
        {
            return _context.Buyers.Add(buyer).Entity;
        }

        public async Task<Buyer> FindAsync(string BuyerIdentityGuid)
        {
            var buyer = await _context.Buyers
                .Include(b => b.Payments)
                .Where(b => b.FullName == BuyerIdentityGuid)
                .SingleOrDefaultAsync();

            return buyer;
        }
    }
}
```

Všimněte si, že rozhraní IBuyerRepository přichází z vrstvy modelu domény jako kontrakt. Implementace úložiště se ale provádí na vrstvě trvalosti a infrastruktury.

EF DbContext dochází prostřednictvím konstruktoru prostřednictvím injektáže závislosti. V kontejneru IOC je sdílená mezi několika úložištěmi v rámci stejného oboru požadavku HTTP, a to díky`ServiceLifetime.Scoped`výchozímu života () v kontejneru (dá se taky explicitně `services.AddDbContext<>`nastavit pomocí).

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a>Metody pro implementaci v úložišti (aktualizace nebo transakce oproti dotazům)

V rámci každé třídy úložiště byste měli umístit metody trvalosti, které aktualizují stav entit obsažených v související agregaci. Nezapomeňte, že mezi agregovaným a souvisejícím úložištěm je relace 1:1. Vezměte v úvahu, že objekt agregované kořenové entity může mít vložené podřízené entity v rámci svého grafu EF. Například kupující může mít více způsobů platby jako související podřízené entity.

Vzhledem k tomu, že je přístup k mikroslužbám řazení v eShopOnContainers také založen na CQS/CQRS, většina dotazů není implementována ve vlastních úložištích. Vývojáři mají volnost v vytváření dotazů a spojení, která potřebují pro prezentační vrstvu bez omezení vyplývajících z agregací, vlastních úložišť na agregaci a na DDD všeobecně. Většina vlastních úložišť navržených v tomto průvodci má několik metod aktualizace nebo transakcí, ale pouze metody dotazů, které jsou potřeba k aktualizaci dat. Například úložiště BuyerRepository implementuje metodu FindAsync, protože aplikace musí před vytvořením nového nákupčího souvisejícího s objednávkou zjistit, zda existuje konkrétní kupující.

Nicméně reálné metody dotazů pro odeslání dat do prezentační vrstvy nebo klientských aplikací jsou implementovány, jak je uvedeno v dotazech CQRS na základě flexibilních dotazů pomocí Dapperem.

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a>Použití vlastního úložiště versus přímé použití EF DbContext

Třída Entity Framework DbContext je založena na pracovní jednotce a vzorech úložiště a lze ji použít přímo z kódu, jako je například z kontroleru ASP.NET Core MVC. To je způsob, jak můžete vytvořit nejjednodušší kód, jako v rámci mikroslužby katalogu CRUD v eShopOnContainers. V případech, kdy chcete nejjednodušší kód, můžete chtít přímo použít třídu DbContext, protože to mnoho vývojářů.

Implementace vlastních úložišť ale poskytuje několik výhod při implementaci složitějších mikroslužeb nebo aplikací. Pracovní jednotka a vzorce úložiště mají za cíl zapouzdřit vrstvu trvalosti infrastruktury, aby bylo možné je oddělit od vrstev aplikace a doménového modelu. Implementace těchto vzorů může usnadnit použití povedených úložišť, které simulují přístup k databázi.

Na obrázku 7-18 vidíte rozdíly mezi nepoužíváním úložišť (přímo pomocí DbContext EF) a s využitím úložišť, která usnadňují navýšení těchto úložišť.

![Porovnání pomocí vlastního úložiště a jednoduchého DbContext: vlastní úložiště přidá vrstvu abstrakce, která se dá použít ke snadnému testování pomocí napodobení úložiště.](./media/image19.png)

**Obrázek 7-18**. Použití vlastních úložišť oproti jednoduchému DbContext

Při napodobování je k dispozici více alternativ. Mohli byste napodobovat jenom úložiště nebo byste mohli napodobovat celou pracovní jednotku. Obvykle je napodobení pouze úložišť dostatečně a složitost pro abstrakci a navýšení celé pracovní jednotky většinou není potřeba.

Později, když se zaměříme na aplikační vrstvu, uvidíte, jak funguje vkládání závislostí v ASP.NET Core a jak je implementováno při použití úložišť.

V krátkém případě vlastní úložiště umožňují testovat kód snadněji pomocí testů jednotek, které nejsou ovlivněny stavem datové vrstvy. Pokud spustíte testy, které také přistupují ke skutečné databázi prostřednictvím Entity Framework, nejedná se o testy jednotek, ale integrační testy, které jsou mnohem pomalejší.

Pokud jste používali DbContext přímo, museli byste ji napředt nebo spustit testy jednotek pomocí SQL Server v paměti s předvídatelnými daty pro testování částí. Ale napodobování DbContext nebo řízení falešných dat vyžaduje více práce, než na úrovni úložiště. Je samozřejmě možné vždy otestovat řadiče MVC.

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a>Životnost instance EF DbContext a IUnitOfWork ve vašem kontejneru IoC

Objekt (vystavený `IUnitOfWork` jako objekt) by měl být sdílen mezi více úložišť v rámci stejného oboru požadavku HTTP. `DbContext` Jedná se například o hodnotu true, pokud se prováděná operace musí zabývat více agregacemi, nebo jednoduše, protože používáte více instancí úložiště. Je také důležité uvést, že `IUnitOfWork` rozhraní je součástí vaší doménové vrstvy, nikoli typu EF Core.

Aby to bylo možné, musí mít instance `DbContext` objektu nastavenou dobu platnosti služby na ServiceLifetime. scoped. Toto je výchozí doba života při registraci `DbContext` `services.AddDbContext` v v kontejneru IOC z metody `Startup.cs` ConfigureServices souboru v projektu webového rozhraní API ASP.NET Core. Následující kód to znázorňuje.

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    // Add framework services.
    services.AddMvc(options =>
    {
        options.Filters.Add(typeof(HttpGlobalExceptionFilter));
    }).AddControllersAsServices();

    services.AddEntityFrameworkSqlServer()
      .AddDbContext<OrderingContext>(options =>
      {
          options.UseSqlServer(Configuration["ConnectionString"],
                               sqlOptions => sqlOptions.MigrationsAssembly(typeof(Startup).GetTypeInfo().
                                                                                    Assembly.GetName().Name));
      },
      ServiceLifetime.Scoped // Note that Scoped is the default choice
                             // in AddDbContext. It is shown here only for
                             // pedagogic purposes.
      );
}
```

Režim vytváření instancí DbContext by neměl být nakonfigurovaný jako ServiceLifetime. přechodný nebo ServiceLifetime. singleton.

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a>Doba života instance úložiště ve vašem kontejneru IoC

Podobným způsobem je, že životnost úložiště by měla být obvykle nastavena jako vymezená (InstancePerLifetimeScope v Autofac). Může to být také přechodný (InstancePerDependency v Autofac), ale vaše služba bude efektivnější v souvislosti s pamětí při použití vymezené životnosti.

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

Všimněte si, že použití životnosti singleton pro úložiště může způsobit vážné problémy s souběžnou dostupností, když je DbContext nastavené na rozsah (InstancePerLifetimeScope) životního cyklu (výchozí doba pro DBContext).

### <a name="additional-resources"></a>Další zdroje

- **Implementace vzorového úložiště a pracovní jednotky v aplikaci ASP.NET MVC** \
  <https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application>

- **Jonathana Allen. Strategie implementace pro model úložiště s Entity Framework, Dapperem a řetězem** \
  <https://www.infoq.com/articles/repository-implementation-strategies>

- **Cesar de la Torre. Porovnávání ASP.NET Corech životností kontejnerových služeb s Autofac IoC instancemi kontejnerů** \
  <https://devblogs.microsoft.com/cesardelatorre/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/>

## <a name="table-mapping"></a>Mapování tabulek

Mapování tabulek identifikuje tabulková data, která mají být dotazována a uložena do databáze. Dříve jste viděli, jak můžete použít doménové entity (například doménu produktu nebo objednávky) k vygenerování souvisejícího schématu databáze. EF je silně navržený kolem konceptu *konvencí*. Otázky adres, jako je například "jaký bude název tabulky?" nebo "jaká vlastnost je primární klíč?" Konvence jsou obvykle založené na konvenčních názvech, například je typický pro primární klíč jako vlastnost, která končí ID.

Podle konvence se Každá entita nastaví tak, aby se namapovala na tabulku se stejným názvem, `DbSet<TEntity>` jako má vlastnost, která zpřístupňuje entitu v odvozeném kontextu. Pokud pro `DbSet<TEntity>` danou entitu není zadána žádná hodnota, použije se název třídy.

### <a name="data-annotations-versus-fluent-api"></a>Datové poznámky versus rozhraní API Fluent

Existuje mnoho dalších konvencí EF Core a většinu z nich lze změnit pomocí datových poznámek nebo rozhraní API Fluent implementovaných v rámci metody OnModelCreating.

Datové poznámky musí být použity na samotných třídách modelů entit, což je výraznější způsob zobrazení z bodu DDD. Důvodem je to, že máte v případě, že máte v tomto modelu v angličtině, datové poznámky týkající se databáze infrastruktury. Na druhé straně je rozhraní Fluent API pohodlný způsob, jak změnit většinu konvencí a mapování v rámci vrstvy infrastruktury pro trvalost dat, takže model entity bude čistý a oddělený od infrastruktury trvalosti.

### <a name="fluent-api-and-the-onmodelcreating-method"></a>Rozhraní Fluent API a metoda OnModelCreating

Jak bylo zmíněno, chcete-li změnit konvence a mapování, můžete použít metodu OnModelCreating ve třídě DbContext.

Řazení mikroslužeb v eShopOnContainers implementuje explicitní mapování a konfiguraci v případě potřeby, jak je znázorněno v následujícím kódu.

```csharp
// At OrderingContext.cs from eShopOnContainers
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
   // ...
   modelBuilder.ApplyConfiguration(new OrderEntityTypeConfiguration());
   // Other entities’ configuration ...
}

// At OrderEntityTypeConfiguration.cs from eShopOnContainers
class OrderEntityTypeConfiguration : IEntityTypeConfiguration<Order>
{
    public void Configure(EntityTypeBuilder<Order> orderConfiguration)
    {
            orderConfiguration.ToTable("orders", OrderingContext.DEFAULT_SCHEMA);

            orderConfiguration.HasKey(o => o.Id);

            orderConfiguration.Ignore(b => b.DomainEvents);

            orderConfiguration.Property(o => o.Id)
                .ForSqlServerUseSequenceHiLo("orderseq", OrderingContext.DEFAULT_SCHEMA);

            //Address Value Object persisted as owned entity type supported since EF Core 2.0
            orderConfiguration.OwnsOne(o => o.Address);

            orderConfiguration.Property<DateTime>("OrderDate").IsRequired();
            orderConfiguration.Property<int?>("BuyerId").IsRequired(false);
            orderConfiguration.Property<int>("OrderStatusId").IsRequired();
            orderConfiguration.Property<int?>("PaymentMethodId").IsRequired(false);
            orderConfiguration.Property<string>("Description").IsRequired(false);

            var navigation = orderConfiguration.Metadata.FindNavigation(nameof(Order.OrderItems));

            // DDD Patterns comment:
            //Set as field (New since EF 1.1) to access the OrderItem collection property through its field
            navigation.SetPropertyAccessMode(PropertyAccessMode.Field);

            orderConfiguration.HasOne<PaymentMethod>()
                .WithMany()
                .HasForeignKey("PaymentMethodId")
                .IsRequired(false)
                .OnDelete(DeleteBehavior.Restrict);

            orderConfiguration.HasOne<Buyer>()
                .WithMany()
                .IsRequired(false)
                .HasForeignKey("BuyerId");

            orderConfiguration.HasOne(o => o.OrderStatus)
                .WithMany()
                .HasForeignKey("OrderStatusId");
    }
}
```

V rámci stejné metody OnModelCreating můžete nastavit všechna mapování Fluent rozhraní API, ale je vhodné rozdělit kód na oddíly a mít více tříd konfigurace, jednu pro každou entitu, jak je znázorněno v příkladu. Zejména u velkých modelů je vhodné mít samostatné třídy konfigurace pro konfiguraci různých typů entit.

Kód v příkladu ukazuje několik explicitních deklarací a mapování. EF Core konvence ale mnoho z těchto mapování provede automaticky, takže skutečný kód, který byste potřebovali v případě, může být menší.

### <a name="the-hilo-algorithm-in-ef-core"></a>Algoritmus Hi/Lo v EF Core

Zajímavým aspektem kódu v předchozím příkladu je, že jako strategii generování klíčů používá [algoritmus Hi/Lo](https://vladmihalcea.com/the-hilo-algorithm/) .

Algoritmus Hi/Lo je užitečný v případě, že před potvrzením změn potřebujete jedinečné klíče. Jako souhrn přiřadí algoritmus Hi-Lo jedinečné identifikátory řádkům tabulky, a to i v závislosti na tom, že se řádek v databázi okamžitě ukládá. To vám umožní začít používat identifikátory hned, jak se děje s pravidelnými sekvenčními identifikátory databáze.

Algoritmus Hi/Lo popisuje mechanismus pro získání dávky jedinečných ID ze související databázové sekvence. Tato ID je bezpečné použít, protože databáze zaručuje jedinečnost, takže mezi uživateli nebudou žádné kolize. Tento algoritmus je zajímavý z těchto důvodů:

- Neruší vzorek pracovní jednotky.

- Získá ID sekvencí v dávkách, aby se minimalizovala výměna zpráv do databáze.

- Vygeneruje lidský čitelný identifikátor, na rozdíl od technik, které používají identifikátory GUID.

EF Core podporuje [Hilo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) pomocí metody ForSqlServerUseSequenceHiLo, jak je znázorněno v předchozím příkladu.

### <a name="map-fields-instead-of-properties"></a>Mapování polí namísto vlastností

Pomocí této funkce, která je dostupná od EF Core 1,1, můžete přímo namapovat sloupce na pole. Je možné, že ve třídě entity nebudete moci používat vlastnosti a pouze mapovat sloupce z tabulky na pole. Běžně se používá pro všechny interní stavy, které nemusejí být k dispozici mimo entitu.

Můžete to provést s jedním polem nebo také s kolekcemi, jako je `List<>` pole. Tento bod byl zmíněn dříve, když jsme probrali modelování tříd doménového modelu, ale tady vidíte, jak se toto mapování provádí `PropertyAccessMode.Field` s konfigurací zvýrazněnou v předchozím kódu.

### <a name="use-shadow-properties-in-ef-core-hidden-at-the-infrastructure-level"></a>Použití vlastností stínu v EF Core skryté na úrovni infrastruktury

Vlastnosti stínu v EF Core jsou vlastnosti, které neexistují v modelu třídy entity. Hodnoty a stavy těchto vlastností se v úrovni infrastruktury uchovávají čistě ve třídě [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) .

## <a name="implement-the-query-specification-pattern"></a>Implementace vzoru specifikace dotazu

Jak je uvedeno dříve v oddílu návrhu, je vzor návrhu založený na doméně navržený jako místo, kde můžete vložit definici dotazu s volitelnou logikou řazení a stránkování.

Vzor specifikace dotazu definuje dotaz v objektu. Chcete-li například zapouzdřit stránkovaný dotaz, který vyhledává některé produkty, můžete vytvořit specifikaci PagedProduct, která bude přebírá nezbytné vstupní parametry (pageNumber, pageSize, Filter atd.). Potom v rámci libovolné metody úložiště (obvykle přetížení seznamu ()) přijme IQuerySpecification a spustí očekávaný dotaz na základě této specifikace.

Příkladem rozhraní Obecné specifikace je následující kód z [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb).

```csharp
// GENERIC SPECIFICATION INTERFACE
// https://github.com/dotnet-architecture/eShopOnWeb

public interface ISpecification<T>
{
    Expression<Func<T, bool>> Criteria { get; }
    List<Expression<Func<T, object>>> Includes { get; }
    List<string> IncludeStrings { get; }
}
```

Pak je implementace základní třídy Obecné specifikace následující.

```csharp
// GENERIC SPECIFICATION IMPLEMENTATION (BASE CLASS)
// https://github.com/dotnet-architecture/eShopOnWeb

public abstract class BaseSpecification<T> : ISpecification<T>
{
    public BaseSpecification(Expression<Func<T, bool>> criteria)
    {
        Criteria = criteria;
    }
    public Expression<Func<T, bool>> Criteria { get; }

    public List<Expression<Func<T, object>>> Includes { get; } =
                                           new List<Expression<Func<T, object>>>();

    public List<string> IncludeStrings { get; } = new List<string>();

    protected virtual void AddInclude(Expression<Func<T, object>> includeExpression)
    {
        Includes.Add(includeExpression);
    }

    // string-based includes allow for including children of children
    // e.g. Basket.Items.Product
    protected virtual void AddInclude(string includeString)
    {
        IncludeStrings.Add(includeString);
    }
}
```

Následující specifikace načte jednu entitu košíku, která má buď ID košíku, nebo ID kupujícího, ke kterému patří košík. Bude [eagerly načíst](https://docs.microsoft.com/ef/core/querying/related-data) kolekci položek košíku.

```csharp
// SAMPLE QUERY SPECIFICATION IMPLEMENTATION

public class BasketWithItemsSpecification : BaseSpecification<Basket>
{
    public BasketWithItemsSpecification(int basketId)
        : base(b => b.Id == basketId)
    {
        AddInclude(b => b.Items);
    }
    public BasketWithItemsSpecification(string buyerId)
        : base(b => b.BuyerId == buyerId)
    {
        AddInclude(b => b.Items);
    }
}
```

A nakonec vidíte, jak obecné úložiště EF může tuto specifikaci použít k filtrování a Eager dat, která se vztahují k danému typu entity T.

```csharp
// GENERIC EF REPOSITORY WITH SPECIFICATION
// https://github.com/dotnet-architecture/eShopOnWeb

public IEnumerable<T> List(ISpecification<T> spec)
{
    // fetch a Queryable that includes all expression-based includes
    var queryableResultWithIncludes = spec.Includes
        .Aggregate(_dbContext.Set<T>().AsQueryable(),
            (current, include) => current.Include(include));

    // modify the IQueryable to include any string-based include statements
    var secondaryResult = spec.IncludeStrings
        .Aggregate(queryableResultWithIncludes,
            (current, include) => current.Include(include));

    // return the result of the query using the specification's criteria expression
    return secondaryResult
                    .Where(spec.Criteria)
                    .AsEnumerable();
}
```

Kromě zapouzdření logiky filtrování může specifikace určit tvar dat, která mají být vrácena, včetně vlastností, které mají být naplněny.

I když nedoporučujeme vracet IQueryable z úložiště, je zcela dobré je v úložišti použít k sestavení sady výsledků. Tento přístup můžete zobrazit v metodě seznamu výše, která používá mezilehlé výrazy IQueryable k sestavení seznamu zahrnutí dotazu před provedením dotazu s kritérii specifikace na posledním řádku.

### <a name="additional-resources"></a>Další zdroje

- **Mapování tabulek** \
  [https://docs.microsoft.com/ef/core/modeling/relational/tables](/ef/core/modeling/relational/tables)

- **Pomocí HiLo vygenerujte klíče s Entity Framework Core** \
  <https://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/>

- **Zálohovaná pole** \
  [https://docs.microsoft.com/ef/core/modeling/backing-field](/ef/core/modeling/backing-field)

- **Steve Smith. Zapouzdřené kolekce v Entity Framework Core** \
  <https://ardalis.com/encapsulated-collections-in-entity-framework-core>

- **Vlastnosti stínu** \
  [https://docs.microsoft.com/ef/core/modeling/shadow-properties](/ef/core/modeling/shadow-properties)

- **Vzor specifikace** \
  <https://deviq.com/specification-pattern/>

> [!div class="step-by-step"]
> [Předchozí](infrastructure-persistence-layer-design.md)Další
> [](nosql-database-persistence-infrastructure.md)
