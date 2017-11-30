---
title: "Implementace vrstvu trvalosti infrastruktury základní Entity Framework"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Implementace vrstvu trvalosti infrastruktury základní Entity Framework"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 508d60d73eb7c0f0cc2cc909613cc4f8712b4aba
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-the-infrastructure-persistence-layer-with-entity-framework-core"></a>Implementace vrstvu trvalosti infrastruktury základní Entity Framework

Při použití relačních databází, jako je například SQL Server, Oracle nebo PostgreSQL doporučený postup je implementace vrstvu trvalosti založené na Entity Framework (EF). EF podporuje LINQ a poskytuje objektů se silným typem pro váš model, jakož i zjednodušené trvalost do vaší databáze.

Rozhraní Entity Framework má dlouho historie v rámci rozhraní .NET Framework. Pokud používáte .NET Core, byste měli použít také Entity Framework Core, který běží na systému Windows nebo Linux stejným způsobem jako .NET Core. Základní EF je kompletní přepisování Entity Frameworku, implementováno s mnohem menší nároky a důležitá vylepšení výkonu.

## <a name="introduction-to-entity-framework-core"></a>Úvod do Entity Framework Core

Základní Entity Framework (EF) je lightweight rozšiřitelný, a přístup technologie a platformy verzi oblíbených datům Entity Framework. Byla zavedená s .NET Core v polovině 2016.

Vzhledem k tomu, že Úvod do základní EF je již k dispozici v dokumentaci společnosti Microsoft, tady jednoduše poskytujeme odkazy na tyto informace.

#### <a name="additional-resources"></a>Další zdroje

-   **Entity Framework Core**
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

V EF základní 1.1 splňovat tyto požadavky DDD může mít prostý pole v entity místo vlastnosti veřejné a privátní setter. Pokud nechcete, aby pole entity externě přístupné, můžete vytvořit pouze atribut nebo pole místo vlastnost. Je třeba použít privátní setter Pokud dáváte přednost tento čisticí přístup.

Podobným způsobem, můžete Teď máte přístup jen pro čtení k kolekce pomocí veřejná vlastnost typu IEnumerable&lt;T&gt;, který je zálohovaný díky členem soukromé pole pro kolekci (jako seznam&lt;&gt;) ve vaší Entita, která využívá EF trvalosti. Předchozí verze Entity Frameworku požadované vlastnosti kolekce pro podporu ICollection&lt;T&gt;, který určená, kdokoli z vývojářů pomocí třídy nadřazená entita může přidat nebo odebrat položky z kolekce jeho vlastnosti. Tato možnost by proti doporučené vzory v DDD.

Soukromé kolekce při vystavení objekt rozhraní IEnumerable jen pro čtení, můžete použít, jak je znázorněno v následujícím příkladu kódu:

```csharp
public class Order : Entity
{
    // Using private fields, allowed since EF Core 1.1
    private DateTime _orderDate;
    // Other fields ...
    private readonly List<OrderItem> _orderItems;

    public IEnumerable<OrderItem> OrderItems => _orderItems.AsReadOnly();

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
        var orderItem = new OrderItem(productId, productName, unitPrice, discount,
            pictureUrl, units);
        _orderItems.Add(orderItem);
    }
}
```

Všimněte si, že vlastnost OrderItems lze přistupovat pouze jen pro čtení pomocí seznamu&lt;&gt;. AsReadOnly(). Tato metoda vytvoří obálku kolem seznamu privátní jen pro čtení tak, že je soubor chráněný proti externí aktualizace. Je výrazně levnější než ToList způsobem, protože nemá zkopírujte všechny položky v kolekci nové; Místo toho provádí pouze jednu operaci alokační haldy pro instanci obálku.

Základní EF poskytuje způsob, jak mapování modelu domény na fyzické databázi bez kontaminujících modelu domény. Je čistá .NET objektů POCO kódu, protože mapování akce je implementována ve vrstvu trvalosti. V této akci mapování budete muset konfigurovat mapování polí do databáze. V následujícím příkladu metody OnModelCreating informuje zvýrazněný EF základní přístup k vlastnosti OrderItems prostřednictvím jeho pole.

