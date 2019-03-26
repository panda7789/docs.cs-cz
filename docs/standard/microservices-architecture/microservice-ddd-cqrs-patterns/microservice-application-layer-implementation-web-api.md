---
title: Implementace aplikační vrstvy mikroslužby pomocí webového rozhraní API
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Pochopení injektáž závislostí, zprostředkovatel vzory a jejich podrobnosti implementace v aplikační vrstvu webového rozhraní API.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: 72ed265284db9d112a0b1e3b966d206dd7f3d1cc
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2019
ms.locfileid: "58464889"
---
# <a name="implement-the-microservice-application-layer-using-the-web-api"></a>Implementace aplikační vrstvy mikroslužby pomocí webového rozhraní API

## <a name="use-dependency-injection-to-inject-infrastructure-objects-into-your-application-layer"></a>Pomocí vkládání závislostí injektovat objekty infrastruktury na úrovni aplikační vrstvy

Jak už bylo zmíněno dříve, aplikační vrstvu je možné implementovat jako součást artefaktu (sestavení), kterou vytváříte, například v projektu webového rozhraní API nebo projektu webové aplikace MVC. V případě mikroslužeb vytvořené pomocí ASP.NET Core aplikační vrstvu obvykle bude vaše knihovna webového rozhraní API. Pokud chcete oddělit, co se chystá v ASP.NET Core (jeho infrastruktury a řadičích) z uživatelského kódu vrstvy vlastní aplikace, může také umístit úrovni aplikační vrstvy v samostatné knihovně tříd, ale to je volitelné.

Například kód vrstvy aplikace pořadí mikroslužeb přímo implementují jako součást **Ordering.API** project (projekt webového rozhraní API ASP.NET Core), jako je uvedené v obrázek 7 – 23.

![Zobrazení Průzkumníka řešení Ordering.API mikroslužeb, zobrazuje podsložky ve složce aplikace: Chování, příkazy, DomainEventHandlers, IntegrationEvents, modely, dotazy a ověření.](./media/image20.png)

**Obrázek 7 – 23**. Aplikační vrstvy v projektu Ordering.API ASP.NET Core webového rozhraní API

