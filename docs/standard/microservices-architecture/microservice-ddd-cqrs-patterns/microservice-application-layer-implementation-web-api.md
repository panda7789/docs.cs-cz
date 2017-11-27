---
title: "Implementace aplikační vrstvu mikroslužbu pomocí rozhraní Web API"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Implementace aplikační vrstvu mikroslužbu pomocí rozhraní Web API"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: d505a2561ae9b8dee05e803fd639387b63b28b70
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-the-microservice-application-layer-using-the-web-api"></a>Implementace aplikační vrstvu mikroslužbu pomocí rozhraní Web API

## <a name="using-dependency-injection-to-inject-infrastructure-objects-into-your-application-layer"></a>Pomocí vkládání závislostí vložení objektů infrastruktury do vaší aplikační vrstvy

Jak je uvedeno nahoře, aplikační vrstvu můžete implementovat jako součást artefaktů, který vytváříte, například v projektu webového rozhraní API nebo projekt aplikace MVC. V případě mikroslužbu, vytvořené s ASP.NET Core aplikační vrstvu bude obvykle knihovnu webového rozhraní API. Pokud chcete k oddělení, co pochází z ASP.NET Core (jeho infrastruktury a řadičů) z vašeho kódu vrstvy vlastní aplikaci, umístíte vaší aplikační vrstvy může také v knihovně samostatné třídy, ale který je volitelné.

Například kód aplikace vrstvy řazení mikroslužbu přímo implementována jako součást **Ordering.API** projektu (projektu webového rozhraní API ASP.NET Core), jako uvedené v obrázek 9-19.

![](./media/image20.png)

**Obrázek 9-19**. Aplikační vrstvu v projektu webového rozhraní API pro jádro ASP.NET Ordering.API

