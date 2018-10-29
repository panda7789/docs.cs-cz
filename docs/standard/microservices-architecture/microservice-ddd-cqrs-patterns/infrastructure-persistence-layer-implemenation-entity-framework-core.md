---
title: Implementace vrstvy trvalosti infrastruktury pomocí Entity Framework Core
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Implementace vrstvy trvalosti infrastruktury pomocí Entity Framework Core
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.openlocfilehash: 663515e0a863ef703006df0f96b4bc8a2976ca78
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50205292"
---
# <a name="implementing-the-infrastructure-persistence-layer-with-entity-framework-core"></a>Implementace vrstvy trvalosti infrastruktury pomocí Entity Framework Core

Při použití relačními databázemi jako SQL Server, Oracle nebo PostgreSQL doporučený postup je implementace vrstvy trvalosti založené na Entity Framework (EF). EF podporuje LINQ a poskytuje objektů se silným typem pro váš model, jakož i zjednodušené trvalost do databáze.

Entity Framework už dlouho jako součást rozhraní .NET Framework. Pokud používáte .NET Core, měli byste použít také Entity Framework Core, která běží na Windows nebo Linuxem v stejným způsobem jako .NET Core. EF Core je kompletní revize Entity Framework, prováděné s mnohem menší nároky na místo a důležitá vylepšení výkonu.

## <a name="introduction-to-entity-framework-core"></a>Úvod do Entity Framework Core

Entity Framework (EF) Core je odlehčený, rozšiřitelné, a multiplatformní verze oblíbených dat Entity Framework přístup k technologii. Byla zavedená s .NET Core v polovině 2016.

Úvod do EF Core je již k dispozici v dokumentaci společnosti Microsoft, tady jednoduše poskytujeme odkazy k těmto informacím.

#### <a name="additional-resources"></a>Další zdroje