ASP.NET Core zahrnuje jednoduchou [integrované kontejner IoC](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (reprezentovaný identifikátorem rozhraní IServiceProvider), který podporuje vkládání konstruktoru ve výchozím nastavení a ASP.NET zpřístupní určité služby prostřednictvím DI. ASP.NET Core používá termín *služby* pro všechny typy zaregistrujete, které budou vloženy prostřednictvím DI. Konfigurace kontejneru integrovaných služeb v ConfigureServices metody ve třídě spuštění vaší aplikace. Závislosti jsou implementované ve službách, které potřebuje typ a která se zaregistruje v kontejner IoC.

Obvykle je vhodné vložit závislosti, které implementují objekty infrastruktury. Velmi typické závislost vkládat je do úložiště. Ale může injektovat další infrastrukturu závislosti, které máte uzavřeny. Pro jednodušší implementace může injektovat přímo pracovní jednotky vzor objektu (objekt EF DbContext), protože je uvolněn objekt DBContext také implementace objektů trvalosti infrastruktury.

V následujícím příkladu vidíte, jak je .NET Core vkládá objekty požadované úložiště pomocí konstruktoru. Třída je obslužná rutina příkazu, což si probereme v další části.

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

Třída používá vložený úložiště k provedení transakcí a zachová tak změny stavu. Nezáleží, jestli je obslužná rutina příkazu, metodu kontroleru webového rozhraní API ASP.NET Core, třídy nebo [DDD aplikační službu](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/). Takže v konečném důsledku je jednoduchou třídu, která používá úložiště, domény entity a další aplikace koordinace způsobem, který je podobný obslužná rutina příkazu. Stejně jako u všech uvedených tříd jako v příkladu pomocí DI podle konstruktoru funguje vkládání závislostí.

### <a name="register-the-dependency-implementation-types-and-interfaces-or-abstractions"></a>Registrace závislosti implementace typy a rozhraní nebo odběrů

Než použijete objekty vloženými prostřednictvím konstruktory, musíte vědět, kde k registraci rozhraní a třídy, které vytvářejí objekty vloženy do vaší třídy aplikace prostřednictvím DI. (Například DI na základě konstruktoru, jak bylo uvedeno výše.)

#### <a name="use-the-built-in-ioc-container-provided-by-aspnet-core"></a>Použít integrované kontejner IoC poskytované ASP.NET Core

Když použijete integrovanou kontejner IoC poskytované ASP.NET Core, zaregistrujete typy, které chcete vložit v metodě ConfigureServices v souboru Startup.cs, stejně jako v následujícím kódu:

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

Nejběžnější vzor registrace typů v kontejner IoC se zaregistrujte pár typy – rozhraní a jeho souvisejících implementace třídy. Pokud požádáte o objektu z kontejner IoC prostřednictvím jakéhokoli konstruktoru, pak požadujete objekt typu rozhraní. Například v předchozím příkladu, poslední řádek uvádí, že když některé z vašich konstruktory jsou závislé na IMyCustomRepository (rozhraní nebo abstraktní), vloží kontejner IoC instance implementace MyCustomSQLServerRepository Třída.

#### <a name="use-the-scrutor-library-for-automatic-types-registration"></a>Použití knihovny Scrutor pro typy automatické registrace

Při použití DI v .NET Core, můžete chtít zkontrolovat sestavení a jeho typy zařízení automaticky zaregistrovalo podle konvence. Tato funkce není aktuálně k dispozici v ASP.NET Core. Můžete však použít [Scrutor](https://github.com/khellang/Scrutor) knihovny, který. Tento přístup je vhodné, když máte desítky typy, které musí být zaregistrovaní v kontejnerech IoC.

#### <a name="additional-resources"></a>Další zdroje

- **Matthew King. Registrace služby Scrutor** \
  [https://www.mking.net/blog/registering-services-with-scrutor](https://www.mking.net/blog/registering-services-with-scrutor)

- **Kristian Hellang. Scrutor.** Úložiště GitHub. \
  [https://github.com/khellang/Scrutor](https://github.com/khellang/Scrutor)

#### <a name="use-autofac-as-an-ioc-container"></a>Použít Autofac jako kontejner IoC

Můžete také používat další technologie IoC kontejnery a zapojte do kanálu ASP.NET Core, stejně jako v pořadí mikroslužeb v aplikaci eShopOnContainers, který používá [Autofac](https://autofac.org/). Při použití Autofac zaregistrujete obvykle typy prostřednictvím modulů, které umožňují rozdělit typy registrace mezi více souborů v závislosti na tom, kde vaše typy jsou, stejně jako jste mohli distribuovat napříč více knihoven tříd typů aplikací.

Například tady je [modul aplikace Autofac](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) pro [Ordering.API webového rozhraní API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) projekt s typy, které se chcete vložit.

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

Autofac má také funkce, která [kontrolovat sestavení a zaregistrujte typy podle konvence název](https://autofac.readthedocs.io/en/latest/register/scanning.html).

Proces registrace a Koncepty jsou velmi podobně jako typy můžete zaregistrovat pomocí integrované technologie ASP.NET Core IoC kontejneru, ale syntaxe při použití Autofac je trochu jiná.

V příkladu kódu je zaregistrovaný abstrakce IOrderRepository spolu s implementací třídy OrderRepository. To znamená, že deklarující konstruktor je závislost prostřednictvím abstrakce IOrderRepository nebo rozhraní, kontejner IoC vloží instanci třídy OrderRepository.

Typ oboru instance určuje způsob sdílení instance mezi požadavky pro stejnou službu nebo závislost. Po odeslání žádosti pro závislost na kontejner IoC může vrátit následující:

- Jedna instance pro každý obor životnost (podle kontejner ASP.NET Core IoC jako *obor*).

- Nové instance za závislosti (podle kontejner ASP.NET Core IoC jako *přechodné*).

- Jedna instance sdílené ve všech objektech pomocí kontejner IoC (podle kontejner ASP.NET Core IoC jako *singleton*).

#### <a name="additional-resources"></a>Další zdroje

- **Úvod do injektáž závislostí v ASP.NET Core** \
  [https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection)

- **Autofac.** Oficiální dokumentaci. \
  [http://docs.autofac.org/en/latest/](http://docs.autofac.org/en/latest/)

- **Porovnání životnosti služby kontejner ASP.NET Core IoC s obory instance kontejner Autofac IoC - Cesarovi de la Torre.** \
  [https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)

## <a name="implement-the-command-and-command-handler-patterns"></a>Implementace vzorů příkazu a obslužná rutina příkazu

V příkladu DI prostřednictvím konstruktoru je znázorněno v předchozí části se kontejner IoC vkládá úložišť pomocí konstruktoru ve třídě. Ale přesně ve kterém byly jejich vloží? V jednoduché webové rozhraní API (například mikroslužeb katalogu v aplikaci eShopOnContainers) můžete do něj vložit na úrovni řadiče MVC, v konstruktoru řadič, v rámci kanálu požadavku ASP.NET Core. Nicméně v počáteční kód v této části ( [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) třídy ze služby Ordering.API v aplikaci eShopOnContainers), injektáž závislostí se provádí prostřednictvím konstruktoru ke konkrétnímu příkazu. Obslužná rutina. Dejte nám vysvětlují, jaké obslužná rutina příkazu je a proč by měli používat.

Příkaz vzor se týká vnitřně model CQRS, která byla zavedena dříve v tomto průvodci. CQRS se dvěma stranami. V první oblasti je dotazů pomocí zjednodušené dotazy s [Dapperem](https://github.com/StackExchange/dapper-dot-net) micro ORM, které bylo vysvětleno dříve. Druhé oblasti se příkazy, které jsou výchozím bodem pro transakce a vstupním kanálem z mimo službu.

Jak je znázorněno v obrázek 7 – 24, vzorek je založen na přijímání příkazy ze strany klienta zpracování je na základě pravidel modelu domény a nakonec uchování států s transakcemi.

![Vyšší úroveň tohoto straně zápisy v modelu CQRS: Uživatelské rozhraní aplikace odešle příkaz prostřednictvím rozhraní API, která získá commandhandler –, který závisí na doménový model a infrastrukturu k aktualizaci databáze.](./media/image21.png)

**Obrázek 7 – 24**. Souhrnný přehled příkazů nebo "transakcí na straně" ve vzoru modelu CQRS

### <a name="the-command-class"></a>Třídy příkazů

Příkaz je žádost o systému a provést akci, která změní stav systému. Příkazy jsou nezbytnými předpoklady a mají být zpracována právě jednou.

Protože příkazy jsou požadavky, jsou obvykle pojmenován s operací imperativní náladu (například "vytvořit" nebo "" aktualizace) a jejich může taky obsahovat typ agregace, jako je například CreateOrderCommand. Na rozdíl od události není příkaz faktů z minulosti; pouze žádost a proto může být odmítnut.

Příkazy můžou pocházet z uživatelského rozhraní v důsledku uživatele požadavek na zahájení nebo ze Správce procesu při procesu manager směruje agregace k provedení akce.

Důležitou vlastnost příkazu je, že ji by měl být zpracovány pouze jednou jednoho příjemce. Je to proto, že příkaz je transakce, kterou chcete provést v aplikaci a jednu akci. Příklad příkazu pro vytvoření stejné pořadí nemají být zpracovány více než jednou. Toto je důležitý rozdíl mezi příkazy a události. Události se dají zpracovávat více než jednou, protože velký počet systémů nebo mikroslužeb může zajímat události.

Kromě toho je důležité, že příkaz zpracovat pouze jednou v případě, že příkaz není idempotentní. Příkaz je idempotentní, pokud jej lze spustit více než jednou beze změny výsledek, vzhledem k povaze příkazu nebo kvůli způsobu, jakým systém zpracovává příkaz.

Je dobrým zvykem, aby vaše příkazy a aktualizuje idempotentní, když má smysl v rámci vaší domény obchodní pravidla a výstupních podmínek. Například pokud chcete použít stejný příklad, pokud z nějakého důvodu (logiku opakování, hacking atd.) stejný příkaz CreateOrder dosáhne váš systém více než jednou, byste měli moct identifikovat a zajištění nevytvářejte více objednávek. K tomu potřebujete připojit nějaký druh identity v konzoli operations a zjistit, jestli je příkaz nebo aktualizace již byla zpracována.

Odeslat příkaz do jednoho příjemce; příkaz není publikována. Publikování je pro události, které uvádějí faktu, něco se stalo a může být zajímavé pro přijímače událostí. V případě události vydavatel nemá žádné obavy, o které příjemce získat události nebo co dělají to. Ale domény nebo integrace událostí jsou různé scénáře už zavedené v předchozích částech.

Příkaz je implementováno třídou, která obsahuje datová pole nebo kolekce se všechny informace, které je potřeba za účelem provedení tohoto příkazu. Příkaz je zvláštní druh z Data přenosu objektu (DTO), který konkrétně slouží k vyžádání změn nebo transakce. Podle přesně, který je nezbytný pro zpracování příkazu a žádné další informace o příkazu samého.

Následující příklad ukazuje zjednodušený CreateOrderCommand třídy. Toto je neměnný příkaz, který se používá v pořadí mikroslužeb v aplikaci eShopOnContainers.

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
// https://msdn.microsoft.com/library/bb383979.aspx
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

V podstatě třídu příkazu obsahuje veškerá data, které potřebujete pro provádění obchodní transakce s použitím objektů modelu domény. Příkazy jsou proto jednoduše datové struktury, které obsahují data jen pro čtení a žádné chování. Název příkazu označuje její účel. V mnoha jazycích jako C#, příkazy jsou reprezentovány jako třídy, ale není true třídy ve smyslu reálné objektově orientovaný.

Jako další vlastnost příkazy jsou neměnné, protože očekávané použití je, že jsou zpracovány přímo pomocí modelu domény. Není potřeba změnit během jejich předpokládané životního cyklu. V C# třídy, neměnnosti můžete dosáhnout tím, že všechny metody setter nebo jiné metody, které se mění vnitřního stavu.

Mějte, že pokud určené pro instalaci nebo očekávat příkazy se obejde procesu serializace/deserializing, vlastnosti musí mít privátní metody setter a `[DataMember]` (nebo `[JsonProperty]`) atribut, jinak nebudou moci deserializátor rekonstrukce objektu v cílovém umístění s požadovanými hodnotami.

Například třída příkaz pro vytvoření objednávky je pravděpodobně podobný z hlediska data pořadí, ve kterém chcete vytvořit, ale pravděpodobně není nutné stejné atributy. Například CreateOrderCommand nemá ID objednávky, protože ještě nebyl vytvořen pořadí.

Mnoho příkaz třídy mohou být jednoduché, které vyžadují jenom několik polí o některé stavy, které je potřeba změnit. Který by byl tento případ Pokud měníte pouze stav objednávky z "v procesu" k "placené" nebo "dodán" pomocí příkazu, který je podobný následujícímu:

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

Některé vývojář podá žádost objekty uživatelského rozhraní nezávisle na jejich DTO příkaz, ale to je jenom pár předvoleb. Je únavné oddělení se nevěnuje přidanou hodnotu a objekty jsou téměř přesně stejný tvar. V aplikaci eShopOnContainers, například některé příkazy pocházejí přímo ze strany klienta.

### <a name="the-command-handler-class"></a>Třída obslužná rutina příkazu

Měli byste implementovat třídu obslužné rutiny konkrétní příkaz pro každý příkaz. To je, jak funguje vzor a je, kde budete používat objekt příkazu, doménových objektů a objektů úložiště infrastruktury. Obslužná rutina příkazu je ve skutečnosti srdce aplikační vrstvu z hlediska modelu CQRS a DDD. Ale veškerou logiku domény by měly být obsaženy v rámci doménové třídy – v rámci agregace kořeny (kořenové entity), podřízené entity, nebo [služby domain services](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), ale není v rozsahu obslužnou rutinu příkazu, což je třída z aplikace vrstva.

Třída obslužná rutina příkazu nabízí silné odrazový můstek tak, jak dosáhnout Princip jednoho odpovědnost (SRP) uvedené v předchozí části.

Obslužná rutina příkazu přijímá příkazu a získá výsledek z agregace, který se používá. Výsledek by měl být úspěšné provedení příkazu nebo výjimku. V případě výjimky by měl být stav systému beze změny.

Obslužná rutina příkazu přijímá obvykle následující kroky:

- Přijímá objekt příkazu, jako je objekt DTO (z [zprostředkovatel](https://en.wikipedia.org/wiki/Mediator_pattern) nebo jiný objekt infrastruktury).

- Ověří, že příkaz je neplatný (Pokud není ověřen zprostředkovatel).

- Vytvoření instance agregačních kořenové instanci, která je cílem aktuální příkaz.

- Metoda se provede na agregační kořenové instanci, získávání požadovaná data z tohoto příkazu.

- Přenese nový stav agregace do jeho související databáze. Tento poslední operaci je aktuální transakci.

Obvykle obslužná rutina příkazu se zabývá jedné agregace využitím agregační kořenem (Kořenová entita). Pokud více agregace by měly mít vliv příjem jediný příkaz, můžete použít domény události šíření stavy nebo akce napříč více agregací.

Důležitý bod je, že při zpracování příkazu veškerou logiku domény by měl být uvnitř doménový model (agregace), plně zapouzdřený a je připravený k testování částí. Obslužná rutina příkazu funguje stejně jako způsob, jak získat doménový model z databáze a jako poslední krok, abyste řekněte vrstvě infrastruktury (úložiště) a zachová tak změny po změně modelu. Výhodou tohoto přístupu je, že jste logiku domény v modelu domény izolované, plně zapouzdřený, bohatě vybaveným a chování Refaktorujte beze změn kódu v aplikaci nebo vrstev infrastruktury, které jsou na úrovni vložení (obslužné rutiny příkazů, webové rozhraní API, úložiště atd.).

Při získání složité a příliš mnoho logiku, která může být pach kód obslužné rutiny příkazů. Seznamte se s nimi a pokud najdete logiku domény Refaktorujte kód pro přesun tohoto chování domény do metody doménových objektů (agregační kořenové a podřízené entity).

Jako příklad třídy obslužné rutiny příkazu následující kód ukazuje stejné CreateOrderCommandHandler třídy, které jste viděli na začátku této kapitole. V tomto případě chceme metody zpracování a operace s objekty modelu domény/agregací.

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

Jedná se obslužná rutina příkazu by měl provést další kroky:

- Pomocí příkazu dat můžete pracovat s agregační kořenové metody a chování.

- Interně v rámci objektů domény vyvolat události domény provádí transakce, ale je transparentní z hlediska of obslužná rutina příkazu.

- Pokud výsledek operace agregace je úspěšné a po dokončení transakce, vyvolat události integrace. (Toto může být také navýšit tak, že infrastruktura třídy typu úložiště.)

#### <a name="additional-resources"></a>Další zdroje

- **Označit Seemann. Za hranice jsou aplikace, ne objektově orientované** \
  [https://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/](https://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/)

- **Příkazy a události** \
  [http://cqrs.nu/Faq/commands-and-events](http://cqrs.nu/Faq/commands-and-events)

- **Obslužná rutina příkazu k čemu slouží?** \
  [http://cqrs.nu/Faq/command-handlers](http://cqrs.nu/Faq/command-handlers)

- **Jimmy Bogard. Příkaz vzory domény – obslužné rutiny** \
  [https://jimmybogard.com/domain-command-patterns-handlers/](https://jimmybogard.com/domain-command-patterns-handlers/)

- **Jimmy Bogard. Příkaz vzory domény – ověření** \
  [https://jimmybogard.com/domain-command-patterns-validation/](https://jimmybogard.com/domain-command-patterns-validation/)

## <a name="the-command-process-pipeline-how-to-trigger-a-command-handler"></a>Proces kanálu příkazu: jak aktivovat obslužná rutina příkazu

Další otázkou je postup vyvolají obslužnou rutinu příkazu. Ručně ji lze volat z každého souvisejícími řadiče ASP.NET Core. Ale, že přístup budou příliš s velkou provázaností a není ideální.

Další dvě hlavní možnosti, které jsou doporučené možnosti jsou:

- Prostřednictvím vzoru artefakt zprostředkovatel v paměti.

- S asynchronní fronty zpráv, mezi řadiče a obslužné rutiny.

### <a name="use-the-mediator-pattern-in-memory-in-the-command-pipeline"></a>Zprostředkovatel model (v paměti) se používá v příkazu kanálu

Jak je znázorněno v obrázek 7 – 25, v přístup modelu CQRS pomocí inteligentních zprostředkovatel, podobně jako na Service bus v paměti, který je dostatečně inteligentní, přesměrovat na obslužnou rutinu správné příkaz na základě typu příkazu nebo objekt DTO přijímají. Jeden černé šipky mezi komponentami představují závislosti mezi objekty (v mnoha případech se vloží prostřednictvím DI) s jejich související interakce.

![Přiblížit na předchozím obrázku: kontroler ASP.NET Core odešle příkaz MediatR pro příkaz kanálu, aby dostanou do odpovídajícího popisovače.](./media/image22.png)

**Obrázek 7 – 25**. Použití vzoru zprostředkovatel v procesu v jedné mikroslužbě CQRS

Důvod, proč pomocí vzoru zprostředkovatel dává smysl je, že v oddílu podnikové aplikace, zpracování požadavků dostat složité. Chcete mít možnost přidávat otevřít počet vyskytující aspekty, jako je protokolování, ověření, auditování a zabezpečení. V těchto případech se můžete spolehnout na kanálu zprostředkovatel (naleznete v tématu [zprostředkovatel vzor](https://en.wikipedia.org/wiki/Mediator_pattern)) můžete poskytnout způsob pro tyto dodatečné chování nebo vyskytující aspekty.

Zprostředkovatel je objekt, který zapouzdřuje "jak" tohoto procesu: koordinuje spuštění na základě stavu, je vyvolána obslužná rutina příkazu způsob nebo datové části zadejte do obslužné rutiny. Pomocí součásti zprostředkovatel můžete použít vyskytující aspekty centralizované a transparentním způsobem použitím dekoratéry (nebo [kanálu chování](https://github.com/jbogard/MediatR/wiki/Behaviors) protože [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0)). Další informace najdete v tématu [Dekoratér vzor](https://en.wikipedia.org/wiki/Decorator_pattern).

Dekorátory a chování jsou podobné [aspekt orientované programování (CHOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming)pouze u konkrétní proces kanálu spravované komponentou zprostředkovatel. V CHOP aspekty, které implementují vyskytující aspekty se používají na základě *aspekt weavers* vložený v době kompilace nebo podle zachycení volání objektu. Oba přístupy typické CHOP se někdy říká, že fungují "jako magic," protože se nejedná snadno zjistit, jak CHOP provede svou práci. Při zpracování komplexnějších závažných problémech nebo oznámení chyb, může být obtížné ladit CHOP. Tyto dekoratéry/chování na druhé straně jsou explicitní a použité pouze v kontextu zprostředkovatel, takže ladění je mnohem více předvídatelný a snadno.

Například v aplikaci eShopOnContainers, řazení mikroslužeb, implementovali jsme dvě ukázkové chování [LogBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) třídy a [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) třídy. Implementace chování je vysvětlené v následující části zobrazující, jak aplikaci eShopOnContainers používá [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) [chování](https://github.com/jbogard/MediatR/wiki/Behaviors).

### <a name="use-message-queues-out-of-proc-in-the-commands-pipeline"></a>Zpráva fronty (z mimoprocesovou) v kanálu příkazu

Další volbou je použití asynchronních zpráv na základě zprostředkovatele nebo fronty zpráv, jak je znázorněno v obrázek 7 – 26. Tato možnost může být spojen s součásti zprostředkovatel bezprostředně před obslužná rutina příkazu.

![Kanál příkazu může být zpracována fronty zpráv vysoká dostupnost pro doručení příkazy do odpovídajícího popisovače.](./media/image23.png)

**Obrázek 7-26**. Pomocí příkazů modelu CQRS fronty zpráv (mimo procesu nebo komunikaci mezi procesy)

Pomocí zpráv fronty potvrďte, že můžete dále příkazy zkomplikovat váš příkaz kanálu, protože budete pravděpodobně muset rozdělit kanál na dva procesy připojené prostřednictvím fronty zpráv externí. Pořád by měl použít potřebujete mít lepší škálovatelnost a výkon podle asynchronní zasílání zpráv. Vezměte v úvahu, že v případě obrázek 7-26, kontroler právě odešle příkaz zprávy ve frontě a vrátí. Potom obslužné rutiny příkazů zpracování zpráv svým vlastním tempem. To znamená úžasných výhod fronty: Fronta zpráv může fungovat jako vyrovnávací paměť v případech, když hyper škálovatelnost je potřeba, například akcie nebo všechny další scénáře s vysokou objemu příchozích dat.

Ale vzhledem k asynchronní povaze fronty zpráv, musíte vymyslet, jak ke komunikaci s klientskou aplikací o úspěch nebo neúspěch zpracování příkazu. Zpravidla nikdy byste neměli používat příkazy "vypal a zapomeň". Každé obchodní aplikace potřebuje vědět, pokud příkaz byl úspěšně zpracována, nebo aspoň ověří a přijmout.

Díky tomu se nebudou moct reagovat na klienta po ověření zprávou příkazu, která byla odeslána do fronty služby asynchronní zvyšuje složitost k vašemu systému, než příkaz v procesu proces, který vrátí výsledek operace po spuštění transakce. Použití front, můžete potřebovat k vrácení výsledku procesu příkaz prostřednictvím jiné operace výsledek zprávy, které se bude vyžadovat další součásti a vlastní komunikační ve vašem systému.

Kromě toho jsou jednosměrná příkazy, které v mnoha případech nemusí být potřeba, jak je vysvětleno v následující zajímavé exchange mezi Burtsev Alexey a Grega Younga: v asynchronní příkazy [online konverzace](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):

> \[Burtsev Alexey\] můžu najít velké množství kódu, pokud uživatelé používají asynchronní zpracování příkazu nebo jedním ze způsobů zasílání zpráv bez z jakéhokoli důvodu k tomu příkaz (nejedná se některé dlouhá operace, nejsou provádění externí asynchronní kód, jsou i nepřecházejí aplikace předěl, který má být pomocí sběrnice zpráv). Proč přinášejí tento zbytečné složitosti A ve skutečnosti, můžu nezaznamenali příklad kódu modelu CQRS se blokování obslužné rutiny příkazů doposud, i když bude správně fungovat ve většině případů.
>
> \[Grega Younga\] \[... \] asynchronní příkaz neexistuje, je ve skutečnosti jiné události. Pokud musí přijmout, co můžete poslat mi a vyvolat událost v případě nesouhlasím, už nejsou vám sděluje mi něco \[tedy není příkaz\]. Jedná o vás uvádí něco udělat. Vypadá to, že jako malého rozdílu v první, ale to má vliv na mnoho.

Asynchronní příkazy zvyšuje složitost systému, protože neexistuje jednoduchý způsob k označení selhání. Proto asynchronní příkazy nedoporučují jiné než potřeby škálování požadavky nebo ve zvláštních případech při komunikaci interní mikroslužeb pomocí zasílání zpráv. V těchto případech je třeba navrhnout samostatného systému generování sestav a obnovení pro chyby.

V počáteční verzi aplikaci eShopOnContainers jsme se rozhodli použít synchronní příkaz zpracování, spuštěné z požadavků HTTP a využitím vzor zprostředkovatel. Který snadno umožňuje vrátit úspěch nebo selhání procesu, jako [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) implementace.

V každém případě je třeba rozhodnutí podle firemních potřeb vaší aplikace nebo na mikroslužbách.

## <a name="implement-the-command-process-pipeline-with-a-mediator-pattern-mediatr"></a>Implementujte proces kanálu příkazu se vzorem, který zprostředkovatel (MediatR)

Jako ukázku implementace Tento průvodce navrhuje pomocí kanálu v procesu založena na vzoru zprostředkovatel ingestování příkaz jednotky a směrování příkazů v paměti, obslužné rutiny příkaz right. V průvodci rovněž navrhuje použití [chování](https://github.com/jbogard/MediatR/wiki/Behaviors) aby bylo možné oddělit vyskytující aspekty.

Pro implementaci v .NET Core jsou více knihoven open-source k dispozici, které implementují vzor zprostředkovatel. Knihovny používané v tomto průvodci se [MediatR](https://github.com/jbogard/MediatR) open source knihovny (vytvořené Jimmy Bogard), ale můžete použít jiný přístup. MediatR je malý a jednoduchý knihovnu, která umožňuje zpracovávat zprávy v paměti jako příkaz, při použití dekoratéry nebo chování.

Pomocí vzoru zprostředkovatel vám pomůže snížit párování a k izolování obavy požadovanou práci, ale automatické připojení k obslužné rutině, který provádí tuto práci – v takovém případě do obslužné rutiny příkazů.

Jiné dobrý důvod, proč použití vzoru zprostředkovatel byl vysvětlené Jimmy Bogard při kontrole tohoto průvodce:

> Myslím, že je zde testování za zmínku – obsahuje vylepšení vzhledu konzistentní okno na chování vašeho systému. V požadavku, odpověď na více instancí. Zjistili jsme tento aspekt poměrně cenné ve vytváření chová konzistentně testy.

Nejprve Podívejme se na řadiče WebAPI ukázky ve skutečnosti použít objekt zprostředkovatel. Pokud jste nepoužili zprostředkovatel objektu, je třeba vložit všechny závislosti pro tento kontroler, například objekt protokolovacího nástroje a další. Konstruktor proto může být poměrně složitá. Na druhé straně Pokud použijete objekt zprostředkovatel, konstruktor řadiče může být mnohem jednodušší, pomocí jenom pár mdildll velký počet závislostí, pokud jste měli jeden do každého vyskytující operace, jako v následujícím příkladu:

```csharp
public class MyMicroserviceController : Controller
{
    public MyMicroserviceController(IMediator mediator,
                                    IMyMicroserviceQueries microserviceQueries)
    // ...
```

Uvidíte, že zprostředkovatel poskytuje přehledné a Štíhlá konstruktor kontroleru webového rozhraní API. Kromě toho v metodách kontroleru, je kód odeslat příkaz k objektu zprostředkovatel téměř jeden řádek:

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

### <a name="implement-idempotent-commands"></a>Implementace idempotentní příkazy

V **aplikaci eShopOnContainers**, pokročilejší příklad než výše posílá CreateOrderCommand objekt z mikroslužeb řazení. Ale protože je o něco složitější obchodní proces objednávání a v našem případě ve skutečnosti spustí v košíku mikroslužeb, tato akce odeslání CreateOrderCommand objektu se provádí z obslužné rutiny události integrace s názvem > UserCheckoutAcceptedIntegrationEvent.cs] (https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) místo jednoduchých řadiče WebAPI volat z klientské aplikace jako v předchozím příkladu jednodušší.

Akce odeslání příkazu MediatR je však poměrně podobné, jak je znázorněno v následujícím kódu.

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

Tento případ ale také trochu blíže advanced, protože jsme také implementace idempotentní příkazy. Proces CreateOrderCommand by měly být idempotentní, takže pokud stejná zpráva pochází z důvodu z jakéhokoli důvodu, třeba opakovaných pokusů, duplicitní přes síť, stejné pořadí business se zpracuje jenom jednou.

Toto je implementováno obchodní příkazy zabalit (v tomto případě CreateOrderCommand) a vloží jej do obecného IdentifiedCommand, což je sledován pomocí funkce ID každé zprávy přicházející přes síť, která má být idempotentní.

V následujícím kódu uvidíte, že IdentifiedCommand není nic jiného než objekt DTO se a ID plus zabalenou obchodní objekt příkazu.

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

Potom commandhandler – pro IdentifiedCommand s názvem [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs) bude v podstatě zkontrolujte, jestli ID už jako část zprávy již existuje v tabulce. Pokud již existuje, příkaz nebude zpracovat znovu, takže se chová jako příkaz idempotentní. Že kód infrastruktury provádí `_requestManager.ExistAsync` volání metody níže.

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

Vzhledem k tomu, že IdentifiedCommand lze chápat jako obchodní příkaz obálky, když firmy příkazu je potřeba zpracovat, protože se nejedná o opakované Id, potom přebírá tento příkaz vnitřní firmy a znovu odešle zprostředkovatel, stejně jako v poslední části kódu uvedeného výše uvedený spuštění `_mediator.Send(message.Command)`, z [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs).

Pokud to provedete, se propojit a spustit příkaz obslužnou rutinu obchodní, v tomto případě, [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) jak je znázorněno v následujícím kódu, kterou je spuštěna transakce v databázi řazení.

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

### <a name="register-the-types-used-by-mediatr"></a>Registrace typů používaných modulem MediatR

Aby MediatR zajímat vaší třídy obslužné rutiny příkazů budete muset zaregistrovat zprostředkovatel třídy a třídy obslužné rutiny příkazů v kontejneru IoC. Ve výchozím nastavení MediatR používá jako kontejner IoC Autofac, ale můžete použít také předdefinované kontejner ASP.NET Core IoC nebo jiném kontejneru, podporuje MediatR.

Následující kód ukazuje, jak registrovat typy a příkazy pro zprostředkovatel při používání Autofac modulů.

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

Toto je umístění "všechno děje" s MediatR.

Protože každá obslužná rutina příkazu implementuje obecné `IAsyncRequestHandler<T>` rozhraní, při registraci sestavení, tento kód zaregistruje k `RegisteredAssemblyTypes` všechny typy označeny jako `IAsyncRequestHandler` při vztahující se `CommandHandlers` s jejich `Commands`, Děkujeme na vztah uvedenými v `CommandHandler` třídy, jako v následujícím příkladu:

```csharp
public class CreateOrderCommandHandler
  : IAsyncRequestHandler<CreateOrderCommand, bool>
{
```

To je kód, který souvisí s obslužné rutiny příkazů příkazy. Obslužná rutina je pouze jednoduchou třídu, ale dědí z `RequestHandler<T>`, kde T je typ příkazu, a zajišťuje MediatR vyvolání správné datová část (příkaz).

## <a name="apply-cross-cutting-concerns-when-processing-commands-with-the-behaviors-in-mediatr"></a>Při zpracování příkazů s chováním v MediatR platí vyskytující aspekty

Existuje ještě jedna věc: nebudou moct použít vyskytující aspekty do kanálu zprostředkovatel. Můžete také zobrazit na konci kód Autofac registrace modulu jak registruje typ chování, konkrétně, vlastní LoggingBehavior třídy a třídy ValidatorBehavior. Ale můžete přidat další vlastní chování, příliš.

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

Že [LoggingBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) třídy je možné implementovat jako následující kód, který ukládá do protokolu informace o obslužná rutina příkazu prováděný a bez ohledu na to, zda byla úspěšná.

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

Právě implementací této chování třídy a tak, že zaregistrujete v kanálu (v MediatorModule výše) všechny příkazy, které jsou zpracovány prostřednictvím MediatR protokolování informací o spuštění.

Aplikaci eShopOnContainers řazení mikroslužeb platí také druhý chování pro základní ověření [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) třídu, která se spoléhá na [FluentValidation](https://github.com/JeremySkinner/FluentValidation) knihovny, jak je znázorněno Následující kód:

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

Chování zde je vyvolání výjimky, pokud se ověření nezdaří, ale může také vrátit objekt výsledku, obsahující výsledek příkazu, pokud byla úspěšná nebo ověření zprávy v případě, že se nepovedlo. To by pravděpodobně bylo snazší zobrazit výsledky ověření pro uživatele.

Potom na základě [FluentValidation](https://github.com/JeremySkinner/FluentValidation) knihovny, jsme vytvořili ověření dat byla dokončena s CreateOrderCommand, stejně jako v následujícím kódu:

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

Můžete například vytvořit další ověření. To je velmi čistá a elegantní způsob, jak implementovat vaše ověření příkaz.

Podobným způsobem je možné implementovat další chování pro další aspekty nebo převeďte společné aspekty, které chcete použít pro příkazy při jejich zpracování.

#### <a name="additional-resources"></a>Další zdroje

##### <a name="the-mediator-pattern"></a>Zprostředkovatel vzor

- **Zprostředkovatel vzor** \
  [https://en.wikipedia.org/wiki/Mediator\_pattern](https://en.wikipedia.org/wiki/Mediator_pattern)

##### <a name="the-decorator-pattern"></a>Vzor dekoratéru

- **Vzor dekoratéru** \
  [https://en.wikipedia.org/wiki/Decorator\_pattern](https://en.wikipedia.org/wiki/Decorator_pattern)

##### <a name="mediatr-jimmy-bogard"></a>MediatR (Jimmy Bogard)

- **MediatR.** Úložiště GitHub. \
  [https://github.com/jbogard/MediatR](https://github.com/jbogard/MediatR)

- **CQRS s MediatR a AutoMapper** \
  [https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/](https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/)

- **Umístí kontrolerům vyváženosti: Příspěvky a příkazy.** \
  [https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/](https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/)

- **Použití vyskytující aspekty s kanálem zprostředkovatel** \
  [https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/](https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/)

- **CQRS a REST: skvěle hodí** \
  [https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/](https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/)

- **Příklady MediatR kanálu** \
  [https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/](https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/)

- **Svislé řez testovací zařízení pro MediatR a ASP.NET Core** \
  [https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/](https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/)

- **Rozšíření MediatR pro vkládání závislostí Microsoft všeobecně dostupné** \
  [https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/](https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/)

##### <a name="fluent-validation"></a>Fluent ověření

- **Jeremy Skinner. FluentValidation.** Úložiště GitHub. \
  [https://github.com/JeremySkinner/FluentValidation](https://github.com/JeremySkinner/FluentValidation)

> [!div class="step-by-step"]
> [Předchozí](microservice-application-layer-web-api-design.md)
> [další](../implement-resilient-applications/index.md)