```csharp
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
    // ...
    modelBuilder.Entity<Order>(ConfigureOrder);
    // Other entities ...
}

void ConfigureOrder(EntityTypeBuilder<Order> orderConfiguration)
{
    // Other configuration ...
    var navigation = orderConfiguration.Metadata.
    FindNavigation(nameof(Order.OrderItems));
    navigation.SetPropertyAccessMode(PropertyAccessMode.Field);
    // Other configuration ...
}
```

Pokud použijete pole místo vlastnosti, je entita OrderItem nastavené jako trvalé stejně, jako by se mělo seznam&lt;OrderItem&gt; vlastnost. Však zveřejňuje jednoho přístupového objektu (metoda AddOrderItem) pro přidání nových položek do pořadí. V důsledku toho chování a data jsou svázané společně a bude konzistentní v rámci aplikace kód, který používá model domény.

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
    }

    public BuyerRepository(OrderingContext context)
    {
        if (context == null)
        {
            throw new ArgumentNullException(
                nameof(context));
        }
        _context = context;
    }

    public Buyer Add(Buyer buyer)
    {
        return _context.Buyers.Add(buyer).Entity;
    }

    public async Task<Buyer> FindAsync(string BuyerIdentityGuid)
    {
        var buyer = await _context.Buyers.Include(b => b.Payments)
            .Where(b => b.FullName == BuyerIdentityGuid)
            .SingleOrDefaultAsync();
        return buyer;
    }
}
```

Všimněte si, že rozhraní IBuyerRepository pochází z vrstvy modelu domény. Implementace úložiště se však provádí na trvalosti a vrstvě infrastruktury.

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

Objekt DbContext (zveřejněné jako objekt IUnitOfWork) může být potřeba sdílet mezi více úložiště v rámci stejného oboru požadavku HTTP. Například to platí při operaci spouštěna musí pracovat s více agregace, ani jednoduše vzhledem k tomu, že používáte více instancí úložiště. Je také důležité zmínit, že rozhraní IUnitOfWork je součástí domény, ne typ EF.

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
        sqlop => sqlop.MigrationsAssembly(typeof(Startup).GetTypeInfo().
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
    [*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/ Implementing-the-Repository-and-Unit-of-work-Patterns-in-an-ASP-NET-MVC-Application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)

-   **Jonathan Allen. Strategie implementace pro úložiště vzor s platformou Entity Framework, Dapper a řetězu**
    [*https://www.infoq.com/articles/repository-implementation-strategies*](https://www.infoq.com/articles/repository-implementation-strategies)

-   **Cesaru členka Torre. Porovnávání životnosti služby kontejner IoC jádro ASP.NET s obory instance kontejner Autofac IoC**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/ Comparing-ASP-NET-Core-IOC-Service-LIFE-Times-and-autofac-IOC-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)

## <a name="table-mapping"></a>Mapování tabulek

Mapování tabulky identifikuje data tabulky, která mají být získaných z a uložit do databáze. Dříve jste viděli, jak lze pomocí entity domény (například produktu nebo pořadí doména) Generovat schéma související databáze. EF je důrazně uspořádaná kolem koncept *konvence*. Konvence adresu otázky typu "Jaký název tabulky bude?" nebo "jaké vlastnost je primární klíč?" Konvence jsou obvykle založené na běžné názvy – například je typické pro primární klíč jako vlastnost, která končí ID.

Podle konvence, každá entita se nastavit tak, aby mapovat do tabulky se stejným názvem jako DbSet&lt;TEntity&gt; vlastnost, která zveřejňuje se entita na odvozené kontextu. Pokud žádné DbSet&lt;TEntity&gt; hodnota je zadaný pro danou entitu, se používá název třídy.

### <a name="data-annotations-versus-fluent-api"></a>Datových poznámek versus rozhraní Fluent API

Existuje mnoho dalších konvence EF jádra a většina z nich lze změnit pomocí datových poznámek nebo rozhraní Fluent API implementována v rámci metody OnModelCreating.

Datových poznámek musí použít na třídy modelu entity, sami, což je více obtěžující způsob, jak z hlediska DDD. Je to proto, že jsou kontaminujících modelu s anotacemi dat související s databázi infrastruktury. Na druhé straně rozhraní Fluent API je pohodlný způsob, jak změnit většina konvence a mapování v rámci vrstvě infrastruktury trvalosti dat, a tak entity model vyčištění a odpojeného od infrastruktury trvalost.

### <a name="fluent-api-and-the-onmodelcreating-method"></a>Rozhraní Fluent API a metody OnModelCreating

Jak je uvedeno, aby bylo možné změnit konvence a mapování, můžete metody OnModelCreating v třídy DbContext. Následující příklad ukazuje, jak jsme to udělat v řazení mikroslužbu v eShopOnContainers.

```csharp
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
    //Other entities
    modelBuilder.Entity<OrderStatus>(ConfigureOrderStatus);
    //Other entities
}

