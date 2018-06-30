---
title: Implementace vrstvu trvalosti infrastruktury základní Entity Framework
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Implementace vrstvu trvalosti infrastruktury základní Entity Framework
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.openlocfilehash: 6003252d7e87428c7f954b57c3b67a041e3f3b15
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106473"
---
# <a name="implementing-the-infrastructure-persistence-layer-with-entity-framework-core"></a>Implementace vrstvu trvalosti infrastruktury základní Entity Framework

Při použití relačních databází, jako je například SQL Server, Oracle nebo PostgreSQL doporučený postup je implementace vrstvu trvalosti založené na Entity Framework (EF). EF podporuje LINQ a poskytuje objektů se silným typem pro váš model, jakož i zjednodušené trvalost do vaší databáze.

Rozhraní Entity Framework má dlouho historie v rámci rozhraní .NET Framework. Pokud používáte .NET Core, byste měli použít také Entity Framework Core, který běží na systému Windows nebo Linux stejným způsobem jako .NET Core. Základní EF je kompletní přepisování Entity Frameworku, implementováno s mnohem menší nároky a důležitá vylepšení výkonu.

## <a name="introduction-to-entity-framework-core"></a>Úvod do Entity Framework Core

Základní Entity Framework (EF) je lightweight rozšiřitelný, a přístup technologie a platformy verzi oblíbených datům Entity Framework. Byla zavedená s .NET Core v polovině 2016.

Vzhledem k tomu, že Úvod do základní EF je již k dispozici v dokumentaci společnosti Microsoft, tady jednoduše poskytujeme odkazy na tyto informace.

#### <a name="additional-resources"></a>Další zdroje