ASP.NET Core zahrnuje jednoduchou [předdefinované kontejner IoC](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (představované rozhraní IServiceProvider), která podporuje vkládání konstruktor ve výchozím nastavení a ASP.NET zpřístupní určité služby prostřednictvím DI. ASP.NET Core používá termín *služby* pro všechny typy zaregistrujete, které budou vloženy prostřednictvím DI. Nakonfigurujete integrované kontejneru služby v metodě ConfigureServices ve třídě spuštění vaší aplikace. Závislostmi se implementují ve služby, které potřebuje typu.

Obvykle je vhodné pro vkládání závislosti, které implementují objekty infrastruktury. Velmi typické závislost vložení je úložiště. Ale může vložit žádné další infrastrukturu závislost, která může mít. Pro jednodušší implementací může přímo vložit vzor objektu pracovní jednotky (objekt EF DbContext), protože DBContext se také implementace objektů trvalost vaší infrastruktury.

V následujícím příkladu vidíte, jak je .NET Core vložení požadované úložiště objektů pomocí konstruktoru. Třída je obslužná rutina příkazu, který vám nabídneme v další části.

```csharp
// Sample command handler
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;

    // Constructor where Dependencies are injected
    public CreateOrderCommandHandler(IOrderRepository orderRepository)
    {
        if (orderRepository == null)
        {
            throw new ArgumentNullException(nameof(orderRepository));
        }
        _orderRepository = orderRepository;
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        //
        // ... Additional code
        //
        // Create the Order AggregateRoot
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic
        // make sure that consistency is preserved across the whole aggregate
        var address = new Address(message.Street, message.City, message.State,
            message.Country, message.ZipCode);
        var order = new Order(address, message.CardTypeId, message.CardNumber,
            message.CardSecurityNumber,
            message.CardHolderName,
            message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                item.Discount, item.PictureUrl, item.Units);
        }

        //Persist the Order through the Repository
        _orderRepository.Add(order);
        var result = await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
        return result > 0;
    }
}
```

Třída vloženého úložiště používá ke spouštění transakce a zachová tak změny stavu. Nezáleží, jestli je obslužná rutina příkazu, metody kontroleru webového rozhraní API ASP.NET Core třídy nebo [služba aplikace DDD](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/). Nakonec je jednoduchý třídu, která používá úložiště, entity domény a další aplikace koordinaci způsobem podobná obslužná rutina příkazu. Stejným způsobem jako pro všechny uvedené třídy, jako v příkladu pomocí DI podle konstruktoru funguje vkládání závislostí.

### <a name="registering-the-dependency-implementation-types-and-interfaces-or-abstractions"></a>Probíhá registrace závislosti implementace typy a rozhraní nebo abstrakce

Než použijete objekty vložit prostřednictvím konstruktory, musíte vědět, kde k registraci rozhraní a třídy, které vytváří objekty vloženy do vaší třídy aplikace prostřednictvím DI. (Například DI na základě konstruktoru, jak je uvedený výše.)

#### <a name="using-the-built-in-ioc-container-provided-by-aspnet-core"></a>Pomocí předdefinovaných kontejner IoC poskytované ASP.NET Core

Pokud používáte integrované kontejner IoC poskytované ASP.NET Core, zaregistrujte se typy, které chcete vložit v metodě ConfigureServices v souboru Startup.cs, jako v následujícím kódu:

```csharp
// Registration of types into ASP.NET Core built-in container
public void ConfigureServices(IServiceCollection services)
{
    // Register out-of-the-box framework services.
    services.AddDbContext<CatalogContext>(c =>
    {
        c.UseSqlServer(Configuration["ConnectionString"]);
    },
    ServiceLifetime.Scoped
    );
    services.AddMvc();
    // Register custom application dependencies.
    services.AddScoped<IMyCustomRepository, MyCustomSQLRepository>();
}
```

Nejběžnější vzor, když zaregistrujete typy na kontejner IoC k registraci pár typy – rozhraní a jeho souvisejících implementace třídy. Pokud budete požadovat objekt z kontejneru IoC prostřednictvím žádné konstruktor, pak požádáte objekt určitého typu rozhraní. Například v předchozím příkladu poslední řádek stavy, pokud žádné z vaší konstruktory jsou závislé na IMyCustomRepository (rozhraní nebo abstrakce), kontejner IoC bude instance implementace MyCustomSQLServerRepository vložit Třída.

#### <a name="using-the-scrutor-library-for-automatic-types-registration"></a>Použití knihovny Scrutor pro registraci automatické typy

Při použití DI v .NET Core, můžete být skenovat sestavení a automatickou registraci typy jejího podle konvence. Tato funkce není aktuálně k dispozici v ASP.NET Core. Můžete však použít [Scrutor](https://github.com/khellang/Scrutor) knihovny pro tento. Tento přístup je vhodné, když máte desítek typy, které musí být registrované ve vašem kontejner IoC.

#### <a name="additional-resources"></a>Další zdroje

-   **Matthew krále. Registrace služby Scrutor**
    [*https://mking.io/blog/registering-services-with-scrutor*](https://mking.io/blog/registering-services-with-scrutor)

<!-- -->

-   **Kristian Hellang. Scrutor.** Úložiště GitHub.
    [*https://github.com/khellang/Scrutor*](https://github.com/khellang/Scrutor)

#### <a name="using-autofac-as-an-ioc-container"></a>Použití Autofac jako kontejner IoC

Můžete také používat další technologie IoC kontejnery a připojte je kanálu ASP.NET Core, stejně jako řazení mikroslužbu v eShopOnContainers, který používá [Autofac](https://autofac.org/). Při použití Autofac obvykle zaregistrovat typy prostřednictvím modulů, které umožňují rozdělení typy registrace mezi více souborů, v závislosti na tom, kde vaše typy jsou, stejně jako typy aplikací, které jsou rozmístěny v několika knihovny tříd může mít.

Například následující je [modulu aplikace Autofac](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) pro [Ordering.API webového rozhraní API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) projektu s typy můžete vložit.

```csharp
public class ApplicationModule
    :Autofac.Module
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

Proces registrace a Koncepty jsou velmi podobně jako typy můžete zaregistrovat pomocí předdefinovaných iOS kontejneru ASP.NET Core, ale syntaxe při použití Autofac je trochu liší.

V příkladu kódu je zaregistrován abstrakci IOrderRepository společně s třída implementace OrderRepository. To znamená, že vždy, když konstruktor je deklarace závislost prostřednictvím abstrakce IOrderRepository nebo rozhraní, kontejner IoC bude instance třídy OrderRepository vložit.

Typ oboru instance Určuje, jak sdílet instanci mezi požadavky pro stejné služby nebo závislostí. Po odeslání žádosti pro závislost na kontejner IoC vrátit následující:

-   Jedna instance pro každý obor doba platnosti (uvedených v kontejneru ASP.NET Core IoC jako *obor*).

-   Nová instance za závislosti (uvedených v kontejneru ASP.NET Core IoC jako *přechodný*).

-   Jedna instance sdílet všechny objekty pomocí kontejner IoC (uvedených v kontejneru ASP.NET Core IoC jako *singleton*).

#### <a name="additional-resources"></a>Další zdroje

-   **Úvod do vkládání závislostí v ASP.NET Core**
    [*https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection*](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection)

-   **Autofac.** Oficiální dokumentaci.
    [*http://docs.autofac.org/en/Latest/*](http://docs.autofac.org/en/latest/)

-   **Cesaru členka Torre. Porovnávání životnosti služby kontejner IoC jádro ASP.NET s obory instance kontejner Autofac IoC**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/ Comparing-ASP-NET-Core-IOC-Service-LIFE-Times-and-autofac-IOC-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)

## <a name="implementing-the-command-and-command-handler-patterns"></a>Implementace vzorů příkaz a obslužná rutina příkazu

V příkladu DI prostřednictvím konstruktor uvedené v předchozí části se kontejner IoC vložení úložiště prostřednictvím konstruktor v třídě. Ale přesně kde se budou vloženy? V jednoduché webové rozhraní API (například mikroslužbu katalogu v eShopOnContainers) vložit je na úrovni řadiče MVC, v konstruktoru řadiče. Ale v této části počáteční kódu ( [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) třídy z Ordering.API služby v rámci eShopOnContainers), vkládání závislostí se provádí pomocí konstruktoru konkrétní příkaz Obslužná rutina. Dejte nám vysvětlují, jaké obslužná rutina příkazu je a proč ji používat.

Příkaz vzor nesouvisí vnitřně CQRS vzor, která byla zavedená dříve v tomto průvodci. CQRS má dvě strany. První oblast je dotazy, zjednodušené dotazy s pomocí [Dapper](https://github.com/StackExchange/dapper-dot-net) malých ORM, který je popsaný výše. Druhý oblast je příkazy, které jsou výchozím bodem pro transakce a vstupní kanál z mimo službu.

Jak znázorňuje obrázek 9-20, vzor je založena na přijímá příkazy ze strany klienta, je na základě pravidel modelu domény zpracování a nakonec uložením stavy s transakce.

![](./media/image21.png)

**Obrázek 9-20**. Podrobný pohled na příkazy nebo "transakcí" straně ve tvaru CQRS

### <a name="the-command-class"></a>Příkaz – třída

Příkaz je žádost o systému a provést akci, která změní stav systému. Příkazy jsou nutné a měla by být zpracována pouze jednou.

Vzhledem k tomu, že jsou příkazy závazné, mají obvykle název s příkazem imperativní chuť (například "vytvořit" nebo "aktualizovat") a může obsahují agregační typu, například CreateOrderCommand. Na rozdíl od události není příkaz faktu v minulosti; je pouze požadavek a proto může být odmítnuta.

Příkazy můžete pocházejí z uživatelského rozhraní v důsledku uživatele žádost o inicializaci nebo ze Správce procesu, když správce proces je odkazovat agregace k provedení akce.

Důležitou vlastností příkazu je, že ho měla by být zpracována pouze jednou podle jednoho příjemce. Je to proto, že je příkaz jednu akci nebo transakce, kterou chcete provést v aplikaci. Stejný příkaz pořadí vytváření například by nemělo zpracovat více než jednou. Toto je důležitý rozdíl mezi příkazy a události. Události může zpracovat více než jednou., protože mnoho systémy nebo mikroslužeb může být zajímá události.

Kromě toho je důležité, aby příkaz zpracovat pouze jednou v případě, že příkaz není idempotent. Příkaz je idempotent, pokud se Dal spustit několikrát beze změny výsledek, vzhledem k povaze příkaz nebo kvůli způsobu, jakým systém zpracovává příkaz.

Je vhodné vytvořit příkazech a aktualizuje idempotent, když má smysl v rámci vaší doméně obchodní pravidla a výstupních podmínek. Například pokud chcete použít stejný příklad, pokud z nějakého důvodu (logika opakovaných pokusů, hackerům, atd.) stejný příkaz CreateOrder dosáhne systému vícekrát, byste měli moct identifikovat ji a ujistěte se, nevytvářejte více objednávek. K tomu potřebujete připojit nějaký druh identity v konzoli operations a zjistit, jestli se příkaz nebo aktualizace již byla zpracována.

Odeslat příkaz na jednoho příjemce; Nepublikujte příkaz. Publikování je pro události integrace, které stavu faktu – něco došlo a může být zajímavé pro přijímače událostí. V případě událostí má vydavatele obavu, o kterých příjemci získat událost nebo co dělají ho. Ale události integrace jsou různé scénáře už zavedená v předchozích částech.

Příkaz je implementováno s třídu, která obsahuje pole dat nebo kolekcí se veškeré informace, které je nutné k provedení tohoto příkazu. Příkaz je zvláštní druh z dat přenosu objektu (DTO), který konkrétně slouží k žádosti o změny nebo transakce. Samotný příkaz vychází přesně informace potřebné pro příkaz a žádné další zpracování.

Následující příklad ukazuje zjednodušený CreateOrderCommand třídy. Toto je neměnné příkaz, který se používá v řazení mikroslužbu v eShopOnContainers.

```csharp
// DDD and CQRS patterns comment
// Note that it is recommended that yuo implement immutable commands
// In this case, immutability is achieved by having all the setters as private
// plus being able to update the data just once, when creating the object
// through the constructor.
// References on immutable commands:
// http://cqrs.nu/Faq
// https://docs.spine3.org/motivation/immutability.html
// http://blog.gauffin.org/2012/06/griffin-container-introducing-command-support/
// https://msdn.microsoft.com/en-us/library/bb383979.aspx
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

    public CreateOrderCommand(List<OrderItemDTO> orderItems, string city,
        string street,
        string state, string country, string zipcode,
        string cardNumber, string cardHolderName, DateTime cardExpiration,
        string cardSecurityNumber, int cardTypeId) : this()
    {
        _orderItems = orderItems;
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

V podstatě třída příkaz obsahuje všechna data, které potřebujete k provádění transakcí firmy pomocí objekty modelu domény. Proto jsou příkazy jednoduše datové struktury, které obsahují data jen pro čtení a žádné chování. Název příkazu označuje jeho účel. V mnoha jazycích, jako je C\#, příkazy jsou reprezentovány jako třídy, ale nejsou true třídy v tom smyslu, skutečně objektově orientovaný.

Jako další vlastnosti jsou příkazy nedá změnit, protože očekávané využití je, že jsou zpracovány přímo pomocí modelu domény. Není potřeba změnit během své předpokládané životnosti. V a C\# třída, lze dosáhnout neměnitelnosti nemá žádné setter nebo jiné metody, které změní vnitřní stav.

Například je pravděpodobně podobný z hlediska data pořadí, ve kterém chcete vytvořit třídu příkazu pro vytvoření pořadí, ale pravděpodobně není nutné provést stejné atributy. Například CreateOrderCommand nemá pořadí ID, protože ještě nebyl vytvořen pořadí.

Mnoho tříd příkaz může být jednoduchý, které vyžadují pouze několik polí o některé stavu, který je potřeba změnit. Který by byl tento případ Pokud měníte jenom stav pořadí z "proces v" na "placené" nebo "shipped" pomocí příkazu, který je podobný následujícímu:

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

Někteří vývojáři zvýšit jejich žádost objekty uživatelského rozhraní odděleně od jejich příkaz DTOs, ale který stačí preference. Je zdlouhavé oddělení se nevěnuje přidanou hodnotu a objekty jsou téměř úplně stejné tvaru. V eShopOnContainers, například příkazy pocházejí přímo ze strany klienta.

### <a name="the-command-handler-class"></a>Obslužná rutina příkazu – třída

Měli byste implementovat třídu obslužné rutiny konkrétní příkaz u každého příkazu. To je, jak funguje vzoru a je kde budete používat objektu command, objektů domény a objektů úložiště infrastruktury. Obslužná rutina je ve skutečnosti jádrem aplikační vrstvu z hlediska CQRS a DDD. Však veškerou logiku domény by měly být obsaženy v rámci domény třídy – v rámci agregační kořeny (kořenové entity), podřízených entit nebo [služby domény](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), ale není v rámci obslužná rutina, která je třída z aplikace vrstva.

Obslužná rutina příkazu přijme příkaz a získá výsledek z agregaci, která se používá. Výsledek musí být buď úspěšné provedení příkazu, nebo k výjimce. V případě výjimky musí být stav systému beze změny.

Obslužná rutina trvá obvykle následující kroky:

-   Obdrží objektu command, jako je DTO (z [zprostředkovatel](https://en.wikipedia.org/wiki/Mediator_pattern) nebo jiného objektu infrastruktury).

-   Ověřuje příkaz je neplatný (Pokud není ověřen zprostředkovatel).

-   Vytvoření instance agregační kořenové instanci, která je cílem aktuální příkaz.

-   V instanci agregační kořenové, získávání požadovaná data z tohoto příkazu se provede metodu.

-   Zůstává v nový stav agregace k související databázi. Tato poslední operace je aktuální transakci.

Se jeden agregace vycházejí z jeho agregační kořenové (kořenové entity) se obvykle týká obslužná rutina příkazu. Pokud více agregace by měl být ovlivněn příjem jeden příkaz, můžete použít události domény ke rozšíří stavy nebo akcí na více agregace

Zde důležité je, že při zpracování příkazu, veškerou logiku domény musí být uvnitř modelu domény (agregace) plně zapouzdřené a připravena k testování jednotek. Obslužná rutina funguje stejně jako způsob, jak získat modelu domény z databáze a jako poslední krok, říct vrstvě infrastruktury (úložiště) a zachová tak změny při změně modelu. Výhodou tohoto přístupu je, že můžete Refaktorovat logiku domény ve model domény izolované, plně zapouzdřené, bohaté, chování beze změny kódu v aplikaci nebo infrastruktury vrstvy, které jsou na úrovni vložení (obslužné rutiny příkazů, webového rozhraní API, úložiště atd.).

Při obslužné rutiny příkazů získat komplexní, se příliš mnoho logikou, který může být pach kódu. Zkontrolujte je a pokud najít logiku domény Refaktorovat kód přesunout této domény chování metody objektů domény (agregační kořenové a podřízené entity).

Jako příklad třídu obslužné rutiny příkaz následující kód ukazuje stejnou třídu CreateOrderCommandHandler, kterou jste viděli na začátku této kapitoly. V takovém případě jsme zdůraznily metody zpracování a operace s objekty nebo agregace modelu domény.

```csharp
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IBuyerRepository _buyerRepository;
    private readonly IOrderRepository _orderRepository;

    public CreateOrderCommandHandler(IBuyerRepository buyerRepository,
        IOrderRepository orderRepository)
    {
        if (buyerRepository == null)
        {
            throw new ArgumentNullException(nameof(buyerRepository));
        }
        if (orderRepository == null)
        {
            throw new ArgumentNullException(nameof(orderRepository));
        }

        _buyerRepository = buyerRepository;
        _orderRepository = orderRepository;
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        //
        // Additional code ...
        //
        // Create the Order aggregate root
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic
        // make sure that consistency is preserved across the whole aggregate
        var order = new Order(buyer.Id, payment.Id,
            new Address(message.Street,
            message.City, message.State,
            message.Country, message.ZipCode));

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                item.Discount, item.PictureUrl, item.Units);
        }

        // Persist the Order through the aggregate's repository
        _orderRepository.Add(order);
        return await _orderRepository.UnitOfWork.SaveChangesAsync();
    }
}
```

Toto jsou obslužná rutina příkazu by měl provést další kroky:

-   Pomocí příkazu dat pracovat s agregační kořenu metody a chování.

-   Interně v rámci objektů domény vyvolávání událostí domény transakce se spustí, ale který je transparentní z hlediska of obslužná rutina příkazu.

-   Pokud je na agregaci výsledek operace úspěšná, a po dokončení transakce, zvýšit obslužná rutina události integrace. (Toto může také vydána infrastruktury třídy jako úložiště.)

#### <a name="additional-resources"></a>Další zdroje

-   **Označit Seemann. V hranicích, jsou aplikace není objektově orientované**
    [*http://blog.ploeh.dk/2011/05/31/AttheBoundaries, orientované ApplicationsareNotObject /*](http://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/)

-   **Příkazy a události**
    [*http://cqrs.nu/Faq/commands-and-events*](http://cqrs.nu/Faq/commands-and-events)

-   **Obslužná rutina příkazu k čemu slouží? ** 
     [ *http://cqrs.nu/Faq/command-handlers*](http://cqrs.nu/Faq/command-handlers)

-   **Jimmy Bogard. Vzory příkaz domény – obslužné rutiny**
    [*https://jimmybogard.com/domain-command-patterns-handlers/*](https://jimmybogard.com/domain-command-patterns-handlers/)

-   **Jimmy Bogard. Vzory příkaz domény – ověření**
    [*https://jimmybogard.com/domain-command-patterns-validation/*](https://jimmybogard.com/domain-command-patterns-validation/)

## <a name="the-command-process-pipeline-how-to-trigger-a-command-handler"></a>Příkaz proces kanálu: spouštění obslužná rutina příkazu

Další otázka se postup vyvolání obslužná rutina příkazu. Ručně ji může volat z každého související řadiče ASP.NET Core. Ale že přístup budou příliš doplněná a není ideální.

Další dvě hlavní možnosti, které jsou doporučené možnosti, jsou:

-   Prostřednictvím artefakt vzor zprostředkovatel v paměti.

-   S frontu asynchronní zpráv mezi řadiče a obslužné rutiny.

### <a name="using-the-mediator-pattern-in-memory-in-the-command-pipeline"></a>Použití vzoru zprostředkovatel (v paměti) v příkazu kanálu

Jak znázorňuje obrázek 9 – 21, v rámci CQRS přístupu použijete inteligentního zprostředkovatel, podobně jako sběrnici v paměti, což je dostatečně inteligentní přesměrování na základě typu příkazu nebo DTO přijímání správné obslužná rutina. Jeden černé šipky mezi součástmi představují závislosti mezi objekty (v mnoha případech vložit prostřednictvím DI) s jejich odpovídající interakce.

![](./media/image22.png)

**Obrázek 9 – 21**. Použití vzoru zprostředkovatel v procesu v jednom mikroslužbu CQRS

Z důvodu, který pomocí vzoru zprostředkovatel smysl je, že v podnikových aplikacích zpracování požadavků můžete získat složitá. Chcete mít možnost Přidat otevřete počet mezi vyjímání otázky, jako je protokolování, ověření, auditování a zabezpečení. V těchto případech můžete spoléhat na kanál zprostředkovatel (najdete v části [zprostředkovatel vzor](https://en.wikipedia.org/wiki/Mediator_pattern)) pro zajištění způsob tyto doplňující chování nebo mezi vyjímání otázky.

Zprostředkovatel je objekt, který zapouzdří "jak" tohoto procesu: ho koordinuje spuštění na základě stavu, je vyvolána způsob obslužná rutina příkazu nebo datové části zadejte do obslužné rutiny. Pomocí součásti zprostředkovatel můžete použít mezi vyjímání obavy centralizované a transparentním způsobem použitím dekoratéry (nebo [kanálu chování](https://github.com/jbogard/MediatR/wiki/Behaviors) od zprostředkovatel v3). (Další informace najdete v tématu [Dekoratéra vzor](https://en.wikipedia.org/wiki/Decorator_pattern).)

Dekoratéry a chování jsou podobné [aspekt orientované programování (CHOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming), pouze u konkrétní proces kanálu spravuje komponentu zprostředkovatel. Aspekty v CHOP, které implementují mezi vyjímání otázky se používají na základě *aspekt weavers* podle zachycení volání objektu nebo vložit během kompilace. Obou přístupů typické CHOP se někdy říká, že fungují "jako"magic, protože není snadno zjistit, jak funguje CHOP svou práci. Při plánování práce s závažných problémech nebo oznámení chyb, může být obtížné ladění CHOP. Tyto dekoratéry chování jsou na druhé straně explicitní a použité jen v kontextu zprostředkovatel, tak ladění je mnohem víc předvídatelný a snadné.

Například v eShopOnContainers řazení mikroslužbu, implementovali jsme dva dekoratéry ukázka, [LogDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/LogDecorator.cs) třídy a [ValidatorDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/ValidatorDecorator.cs) třídy. Implementace dekoratéra je vysvětleno v další části. Všimněte si, že v budoucí verzi, bude eShopOnContainers migrovat do [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) a přesunout do [chování](https://github.com/jbogard/MediatR/wiki/Behaviors) místo použití dekorátory.

### <a name="using-message-queues-out-of-proc-in-the-commands-pipeline"></a>Pomocí fronty zpráv (out-of-proc) v příkazu kanálu

Další možnost je použít asynchronní zprávy na základě zprostředkovatelé nebo fronty zpráv, jak je znázorněno v obrázek 9 – 22. Tato možnost může být spojen s komponentu zprostředkovatel bezprostředně před obslužná rutina příkazu.

![](./media/image23.png)

**Obrázek 9 – 22**. Pomocí příkazů CQRS fronty zpráv (mimo proces a komunikaci mezi procesy)

Pomocí zprávy fronty přijmout, že můžete další příkazy zkomplikovat kanálu váš příkaz, protože budete pravděpodobně muset kanál rozdělit do dvou procesů připojené prostřednictvím fronty externí zpráv. Stále by měl použít pokud potřebujete mít lepší škálovatelnost a výkon podle asynchronní zasílání zpráv. Zvažte, že v případě obrázek 9 22, řadičem právě odešle příkaz zprávy do fronty a vrátí. Obslužné rutiny příkazů pak zpracování zpráv vlastním tempem. To znamená uvítali front – fronty zpráv vystupovat jako vyrovnávací paměť v případech hyper škálovatelnost je potřebné, například pro akcií nebo všechny další scénáře s k velkému počtu vstupní data.

Ale kvůli asynchronní povaha fronty zpráv, musíte zjistit, jak komunikaci s aplikací klienta o úspěchu nebo neúspěchu procesu příkaz. Platí pravidlo nikdy byste neměli používat "fire a zapomněli" příkazy. Každé obchodní aplikace je potřeba vědět, pokud příkaz byla úspěšně zpracována, nebo aspoň ověřit a přijmout.

Proto schopnost reagovat na klienta po ověření příkaz zprávu, která byla odeslána do asynchronní fronty přidá složitost k vašemu systému, ve srovnání se příkazu v procesu proces, který vrátí výsledek operace po spuštění transakce. Pomocí front, budete možná muset vrátit výsledek procesu příkaz prostřednictvím jiné operace výsledek zprávy, které se bude vyžadovat další součásti a vlastní komunikace v systému.

Kromě toho jsou asynchronní příkazy jednosměrný příkazů, které jsou v mnoha případech nemusí být potřeba, jak je vysvětleno v následující zajímavé výměny mezi Burtsev Alexey a Gregu malé v [online konverzace](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):

\[Burtsev Alexey\] najít velké množství kódu kde lidí používá asynchronní zpracování příkazu nebo jedním ze způsobů příkaz zasílání zpráv bez jakéhokoli důvodu Uděláte to tak (jejich nejsou prováděním dlouhé operace, budou nejsou provádění kódu externí asynchronní, se i nepřecházejí aplikace předěl, který má být pomocí sběrnice zpráv). Proč se zavést tento nepotřebné složitost? A ve skutečnosti, I nezaznamenali CQRS příklad kódu se blokování obslužné rutiny příkazů dosavadní práce, i když bude ve většině případů pracovat správně.

\[Gregu Young\] \[... \] příkaz asynchronní neexistuje, je ve skutečnosti jinou událost. Pokud musí Souhlasím, co můžete poslat mi a vyvolat událost, pokud nesouhlasím, už jste zobrazuje oznámení něco udělat. Je vám zobrazuje oznámení, které něco udělat. Tohle vypadá jako malého rozdílu v první, ale má mnoho dopad.

Asynchronní příkazy výrazně zvýšit složitost systému, protože neexistuje žádný jednoduchý způsob označující selhání. Proto asynchronní příkazy nedoporučují jiné než potřeby škálování požadavky nebo ve zvláštních případech při komunikaci interní mikroslužeb pomocí zasílání zpráv. V těchto případech je nutné vytvořit samostatné vytváření sestav a obnovení systému pro selhání.

V původní verzi eShopOnContainers jsme se rozhodli použít příkaz synchronní zpracování, spuštěné z požadavků HTTP a řídí vzoru zprostředkovatel. Který snadno umožňuje vrátit úspěch nebo selhání procesu, jako v [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) implementace.

V každém případě to by měl být na základě požadavků vaší aplikace nebo na mikroslužbu obchodní rozhodnutí.

## <a name="implementing-the-command-process-pipeline-with-a-mediator-pattern-mediatr"></a>Implementace příkaz proces kanálu pomocí vzoru zprostředkovatel (MediatR)

Jako ukázka provádění Tento průvodce navrhuje pomocí kanálu v procesu na základě vzoru zprostředkovatel k přijímání příkaz jednotky a směrování, v paměti, obslužné rutiny příkaz right. Průvodce také navrhne použití dekoratéry nebo [chování](https://github.com/jbogard/MediatR/wiki/Behaviors) k oddělení mezi vyjímání otázky.

Pro implementaci v .NET Core jsou více knihovny open-source dostupné které implementují vzoru zprostředkovatel. Knihovna používané v tomto průvodci se [MediatR](https://github.com/jbogard/MediatR) knihovny open-source (vytvořený Jimmy Bogard), ale může použít jiná možnost. MediatR je malý a jednoduchý knihovny, která umožňuje zpracování zpráv v paměti jako příkaz, při použití dekoratéry nebo chování.

Použití vzoru zprostředkovatel vám pomůže snížit párování a izolovat si nemuseli dělat starosti požadovaný práce při automatické připojování k obslužná rutina, která provádí svou práci – v takovém případě do obslužné rutiny příkazů.

Dalším důvodem dobrý k použití vzoru zprostředkovatel byl vysvětlené Jimmy Bogard při revizi této příručce:

Myslím, může být důležité zmínit, zde testování – poskytuje okno konzistentním změněnými do chování systému. V požadavku, odpověď na více systémů. Jsme zjistili tento aspekt velmi cenné v budově konzistentně chovají testy.

První dejte nám prohlédněte si kód řadiče ve skutečnosti použít objekt zprostředkovatel. Pokud nebyly používá zprostředkovatel objektu, musíte vložit všechny závislosti pro tento kontroler, třeba objekt protokolovacího nástroje a další. Konstruktor proto může být poměrně složitá. Na druhé straně Pokud chcete použít objekt zprostředkovatel, konstruktoru řadiče může být značnou měrou s několika závislosti místo velký počet závislostí, které byste měli Pokud jste měli jednu na operace vyjímání mezi, jako v následujícím příkladu:

```csharp
public class OrdersController : Controller
{
    public OrdersController(IMediator mediator,
        IOrderQueries orderQueries)
    // ...
```

Uvidíte, že zprostředkovatel poskytuje vyčištění a štíhlého konstruktor kontroleru webového rozhraní API. Kromě toho v rámci metody kontroleru kód odeslat příkaz k objektu zprostředkovatel je téměř jeden řádek:

```csharp
[Route("new")]
[HttpPost]
public async Task<IActionResult> CreateOrder([FromBody]CreateOrderCommand
    createOrderCommand)
{
    var commandResult = await _mediator.SendAsync(createOrderCommand);
    return commandResult ? (IActionResult)Ok() : (IActionResult)BadRequest();
}
```

Aby MediatR vědět třídy obslužná rutina příkazu budete muset registrovat zprostředkovatel třídy a třídy obslužné rutiny příkazů ve vašem kontejner IoC. Ve výchozím nastavení MediatR používá Autofac jako kontejner IoC, ale můžete také použít integrované kontejner IoC jádro ASP.NET nebo jiných kontejneru, nepodporuje MediatR.

Následující kód ukazuje, jak registrovat typy a příkazy pro zprostředkovatel při použití Autofac moduly.

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        builder.RegisterAssemblyTypes(typeof(IMediator).GetTypeInfo().Assembly)
            .AsImplementedInterfaces();
        builder.RegisterAssemblyTypes(typeof(CreateOrderCommand)
            .GetTypeInfo().Assembly)
            .As(o => o.GetInterfaces()
            .Where(i => i.IsClosedTypeOf(typeof(IAsyncRequestHandler<,>)))
            .Select(i => new KeyedService("IAsyncRequestHandler", i)));
        builder.RegisterGenericDecorator(typeof(LogDecorator<,>),
            typeof(IAsyncRequestHandler<,>), "IAsyncRequestHandler");

        // Other types registration
    }
}
```

Protože každý obslužná rutina příkazu implementuje rozhraní s obecné IAsyncRequestHandler&lt;T&gt; a poté zkontroluje RegisteredAssemblyTypes objektu obslužná rutina je propojovat s jeho obslužná rutina příkazu každý příkaz, protože, relace je uvedeno v třídě commandhandler – jako v následujícím příkladu:

```csharp
public class CreateOrderCommandHandler
  : IAsyncRequestHandler<CreateOrderCommand, bool>
{
```

Toto je kód, který příkazy koreluje s obslužné rutiny příkazů. Obslužná rutina je pouze jednoduchou třídu, ale dědí z RequestHandler&lt;T&gt;, a MediatR zajišťuje je volán s správné datové části.

## <a name="applying-cross-cutting-concerns-when-processing-commands-with-the-mediator-and-decorator-patterns"></a>Při zpracování příkazů vzory zprostředkovatel a Dekoratéra použití mezi vyjímání otázky

Neexistuje jeden krok: schopnost použít mezi vyjímání obavy zprostředkovatel kanálu. Můžete také zjistit na konci kód Autofac registrace modulu jak se registrují dekoratéra, konkrétně zadejte vlastní třídu LogDecorator.

Znovu si všimněte, že budoucí verzi systému eShopOnContainers se bude migrovat do [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) a přesunout do [chování](https://github.com/jbogard/MediatR/wiki/Behaviors) místo použití dekorátory.

Aby [LogDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/LogDecorator.cs) třídy mohou být provedena jako následující kód, který ukládá do protokolu informace o obslužná rutina se spouští a bez ohledu na jeho, jestli byla úspěšná.

```csharp
public class LogDecorator<TRequest, TResponse>
    : IAsyncRequestHandler<TRequest, TResponse>
    where TRequest : IAsyncRequest<TResponse>
{
    private readonly IAsyncRequestHandler<TRequest, TResponse> _inner;
    private readonly ILogger<LogDecorator<TRequest, TResponse>> _logger;

    public LogDecorator(
        IAsyncRequestHandler<TRequest, TResponse> inner,
        ILogger<LogDecorator<TRequest, TResponse>> logger)
    {
        _inner = inner;
        _logger = logger;
    }

    public async Task<TResponse> Handle(TRequest message)
    {
        _logger.LogInformation($"Executing command {_inner.GetType().FullName}");
        var response = await _inner.Handle(message);
        _logger.LogInformation($"Succeeded executed command{_inner.GetType().FullName}");
        return response;
    }
}
```

Právě implementací této třídy dekoratéra a architekturu kanál s ním všechny příkazy, které jsou zpracované pomocí MediatR protokolování informace o provádění.

EShopOnContainers řazení mikroslužbu platí také pro základní ověření, druhý dekoratéra [ValidatorDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/ValidatorDecorator.cs) třídu, která závisí na [FluentValidation](https://github.com/JeremySkinner/FluentValidation) knihovny, jak je znázorněno Následující kód:

```csharp
public class ValidatorDecorator<TRequest, TResponse>
    : IAsyncRequestHandler<TRequest, TResponse>
    where TRequest : IAsyncRequest<TResponse>
{
    private readonly IAsyncRequestHandler<TRequest, TResponse> _inner;
    private readonly IValidator<TRequest>[] _validators;

    public ValidatorDecorator(
        IAsyncRequestHandler<TRequest, TResponse> inner,
        IValidator<TRequest>[] validators)
    {
        _inner = inner;
        _validators = validators;
    }

    public async Task<TResponse> Handle(TRequest message)
    {
        var failures = _validators
            .Select(v => v.Validate(message))
            .SelectMany(result => result.Errors)
            .Where(error => error != null)
            .ToList();
            if (failures.Any())
            {
                throw new OrderingDomainException(
                $"Command Validation Errors for type {typeof(TRequest).Name}",
                new ValidationException("Validation exception", failures));
            }
            var response = await _inner.Handle(message);
        return response;
    }
}
```

Pak na základě [FluentValidation](https://github.com/JeremySkinner/FluentValidation) knihovna, kterou jsme vytvořili ověření dat předávaných s CreateOrderCommand, jako v následujícím kódu:

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
        RuleFor(command => command.CardExpiration).NotEmpty().Must(BeValidExpirationDate).
            WithMessage("Please specify a valid card expiration date");
        RuleFor(command => command.CardSecurityNumber).NotEmpty().Length(3);
        RuleFor(command => command.CardTypeId).NotEmpty();
        RuleFor(command => command.OrderItems).
            Must(ContainOrderItems).WithMessage("No order items found");
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

Můžete vytvořit další ověření. Toto je velmi vyčištění a elegantní způsob, jak implementovat vaše příkaz ověření.

Podobným způsobem může implementovat jiné dekoratéry pro další aspekty nebo mezi vyjímání aspekty, které chcete použít k příkazům při jejich zpracování.

#### <a name="additional-resources"></a>Další zdroje

##### <a name="the-mediator-pattern"></a>Zprostředkovatel vzor

-   **Zprostředkovatel vzor**
    [*https://en.wikipedia.org/wiki/Mediator\_vzor*](https://en.wikipedia.org/wiki/Mediator_pattern)

##### <a name="the-decorator-pattern"></a>Vzor dekoratéra

-   **Vzor dekoratéra**
    [*https://en.wikipedia.org/wiki/Decorator\_vzor*](https://en.wikipedia.org/wiki/Decorator_pattern)

##### <a name="mediatr-jimmy-bogard"></a>MediatR (Jimmy Bogard)

-   **MediatR.** Úložiště GitHub.
    [*https://github.com/jbogard/MediatR*](https://github.com/jbogard/MediatR)

-   **CQRS s MediatR a AutoMapper**
    [*https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/*](https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/)

-   **Umístí řadičů vyváženosti: příspěvky a příkazy. ** 
     [ *https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/*](https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/)

-   **Boji se mezi vyjímání otázky se zřetězením příkazů zprostředkovatel**
    [*https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/*](https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/)

-   **CQRS a REST: ideální doplněk**
    [*https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/*](https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/)

-   **Příklady MediatR kanálu**
    [*https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/*](https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/)

-   **Svislé řez testovací zařízení pro MediatR a ASP.NET Core**
    *<https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/>*

-   **Rozšíření MediatR pro vkládání závislostí Microsoft vydané**
    [*https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/*](https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/)

##### <a name="fluent-validation"></a>Fluent ověření

-   **Jirka Skinner. FluentValidation.** Úložiště GitHub.
    [*https://github.com/JeremySkinner/FluentValidation*](https://github.com/JeremySkinner/FluentValidation)

>[!div class="step-by-step"]
[Předchozí] (microservice-application-layer-web-api-design.md) [Další] (.. /Implement-resilient-Applications/index.MD)