void ConfigureOrder(EntityTypeBuilder<Order> orderConfiguration)
{
    orderConfiguration.ToTable("orders", DEFAULT_SCHEMA);
    orderConfiguration.HasKey(o => o.Id);
    orderConfiguration.Property(o => o.Id).ForSqlServerUseSequenceHiLo("orderseq", DEFAULT_SCHEMA);
    orderConfiguration.Property<DateTime>("OrderDate").IsRequired();
    orderConfiguration.Property<string>("Street").IsRequired();
    orderConfiguration.Property<string>("State").IsRequired();
    orderConfiguration.Property<string>("City").IsRequired();
    orderConfiguration.Property<string>("ZipCode").IsRequired();
    orderConfiguration.Property<string>("Country").IsRequired();
    orderConfiguration.Property<int>("BuyerId").IsRequired();
    orderConfiguration.Property<int>("OrderStatusId").IsRequired();
    orderConfiguration.Property<int>("PaymentMethodId").IsRequired();

    var navigation =
    orderConfiguration.Metadata.FindNavigation(nameof(Order.OrderItems));
    // DDD Patterns comment:
    // Set as Field (new since EF 1.1) to access
    // the OrderItem collection property as a field
    navigation.SetPropertyAccessMode(PropertyAccessMode.Field);

    orderConfiguration.HasOne(o => o.PaymentMethod)
        .WithMany()
        .HasForeignKey("PaymentMethodId")
        .OnDelete(DeleteBehavior.Restrict);
        orderConfiguration.HasOne(o => o.Buyer)
        .WithMany()
        .HasForeignKey("BuyerId");
        orderConfiguration.HasOne(o => o.OrderStatus)
        .WithMany()
        .HasForeignKey("OrderStatusId");
}
```

Můžete nastavit všechna rozhraní Fluent API mapování v rámci stejné metody OnModelCreating, ale doporučuje se oddílu tento kód a mít více submethods, jeden pro každou entitu, jak je znázorněno v příkladu. U modelů, zejména velké může i být vhodné mít samostatné zdrojové soubory (statické třídy) pro konfiguraci různých entity typů.

Kód v ukázce je explicitní. Konvence EF základní však provádění většiny to automaticky, takže skutečný kód, který by potřebujete k zápisu do dosáhnout samé by být mnohem menší.

### <a name="the-hilo-algorithm-in-ef-core"></a>Algoritmus HIS použití/Lo v EF jádra

Zajímavé aspekt kódu v předchozím příkladu je, že používá [HIS použití/Lo algoritmus](https://vladmihalcea.com/2014/06/23/the-hilo-algorithm/) jako strategie generování klíče.

Algoritmus HIS použití/Lo je užitečné, když potřebujete jedinečné klíče. Jako souhrn přiřadí algoritmus HIS použití-u jedinečné identifikátory řádky tabulky při není v závislosti na ukládání řádek v databázi okamžitě. Díky tomu můžete začít používat identifikátory hned, jak se stane s standardní sekvenční databázi ID.

Algoritmus HIS použití/Lo popisuje mechanismus pro generování bezpečné ID na straně klienta a nikoli v databázi. *Bezpečné* v tomto kontextu znamená bez kolizí. Tento algoritmus je zajímavé z těchto důvodů:

-   Nedochází k přerušení vzoru pracovní jednotky.

-   Nevyžaduje se, že odezev generátory pořadí způsob, jak provést v jiné systémy DBMS.

-   Vygeneruje lidského čitelný identifikátor, na rozdíl od techniky, které používají identifikátory GUID.

Jádro EF podporuje [HiLo](http://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) ForSqlServerUseSequenceHiLo metodou, jak je znázorněno v předchozím příkladu.

### <a name="mapping-fields-instead-of-properties"></a>Mapování polí místo vlastnosti

S funkcí 1.1 EF jádra, která se mapuje na pole sloupců je možné nechcete použít jakékoli vlastnosti ve třídě entity a jenom pro mapování sloupce z tabulky na pole. Běžně používá pro který by privátní pole pro všechny vnitřní stav, která nemusí být subjekty mimo entity.

EF 1.1 podporuje mapováním pole bez související vlastnosti na sloupec v databázi. To provedete pomocí jednoho pole nebo také pomocí kolekcí, jako je seznam&lt; &gt; pole. Tento bod jsem už zmínili dřív když jsme se bavili modelování třídy modelu domény, ale zde se zobrazí, jak se provádí mapování s konfigurací PropertyAccessMode.Field zvýrazněných v předchozí kód.

### <a name="using-shadow-properties-in-value-objects-for-hidden-ids-at-the-infrastructure-level"></a>Používání stínové vlastností v objektech hodnota skrytá ID na úrovni infrastruktury

Vlastnosti stínové v základní EF jsou vlastnosti, které nejsou k dispozici do třídy modelu entity. Hodnoty a stavy tyto vlastnosti jsou zachována výhradně v [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) třídy na úrovni infrastruktury.

Z DDD hlediska jsou vlastnosti stínové pohodlný způsob, jak implementovat objekty hodnota skrytím ID jako primární klíč stínové vlastnost. To je důležité, protože objekt hodnoty by neměl mít identity (alespoň, můžete by neměl mít ID ve vrstvě modelu domény při shaping hodnota objektů). Zde bod nemá, od aktuální verze EF základní EF základní způsob, jak implementovat objekty hodnotu jako [komplexní typy](https://msdn.microsoft.com/library/jj680147(v=vs.113).aspx), jak je možné v EF 6.x. To je důvod, proč potřebujete aktuálně implementovat objekt hodnoty jako entity s skrytá ID (primární klíč) nastavit jako vlastnost stínové.

Jak vidíte v [objekt hodnoty adres](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs) v eShopOnContainers, v modelu adresu nevidíte ID:

```csharp
public class Address : ValueObject
{
    public String Street { get; private set; }
    public String City { get; private set; }
    public String State { get; private set; }
    public String Country { get; private set; }
    public String ZipCode { get; private set; }
    //Constructor initializing, etc
}
```

Ale v pozadí, je potřeba zadat ID tak, aby základní EF je možné zachovat tato data v tabulkách databáze. Provedeme to v metodě ConfigureAddress [OrderingContext.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Infrastructure/OrderingContext.cs) třídy na úrovni infrastruktury, proto jsme není znečištění směrovány správu modelu domény s EF infrastruktury kódem.

```csharp
void ConfigureAddress(EntityTypeBuilder<Address> addressConfiguration)
{
    addressConfiguration.ToTable("address", DEFAULT_SCHEMA);
    // DDD pattern comment:
    // Implementing the Address ID as a shadow property, because the
    // address is a value object and an identity is not required for a
    // value object
    // EF Core just needs the ID so it can store it in a database table
    // See: https://docs.microsoft.com/ef/core/modeling/shadow-properties
    addressConfiguration.Property<int>("Id").IsRequired();
    addressConfiguration.HasKey("Id");
}
```

#### <a name="additional-resources"></a>Další zdroje

-   **Tabulky mapování**
    [*https://docs.microsoft.com/ef/core/modeling/relational/tables*](https://docs.microsoft.com/ef/core/modeling/relational/tables)

-   **Používá ke generování klíče Entity Framework Core HiLo**
    [*http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/*](http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/)

-   **Zálohování pole**
    [*https://docs.microsoft.com/ef/core/modeling/backing-field*](https://docs.microsoft.com/ef/core/modeling/backing-field)

-   **Steve Smith. Zapouzdřené kolekcí v Entity Framework Core**
    [*http://ardalis.com/encapsulated-collections-in-entity-framework-core*](http://ardalis.com/encapsulated-collections-in-entity-framework-core)

-   **Stínové vlastnosti**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)


>[!div class="step-by-step"]
[Předchozí] (infrastruktury trvalost layer-design.md) [Další] (nosql-database trvalost infrastructure.md)