-   **Základní Entity Framework**
    [*https://docs.microsoft.com/ef/core/*](https://docs.microsoft.com/ef/core/)

-   **Začínáme s ASP.NET Core a Entity Framework Core pomocí sady Visual Studio**
    [*https://docs.microsoft.com/aspnet/core/data/ef-mvc/*](https://docs.microsoft.com/aspnet/core/data/ef-mvc/)

-   **Třída DbContext**
    [*https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext*](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext)

-   **Porovnání EF základní & EF6.x**
    [*https://docs.microsoft.com/ef/efcore-and-ef6/index*](https://docs.microsoft.com/ef/efcore-and-ef6/index)

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a>Infrastruktury v Entity Framework Core z hlediska DDD

Z DDD hlediska, je důležitou schopností EF možnost používat domény entity objektů POCO, také známé v terminologii EF jako objektů POCO *kód – první entity*. Pokud používáte domény entity objektů POCO, tříd modelu domény jsou trvalost – které ignorují, následující [trvalost které](http://deviq.com/persistence-ignorance/) a [infrastruktury které](https://ayende.com/blog/3137/infrastructure-ignorance) zásady.

Za vzory DDD by měl zapouzdřovat domény chování a pravidla v rámci třídy entity samostatně, takže ho můžete řídit výstupních podmínek, ověření a pravidel, při přístupu k jakékoli kolekce. Proto není vhodné v DDD umožňující veřejný přístup do kolekcí podřízených entit nebo hodnota objekty. Místo toho kterou chcete vystavit metody, které řídí, jak a kdy mohou být aktualizovány polí a vlastností kolekce, a jaké chování a akcí, má dojít, pokud k tomu dojde.

Od verze 1.1 základní EF splňovat tyto požadavky DDD, může mít prostý pole v místo veřejné vlastnosti vaší entity. Pokud nechcete, aby pole entity externě přístupné, můžete vytvořit pouze atribut nebo pole místo vlastnost. Můžete také použít privátní vlastnost Setter.

Podobným způsobem, můžete Teď máte přístup jen pro čtení k kolekce pomocí zadané jako veřejná vlastnost `IReadOnlyCollection<T>`, který je zálohovaný díky členem soukromé pole pro kolekci (například `List<T>`) ve vaší entity, které jsou závislé na EF trvalosti. Předchozí verze Entity Frameworku požadované vlastnosti kolekce pro podporu `ICollection<T>`, který určená, kdokoli z vývojářů pomocí třídy nadřazená entita může přidat nebo odebrat položky přes jeho vlastnost kolekce. Tato možnost by proti doporučené vzory v DDD.

Můžete použít kolekci privátní při vystavení jen pro čtení `IReadOnlyCollection<T>` objektu, jak je znázorněno v následujícím příkladu kódu:

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

Všimněte si, že `OrderItems` vlastnost lze přistupovat pouze jako jen pro čtení pomocí `IReadOnlyCollection<OrderItem>`. Tento typ je jen pro čtení, takže je chráněný proti externí pravidelných aktualizace. 

Základní EF poskytuje způsob, jak mapování modelu domény na fyzické databázi bez "kontaminujících" modelu domény. Je čistá .NET objektů POCO kódu, protože mapování akce je implementována ve vrstvu trvalosti. V této akci mapování budete muset konfigurovat mapování polí do databáze. V následujícím příkladu metody OnModelCreating informuje zvýrazněný EF základní přístup k vlastnosti OrderItems prostřednictvím jeho pole.

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

Pokud použijete pole místo vlastnosti, je entita OrderItem nastavené jako trvalé stejně, jako by se mělo seznam&lt;OrderItem&gt; vlastnost. Však zveřejňuje jednoho přístupového objektu, `AddOrderItem` metoda pro přidání nových položek do pořadí. V důsledku toho chování a data jsou svázané společně a bude konzistentní v rámci aplikace kód, který používá model domény.

## <a name="implementing-custom-repositories-with-entity-framework-core"></a>Implementace vlastní úložiště základní Entity Framework

Na úrovni implementace úložiště je jednoduše třídu s kódem trvalosti dat, koordinuje jednotka práce (DBContext v základní EF) při provádění aktualizací, jak je znázorněno v následující třídy:

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

Všimněte si, že rozhraní IBuyerRepository pochází z vrstvy modelu domény jako kontraktu. Implementace úložiště se však provádí na trvalosti a vrstvě infrastruktury.

EF DbContext přicházejí konstruktoru pomocí vkládání závislostí. Jsou sdílena mezi několika úložiště v rámci stejného oboru požadavku HTTP, díky jeho výchozí doba života (ServiceLifetime.Scoped) v kontejneru IoC (která může také být explicitně nastaveny službou. AddDbContext&lt;&gt;).

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a>Metody k implementaci v úložišti (aktualizace nebo transakce a dotazy)

V rámci každé třídy úložiště byste měli umístit trvalost metody, které aktualizuje stav entity obsažený v jeho související agregace. Mějte na paměti, že existuje relace 1: 1 mezi agregace a jeho souvisejících úložiště. Vezměte v úvahu, že objekt entity agregační kořenové může vložených podřízených entit v rámci jeho EF grafu. Například kupujících může mít více způsoby platby jako souvisejících podřízených entit.

Vzhledem k tomu, že přístup pro řazení mikroslužbu v eShopOnContainers také podle CQS/CQRS, většinu dotazů nejsou implementované v vlastní úložiště. Vývojáři mají možnost používat tato zařízení k vytvoření dotazů a spojení, které potřebují pro prezentační vrstvy bez omezení, způsobené agregace, vlastní úložiště na agregaci a DDD obecně. Většina vlastní úložiště navrhované tímto průvodcem má několik aktualizací nebo transakční metody, ale jenom metody dotazů nutná, aby se aktualizovat data. Například úložiště BuyerRepository implementuje metodu asynchronně vyhledá, protože aplikace je potřeba vědět, zda existuje konkrétní kupujících před vytvořením nového kupujících související s pořadí.

Však budete implementovat metody skutečné dotazů se získat data k odeslání do prezentační vrstvy nebo klienta aplikace, jak je uvedeno v dotazech CQRS podle flexibilní dotazy pomocí Dapper.

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a>Použití vlastního úložiště a kdy EF DbContext přímo

Třída Entity Framework DbContext podle vzorů jednotky práce a úložiště a slouží přímo z vašeho kódu, například z řadiče ASP.NET Core MVC. To znamená způsob, jakým můžete vytvořit kód nejjednodušší jako mikroslužbu katalogu CRUD v eShopOnContainers. V případech, kde chcete nejjednodušší kód možné můžete přímo použití třídy DbContext, stejně jako celá řada vývojářů.

Ale implementace vlastní úložiště nabízí několik výhod při implementaci složitější mikroslužeb nebo aplikace. Vzory jednotky práce a úložiště jsou určeny k zapouzdření vrstvu trvalosti infrastruktury, je odpojená od aplikace a vrstvy modelu domény. Implementace tyto vzory usnadnit používání imitované úložišť simulaci přístup k databázi.

Obrázek 9 až 18 se zobrazí rozdíly mezi nepoužíváte úložiště (přímo pomocí EF DbContext) a kdy úložiště, které usnadňují model těchto úložiště.

![](./media/image19.png)

**Obrázek 9 až 18**. Použití vlastní úložiště versus prostý DbContext

Při mocking se více alternativy. Může model právě úložiště nebo může model celou pracovní jednotka. Obvykle mocking právě úložiště je dostatek a složitost a abstraktní model celou pracovní jednotka není obvykle nutné.

Později když se zaměříme na aplikační vrstvu, zobrazí se fungování vkládání závislostí v ASP.NET Core a jak jsou implementované při použití úložiště.

Stručně řečeno vlastní úložiště umožňují snadněji testování kódu pomocí jednotkových testů, které nejsou vliv stav dat vrstvy. Pokud spustíte testy, které také přístup k databázi skutečné prostřednictvím rozhraní Entity Framework, nejsou testování částí, ale testy integrace, které jsou mnohem nižší.

Pokud jste používali DbContext přímo, jenom možnost, kterou byste měli by mohla být spouštění testů jednotek pomocí serveru SQL v paměti s předvídatelný dat pro testování částí. Nebude moci řídit mock objektů a falešných dat na úrovni úložiště stejným způsobem. Samozřejmě může vždy otestovat řadiče MVC.

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a>EF DbContext a IUnitOfWork doba platnosti instance v vaší kontejner IoC

Objekt DbContext (zveřejněné jako objekt IUnitOfWork) může být potřeba sdílet mezi více úložiště v rámci stejného oboru požadavku HTTP. Například to platí při operaci spouštěna musí pracovat s více agregace, ani jednoduše vzhledem k tomu, že používáte více instancí úložiště. Je také důležité zmínit, že rozhraní IUnitOfWork je součástí vaší domény vrstvy, není typ EF jádra.

Aby bylo možné provést, musí mít jeho služby dobu života nastavenu na ServiceLifetime.Scoped instanci objekt DbContext. Toto je výchozí doba života při registraci DbContext s služeb. AddDbContext ve vaší kontejner IoC z metody ConfigureServices souboru Startup.cs v projektu webového rozhraní API ASP.NET Core. Následující kód to znázorňuje.

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

Režim vytváření instancí DbContext by se neměla konfigurovat jako ServiceLifetime.Transient nebo ServiceLifetime.Singleton.

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a>Doba platnosti instance úložiště v vaší kontejner IoC

Podobným způsobem musí být v úložišti životnost obvykle nastavená jako oboru (InstancePerLifetimeScope v Autofac). Také může být přechodná (InstancePerDependency v Autofac), ale vaše služba bude efektivnější v paměti namapoval při použití vymezená životního cyklu.

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

Všimněte si, že pomocí singleton doba platnosti pro úložiště by mohla způsobovat můžete souběžnosti závažné problémy vaší DbContext nastavena na obor životnosti (InstancePerLifetimeScope) (výchozí doba života pro DBContext).

#### <a name="additional-resources"></a>Další zdroje

-   **Implementace úložiště a jednotky pracovních vzorů v aplikaci ASP.NET MVC**
    [*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)

-   **Jonathan Allen. Strategie implementace pro vzor úložiště s platformou Entity Framework, Dapper a řetězec**
    [*https://www.infoq.com/articles/repository-implementation-strategies*](https://www.infoq.com/articles/repository-implementation-strategies)

-   **Cesaru členka Torre. Porovnávání životnosti služby kontejner IoC jádro ASP.NET s obory instance kontejner Autofac IoC**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)

## <a name="table-mapping"></a>Mapování tabulek

Mapování tabulky identifikuje data tabulky, která mají být získaných z a uložit do databáze. Dříve jste viděli, jak lze pomocí entity domény (například produktu nebo pořadí doména) Generovat schéma související databáze. EF je důrazně uspořádaná kolem koncept *konvence*. Konvence adresu otázky typu "Jaký název tabulky bude?" nebo "jaké vlastnost je primární klíč?" Konvence jsou obvykle založené na běžné názvy – například je typické pro primární klíč jako vlastnost, která končí ID.

Podle konvence, každá entita se nastavit tak, aby mapovat do tabulky se stejným názvem jako DbSet&lt;TEntity&gt; vlastnost, která zveřejňuje se entita na odvozené kontextu. Pokud žádné DbSet&lt;TEntity&gt; hodnota je zadaný pro danou entitu, se používá název třídy.

### <a name="data-annotations-versus-fluent-api"></a>Datových poznámek versus rozhraní Fluent API

Existuje mnoho dalších konvence EF jádra a většina z nich lze změnit pomocí datových poznámek nebo rozhraní Fluent API implementována v rámci metody OnModelCreating.

Datových poznámek musí použít na třídy modelu entity, sami, což je více obtěžující způsob, jak z hlediska DDD. Je to proto, že jsou kontaminujících modelu s anotacemi dat související s databázi infrastruktury. Na druhé straně rozhraní Fluent API je pohodlný způsob, jak změnit většina konvence a mapování v rámci vrstvě infrastruktury trvalosti dat, a tak entity model vyčištění a odpojeného od infrastruktury trvalost.

### <a name="fluent-api-and-the-onmodelcreating-method"></a>Rozhraní Fluent API a metody OnModelCreating

Jak je uvedeno, aby bylo možné změnit konvence a mapování, můžete metody OnModelCreating v třídy DbContext. 

Řazení mikroslužbu v eShopOnContainers implementuje explicitní mapování a konfigurace v případě potřeby, jak je znázorněno v následujícím kódu.

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

Můžete nastavit všechna rozhraní Fluent API mapování v rámci stejné metody OnModelCreating, ale doporučuje se oddílu tento kód a mít více tříd konfigurace, jeden pro každou entitu, jak je znázorněno v příkladu. Zejména pro zvlášť velké modely se doporučuje mít třídy samostatné konfigurace pro konfiguraci různých entity typů.

V příkladu kód ukazuje několik explicitní deklarace a mapování. Ale EF základní konvence tomu mnoho z těchto mapování automaticky, skutečný kód, který je nutné ve vašem případě může být menší.


### <a name="the-hilo-algorithm-in-ef-core"></a>Algoritmus HIS použití/Lo v EF jádra

Zajímavé aspekt kódu v předchozím příkladu je, že používá [HIS použití/Lo algoritmus](https://vladmihalcea.com/the-hilo-algorithm/) jako strategie generování klíče.

Algoritmus HIS použití/Lo je užitečné, když potřebujete jedinečné klíče. Jako souhrn přiřadí algoritmus HIS použití-u jedinečné identifikátory řádky tabulky při není v závislosti na ukládání řádek v databázi okamžitě. Díky tomu můžete začít používat identifikátory hned, jak se stane s standardní sekvenční databázi ID.

Algoritmus HIS použití/Lo popisuje mechanismus pro generování bezpečné ID na straně klienta a nikoli v databázi. *Bezpečné* v tomto kontextu znamená bez kolizí. Tento algoritmus je zajímavé z těchto důvodů:

-   Nedochází k přerušení vzoru pracovní jednotky.

-   Nevyžaduje se, že odezev generátory pořadí způsob, jak provést v jiné systémy DBMS.

-   Vygeneruje lidského čitelný identifikátor, na rozdíl od techniky, které používají identifikátory GUID.

Jádro EF podporuje [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) ForSqlServerUseSequenceHiLo metodou, jak je znázorněno v předchozím příkladu.

### <a name="mapping-fields-instead-of-properties"></a>Mapování polí místo vlastnosti

Pomocí této funkce dostupné od verze 1.1 základní EF, můžete přímo namapovat sloupce na pole. Je možné nechcete použít vlastnosti ve třídě entity a jenom pro mapování sloupce z tabulky na pole. Běžně používá pro který by privátní pole pro všechny vnitřní stav, která nemusí být subjekty mimo entity. 

To provedete pomocí jednoho pole nebo také pomocí kolekcí, jako je třeba `List<>` pole. Tento bod již bylo zmíněno dříve když jsme se bavili modelování třídy modelu domény, ale zde se zobrazí, jak se provádí mapování pomocí `PropertyAccessMode.Field` konfigurace zvýrazněných v předchozí kód.

### <a name="using-shadow-properties-in-ef-core-hidden-at-the-infrastructure-level"></a>Použití stínové vlastnosti v EF jádra, skrytý na úrovni infrastruktury

Vlastnosti stínové v základní EF jsou vlastnosti, které nejsou k dispozici do třídy modelu entity. Hodnoty a stavy tyto vlastnosti jsou zachována výhradně v [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) třídy na úrovni infrastruktury.


## <a name="implementing-the-specification-pattern"></a>Implementace vzoru specifikace

Zavádí dříve v části návrhu, je vzor specifikace (plným názvem být specifikaci dotazu vzor) vzor návrhu Domain-Driven určená jako místo, kde můžete ukládat definici dotazu s volitelné, řazení a stránkování logiku. Vzor specifikace definuje dotazu v objektu. Chcete-li zapouzdření stránkové dotaz, který hledá některé produkty, například můžete vytvořit specifikaci PagedProduct, která se mají potřebné vstupní parametry (pageNumber pageSize, filtr, atd.). Metoda žádné úložiště (obvykle přetížení List()) by pak přijměte ISpecification a spusťte očekávané dotaz založený na této specifikaci.

Následující kód je například obecné specifikace rozhraní [eShopOnweb](https://github.com/dotnet-architecture/eShopOnWeb). 

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

Potom implementace specifikace obecné základní třídy je následující.

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

V následující specifikaci načte košík jedné entity, danou košíku ID nebo ID kupujících, do kterého patří košíku. Zruší [přes zatížení](https://docs.microsoft.com/en-us/ef/core/querying/related-data) kolekce položky košíku.

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

A nakonec se zobrazí pod jak obecné EF úložiště můžete použít tyto specifikace na filtr a eager zatížení dat souvisejících s danou entitu typu T.

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
Kromě zapouzdřením filtrování logiku, specifikace zadejte obrazec data, která mají být vráceny, včetně vlastnosti, které k naplnění. 

I když nepodporujeme doporučené vrácení IQueryable z úložiště, je v pořádku perfektně jejich použití v rámci úložiště vytvořit sadu výsledků. Zobrazí se tento postup použít v seznamu metodu výše, která používá zprostředkující IQueryable výrazy k sestavení dotazu seznamu zahrnuje před provedením dotazu s kritérii v specifikaci na posledním řádku.


#### <a name="additional-resources"></a>Další zdroje

-   **Mapování tabulek**
    [*https://docs.microsoft.com/ef/core/modeling/relational/tables*](https://docs.microsoft.com/ef/core/modeling/relational/tables)

-   **Použití HiLo ke generování klíče Entity Framework Core**
    [*http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/*](http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/)

-   **Základní pole**
    [*https://docs.microsoft.com/ef/core/modeling/backing-field*](https://docs.microsoft.com/ef/core/modeling/backing-field)

-   **Steve Smith. Obsah zapouzdřeného kolekcí v Entity Framework Core**
    [*https://ardalis.com/encapsulated-collections-in-entity-framework-core*](https://ardalis.com/encapsulated-collections-in-entity-framework-core)

-   **Stínové vlastnosti**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)

-   **Specifikace vzor**
    [*http://deviq.com/specification-pattern/*](http://deviq.com/specification-pattern/)
    

>[!div class="step-by-step"]
[Předchozí](infrastructure-persistence-layer-design.md)
[další](nosql-database-persistence-infrastructure.md)
