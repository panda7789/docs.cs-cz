---
title: Implementace vrstvy trvalosti infrastruktury pomocí Entity Framework Core
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Prozkoumejte podrobnosti implementace pro vrstvu trvalost infrastruktury pomocí jádra entity frameworku.
ms.date: 01/30/2020
ms.openlocfilehash: 7ab3be0d6a5affda478f7ec8f6c356571e304759
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805489"
---
# <a name="implement-the-infrastructure-persistence-layer-with-entity-framework-core"></a>Implementace vrstvy trvalosti infrastruktury pomocí jádra entity

Při použití relační databáze, jako je SQL Server, Oracle nebo PostgreSQL, doporučeným přístupem je implementace vrstvy trvalosti na základě entity framework (EF). EF podporuje LINQ a poskytuje objekty silného typu pro váš model, stejně jako zjednodušenou trvalost do databáze.

Entity Framework má dlouhou historii jako součást rozhraní .NET Framework. Při použití .NET Core, měli byste také použít Entity Framework Core, který běží na Windows nebo Linux stejným způsobem jako .NET Core. EF Core je kompletní přepsání entity frameworku, který je implementován s mnohem menší stopou a důležitými vylepšeními výkonu.

## <a name="introduction-to-entity-framework-core"></a>Úvod do jádra rámce entity

Entity Framework (EF) Core je lehká, rozšiřitelná a multiplatformní verze populární technologie přístupu k datům Entity Framework. To bylo představeno s .NET Core v polovině roku 2016.

Vzhledem k tomu, že úvod do EF Core je již k dispozici v dokumentaci společnosti Microsoft, zde jednoduše poskytujeme odkazy na tyto informace.

### <a name="additional-resources"></a>Další zdroje

