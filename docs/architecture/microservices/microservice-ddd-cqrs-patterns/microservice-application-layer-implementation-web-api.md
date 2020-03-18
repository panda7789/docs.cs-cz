---
title: Implementace aplikační vrstvy mikroslužby pomocí webového rozhraní API
description: Seznamte se s vkládáním závislostí a vzory mediátorů a podrobnostmi jejich implementace v aplikační vrstvě webového rozhraní API.
ms.date: 01/30/2020
ms.openlocfilehash: a88f3bfd11ea06df085ca82ed7265cb37006fc31
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77502449"
---
# <a name="implement-the-microservice-application-layer-using-the-web-api"></a>Implementace aplikační vrstvy mikroslužeb pomocí webového rozhraní API

## <a name="use-dependency-injection-to-inject-infrastructure-objects-into-your-application-layer"></a>Použití vkládání závislostí k vkládání objektů infrastruktury do aplikační vrstvy

Jak již bylo zmíněno dříve, aplikační vrstva může být implementována jako součást artefaktu (sestavení), který vytváříte, například v rámci projektu webového rozhraní API nebo projektu webové aplikace MVC. V případě mikroslužby vytvořené s ASP.NET Core, aplikační vrstva bude obvykle vaše knihovna webového rozhraní API. Pokud chcete oddělit to, co přichází z ASP.NET Core (jeho infrastruktury a řadiče) z vašeho kódu vlastní aplikační vrstvy, můžete také umístit aplikační vrstvu do samostatné knihovny tříd, ale to je volitelné.

Například kód aplikační vrstvy řazení mikroslužby je přímo implementována jako součást projektu **Ordering.API** (projekt ASP.NET core web API), jak je znázorněno na obrázku 7-23.

:::image type="complex" source="./media/microservice-application-layer-implementation-web-api/ordering-api-microservice.png" alt-text="Snímek obrazovky mikroslužby Ordering.API v Průzkumníku řešení.":::
Zobrazení Průzkumník řešení mikroslužby Ordering.API zobrazující podsložky ve složce Aplikace: Chování, příkazy, DomainEventHandlers, IntegrationEvents, Modely, Dotazy a ověření.
:::image-end:::

**Obrázek 7-23**. Aplikační vrstva v projektu Ordering.API ASP.NET Core Web API