-   **Entity Framework Core**
    [*https://docs.microsoft.com/ef/core/*](https://docs.microsoft.com/ef/core/)

-   **Začínáme s ASP.NET Core a Entity Framework Core pomocí sady Visual Studio**
    [*https://docs.microsoft.com/aspnet/core/data/ef-mvc/*](https://docs.microsoft.com/aspnet/core/data/ef-mvc/)

-   **Třídy DbContext**
    [*https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext*](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext)

-   **Porovnání EF Core a EF6.x**
    [*https://docs.microsoft.com/ef/efcore-and-ef6/index*](https://docs.microsoft.com/ef/efcore-and-ef6/index)

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a>Infrastruktura v Entity Framework Core z hlediska DDD

Z DDD hlediska, je důležité funkce EF umožňuje používat entity domény POCO, označuje se taky v, řečeno terminologií EF jako POCO *založeno na kódu entity*. Pokud používáte entity domény POCO, vaše doménové třídy modelu jsou ignorujících, následující [trvalost neznalosti](https://deviq.com/persistence-ignorance/) a [infrastruktury neznalosti](https://ayende.com/blog/3137/infrastructure-ignorance) zásady.

Za vzorů DDD by měl zapouzdření domény chování a pravidel v rámci třídy entita, takže ho můžete řídit výstupních podmínek, ověření a pravidla při přístupu k žádné kolekce. Proto není vhodné v DDD umožní veřejný přístup ke kolekcím podřízené entity nebo hodnota objekty. Místo toho chcete vystavit metody, které řídí, kdy a jak můžete aktualizovat pole a kolekce vlastností, a jaké chování a akce dojde, pokud k tomu dojde.

Od verze EF Core 1.1 splňovat tyto požadavky na DDD může mít jednoduchého pole v entitách místo veřejné vlastnosti. Pokud nechcete, aby pole entity externě dostupná, můžete vytvořit pouze atribut nebo pole namísto vlastnost. Můžete také použít privátní vlastnost Setter.

Podobným způsobem, můžete teď mít přístup jen pro čtení ke kolekcím s použitím veřejné vlastnosti typu `IReadOnlyCollection<T>`, který je zálohovaný díky člena soukromé pole pro kolekci (podobně jako `List<T>`) ve vaší entitě, která závisí na EF trvalosti. Předchozí verze rozhraní Entity Framework požadované vlastnosti kolekce pro podporu `ICollection<T>`, který znamenalo, že každý vývojář horizontálních oddílů pomocí třídy nadřazená entita může přidat nebo odebrat položky prostřednictvím její vlastnosti kolekce. Tato možnost by proti doporučené vzory v DDD.

Můžete použít soukromé kolekce při zobrazení jen pro čtení `IReadOnlyCollection<T>` objektu, jak je znázorněno v následujícím příkladu kódu:

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

Všimněte si, že `OrderItems` vlastnosti lze přistupovat pouze jako jen pro čtení pomocí `IReadOnlyCollection<OrderItem>`. Tento typ je jen pro čtení, takže je chráněný proti externí pravidelné aktualizace. 

EF Core nabízí způsob, jak mapovat model domény do fyzické databáze bez "kontaminujících" doménový model. Je čistě .NET objektů POCO kódu, protože akce mapování je implementována v vrstvy trvalosti. V této akci mapování budete muset nakonfigurovat mapování polí pro databází. V následujícím příkladu je to metoda OnModelCreating říká zvýrazněný kód EF Core pro přístup k vlastnosti OrderItems prostřednictvím jeho pole.

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

Při použití polí místo vlastností OrderItem entity je trvalý stejně, jako kdyby byla seznam&lt;OrderItem&gt; vlastnost. Však poskytuje jeden přistupující objekt, `AddOrderItem` metoda pro přidání nových položek do pořadí. V důsledku toho chování a data jsou spojených dohromady a budou konzistentní v rámci jakýkoli kód aplikace, který používá model domény.

## <a name="implementing-custom-repositories-with-entity-framework-core"></a>Implementace vlastního úložiště s Entity Framework Core

Na úrovni implementace úložiště je jednoduše třídu s kódem trvalosti dat koordinuje přes určitou jednotku práce (DBContext v EF Core) při provádění aktualizací, jak je znázorněno v následující třídy:

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

Všimněte si, že rozhraní IBuyerRepository pochází z vrstvě doménového modelu jako kontrakt. Implementace úložiště se však provádí na stálost a vrstvy infrastruktury.

EF DbContext prochází konstruktoru pomocí vkládání závislostí. Je sdílen mezi více úložišť v rámci stejného oboru požadavku HTTP, díky výchozí dobu života (ServiceLifetime.Scoped) v kontejneru IoC (což lze také explicitně nastavit službami. AddDbContext&lt;&gt;).

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a>Metody k implementaci v úložišti (aktualizace nebo transakce a dotazy)

V rámci každé třídy úložiště byste měli umístit trvalost metody, které aktualizuje stav entity obsažené podle jeho související agregace. Mějte na paměti, že je relace 1: 1 mezi agregaci a její související úložiště. Vezměte v úvahu, že objekt agregační kořenové entity může být vloženy podřízené entity v rámci jeho EF grafu. Kupující například může mít více způsoby platby jako související podřízené entity.

Vzhledem k tomu, že přístup k řazení mikroslužeb v aplikaci eShopOnContainers také podle CQS/modelu CQRS, většina dotazů, které nejsou implementované ve vlastní úložiště. Vývojáři moci svobodně vytvářet dotazy a spojení, které potřebují pro prezentační vrstva bez omezení stanovené agregace, vlastní úložiště za agregaci a DDD obecně. Většina vlastních úložišť navrhl Tato příručka má několik aktualizací nebo transakční metody, ale pouze metody dotazu nutná, aby se data aktualizovat. Například BuyerRepository úložiště implementuje metody asynchronně vyhledá, protože aplikace je potřeba vědět, jestli konkrétní kupujících existuje. před vytvořením nové odběratele související s objednávkou.

Však jsou implementované metody skutečné dotazu zobrazíte data k odeslání do prezentační vrstvy nebo klientské aplikace, jak je uvedeno v modelu CQRS dotazů založených na použití Dapperem flexibilní dotazy.

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a>Používání vlastního úložiště versus přímo pomocí EF DbContext

Třídy DbContext v Entity Framework je podle vzorů pracovní jednotky a úložiště a můžou používat přímo v kódu, například z kontroler ASP.NET Core MVC. To znamená tak, jak můžete vytvořit nejjednodušší kód, stejně jako v katalogu mikroslužby CRUD v aplikaci eShopOnContainers. V případech, kde chcete nejjednodušší kód je to možné můžete přímo použít třídy DbContext, stejně jako mnoho vývojářů.

Nicméně implementace vlastního úložiště poskytuje několik výhod při provádění složitějších mikroslužby nebo aplikace. Tyto vzory se dají pracovní jednotky a úložiště jsou určeny k zapouzdření vrstvy trvalosti infrastruktury, takže je oddělený od aplikace a vrstvy modelu domény. Implementaci těchto vzorců můžete využívají mock úložišť, které simulují přístup k databázi.

Obrázek 9-18 se zobrazí rozdíly mezi bez použití úložiště (přímo pomocí EF DbContext) oproti použití úložiště, které usnadňují napodobení taková úložiště.

![](./media/image19.png)

**Obrázek 9-18**. Používání vlastního úložiště a prostý DbContext

Při vytvoření modelu se více alternativy. Může napodobení jenom úložiště nebo může napodobení celou jednotku práce. Obvykle napodobování jenom úložiště je dostatek a složitosti se abstraktní a napodobení celou jednotku práce obvykle není potřeba.

Později když jsme se zaměřit na aplikační vrstvu, zobrazí se fungování injektáž závislostí v ASP.NET Core a jak je implementován při použití úložiště.

Stručně řečeno vlastní úložiště využijete k otestování kódu snadněji s testy jednotek, které nejsou ovlivněny stav dat vrstvy. Pokud spouštíte testy, které také přístup k databázi skutečné přes rozhraní Entity Framework, nejsou testy jednotek, ale integrační testy, které jsou mnohem pomalejší.

Pokud jste používali DbContext přímo, pouze možnost, kterou byste měli by pro spouštění testů jednotek s použitím SQL serveru v paměti s předvídatelným dat pro testování částí. Nebude moct řídit mock objektů a falešných dat stejně jako na úrovni úložiště. Samozřejmě může vždy testovací kontrolery MVC.

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a>Životnost instance EF DbContext a IUnitOfWork ve vašem kontejneru IoC

Objekt DbContext (vystavena jako objekt IUnitOfWork) může být nutné sdílet mezi více úložišť v rámci stejného oboru požadavku HTTP. Například to platí při prováděnou operace musí zacházet s více agregace nebo jednoduše vzhledem k tomu, že používáte více instancí úložiště. Je také důležité zmínit, že rozhraní IUnitOfWork je součástí domény vrstvy, není typem EF Core.

K tomu, musí mít jeho služby dobu života nastavenu na ServiceLifetime.Scoped instanci objektu DbContext. Toto je výchozí doba života, při registraci DbContext pomocí služby. AddDbContext ve vašem kontejneru IoC z metody ConfigureServices Startup.cs soubor v projektu webového rozhraní API ASP.NET Core. Následující kód to znázorňuje.

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

Režim instanciace DbContext by neměl být nakonfigurován jako ServiceLifetime.Transient nebo ServiceLifetime.Singleton.

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a>Životnost instance úložiště ve vašem kontejneru IoC

Podobným způsobem musí být obvykle nastavená doba života úložiště jako s vymezeným oborem (InstancePerLifetimeScope v Autofac). Také může být přechodná (InstancePerDependency Autofac), ale vaše služba bude mnohem efektivnější, pokud jde o paměti, při použití s vymezeným oborem životnost.

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

Všimněte si, že pomocí typu singleton životnost úložiště, které může způsobit vážné souběžnosti problémy Pokud váš kontext databáze je nastavena na obor (InstancePerLifetimeScope) životnost (výchozí doba života pro DBContext).

#### <a name="additional-resources"></a>Další zdroje

-   **Implementace úložiště a jednotky pracovních vzorů v aplikaci ASP.NET MVC**
    [*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)

-   **Jonathan Allen. Strategie implementace pro model úložiště s Dapper, Entity Framework a řetězce**
    [*https://www.infoq.com/articles/repository-implementation-strategies*](https://www.infoq.com/articles/repository-implementation-strategies)

-   **De la Torre Cesarovi. Porovnání doby života služby kontejner ASP.NET Core IoC s obory instance kontejner Autofac IoC**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)

## <a name="table-mapping"></a>Mapování tabulek

Mapování tabulek identifikuje měl posílat dotaz z tabulky dat a uložit do databáze. Dříve jste viděli použití domény entity (například doména produktu nebo pořadí) k vygenerování schématu databáze. EF důrazně navržené s ohledem na konceptu *konvence*. Konvence adresu otázky typu "Jaký název tabulky bude?" nebo "co vlastnost je primárním klíčem?" Konvence většinou vycházejí konvenční názvy, například je typické pro primární klíč, bude vlastnost, která končí ID.

Podle konvence, každá entita se nastavit tak, aby mapovat do tabulky se stejným názvem jako DbSet&lt;TEntity&gt; vlastnost, která zveřejňuje entity v kontextu odvozené. Pokud žádné DbSet&lt;TEntity&gt; hodnota je k dispozici pro danou entitu, se používá název třídy.

### <a name="data-annotations-versus-fluent-api"></a>Datové poznámky a rozhraní Fluent API

Existuje mnoho dalších konvence EF Core a většina z nich můžete změnit pomocí anotacemi dat nebo Fluent API implementovaná v metodě OnModelCreating.

Anotací dat musí být použita u tříd modelu entity, sami, což je víc obtěžující způsob, jak z hlediska DDD. Je to proto, že jsou kontaminujících modelu s anotacemi dat související s infrastrukturou databáze. Na druhé straně rozhraní Fluent API je pohodlný způsob, jak změnit většina konvence a mapování v rámci vaší vrstvu infrastruktury trvalosti dat, takže modelu entity budou čisté a oddělený od infrastruktury trvalosti.

### <a name="fluent-api-and-the-onmodelcreating-method"></a>Rozhraní Fluent API a OnModelCreating – metoda

Jak už bylo zmíněno, chcete-li změnit mapování a konvence můžete OnModelCreating metodu do třídy DbContext. 

Pořadí mikroslužeb v aplikaci eShopOnContainers implementuje explicitního mapování a konfigurace, pokud je nepotřebujete, jak je znázorněno v následujícím kódu.

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

Můžete nastavit všechna rozhraní Fluent API mapování v rámci stejné metody OnModelCreating, ale doporučuje se rozdělit tento kód a mít více tříd konfigurace, jeden pro každou entitu, jak je znázorněno v příkladu. Zejména u modelů, zejména velkých je vhodné mít samostatné konfigurace třídy pro konfiguraci typy různých entit.

Kódem v příkladu ukazuje několik explicitní deklarace a mapování. EF Core konvence však mnohé z těchto mapování automaticky, takže skutečný kód, který je třeba ve vašem případě může být menší.


### <a name="the-hilo-algorithm-in-ef-core"></a>Dobrý den/Lo algoritmus v EF Core

Zajímavým aspektem kód v předchozím příkladu je, že používá [Dobrý den/Lo algoritmus](https://vladmihalcea.com/the-hilo-algorithm/) jako strategie generování klíčů.

Dobrý den/Lo algoritmus je užitečné, když budete potřebovat jedinečné klíče. Jako souhrn algoritmus Hi-Lo přiřadí jedinečné identifikátory řádky tabulky během není v závislosti na tom okamžitě ukládání řádku v databázi. Tímto způsobem můžete rovnou začít využívat identifikátory, jak se stane s ID regulární sekvenční databází.

Dobrý den/Lo algoritmus popisuje mechanismus pro generování bezpečné ID na straně klienta, nikoli v databázi. *Bezpečné* v tomto kontextu označuje bez kolizí. Tento algoritmus je zajímavé z těchto důvodů:

-   Nedojde k poškození vzor jednotkou práce.

-   Nevyžaduje se, že má zpáteční převod generátorů pořadí způsob, jak provést v jiných systémech DBMS.

-   Generuje lidské čitelné identifikátor, na rozdíl od techniky, které používají identifikátory GUID.

EF Core podporuje [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) ForSqlServerUseSequenceHiLo metodou, jak je znázorněno v předchozím příkladu.

### <a name="mapping-fields-instead-of-properties"></a>Mapování polí místo vlastností

Pomocí této funkce dostupné od verze EF Core 1.1, můžete přímo namapovat sloupce pole. Je možné používat vlastnosti ve třídě entity a pouze pro mapování sloupců z tabulky na pole. Běžným účelem pro, který by privátní pole pro všechny vnitřní stav, které není potřeba přistupovat z mimo entitu. 

Můžete udělat pomocí jednoho pole nebo také s kolekcemi, jako je třeba `List<>` pole. Tento bod jsem už zmínili dřív když jsme probírali modelování tříd modelu domény, ale tady vidíte, jak se pomocí provádí mapování `PropertyAccessMode.Field` konfigurace zvýrazněných v předchozím kódu.

### <a name="using-shadow-properties-in-ef-core-hidden-at-the-infrastructure-level"></a>Použití stínové vlastnosti v EF Core, skrytý na úrovni infrastruktury

Stínové vlastnosti v EF Core jsou vlastnosti, které neexistují v třídě modelu entity. Hodnoty a stavy z těchto vlastností jsou zachovány v čistě [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) třídy na úrovni infrastruktury.


## <a name="implementing-the-specification-pattern"></a>Implementace vzoru specifikace

Zavedeném dříve v části návrhu, vzor specifikace (úplného názvu bude vzor dotazu specification) je vzor Domain-Driven Design navržený místem, kde můžete ukládat definice dotazu s volitelné, řazení a stránkování logiku. Vzor specifikace definuje dotaz v objektu. Například pokud chcete zapouzdřit stránkovaného dotaz, který vyhledá některé produkty můžete vytvořit PagedProduct specifikace, která přebírá nezbytné vstupní parametry (pageNumber pageSize, filter, atd.). Metoda v libovolném adresáři (obvykle List() přetížení) by potom přijměte ISpecification a spustíte očekávané dotaz založený na specifikaci.

Příklad obecného rozhraní specifikace je následující kód z [eShopOnweb](https://github.com/dotnet-architecture/eShopOnWeb). 

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

Implementace obecný specifikace základní třídy je následující.

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

Specifikace načte jeden nákupní košík entity košíku ID nebo ID kupujících, ke kterému patří košíku. Bude [nemůžou dočkat, až zatížení](https://docs.microsoft.com/ef/core/querying/related-data) kolekce položek nákupním košíku.

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

A nakonec můžete vidět dole použití obecného úložiště EF specifikace filtru a zatížení eager data související s danou entitu typu T.

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
Kromě zapouzdření logiku filtrování, specifikace určit tvar dat, který se má vrátit, včetně vlastnosti, které chcete vyplnit. 

I když není doporučenou vrátit IQueryable z úložiště, je naprosto bez problémů se dají použít v rámci tohoto úložiště k vytvoření sady výsledků. Zobrazí se tento přístup používá se v seznamu výše uvedené, metody, která používá přechodných výrazů IQueryable k vytvoření dotazu na seznam zahrnuje před provedením dotazu s kritérii pro specifikaci na posledním řádku.


#### <a name="additional-resources"></a>Další zdroje

-   **Mapování tabulek**
    [*https://docs.microsoft.com/ef/core/modeling/relational/tables*](https://docs.microsoft.com/ef/core/modeling/relational/tables)

-   **Použití HiLo generování klíčů s Entity Framework Core**
    [*http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/*](http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/)

-   **Pomocná pole**
    [*https://docs.microsoft.com/ef/core/modeling/backing-field*](https://docs.microsoft.com/ef/core/modeling/backing-field)

-   **Steve Smith. Zapouzdřený objekt kolekce v Entity Framework Core**
    [*https://ardalis.com/encapsulated-collections-in-entity-framework-core*](https://ardalis.com/encapsulated-collections-in-entity-framework-core)

-   **Stínové vlastnosti**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)

-   **Vzor specifikace**
    [*https://deviq.com/specification-pattern/*](https://deviq.com/specification-pattern/)
    

>[!div class="step-by-step"]
[Předchozí](infrastructure-persistence-layer-design.md)
[další](nosql-database-persistence-infrastructure.md)