- **Jádro rámce entity** \
  [https://docs.microsoft.com/ef/core/](/ef/core/)

- **Začínáme s ASP.NET jádra a frameworku entity pomocí sady Visual Studio** \
  [https://docs.microsoft.com/aspnet/core/data/ef-mvc/](/aspnet/core/data/ef-mvc/)

- **Třída DbContext** \
  [https://docs.microsoft.com/dotnet/api/microsoft.entityframeworkcore.dbcontext](xref:Microsoft.EntityFrameworkCore.DbContext)

- **Porovnání ef jádra & EF6.x** \
  [https://docs.microsoft.com/ef/efcore-and-ef6/index](/ef/efcore-and-ef6/index)

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a>Infrastruktura v jádru entity z hlediska DDD

Z hlediska DDD je důležitou schopností EF schopnost používat entity domény POCO, známé také v terminologii EF jako *entity poco code first*. Pokud používáte entity domény POCO, vaše třídy modelu domény jsou neznalost inaste, podle zásad [neznalosti trvalosti](https://deviq.com/persistence-ignorance/) a [infrastruktury nevědomosti.](https://ayende.com/blog/3137/infrastructure-ignorance)

Podle vzorů DDD byste měli zapouzdřit chování domény a pravidla v rámci samotné třídy entity, aby mohla řídit invarianty, ověření a pravidla při přístupu k libovolné kolekci. Proto není v DDD vhodné povolit veřejný přístup k kolekcím podřízených entit nebo hodnotových objektů. Místo toho chcete vystavit metody, které řídí, jak a kdy mohou být aktualizovány vaše pole a kolekce vlastností a jaké chování a akce by mělo dojít, když k tomu dojde.

Vzhledem k tomu, EF Core 1.1, ke splnění těchto požadavků DDD, můžete mít prostý chod ve vašich entit namísto veřejných vlastností. Pokud nechcete, aby pole entity bylo externě přístupné, můžete místo vlastnosti vytvořit atribut nebo pole. Můžete také použít soukromé nemovitosti setters.

Podobným způsobem můžete nyní mít přístup jen pro čtení ke kolekcím `IReadOnlyCollection<T>`pomocí veřejné vlastnosti zadané jako , která je `List<T>`zálohována soukromým členem pole pro kolekci (jako ) ve vaší entitě, která závisí na EF pro trvalost. Předchozí verze entity Framework požadované vlastnosti kolekce pro podporu `ICollection<T>`, což znamenalo, že každý vývojář pomocí třídy nadřazené entity můžete přidat nebo odebrat položky prostřednictvím svých kolekcí vlastností. Tato možnost by byla v rozporu s doporučenými vzory v DDD.

Můžete použít soukromou kolekci při vystavení `IReadOnlyCollection<T>` objektu jen pro čtení, jak je znázorněno v následujícím příkladu kódu:

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

Vlastnost `OrderItems` je přístupná pouze jako jen `IReadOnlyCollection<OrderItem>`pro čtení pomocí . Tento typ je jen pro čtení, takže je chráněn před pravidelnými externími aktualizacemi.

EF Core poskytuje způsob, jak mapovat model domény do fyzické databáze bez "kontaminace" modelu domény. Je to čistý kód POCO .NET, protože akce mapování je implementována ve vrstvě trvalosti. V této akci mapování je třeba nakonfigurovat mapování polí na databázi. V následujícím příkladu `OnModelCreating` metody `OrderingContext` z `OrderEntityTypeConfiguration` a třídy `SetPropertyAccessMode` volání říká EF `OrderItems` Core pro přístup k vlastnosti prostřednictvím jeho pole.

```csharp
// At OrderingContext.cs from eShopOnContainers
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
   // ...
   modelBuilder.ApplyConfiguration(new OrderEntityTypeConfiguration());
   // Other entities' configuration ...
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

Při použití polí namísto `OrderItem` vlastností je entita `List<OrderItem>` trvalá, jako by měla vlastnost. Však zpřístupňuje jeden přistupující `AddOrderItem` ho, metoda pro přidání nových položek do pořadí. V důsledku toho jsou chování a data spojeny dohromady a budou konzistentní v celém kódu aplikace, který používá model domény.

## <a name="implement-custom-repositories-with-entity-framework-core"></a>Implementace vlastních úložišť pomocí jádra entity frameworku

Na úrovni implementace je úložiště jednoduše třídou s kódem trvalost dat koordinovanou jednotkou práce (DBContext v EF Core) při provádění aktualizací, jak je znázorněno v následující třídě:

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

        public async Task<Buyer> FindAsync(string buyerIdentityGuid)
        {
            var buyer = await _context.Buyers
                .Include(b => b.Payments)
                .Where(b => b.FullName == buyerIdentityGuid)
                .SingleOrDefaultAsync();

            return buyer;
        }
    }
}
```

Rozhraní `IBuyerRepository` pochází z vrstvy modelu domény jako kontrakt. Implementace úložiště se však provádí ve vrstvě trvalosti a infrastruktury.

EF DbContext přichází prostřednictvím konstruktoru prostřednictvím vkládání závislostí. Je sdílena mezi více úložišť v rámci stejného oboru`ServiceLifetime.Scoped`požadavku HTTP, díky jeho výchozí životnosti `services.AddDbContext<>`( ) v kontejneru IoC (který lze také explicitně nastavit).

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a>Metody implementace v úložišti (aktualizace nebo transakce versus dotazy)

V rámci každé třídy úložiště byste měli umístit metody trvalosti, které aktualizují stav entit obsažených v související agregaci. Nezapomeňte, že existuje vztah 1:1 mezi agregací a souvisejícím úložištěm. Zvažte, že agregovaný objekt kořenové entity může mít vložené podřízené entity v rámci svého EF grafu. Kupující může mít například více platebních metod jako spřízněné podřízené entity.

Vzhledem k tomu, že přístup pro řazení mikroslužeb v eShopOnContainers je také založen na CQS/CQRS, většina dotazů nejsou implementovány ve vlastních úložištích. Vývojáři mají svobodu vytvářet dotazy a spojení, které potřebují pro prezentační vrstvu bez omezení uložených agregacemi, vlastními úložišti na agregaci a DDD obecně. Většina vlastních úložišť navržených touto příručkou má několik metod aktualizace nebo transakce, ale pouze metody dotazu potřebné k aktualizaci dat. Například BuyerRepository úložiště implementuje FindAsync metodu, protože aplikace potřebuje vědět, zda konkrétní kupující existuje před vytvořením nového kupujícího související s objednávkou.

Skutečné metody dotazu pro získání dat k odeslání do prezentační vrstvy nebo klientských aplikací jsou však implementovány, jak je uvedeno, v dotazech CQRS na základě flexibilních dotazů pomocí Dapper.

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a>Použití vlastního úložiště versus přímé použití EF DbContext

Entity Framework DbContext Třída je založena na jednotky práce a úložiště vzory a lze použít přímo z vašeho kódu, například z ASP.NET core MVC řadič. Vzory jednotky práce a úložiště mají za následek nejjednodušší kód, jako v mikroslužbě katalogu CRUD v eShopOnContainers. V případech, kdy chcete nejjednodušší možný kód, můžete chtít přímo použít třídu DbContext, jako mnoho vývojářů.

Implementace vlastních úložišť však poskytuje několik výhod při implementaci složitějších mikroslužeb nebo aplikací. Vzory jednotky práce a úložiště jsou určeny k zapouzdření vrstvy trvalosti infrastruktury tak, aby byla oddělena od vrstev aplikace a modelu domény. Implementace těchto vzorů může usnadnit použití mock repozitáře simulující přístup k databázi.

Na obrázku 7-18 můžete vidět rozdíly mezi nepoužívání maže (přímo pomocí EF DbContext) a pomocí úložišť, což usnadňuje zesměšňovat tyto repozitáře.

![Diagram znázorňující součásti a tok dat ve dvou úložištích.](./media/infrastructure-persistence-layer-implemenation-entity-framework-core/custom-repo-versus-db-context.png)

**Obrázek 7-18**. Použití vlastních úložišť versus prostého kontextu DbContext

Obrázek 7-18 ukazuje, že pomocí vlastního úložiště přidá vrstvu abstrakce, která může být použita k usnadnění testování zesměšňováním úložiště. Existuje několik alternativ při zesměšňování. Dalo by se zesměšňovat jen repozitáře, nebo byste mohli zesměšňovat celou jednotku práce. Obvykle zesměšňovat jen repozitáře je dost, a složitost abstraktní a zesměšňovat celou jednotku práce je obvykle není potřeba.

Později, když se zaměříme na aplikační vrstvu, uvidíte, jak funguje vkládání závislostí v ASP.NET Core a jak se implementuje při používání úložišť.

Stručně řečeno, vlastní úložiště umožňují testovat kód snadněji s testy částí, které nejsou ovlivněny stavem datové vrstvy. Pokud spustíte testy, které také přístup k databázi prostřednictvím entity framework, nejsou testy částí, ale integrační testy, které jsou mnohem pomalejší.

Pokud jste používali DbContext přímo, budete muset zesměšňovat nebo spustit testy částí pomocí SQL Server v paměti s předvídatelná data pro testování částí. Ale zesměšňování DbContext nebo ovládání falešných dat vyžaduje více práce než zesměšňování na úrovni úložiště. Samozřejmě můžete vždy otestovat řadiče MVC.

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a>Ef DbContext a IUnitOfWork životnost instance v kontejneru IoC

Objekt `DbContext` (vystavený `IUnitOfWork` jako objekt) by měl být sdílen mezi více úložišť v rámci stejného oboru požadavku HTTP. Například to platí, když operace, která je prováděna, musí řešit více agregací nebo jednoduše proto, že používáte více instancí úložiště. Je také důležité zmínit, `IUnitOfWork` že rozhraní je součástí vrstvy domény, nikoli typu EF Core.

Za tímto účelem musí `DbContext` mít instance objektu nastavenou na servicelifetime.Scoped. Toto je výchozí doba `DbContext` života `services.AddDbContext` při registraci s v kontejneru `Startup.cs` IoC z ConfigureServices metoda souboru v projektu ASP.NET core web api. Následující kód to znázorňuje.

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

Režim instance DbContext by neměl být nakonfigurován jako ServiceLifetime.Transient nebo ServiceLifetime.Singleton.

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a>Životnost instance úložiště v kontejneru IoC

Podobným způsobem by měla být obvykle nastavena životnost úložiště jako obor (InstancePerLifetimeScope v Autofac). Může být také přechodné (InstancePerDependency v Autofac), ale vaše služba bude efektivnější, pokud jde o paměť při použití rozsahem životnost.

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

Použití životnosti singleton pro úložiště může způsobit vážné problémy souběžnosti při dbcontext je nastavena na rozsah (InstancePerLifetimeScope) životnost (výchozí životnost dbcontext).

### <a name="additional-resources"></a>Další zdroje

- **Implementace úložiště a jednotky pracovních vzorů v ASP.NET aplikace MVC** \
  <https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application>

- **Jonathanallen, to je ono. Prováděcí strategie pro model úložiště s rámcem entity, dapper a řetězce** \
  <https://www.infoq.com/articles/repository-implementation-strategies>

- **Cesar de la Torre. Porovnání ASP.NET životnosti služby kontejneru Core IoC s obory instancí kontejneru Autofac IoC** \
  <https://devblogs.microsoft.com/cesardelatorre/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/>

## <a name="table-mapping"></a>Mapování tabulek

Mapování tabulky identifikuje data tabulky, která mají být dotazována z databáze a uložena do ní. Dříve jste viděli, jak lze entity domény (například produkt nebo doména objednávky) použít ke generování souvisejícího schématu databáze. EF je silně koncipovanou kolem konceptu *konvencí*. Konvence se zabývají otázkami jako "Jaký bude název tabulky?" nebo "Jaká vlastnost je primárním klíčem?" Konvence jsou obvykle založeny na konvenční názvy. Například je typické pro primární klíč je vlastnost, `Id`která končí .

Podle konvence bude každá entita nastavena tak, aby `DbSet<TEntity>` mapovala tabulku se stejným názvem jako vlastnost, která entitu zveřejňuje v odvozeném kontextu. Pokud `DbSet<TEntity>` pro danou entitu není k dispozici žádná hodnota, použije se název třídy.

### <a name="data-annotations-versus-fluent-api"></a>Poznámky k datům versus fluent api

Existuje mnoho dalších EF Core konvence a většina z nich lze změnit pomocí anotací dat nebo Fluent API, implementované v rámci OnModelCreating metody.

Poznámky k datům musí být použity na samotných třídách modelu entity, což je z hlediska DDD rušivější způsob. Důvodem je, že kontaminujete model datovými anotacemi souvisejícími s databází infrastruktury. Na druhou stranu Fluent API je pohodlný způsob, jak změnit většinu konvencí a mapování v rámci vrstvy infrastruktury trvalosti dat, takže model entity bude čistý a oddělený od infrastruktury trvalosti.

### <a name="fluent-api-and-the-onmodelcreating-method"></a>Fluent API a metoda OnModelCreating

Jak již bylo zmíněno, chcete-li změnit konvence a mapování, můžete použít OnModelCreating metoda v DbContext třídy.

Řazení mikroslužby v eShopOnContainers implementuje explicitní mapování a konfiguraci, v případě potřeby, jak je znázorněno v následujícím kódu.

```csharp
// At OrderingContext.cs from eShopOnContainers
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
   // ...
   modelBuilder.ApplyConfiguration(new OrderEntityTypeConfiguration());
   // Other entities' configuration ...
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
            .UseHiLo("orderseq", OrderingContext.DEFAULT_SCHEMA);

        //Address value object persisted as owned entity type supported since EF Core 2.0
        orderConfiguration
            .OwnsOne(o => o.Address, a =>
            {
                a.WithOwner();
            });

        orderConfiguration
            .Property<int?>("_buyerId")
            .UsePropertyAccessMode(PropertyAccessMode.Field)
            .HasColumnName("BuyerId")
            .IsRequired(false);

        orderConfiguration
            .Property<DateTime>("_orderDate")
            .UsePropertyAccessMode(PropertyAccessMode.Field)
            .HasColumnName("OrderDate")
            .IsRequired();

        orderConfiguration
            .Property<int>("_orderStatusId")
            .UsePropertyAccessMode(PropertyAccessMode.Field)
            .HasColumnName("OrderStatusId")
            .IsRequired();

        orderConfiguration
            .Property<int?>("_paymentMethodId")
            .UsePropertyAccessMode(PropertyAccessMode.Field)
            .HasColumnName("PaymentMethodId")
            .IsRequired(false);

        orderConfiguration.Property<string>("Description").IsRequired(false);

        var navigation = orderConfiguration.Metadata.FindNavigation(nameof(Order.OrderItems));

        // DDD Patterns comment:
        //Set as field (New since EF 1.1) to access the OrderItem collection property through its field
        navigation.SetPropertyAccessMode(PropertyAccessMode.Field);

        orderConfiguration.HasOne<PaymentMethod>()
            .WithMany()
            .HasForeignKey("_paymentMethodId")
            .IsRequired(false)
            .OnDelete(DeleteBehavior.Restrict);

        orderConfiguration.HasOne<Buyer>()
            .WithMany()
            .IsRequired(false)
            .HasForeignKey("_buyerId");

        orderConfiguration.HasOne(o => o.OrderStatus)
            .WithMany()
            .HasForeignKey("_orderStatusId");
    }
}
```

Můžete nastavit všechna mapování rozhraní API `OnModelCreating` Fluent v rámci stejné metody, ale je vhodné rozdělit tento kód a mít více konfiguračních tříd, jeden na entitu, jak je znázorněno v příkladu. Zejména u velkých modelů je vhodné mít samostatné třídy konfigurace pro konfiguraci různých typů entit.

Kód v příkladu ukazuje několik explicitní deklarace a mapování. Ef Core konvence však mnoho z těchto mapování automaticky, takže skutečný kód, který byste potřebovali ve vašem případě může být menší.

### <a name="the-hilo-algorithm-in-ef-core"></a>Algoritmus Hi/Lo v EF core

Zajímavým aspektem kódu v předchozím příkladu je, že používá [algoritmus Hi/Lo](https://vladmihalcea.com/the-hilo-algorithm/) jako strategii generování klíčů.

Algoritmus Hi/Lo je užitečný, když potřebujete jedinečné klíče před potvrzením změn. Jako souhrn algoritmus Hi-Lo přiřadí jedinečné identifikátory řádkům tabulky, aniž by to v závislosti na okamžitém uložení řádku v databázi. To vám umožní začít používat identifikátory hned, jak se to děje s pravidelnými sekvenčními ID databáze.

Algoritmus Hi/Lo popisuje mechanismus pro získání dávky jedinečných ID z související databázové sekvence. Tyto ID jsou bezpečné použití, protože databáze zaručuje jedinečnost, takže nedojde ke kolizím mezi uživateli. Tento algoritmus je zajímavý z těchto důvodů:

- Nepřeruší vzor jednotky práce.

- Získá id sekvence v dávkách, aby se minimalizovalo zpáteční cesty do databáze.

- Generuje lidský čitelný identifikátor, na rozdíl od technik, které používají identifikátory GUID.

EF Core podporuje [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) s `UseHiLo` metodou, jak je znázorněno v předchozím příkladu.

### <a name="map-fields-instead-of-properties"></a>Mapování polí místo vlastností

Pomocí této funkce, která je k dispozici od EF Core 1.1, můžete přímo mapovat sloupce na pole. Je možné nepoužívat vlastnosti ve třídě entity a pouze mapovat sloupce z tabulky na pole. Běžné použití, které by soukromé pole pro všechny vnitřní stav, které není nutné přistupovat z mimo entitu.

Můžete to provést s jednotlivými poli nebo `List<>` také s kolekcemi, jako je pole. Tento bod byl zmíněn dříve, když jsme diskutovali modelování tříd modelu domény, `PropertyAccessMode.Field` ale zde můžete vidět, jak se provádí toto mapování s konfigurací zvýrazněnou v předchozím kódu.

### <a name="use-shadow-properties-in-ef-core-hidden-at-the-infrastructure-level"></a>Použití vlastností stínů v ef jádru, skrytých na úrovni infrastruktury

Vlastnosti stínů v jádru EF jsou vlastnosti, které neexistují v modelu třídy entit. Hodnoty a stavy těchto vlastností jsou udržovány čistě ve třídě [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) na úrovni infrastruktury.

## <a name="implement-the-query-specification-pattern"></a>Implementace vzoru specifikace dotazu

Jak bylo zavedeno dříve v části návrhu, vzor specifikace dotazu je vzor návrhu řízeného doménou navržený jako místo, kam můžete umístit definici dotazu s volitelnou logikou řazení a stránkování.

Vzor Specifikace dotazu definuje dotaz v objektu. Chcete-li například zapouzdřit stránkovaný dotaz, který vyhledá některé produkty, můžete vytvořit specifikaci PagedProduct, která přebírá potřebné vstupní parametry (pageNumber, pageSize, filter atd.). Potom v rámci jakékoli metody úložiště (obvykle List() přetížení) by přijmout IQuerySpecification a spustit očekávaný dotaz na základě této specifikace.

Příkladem obecného rozhraní Specifikace je následující kód z [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb).

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

Implementace základní třídy obecné specifikace je potom následující.

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

Následující specifikace načte jednu entitu košíku, která je uvedena buď ID košíku, nebo ID kupujícího, kterému košík patří. Bude [dychtivě načíst](/ef/core/querying/related-data) `Items` sbírku košíku.

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

A nakonec můžete vidět níže, jak obecné EF úložiště můžete použít takové specifikace filtrovat a dychtivé načítání dat souvisejících s danou entitou typu T.

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

Kromě logiky zapouzdření filtrování může specifikace určit tvar dat, která mají být vrácena, včetně vlastností, které mají být naplněny.

I když nedoporučujeme návrat `IQueryable` z úložiště, je naprosto v pořádku je použít v úložišti k vytvoření sady výsledků. Tento přístup použitý ve výše uvedené metodě `IQueryable` List, která používá zprostředkující výrazy k sestavení seznamu zahrnutí dotazu před provedením dotazu s kritérii specifikace na posledním řádku.

### <a name="additional-resources"></a>Další zdroje

- **Mapování tabulky** \
  [https://docs.microsoft.com/ef/core/modeling/relational/tables](/ef/core/modeling/relational/tables)

- **Použití HiLo ke generování klíčů pomocí jádra entity frameworku** \
  <https://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/>

- **Doprovodná pole** \
  [https://docs.microsoft.com/ef/core/modeling/backing-field](/ef/core/modeling/backing-field)

- **Steva Smithe. Zapouzdřené kolekce v jádru entity frameworku** \
  <https://ardalis.com/encapsulated-collections-in-entity-framework-core>

- **Vlastnosti stínu** \
  [https://docs.microsoft.com/ef/core/modeling/shadow-properties](/ef/core/modeling/shadow-properties)

- **Vzor specifikace** \
  <https://deviq.com/specification-pattern/>

> [!div class="step-by-step"]
> [Předchozí](infrastructure-persistence-layer-design.md)
> [další](nosql-database-persistence-infrastructure.md)