ASP.NET Core obsahuje jednoduchý [integrovaný kontejner IoC](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (reprezentovaný rozhraním IServiceProvider), který ve výchozím nastavení podporuje vkládání konstruktoru a ASP.NET zpřístupňuje určité služby prostřednictvím di. ASP.NET Core používá termín *služby* pro všechny typy, které zaregistrujete, které budou vloženy prostřednictvím DI. Služby integrovaného kontejneru nakonfigurujete v metodě ConfigureServices ve třídě Startup vaší aplikace. Vaše závislosti jsou implementovány ve službách, které typ potřebuje a které se zaregistrujete v kontejneru IoC.

Obvykle chcete vložit závislosti, které implementují objekty infrastruktury. Velmi typická závislost na injekci je úložiště. Ale můžete vložit jakékoli jiné infrastruktury závislost, která může mít. Pro jednodušší implementace můžete přímo vložit objekt vzor jednotky práce (EF DbContext objekt), protože DBContext je také implementace objektů trvalosti infrastruktury.

V následujícím příkladu uvidíte, jak rozhraní .NET Core vstřikuje požadované objekty úložiště prostřednictvím konstruktoru. Třída je obslužná rutina příkazu, kterou budeme pokrýt v další části.

```csharp
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;
    private readonly IIdentityService _identityService;
    private readonly IMediator _mediator;

    // Using DI to inject infrastructure persistence Repositories
    public CreateOrderCommandHandler(IMediator mediator,
                                     IOrderRepository orderRepository,
                                     IIdentityService identityService)
    {
        _orderRepository = orderRepository ??
                          throw new ArgumentNullException(nameof(orderRepository));
        _identityService = identityService ??
                          throw new ArgumentNullException(nameof(identityService));
        _mediator = mediator ??
                                 throw new ArgumentNullException(nameof(mediator));
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        // Create the Order AggregateRoot
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic
        // make sure that consistency is preserved across the whole aggregate
        var address = new Address(message.Street, message.City, message.State,
                                  message.Country, message.ZipCode);
        var order = new Order(message.UserId, address, message.CardTypeId,
                              message.CardNumber, message.CardSecurityNumber,
                              message.CardHolderName, message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                               item.Discount, item.PictureUrl, item.Units);
        }

        _orderRepository.Add(order);

        return await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
    }
}
```

Třída používá vložené úložiště k provedení transakce a zachovat změny stavu. Nezáleží na tom, zda je tato třída obslužnou rutinou příkazu, metodou řadiče ASP.NET Core Web API nebo [aplikační službou DDD](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/). Je to nakonec jednoduchá třída, která používá úložiště, entity domény a další koordinaci aplikací způsobem podobným obslužné rutině příkazu. Vkládání závislostí funguje stejným způsobem pro všechny uvedené třídy, jako v příkladu pomocí DI na základě konstruktoru.

### <a name="register-the-dependency-implementation-types-and-interfaces-or-abstractions"></a>Registrace typů implementace závislostí a rozhraní nebo abstrakcí

Před použitím objektů vstřikovaných prostřednictvím konstruktory, musíte vědět, kde zaregistrovat rozhraní a třídy, které vytvářejí objekty vložené do tříd aplikace prostřednictvím DI. (Stejně jako DI na základě konstruktoru, jak je znázorněno výše.)

#### <a name="use-the-built-in-ioc-container-provided-by-aspnet-core"></a>Používejte vestavěný ioc kontejner dodaný ASP.NET Core

Při použití integrovaného kontejneru IoC poskytovaného ASP.NET Core zaregistrujete typy, které chcete vložit do metody ConfigureServices v souboru Startup.cs, jako v následujícím kódu:

```csharp
// Registration of types into ASP.NET Core built-in container
public void ConfigureServices(IServiceCollection services)
{
    // Register out-of-the-box framework services.
    services.AddDbContext<CatalogContext>(c =>
        c.UseSqlServer(Configuration["ConnectionString"]),
        ServiceLifetime.Scoped);

    services.AddMvc();
    // Register custom application dependencies.
    services.AddScoped<IMyCustomRepository, MyCustomSQLRepository>();
}
```

Nejběžnější vzor při registraci typů v kontejneru IoC je zaregistrovat dvojici typů – rozhraní a jeho související implementace třídy. Potom při vyžádání objektu z kontejneru IoC prostřednictvím libovolného konstruktoru, požádáte o objekt určitého typu rozhraní. Například v předchozím příkladu poslední řádek uvádí, že když některý z vašich konstruktorů mají závislost na IMyCustomRepository (rozhraní nebo abstrakce), kontejner IoC vloží instanci implementace MyCustomSQLServerRepository Třída.

#### <a name="use-the-scrutor-library-for-automatic-types-registration"></a>Použití knihovny Scrutor pro automatickou registraci typů

Při použití DI v .NET Core, můžete chtít mít možnost skenovat sestavení a automaticky zaregistrovat jeho typy podle konvence. Tato funkce není v současné době k dispozici v ASP.NET Core. K tomu však můžete použít knihovnu [Scrutor.](https://github.com/khellang/Scrutor) Tento přístup je vhodný, pokud máte desítky typů, které je třeba zaregistrovat v kontejneru IoC.

#### <a name="additional-resources"></a>Další zdroje

- **Matthew King, to je ono. Registrace služeb u společnosti Scrutor** \
  <https://www.mking.net/blog/registering-services-with-scrutor>

- **Kristian Hellang. Scrutor.** úložiště GitHub. \
  <https://github.com/khellang/Scrutor>

#### <a name="use-autofac-as-an-ioc-container"></a>Použití aplikace Autofac jako kontejneru ioC

Můžete také použít další ioc kontejnery a připojit je do kanálu ASP.NET Core, jako v objednávání mikroslužby v eShopOnContainers, který používá [Autofac](https://autofac.org/). Při použití Autofac obvykle zaregistrujete typy prostřednictvím modulů, které umožňují rozdělit typy registrace mezi více souborů v závislosti na tom, kde jsou vaše typy, stejně jako byste mohli mít typy aplikací distribuovány mezi více knihovnami tříd.

Například následující je [modul aplikace Autofac](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) pro projekt [Ordering.API web API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) s typy, které budete chtít vložit.

```csharp
public class ApplicationModule : Autofac.Module
{
    public string QueriesConnectionString { get; }
    public ApplicationModule(string qconstr)
    {
        QueriesConnectionString = qconstr;
    }

    protected override void Load(ContainerBuilder builder)
    {
        builder.Register(c => new OrderQueries(QueriesConnectionString))
            .As<IOrderQueries>()
            .InstancePerLifetimeScope();
        builder.RegisterType<BuyerRepository>()
            .As<IBuyerRepository>()
            .InstancePerLifetimeScope();
        builder.RegisterType<OrderRepository>()
            .As<IOrderRepository>()
            .InstancePerLifetimeScope();
        builder.RegisterType<RequestManager>()
            .As<IRequestManager>()
            .InstancePerLifetimeScope();
   }
}
```

Autofac má také funkci pro [skenování sestavení a registrovat typy podle konvencí názvů](https://autofac.readthedocs.io/en/latest/register/scanning.html).

Proces registrace a koncepty jsou velmi podobné způsobu, jakým můžete registrovat typy s vestavěným ASP.NET kontejneru Core IoC, ale syntaxe při použití Autofac je trochu jiná.

V ukázkovém kódu je registrována abstrakce IOrderRepository spolu s implementační třídou OrderRepository. To znamená, že vždy, když konstruktor deklaruje závislost prostřednictvím abstrakce Nebo rozhraní IOrderRepository, kontejner IoC vloží instanci třídy OrderRepository.

Typ oboru instance určuje, jak je instance sdílena mezi požadavky pro stejnou službu nebo závislost. Při požadavku na závislost kontejner ioC můžete vrátit následující:

- Jedna instance na rozsah životnosti (uvedená v kontejneru ASP.NET core ioc podle *rozsahu).*

- Nová instance na závislost (uvedená v kontejneru ASP.NET core ioc jako *přechodná).*

- Jedna instance sdílená mezi všemi objekty pomocí kontejneru IoC (označovaná v kontejneru ASP.NET core ioc jako *singleton).*

#### <a name="additional-resources"></a>Další zdroje

- **Úvod do vkládání závislostí v ASP.NET core** \
  [https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection](/aspnet/core/fundamentals/dependency-injection)

- **Autofac.** Oficiální dokumentace. \
  <https://docs.autofac.org/en/latest/>

- **Porovnání ASP.NET životnosti kontejneru Core IoC s obory instancí kontejneru Autofac IoC - Cesar de la Torre.** \
  <https://devblogs.microsoft.com/cesardelatorre/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/>

## <a name="implement-the-command-and-command-handler-patterns"></a>Implementace vzorů Příkaz a Obslužná rutina příkazů

V příkladu konstruktoru DI-through-constructor ukázáno v předchozí části kontejner IoC vstřikoval úložiště prostřednictvím konstruktoru ve třídě. Ale kam přesně jim byla píchnutá injekce? V jednoduché webové rozhraní API (například mikroslužby katalogu v eShopOnContainers) je vložíte na úrovni řadičů MVC v konstruktoru řadiče jako součást kanálu požadavků ASP.NET Core. V počátečním kódu této části (třída [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) ze služby Ordering.API v eShopOnContainers) se však vkládání závislostí provádí prostřednictvím konstruktoru konkrétní obslužné rutiny příkazu. Dovolte nám vysvětlit, co je obslužná rutina příkazu a proč byste ji chtěli používat.

Command vzor je vnitřně souvisí se vzorem CQRS, který byl zaveden dříve v této příručce. CQRS má dvě strany. První oblastí jsou dotazy, pomocí zjednodušených dotazů s [Dapper](https://github.com/StackExchange/dapper-dot-net) micro ORM, který byl vysvětlen dříve. Druhá oblast je příkazy, které jsou výchozím bodem pro transakce a vstupní kanál mimo službu.

Jak je znázorněno na obrázku 7-24, vzor je založen na přijímání příkazů ze strany klienta, jejich zpracování na základě pravidel modelu domény a nakonec trvalé stavy s transakcemi.

![Diagram znázorňující tok dat vysoké úrovně z klienta do databáze.](./media/microservice-application-layer-implementation-web-api/high-level-writes-side.png)

**Obrázek 7-24**. Zobrazení příkazů na vysoké úrovni nebo "transakční strana" ve vzoru CQRS

Obrázek 7-24 ukazuje, že aplikace rozhraní odesílá příkaz `CommandHandler`prostřednictvím rozhraní API, který se dostane do , který závisí na modelu domény a infrastruktury, aktualizovat databázi.

### <a name="the-command-class"></a>Třída příkazů

Příkaz je požadavek, aby systém provedl akci, která mění stav systému. Příkazy jsou nezbytné a měly by být zpracovány pouze jednou.

Vzhledem k tomu, že příkazy jsou imperativy, jsou obvykle pojmenovány se slovesem v imperativní náladě (například "create" nebo "update") a mohou zahrnovat agregační typ, například CreateOrderCommand. Na rozdíl od události, příkaz není fakt z minulosti; je to pouze žádost, a proto může být zamítnuta.

Příkazy mohou pocházet z uživatelského rozhraní v důsledku, že uživatel iniciuje požadavek, nebo od správce procesů, když správce procesů řídí agregaci k provedení akce.

Důležitou vlastností příkazu je, že by měl být zpracován pouze jednou jedním přijímačem. Důvodem je, že příkaz je jedna akce nebo transakce, které chcete provést v aplikaci. Například stejný příkaz vytvoření objednávky by neměl být zpracován více než jednou. To je důležitý rozdíl mezi příkazy a událostmi. Události mohou být zpracovány vícekrát, protože mnoho systémů nebo mikroslužeb může mít zájem o událost.

Kromě toho je důležité, aby příkaz byl zpracován pouze jednou v případě, že příkaz není idempotentní. Příkaz je idempotentní, pokud jej lze provést vícekrát bez změny výsledku, a to buď z důvodu povahy příkazu, nebo z důvodu způsobu, jakým systém zpracovává příkaz.

Je vhodné, aby vaše příkazy a aktualizace idempotentní, když to dává smysl podle obchodních pravidel vaší domény a invariants. Chcete-li například použít stejný příklad, pokud z nějakého důvodu (opakování logiky, hacking, atd.) stejný příkaz CreateOrder dosáhne vašeho systému vícekrát, měli byste být schopni jej identifikovat a zajistit, že nevytvoříte více objednávek. Chcete-li tak učinit, je třeba připojit nějaký druh identity v operacích a zjistit, zda příkaz nebo aktualizace již byla zpracována.

Odešlete příkaz jednomu příjemci; nepublikujete příkaz. Publikování je pro události, které uvádějí skutečnost – že se něco stalo a může být zajímavé pro příjemce událostí. V případě událostí, vydavatel nemá žádné obavy o tom, které přijímače získat událost nebo co dělají. Ale události domény nebo integrace jsou jiný příběh, který již byl zaveden v předchozích částech.

Příkaz je implementován s třídou, která obsahuje datová pole nebo kolekce se všemi informacemi, které jsou potřebné k provedení tohoto příkazu. Příkaz je zvláštní druh objektu přenosu dat (DTO), který se používá speciálně k vyžádání změn nebo transakcí. Samotný příkaz je založen přesně na informacích, které jsou potřebné pro zpracování příkazu, a nic víc.

Následující příklad ukazuje zjednodušenou `CreateOrderCommand` třídu. Toto je neměnný příkaz, který se používá v řazení mikroslužby v eShopOnContainers.

```csharp
// DDD and CQRS patterns comment
// Note that we recommend that you implement immutable commands
// In this case, immutability is achieved by having all the setters as private
// plus being able to update the data just once, when creating the object
// through the constructor.
// References on immutable commands:
// http://cqrs.nu/Faq
// https://docs.spine3.org/motivation/immutability.html
// http://blog.gauffin.org/2012/06/griffin-container-introducing-command-support/
// https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties
[DataContract]
public class CreateOrderCommand
    :IAsyncRequest<bool>
{
    [DataMember]
    private readonly List<OrderItemDTO> _orderItems;
    [DataMember]
    public string City { get; private set; }
    [DataMember]
    public string Street { get; private set; }
    [DataMember]
    public string State { get; private set; }
    [DataMember]
    public string Country { get; private set; }
    [DataMember]
    public string ZipCode { get; private set; }
    [DataMember]
    public string CardNumber { get; private set; }
    [DataMember]
    public string CardHolderName { get; private set; }
    [DataMember]
    public DateTime CardExpiration { get; private set; }
    [DataMember]
    public string CardSecurityNumber { get; private set; }
    [DataMember]
    public int CardTypeId { get; private set; }
    [DataMember]
    public IEnumerable<OrderItemDTO> OrderItems => _orderItems;

    public CreateOrderCommand()
    {
        _orderItems = new List<OrderItemDTO>();
    }

    public CreateOrderCommand(List<BasketItem> basketItems, string city,
        string street,
        string state, string country, string zipcode,
        string cardNumber, string cardHolderName, DateTime cardExpiration,
        string cardSecurityNumber, int cardTypeId) : this()
    {
        _orderItems = MapToOrderItems(basketItems);
        City = city;
        Street = street;
        State = state;
        Country = country;
        ZipCode = zipcode;
        CardNumber = cardNumber;
        CardHolderName = cardHolderName;
        CardSecurityNumber = cardSecurityNumber;
        CardTypeId = cardTypeId;
        CardExpiration = cardExpiration;
    }

    public class OrderItemDTO
    {
        public int ProductId { get; set; }
        public string ProductName { get; set; }
        public decimal UnitPrice { get; set; }
        public decimal Discount { get; set; }
        public int Units { get; set; }
        public string PictureUrl { get; set; }
    }
}
```

V podstatě třída příkazu obsahuje všechna data, která potřebujete pro provádění obchodní transakce pomocí objektů modelu domény. Příkazy jsou tedy jednoduše datové struktury, které obsahují data jen pro čtení a žádné chování. Název příkazu označuje jeho účel. V mnoha jazycích, jako je C#, příkazy jsou reprezentovány jako třídy, ale nejsou pravdivé třídy v reálném objektově orientovaný smysl.

Jako další charakteristiku jsou příkazy neměnné, protože očekávané využití je, že jsou zpracovány přímo modelem domény. Během předpokládaného života se nemusí měnit. Ve třídě C# nelze neměnnost dosáhnout tím, že nemá žádné nastavení nebo jiné metody, které mění vnitřní stav.

Mějte na paměti, že pokud máte v úmyslu nebo očekáváte, že příkazy projdou procesem `[DataMember]` serializace a deserializace, vlastnosti musí mít soukromý setter a (nebo `[JsonProperty]`) atribut. V opačném případě deserializátor nebude možné rekonstruovat objekt v cílovém umístění s požadovanými hodnotami. Můžete také použít skutečně jen pro čtení vlastnosti, pokud třída má konstruktor s parametry pro všechny vlastnosti, s `[JsonConstructor]`obvyklou camelCase konvence pojmenování a anotovat konstruktor jako . Tato možnost však vyžaduje více kódu.

Například třída příkazů pro vytvoření objednávky je pravděpodobně podobná z hlediska dat pořadí, ve kterém chcete vytvořit, ale pravděpodobně nepotřebujete stejné atributy. Například `CreateOrderCommand` nemá ID objednávky, protože objednávka ještě nebyla vytvořena.

Mnoho tříd příkazů může být jednoduché, vyžadující pouze několik polí o některém stavu, který je třeba změnit. To by bylo v případě, že jste právě mění stav objednávky z "v procesu" na "placené" nebo "odeslány" pomocí příkazu podobnénásledující:

```csharp
[DataContract]
public class UpdateOrderStatusCommand
    :IAsyncRequest<bool>
{
    [DataMember]
    public string Status { get; private set; }

    [DataMember]
    public string OrderId { get; private set; }

    [DataMember]
    public string BuyerIdentityGuid { get; private set; }
}
```

Někteří vývojáři, aby jejich objekty požadavku ui oddělit od jejich příkazu DTO, ale to je jen otázkou preference. Jedná se o únavné oddělení s nevelkou přidanou hodnotou a objekty mají téměř přesně stejný tvar. Například v eShopOnContainers některé příkazy pocházejí přímo ze strany klienta.

### <a name="the-command-handler-class"></a>Třída obslužné rutiny příkazu

Pro každý příkaz byste měli implementovat určitou třídu obslužné rutiny příkazu. Tak funguje vzor a je místo, kde budete používat objekt příkazu, objekty domény a objekty úložiště infrastruktury. Obslužná rutina příkazu je ve skutečnosti srdcem aplikační vrstvy z hlediska CQRS a DDD. Všechny logiky domény by však měly být obsaženy ve třídách domény – v rámci agregačních kořenových adresářů (kořenové entity), podřízených entit nebo [doménových služeb](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), ale ne v rámci obslužné rutiny příkazu, což je třída z aplikační vrstvy.

Třída obslužné rutiny příkazu nabízí silný odrazový můstek v cestě k dosažení principu jednotné odpovědnosti (SRP) uvedeného v předchozí části.

Obslužná rutina příkazu obdrží příkaz a získá výsledek z agregace, která se používá. Výsledkem by mělo být úspěšné spuštění příkazu nebo výjimka. V případě výjimky by měl být stav systému nezměněn.

Obslužná rutina příkazu obvykle provádí následující kroky:

- Přijímá objekt příkazu, jako DTO (z [mediátoru](https://en.wikipedia.org/wiki/Mediator_pattern) nebo jiného objektu infrastruktury).

- Ověří, zda je příkaz platný (pokud není ověřen mediátorem).

- Konkretizoval agregační kořenovou instanci, která je cílem aktuálního příkazu.

- Spustí metodu na agregační kořenové instanci, získání požadovaných dat z příkazu.

- Zachová nový stav agregace do související databáze. Tato poslední operace je skutečná transakce.

Obslužná rutina příkazu se obvykle zabývá jedinou agregací řízenou jeho agregační kořenovou (kořenovou entitou). Pokud by příjem jednoho příkazu měl ovlivnit více agregací, můžete použít události domény k šíření stavů nebo akcí napříč více agregacemi.

Důležitým bodem je, že při zpracování příkazu by měla být veškerá logika domény uvnitř modelu domény (agregace), plně zapouzdřena a připravena pro testování částí. Obslužná rutina příkazu funguje pouze jako způsob, jak získat model domény z databáze a jako poslední krok, sdělit vrstvu infrastruktury (úložiště) zachovat změny při změně modelu. Výhodou tohoto přístupu je, že můžete refaktorovat logiku domény v izolovaném, plně zapouzdřeném, bohatém modelu behaviorální domény bez změny kódu ve vrstvách aplikace nebo infrastruktury, což jsou úroveň instalace (obslužné rutiny příkazů, webové rozhraní API, repozitáře atd.).

Když příkaz obslužné rutiny získat složité, s příliš mnoho logiky, které může být zápach kódu. Zkontrolujte je a pokud najdete logiku domény, refaktorovat kód přesunout chování domény na metody objektů domény (agregační kořenové a podřízené entity).

Jako příklad třídy obslužné rutiny `CreateOrderCommandHandler` příkazu následující kód ukazuje stejnou třídu, kterou jste viděli na začátku této kapitoly. V tomto případě chceme zvýraznit Handle metodu a operace s objekty modelu domény/agregace.

```csharp
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;
    private readonly IIdentityService _identityService;
    private readonly IMediator _mediator;

    // Using DI to inject infrastructure persistence Repositories
    public CreateOrderCommandHandler(IMediator mediator,
                                     IOrderRepository orderRepository,
                                     IIdentityService identityService)
    {
        _orderRepository = orderRepository ??
                          throw new ArgumentNullException(nameof(orderRepository));
        _identityService = identityService ??
                          throw new ArgumentNullException(nameof(identityService));
        _mediator = mediator ??
                                 throw new ArgumentNullException(nameof(mediator));
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        // Create the Order AggregateRoot
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic
        // make sure that consistency is preserved across the whole aggregate
        var address = new Address(message.Street, message.City, message.State,
                                  message.Country, message.ZipCode);
        var order = new Order(message.UserId, address, message.CardTypeId,
                              message.CardNumber, message.CardSecurityNumber,
                              message.CardHolderName, message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                               item.Discount, item.PictureUrl, item.Units);
        }

        _orderRepository.Add(order);

        return await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
    }
}
```

Jedná se o další kroky, které by měla obslužná rutina příkazu provést:

- Data příkazu slouží k provozu s metodami a chováním agregačního kořenového adresáře.

- Interně v rámci objekty domény, raise události domény při provádění transakce, ale to je transparentní z hlediska obslužné rutiny příkazu.

- Pokud je výsledek operace agregace úspěšný a po dokončení transakce, zvyšte události integrace. (Ty mohou být také vyvolány třídami infrastruktury, jako jsou repozitáře.)

#### <a name="additional-resources"></a>Další zdroje

- **Mark Seemann. Na hranicích nejsou aplikace objektově orientované.** \
  <https://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/>

- **Příkazy a události** \
  <https://cqrs.nu/Faq/commands-and-events>

- **K čemu dělá obslužná rutina příkazu?** \
  <https://cqrs.nu/Faq/command-handlers>

- **Jimmyho Bogarda. Vzory příkazů domény – obslužné rutiny** \
  <https://jimmybogard.com/domain-command-patterns-handlers/>

- **Jimmyho Bogarda. Vzory příkazů domény – ověření** \
  <https://jimmybogard.com/domain-command-patterns-validation/>

## <a name="the-command-process-pipeline-how-to-trigger-a-command-handler"></a>Kanál procesu příkazu: jak spustit obslužnou rutinu příkazu

Další otázkou je, jak vyvolat obslužnou rutinu příkazu. Můžete ručně volat z každého souvisejícího ASP.NET core řadič. Tento přístup by však byl příliš spojený a není ideální.

Další dvě hlavní možnosti, které jsou doporučené možnosti, jsou:

- Prostřednictvím artefaktu vzoru mediátoru v paměti.

- S asynchronní fronty zpráv, mezi řadiči a obslužné rutiny.

### <a name="use-the-mediator-pattern-in-memory-in-the-command-pipeline"></a>Použití vzoru mediátoru (v paměti) v kanálu příkazů

Jak je znázorněno na obrázku 7-25, v přístupu CQRS používáte inteligentní mediátor, podobný sběrnici v paměti, která je dostatečně chytrá, aby přesměrovala na správnou obslužnou rutinu příkazu na základě typu příkazu nebo přijatého DTO. Jednotlivé černé šipky mezi součástmi představují závislosti mezi objekty (v mnoha případech injekčně prostřednictvím DI) s jejich související interakce.

![Diagram znázorňující podrobnější tok dat z klienta do databáze.](./media/microservice-application-layer-implementation-web-api/mediator-cqrs-microservice.png)

**Obrázek 7-25**. Použití vzoru mediátoru v procesu v jedné mikroslužbě CQRS

Výše uvedený diagram znázorňuje přiblížení z obrázku 7-24: řadič ASP.NET Core odešle příkaz do kanálu příkazů MediatR, takže se dostanou k příslušné obslužné rutině.

Důvod, proč použití vzoru mediátoru dává smysl, je, že v podnikových aplikacích se požadavky na zpracování mohou zkomplikovat. Chcete mít možnost přidat otevřený počet průřezových problémů, jako je protokolování, ověřování, audit a zabezpečení. V těchto případech se můžete spolehnout na kanál mediátora (viz [Vzor mediátora)](https://en.wikipedia.org/wiki/Mediator_pattern)poskytnout prostředky pro tyto další chování nebo průřezové obavy.

Mediátor je objekt, který zapouzdřuje "jak" tohoto procesu: koordinuje provádění na základě stavu, způsob, jakým je vyvolána obslužná rutina příkazu, nebo datová část, kterou poskytnete obslužné rutině. U součásti mediátora můžete použít průřezové obavy centralizovaným a transparentním způsobem použitím [dekorátorů](https://github.com/jbogard/MediatR/wiki/Behaviors) (nebo chování potrubí od [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0)). Další informace naleznete [decorator vzor](https://en.wikipedia.org/wiki/Decorator_pattern).

Dekoratory a chování jsou podobné [aspekty orientované programování (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming), platí pouze pro konkrétní proces kanálu spravované ho komponenty mediátora. Aspekty v AOP, které implementují průřezové obavy, jsou použity na základě *aspektu tkalců* vstřikovaných v době kompilace nebo na základě zachycení volání objektu. Oba typické Přístupy AOP jsou někdy řekl, aby práce "jako kouzlo," protože to není snadné vidět, jak AOP dělá svou práci. Při řešení závažných problémů nebo chyb může být obtížné ladit AOP. Na druhou stranu tyto decorators/behaviors jsou explicitní a použít pouze v kontextu mediátora, takže ladění je mnohem předvídatelnější a snadné.

Například v eShopOnContainers objednávání mikroslužby jsme implementovali dvě ukázkové chování, [Třída LogBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) a třída [ValidatorBehavior.](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) Implementace chování je vysvětlena v další části tím, že ukazuje, jak eShopOnContainers používá [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) [chování](https://github.com/jbogard/MediatR/wiki/Behaviors).

### <a name="use-message-queues-out-of-proc-in-the-commands-pipeline"></a>Použití front zpráv (mimo proc) v kanálu příkazu

Další možností je použití asynchronních zpráv založených na zprostředkovatelích nebo frontách zpráv, jak je znázorněno na obrázku 7-26. Tato možnost by mohla být také kombinována s komponentou mediátora přímo před obslužnou rutinou příkazu.

![Diagram znázorňující tok dat pomocí fronty zpráv HA.](./media/microservice-application-layer-implementation-web-api/add-ha-message-queue.png)

**Obrázek 7-26**. Použití front zpráv (mimo proces a meziprocesová komunikace) s příkazy CQRS

Kanál příkazu může být také zpracován frontou zpráv s vysokou dostupností pro doručení příkazů příslušné obslužné rutině. Použití fronty zpráv k přijetí příkazů může dále komplikovat kanálu příkazu, protože pravděpodobně budete muset rozdělit kanál do dvou procesů připojených prostřednictvím fronty externích zpráv. Přesto by měl být použit, pokud potřebujete mít lepší škálovatelnost a výkon na základě asynchronní zasílání zpráv. Zvažte, že v případě obrázku 7-26 řadič pouze odešle zprávu příkazu do fronty a vrátí. Potom obslužné rutiny příkazů zpracovávají zprávy vlastním tempem. To je velká výhoda front: fronta zpráv může fungovat jako vyrovnávací paměť v případech, kdy je potřeba hyper škálovatelnost, například pro stavy nebo jakýkoli jiný scénář s velkým objemem dat příchozího přenosu dat.

Z důvodu asynchronní povahy front zpráv je však nutné zjistit, jak komunikovat s klientskou aplikací o úspěchu nebo neúspěchu procesu příkazu. Zpravidla byste nikdy neměli používat příkazy "oheň a zapomenout". Každá obchodní aplikace potřebuje vědět, zda byl příkaz zpracován úspěšně nebo alespoň ověřen a přijat.

Proto je schopen reagovat na klienta po ověření příkazu zprávy, která byla odeslána do asynchronní fronty zvyšuje složitost systému, ve srovnání s procesem příkazu v procesu v procesu, který vrátí výsledek operace po spuštění transakce. Pomocí front může být nutné vrátit výsledek procesu příkazu prostřednictvím jiných zpráv výsledků operace, které budou vyžadovat další součásti a vlastní komunikaci v systému.

Kromě toho asynchronní příkazy jsou jednosměrné příkazy, které v mnoha případech nemusí být potřeba, jak je vysvětleno v následující zajímavé výměně mezi Burtsev Alexey a Greg Young v [online konverzaci](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):

> \[Burtsev Alexey najdu spoustu kódu, kde lidé používají asynchronní příkaz zpracování nebo jednosměrný příkaz zasílání zpráv bez jakéhokoli důvodu, aby tak učinily\] (nejsou dělat nějaké dlouhé operace, nejsou provádění externí asynchronní kód, nemají ani přes hranice aplikace, které mají být pomocí sběrnice zpráv). Proč zavádějí tuto zbytečnou složitost? A vlastně jsem neviděl příklad kódu CQRS s blokováním obslužných rutin příkazů, i když to bude fungovat v pohodě ve většině případů.
>
> \[Greg\] \[Mladý ... \] asynchronní příkaz neexistuje; Je to vlastně další událost. Pokud musím přijmout to, co mi pošlete a vyvolat událost, pokud nesouhlasím, už mi říkáte, abych udělal něco, co \[je, není to příkaz\]. Říkáš mi, že se něco stalo. To se zdá jako mírný rozdíl na první, ale to má mnoho důsledků.

Asynchronní příkazy výrazně zvyšují složitost systému, protože neexistuje žádný jednoduchý způsob, jak označit selhání. Proto asynchronní příkazy nejsou doporučeny jiné než při škálování požadavky jsou potřeba nebo ve zvláštních případech při komunikaci interní mikroslužeb prostřednictvím zasílání zpráv. V těchto případech je nutné navrhnout samostatný systém vykazování a obnovení pro selhání.

V počáteční verzi eShopOnContainers jsme se rozhodli použít synchronní zpracování příkazů, začalo z HTTP požadavků a řízeno vzorem Mediátora. To vám snadno umožňuje vrátit úspěch nebo neúspěch procesu, jako v implementaci [CreateOrderCommandHandler.](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs)

V každém případě by to mělo být rozhodnutí založené na obchodních požadavcích vaší aplikace nebo mikroslužby.

## <a name="implement-the-command-process-pipeline-with-a-mediator-pattern-mediatr"></a>Implementace kanálu procesu příkazu se vzorem mediátora (MediatR)

Jako ukázkovou implementaci tato příručka navrhuje použití kanálu v procesu založeného na vzoru mediátoru k řízení příkazů a příkazů trasy v paměti na správné obslužné rutiny příkazů. Průvodce také navrhuje použití [chování](https://github.com/jbogard/MediatR/wiki/Behaviors) s cílem oddělit průřezové obavy.

Pro implementaci v .NET Core je k dispozici více knihoven s otevřeným zdrojovým kódem, které implementují vzor Mediator. Knihovna použitá v této příručce je open-source knihovna [MediatR](https://github.com/jbogard/MediatR) (vytvořená Jimmy Bogard), ale můžete použít jiný přístup. MediatR je malá a jednoduchá knihovna, která umožňuje zpracovávat zprávy v paměti jako příkaz při použití dekorátorů nebo chování.

Použití vzoru mediátoru pomáhá snížit párování a izolovat obavy požadované práce, zatímco automatické připojení k obslužné rutině, která provádí tuto práci – v tomto případě k obslužné rutině příkazů.

Dalším dobrým důvodem pro použití mediator vzor byl vysvětlen Jimmy Bogard při kontrole této příručky:

> Myslím, že by stálo za zmínku testování zde - poskytuje pěkný konzistentní okno do chování vašeho systému. Požadavek-in, odpověď-out. Zjistili jsme, že aspekt docela cenné při budování důsledně chovat testy.

Nejprve se podívejme na ukázkový řadič WebAPI, kde byste skutečně použili objekt mediátora. Pokud jste nepoužívali objekt mediátoru, budete muset vložit všechny závislosti pro tento řadič, věci jako objekt protokolování a další. Proto by konstruktor být poměrně složité. Na druhou stranu, pokud použijete objekt mediátoru, konstruktor řadiče může být mnohem jednodušší, jen s několika závislostmi namísto mnoha závislostí, pokud jste měli jednu na operaci průřezu, jako v následujícím příkladu:

```csharp
public class MyMicroserviceController : Controller
{
    public MyMicroserviceController(IMediator mediator,
                                    IMyMicroserviceQueries microserviceQueries)
    {
        // ...
    }
}
```

Uvidíte, že mediátor poskytuje čistý a štíhlý konstruktor řadiče webového rozhraní API. Kromě toho v rámci metody kontroleru kód pro odeslání příkazu do objektu mediátora je téměř jeden řádek:

```csharp
[Route("new")]
[HttpPost]
public async Task<IActionResult> ExecuteBusinessOperation([FromBody]RunOpCommand
                                                               runOperationCommand)
{
    var commandResult = await _mediator.SendAsync(runOperationCommand);

    return commandResult ? (IActionResult)Ok() : (IActionResult)BadRequest();
}
```

### <a name="implement-idempotent-commands"></a>Implementace idempotentních příkazů

V **eShopOnContainers**, pokročilejší příklad než výše je odeslání CreateOrderCommand objekt z objednávání mikroslužby. Ale protože objednání obchodní proces je trochu složitější a v našem případě se skutečně spustí v mikroslužbě košíku, tato akce odeslání CreateOrderCommand objekt se provádí z obslužné rutiny události integrace s názvem [UserCheckoutAcceptedIntegrationEventHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) namísto jednoduchého řadiče WebAPI volána z klientské aplikace jako v předchozím jednoduššípříkladu.

Nicméně, akce odeslání příkazu MediatR je docela podobný, jak je znázorněno v následujícím kódu.

```csharp
var createOrderCommand = new CreateOrderCommand(eventMsg.Basket.Items,
                                                eventMsg.UserId, eventMsg.City,
                                                eventMsg.Street, eventMsg.State,
                                                eventMsg.Country, eventMsg.ZipCode,
                                                eventMsg.CardNumber,
                                                eventMsg.CardHolderName,
                                                eventMsg.CardExpiration,
                                                eventMsg.CardSecurityNumber,
                                                eventMsg.CardTypeId);

var requestCreateOrder = new IdentifiedCommand<CreateOrderCommand,bool>(createOrderCommand,
                                                                        eventMsg.RequestId);
result = await _mediator.Send(requestCreateOrder);
```

Tento případ je však také trochu pokročilejší, protože také implementujeme idempotentní příkazy. Proces CreateOrderCommand by měl být idempotentní, takže pokud je stejná zpráva duplikována prostřednictvím sítě, z jakéhokoli důvodu, jako je opakování, bude stejný obchodní příkaz zpracován pouze jednou.

To je implementováno zabalením obchodního příkazu (v tomto případě CreateOrderCommand) a vložením do obecného IdentifiedCommand, který je sledován ID každé zprávy přicházející prostřednictvím sítě, která musí být idempotentní.

V níže uvedeném kódu uvidíte, že IdentifiedCommand není nic jiného než DTO s a ID plus zabalené obchodní příkaz objektu.

```csharp
public class IdentifiedCommand<T, R> : IRequest<R>
    where T : IRequest<R>
{
    public T Command { get; }
    public Guid Id { get; }
    public IdentifiedCommand(T command, Guid id)
    {
        Command = command;
        Id = id;
    }
}
```

Potom CommandHandler pro IdentifiedCommand s názvem [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs) bude v podstatě zkontrolovat, zda ID přichází jako součást zprávy již existuje v tabulce. Pokud již existuje, tento příkaz nebude znovu zpracován, takže se chová jako idempotentní příkaz. Tento kód infrastruktury `_requestManager.ExistAsync` se provádí pomocí volání metody níže.

```csharp
// IdentifiedCommandHandler.cs
public class IdentifiedCommandHandler<T, R> :
                                   IAsyncRequestHandler<IdentifiedCommand<T, R>, R>
                                   where T : IRequest<R>
{
    private readonly IMediator _mediator;
    private readonly IRequestManager _requestManager;

    public IdentifiedCommandHandler(IMediator mediator,
                                    IRequestManager requestManager)
    {
        _mediator = mediator;
        _requestManager = requestManager;
    }

    protected virtual R CreateResultForDuplicateRequest()
    {
        return default(R);
    }

    public async Task<R> Handle(IdentifiedCommand<T, R> message)
    {
        var alreadyExists = await _requestManager.ExistAsync(message.Id);
        if (alreadyExists)
        {
            return CreateResultForDuplicateRequest();
        }
        else
        {
            await _requestManager.CreateRequestForCommandAsync<T>(message.Id);

            // Send the embedded business command to mediator
            // so it runs its related CommandHandler
            var result = await _mediator.Send(message.Command);

            return result;
        }
    }
}
```

Vzhledem k tomu, identifiedcommand funguje jako obálka obchodního příkazu, když obchodní příkaz musí být zpracovány, protože není opakované Id, pak se, že vnitřní obchodní příkaz `_mediator.Send(message.Command)`a re-odešle jej mediator, jako v poslední části kódu je uvedeno výše při spuštění , z [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs).

Když to dělá, bude propojovat a spouštět obslužnou rutinu obchodního příkazu, v tomto případě [CreateOrderCommandHandler,](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) který spouštějí transakce proti objednávání databáze, jak je znázorněno v následujícím kódu.

```csharp
// CreateOrderCommandHandler.cs
public class CreateOrderCommandHandler
                                   : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;
    private readonly IIdentityService _identityService;
    private readonly IMediator _mediator;

    // Using DI to inject infrastructure persistence Repositories
    public CreateOrderCommandHandler(IMediator mediator,
                                     IOrderRepository orderRepository,
                                     IIdentityService identityService)
    {
        _orderRepository = orderRepository ??
                          throw new ArgumentNullException(nameof(orderRepository));
        _identityService = identityService ??
                          throw new ArgumentNullException(nameof(identityService));
        _mediator = mediator ??
                                 throw new ArgumentNullException(nameof(mediator));
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        // Add/Update the Buyer AggregateRoot
        var address = new Address(message.Street, message.City, message.State,
                                  message.Country, message.ZipCode);
        var order = new Order(message.UserId, address, message.CardTypeId,
                              message.CardNumber, message.CardSecurityNumber,
                              message.CardHolderName, message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                               item.Discount, item.PictureUrl, item.Units);
        }

        _orderRepository.Add(order);

        return await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
    }
}
```

### <a name="register-the-types-used-by-mediatr"></a>Registrace typů používaných programem MediatR

Aby byl MediatR informován o třídách obslužné rutiny příkazů, musíte zaregistrovat třídy mediátorů a třídy obslužné rutiny příkazů v kontejneru IoC. Ve výchozím nastavení používá MediatR Autofac jako kontejner IoC, ale můžete také použít předdefinovaný ASP.NET kontejneru Core IoC nebo jiného kontejneru podporovaného programem MediatR.

Následující kód ukazuje, jak zaregistrovat typy a příkazy mediátora při použití modulů Autofac.

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        builder.RegisterAssemblyTypes(typeof(IMediator).GetTypeInfo().Assembly)
            .AsImplementedInterfaces();

        // Register all the Command classes (they implement IAsyncRequestHandler)
        // in assembly holding the Commands
        builder.RegisterAssemblyTypes(
                              typeof(CreateOrderCommand).GetTypeInfo().Assembly).
                                   AsClosedTypesOf(typeof(IAsyncRequestHandler<,>));
        // Other types registration
        //...
    }
}
```

To je místo, kde "kouzlo se stane" s MediatR.

Vzhledem k tomu, `IAsyncRequestHandler<T>` že každý příkaz obslužná rutina `RegisteredAssemblyTypes` implementuje `IAsyncRequestHandler` obecné rozhraní, `CommandHandlers` při `Commands`registraci sestavení, kód `CommandHandler` registruje se všemi typy označené jako při vztahu s jejich , díky vztahu uvedenéve třídě, jako v následujícím příkladu:

```csharp
public class CreateOrderCommandHandler
  : IAsyncRequestHandler<CreateOrderCommand, bool>
{
```

To je kód, který koreluje příkazy s obslužnými rutinami příkazů. Obslužná rutina je pouze `RequestHandler<T>`jednoduchá třída, ale dědí z , kde T je typ příkazu a MediatR zajišťuje, že je vyvolána se správnou datovou částí (příkaz).

## <a name="apply-cross-cutting-concerns-when-processing-commands-with-the-behaviors-in-mediatr"></a>Použití průřezových zájmů při zpracování příkazů pomocí příkazů v programu MediatR

Je tu ještě jedna věc: možnost aplikovat průřezové obavy na potrubí mediátorů. Můžete také vidět na konci kódu registračního modulu Autofac, jak registruje typ chování, konkrétně vlastní LoggingBehavior třídy a ValidatorBehavior třídy. Ale můžete přidat i další vlastní chování.

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        builder.RegisterAssemblyTypes(typeof(IMediator).GetTypeInfo().Assembly)
            .AsImplementedInterfaces();

        // Register all the Command classes (they implement IAsyncRequestHandler)
        // in assembly holding the Commands
        builder.RegisterAssemblyTypes(
                              typeof(CreateOrderCommand).GetTypeInfo().Assembly).
                                   AsClosedTypesOf(typeof(IAsyncRequestHandler<,>));
        // Other types registration
        //...
        builder.RegisterGeneric(typeof(LoggingBehavior<,>)).
                                                   As(typeof(IPipelineBehavior<,>));
        builder.RegisterGeneric(typeof(ValidatorBehavior<,>)).
                                                   As(typeof(IPipelineBehavior<,>));
    }
}
```

Že [LoggingBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) třídy lze implementovat jako následující kód, který protokoluje informace o příkazu obslužné rutiny, která je spuštěna a zda byla úspěšná nebo ne.

```csharp
public class LoggingBehavior<TRequest, TResponse>
         : IPipelineBehavior<TRequest, TResponse>
{
    private readonly ILogger<LoggingBehavior<TRequest, TResponse>> _logger;
    public LoggingBehavior(ILogger<LoggingBehavior<TRequest, TResponse>> logger) =>
                                                                  _logger = logger;

    public async Task<TResponse> Handle(TRequest request,
                                        RequestHandlerDelegate<TResponse> next)
    {
        _logger.LogInformation($"Handling {typeof(TRequest).Name}");
        var response = await next();
        _logger.LogInformation($"Handled {typeof(TResponse).Name}");
        return response;
    }
}
```

Pouze implementací této třídy chování a registrací v kanálu (v MediatorModule výše), všechny příkazy zpracované prostřednictvím MediatR bude protokolování informací o provádění.

EShopOnContainers objednávání mikroslužby také platí druhé chování pro základní ověření, [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) třídy, která závisí na knihovně [FluentValidation,](https://github.com/JeremySkinner/FluentValidation) jak je znázorněno v následujícím kódu:

```csharp
public class ValidatorBehavior<TRequest, TResponse>
         : IPipelineBehavior<TRequest, TResponse>
{
    private readonly IValidator<TRequest>[] _validators;
    public ValidatorBehavior(IValidator<TRequest>[] validators) =>
                                                         _validators = validators;

    public async Task<TResponse> Handle(TRequest request,
                                        RequestHandlerDelegate<TResponse> next)
    {
        var failures = _validators
            .Select(v => v.Validate(request))
            .SelectMany(result => result.Errors)
            .Where(error => error != null)
            .ToList();

        if (failures.Any())
        {
            throw new OrderingDomainException(
                $"Command Validation Errors for type {typeof(TRequest).Name}",
                        new ValidationException("Validation exception", failures));
        }

        var response = await next();
        return response;
    }
}
```

Chování zde vyvolává výjimku, pokud se ověření nezdaří, ale můžete také vrátit výsledný objekt, který obsahuje výsledek příkazu, pokud byl úspěšný, nebo ověřovací zprávy v případě, že tomu tak nebylo. To by pravděpodobně usnadnilo zobrazení výsledků ověření uživateli.

Potom na základě knihovny [FluentValidation](https://github.com/JeremySkinner/FluentValidation) jsme vytvořili ověření dat předaná pomocí příkazu CreateOrderCommand, jako v následujícím kódu:

```csharp
public class CreateOrderCommandValidator : AbstractValidator<CreateOrderCommand>
{
    public CreateOrderCommandValidator()
    {
        RuleFor(command => command.City).NotEmpty();
        RuleFor(command => command.Street).NotEmpty();
        RuleFor(command => command.State).NotEmpty();
        RuleFor(command => command.Country).NotEmpty();
        RuleFor(command => command.ZipCode).NotEmpty();
        RuleFor(command => command.CardNumber).NotEmpty().Length(12, 19);
        RuleFor(command => command.CardHolderName).NotEmpty();
        RuleFor(command => command.CardExpiration).NotEmpty().Must(BeValidExpirationDate).WithMessage("Please specify a valid card expiration date");
        RuleFor(command => command.CardSecurityNumber).NotEmpty().Length(3);
        RuleFor(command => command.CardTypeId).NotEmpty();
        RuleFor(command => command.OrderItems).Must(ContainOrderItems).WithMessage("No order items found");
    }

    private bool BeValidExpirationDate(DateTime dateTime)
    {
        return dateTime >= DateTime.UtcNow;
    }

    private bool ContainOrderItems(IEnumerable<OrderItemDTO> orderItems)
    {
        return orderItems.Any();
    }
}

```

Můžete vytvořit další ověření. Toto je velmi čistý a elegantní způsob, jak implementovat ověření příkazu.

Podobným způsobem můžete implementovat další chování pro další aspekty nebo průřezové obavy, které chcete použít na příkazy při jejich zpracování.

#### <a name="additional-resources"></a>Další zdroje

##### <a name="the-mediator-pattern"></a>Vzor mediátora

- **Vzor mediátora** \
  [https://en.wikipedia.org/wiki/Mediator\_pattern](https://en.wikipedia.org/wiki/Mediator_pattern)

##### <a name="the-decorator-pattern"></a>Dekoratér vzor

- **Dekoratér vzor** \
  [https://en.wikipedia.org/wiki/Decorator\_pattern](https://en.wikipedia.org/wiki/Decorator_pattern)

##### <a name="mediatr-jimmy-bogard"></a>Zprostředkovatel (Jimmy Bogard)

- **Zprostředkovatel.** úložiště GitHub. \
  <https://github.com/jbogard/MediatR>

- **CQRS s MediatR a AutoMapper** \
  <https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/>

- **Dejte své ovladače na dietu: POSTs a příkazy.** \
  <https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/>

- **Řešení průřezových problémů pomocí potrubí mediátorů** \
  <https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/>

- **CQRS a REST: perfektní shoda** \
  <https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/>

- **Příklady kanálu MediatR** \
  <https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/>

- **Svislá testovací svítidla pro mediatr a ASP.NET jádra** \
  <https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/>

- **Byla vydána rozšíření MediatR pro vkládání závislostí společnosti Microsoft** \
  <https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/>

##### <a name="fluent-validation"></a>Plynulá validace

- **Jeremy Skinner. FluentValidation.** úložiště GitHub. \
  <https://github.com/JeremySkinner/FluentValidation>

> [!div class="step-by-step"]
> [Předchozí](microservice-application-layer-web-api-design.md)
> [další](../implement-resilient-applications/index.md)
