---
title: Implementace aplikační vrstvy mikroslužeb pomocí webového rozhraní API
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Seznamte se s vkládáním závislostí a vzorci a jejich podrobnostmi o implementaci v aplikační vrstvě webového rozhraní API.
ms.date: 10/08/2018
ms.openlocfilehash: 0f6f47dd5f67fb18695715e5cfc9179206ef6bcf
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834356"
---
# <a name="implement-the-microservice-application-layer-using-the-web-api"></a>Implementace aplikační vrstvy mikroslužeb pomocí webového rozhraní API

## <a name="use-dependency-injection-to-inject-infrastructure-objects-into-your-application-layer"></a>Použití injektáže závislosti k vložení objektů infrastruktury do vrstvy aplikace

Jak bylo zmíněno dříve, aplikační vrstvu lze implementovat jako součást artefaktu (sestavení), který sestavíte, například v rámci projektu webového rozhraní API nebo projektu webové aplikace MVC. V případě mikroslužby vytvořené pomocí ASP.NET Core bude aplikační vrstva obvykle vaší knihovnou webového rozhraní API. Pokud chcete oddělit to, co pochází z ASP.NET Core (jeho infrastruktura a řadiče) z vlastního kódu vrstvy aplikace, můžete také umístit vrstvu aplikace do samostatné knihovny tříd, ale to je volitelné.

Například kód aplikační vrstvy řazení mikroslužba je implementován přímo jako součást projektu **objednávání. API** (ASP.NET Core projekt webového rozhraní API), jak je znázorněno na obrázku 7-23.

![Průzkumník řešení zobrazení pořadí. rozhraní API mikroslužby, které zobrazuje podsložky ve složce aplikace: chování, příkazy, DomainEventHandlers, IntegrationEvents, modely, dotazy a ověřování.](./media/image20.png)

**Obrázek 7-23**. Aplikační vrstva v projektu objednávání. API ASP.NET Core Web API

ASP.NET Core obsahuje jednoduchý [integrovaný kontejner IOC](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (reprezentovaný rozhraním IServiceProvider), který podporuje vkládání konstruktoru ve výchozím nastavení a ASP.NET zpřístupňuje určité služby prostřednictvím di. ASP.NET Core používá termín *služby* pro jakýkoli typ, který zaregistrujete, který bude VLOŽEN přes di. Předdefinované služby kontejneru v metodě ConfigureServices ve třídě Startup vaší aplikace nakonfigurujete. Vaše závislosti jsou implementované v rámci služeb, které typ vyžaduje a které zaregistrujete do kontejneru IoC.

Obvykle chcete vložit závislosti, které implementují objekty infrastruktury. Velmi typickou závislostí pro vkládání je úložiště. Mohli byste ale vložit jakoukoli další závislost infrastruktury, kterou můžete mít. Pro jednodušší implementace můžete přímo vložit objekt vzorce pracovní jednotky (objekt EF DbContext), protože DBContext je také implementace objektů trvalé infrastruktury.

V následujícím příkladu uvidíte, jak .NET Core vkládá požadované objekty úložiště prostřednictvím konstruktoru. Třída je obslužná rutina příkazu, kterou si pokryjeme v další části.

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

Třída používá vložená úložiště ke spuštění transakce a uchování změn stavu. Nezáleží na tom, zda je tato třída obslužná rutina příkazu, metoda ASP.NET Core webového rozhraní API nebo [DDD aplikační službu](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/). Je to nakonec jednoduchá třída, která používá úložiště, entity domény a další koordinaci aplikací podobným způsobem jako obslužná rutina příkazu. Vkládání závislostí funguje stejným způsobem pro všechny uvedené třídy, jako v příkladu pomocí příkazu DI založeného na konstruktoru.

### <a name="register-the-dependency-implementation-types-and-interfaces-or-abstractions"></a>Zaregistrujte typy implementace závislosti a rozhraní nebo abstrakce.

Před použitím objektů, které byly vloženy prostřednictvím konstruktorů, je třeba znát, kam mají být registrována rozhraní a třídy, které tvoří objekty vložené do tříd aplikace prostřednictvím DI. (Jako DI založené na konstruktoru, jak je uvedeno výše.)

#### <a name="use-the-built-in-ioc-container-provided-by-aspnet-core"></a>Použijte integrovaný kontejner IoC poskytovaný ASP.NET Core

Použijete-li integrovaný kontejner IoC poskytovaný ASP.NET Core, zaregistrujete typy, které chcete vložit do metody ConfigureServices v souboru Startup.cs, jak je uvedeno v následujícím kódu:

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

Nejběžnějším vzorem při registraci typů v kontejneru IoC je registrace páru typů – rozhraní a související implementační třídy. Pak při vyžádání objektu z kontejneru IoC prostřednictvím libovolného konstruktoru si vyžádáte objekt určitého typu rozhraní. Například v předchozím příkladu poslední řádek uvádí, že pokud některý z konstruktorů má závislost na IMyCustomRepository (rozhraní nebo abstrakci), kontejner IoC vloží instanci implementace MyCustomSQLServerRepository Deník.

#### <a name="use-the-scrutor-library-for-automatic-types-registration"></a>Pro registraci automatických typů použít knihovnu Scrutor

Při použití funkce DI v .NET Core můžete chtít skenovat sestavení a automaticky registrovat jeho typy podle konvencí. Tato funkce není v současnosti k dispozici v ASP.NET Core. Pro to však můžete použít knihovnu [Scrutor](https://github.com/khellang/Scrutor) . Tento přístup je vhodný, když máte desítky typů, které je třeba registrovat v kontejneru IoC.

#### <a name="additional-resources"></a>Další zdroje informací:

- **Matthew krále. Registrace služeb pomocí Scrutor** \
  <https://www.mking.net/blog/registering-services-with-scrutor>

- **Kristian Hellang. Scrutor.** Úložiště GitHub. \
  <https://github.com/khellang/Scrutor>

#### <a name="use-autofac-as-an-ioc-container"></a>Použití Autofac jako kontejneru IoC

Můžete také použít další kontejnery IoC a zapojit je do kanálu ASP.NET Core, jako při řazení mikroslužby v eShopOnContainers, která používá [Autofac](https://autofac.org/). Při použití Autofac obvykle zaregistrujete typy přes moduly, které umožňují rozdělit typy registrace mezi více soubory v závislosti na tom, kde jsou typy aplikace, stejně jako typy aplikací distribuované napříč více knihovnami tříd.

Následuje příklad, který je [modul aplikace Autofac](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) pro projekt [Web API pro objednávání. API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) s typy, které budete chtít vložit.

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

Autofac má také funkci pro [skenování sestavení a typů registru podle konvencí názvů](https://autofac.readthedocs.io/en/latest/register/scanning.html).

Proces registrace a koncepty jsou velmi podobné způsobu, jakým můžete registrovat typy s integrovaným ASP.NET Core kontejnerem IoC, ale syntaxe při použití Autofac je trochu odlišná.

V příkladu kódu je abstrakce IOrderRepository zaregistrována spolu s implementační třídou OrderRepository. To znamená, že pokaždé, když konstruktor deklaruje závislost prostřednictvím abstrakce nebo rozhraní IOrderRepository, kontejner IoC vloží instanci třídy OrderRepository.

Typ rozsahu instance Určuje, jak je instance sdílena mezi požadavky na stejnou službu nebo závislost. Při vytvoření žádosti o závislost může kontejner IoC vrátit následující:

- Jedna instance na rozsah doby života (v kontejneru ASP.NET Core IoC jako *obor*).

- Nová instance na závislost (dále uváděná v kontejneru ASP.NET Core IoC jako *přechodné*).

- Jedna instance sdílená napříč všemi objekty pomocí kontejneru IoC (dále v kontejneru ASP.NET Core IoC jako *singleton*).

#### <a name="additional-resources"></a>Další zdroje informací:

- **Úvod do injektáže závislosti v ASP.NET Core** \
  [https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection](/aspnet/core/fundamentals/dependency-injection)

- **Autofac.** Oficiální dokumentace. \
  <https://docs.autofac.org/en/latest/>

- **Porovnávání ASP.NET Core IoCch kontejnerových služeb s Autofac IoC instancemi kontejnerů – Cesar de la Torre.** \
  <https://devblogs.microsoft.com/cesardelatorre/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/>

## <a name="implement-the-command-and-command-handler-patterns"></a>Implementace vzorů obslužných rutin příkazů a příkazů

V příkladu typu DI-through-konstruktoru zobrazeném v předchozí části kontejner IoC vložil úložiště do konstruktoru ve třídě. Ale přesně tam, kde byly vloženy? V jednoduchém webovém rozhraní API (například služba katalogu eShopOnContainers) je vložíte do úrovně řadiče MVC v konstruktoru kontroleru jako součást kanálu žádosti o ASP.NET Core. Nicméně v úvodním kódu této části (třída [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) ze služby Ordering. API v eShopOnContainers) je vkládání závislostí provedeno prostřednictvím konstruktoru konkrétní obslužné rutiny příkazu. Vysvětlete, co je obslužná rutina příkazu, a proč byste ji chtěli použít.

Vzor příkazu je vnitřně spojen se vzorem CQRS, který byl představen dříve v této příručce. CQRS má dvě strany. První oblast se dotazuje pomocí zjednodušených dotazů s [dapperem](https://github.com/StackExchange/dapper-dot-net) Micro ORM, které bylo vysvětleno dříve. Druhá oblast je příkazy, které jsou výchozím bodem pro transakce, a vstupní kanál mimo službu.

Jak je znázorněno na obrázku 7-24, je vzor založený na přijímání příkazů ze strany klienta, jejich zpracování na základě pravidel doménové struktury a nakonec trvalého uchování stavů transakcemi.

![Zobrazení vysoké úrovně na straně zápisu v CQRS: aplikace uživatelského rozhraní odesílá příkaz prostřednictvím rozhraní API, které se dostane k CommandHandler –, které závisí na doménovém modelu a infrastruktuře pro aktualizaci databáze.](./media/image21.png)

**Obrázek 7-24**. Pohled na vysoké úrovni příkazů nebo "na straně transakčního" ve vzoru CQRS

### <a name="the-command-class"></a>Třída příkazu

Příkaz je požadavek, aby systém provedl akci, která mění stav systému. Příkazy jsou naléhavé a měly by se zpracovat jenom jednou.

Vzhledem k tomu, že jsou příkazy nezbytné, jsou obvykle pojmenovány pomocí příkazu v imperativní náladě (například "Create" nebo "Update") a mohou zahrnovat agregovaný typ, například CreateOrderCommand. Na rozdíl od události není příkaz fakt z minulosti; je to jenom žádost, a proto může být zamítnutá.

Příkazy mohou pocházet z uživatelského rozhraní v důsledku toho, že uživatel zahajuje požadavek, nebo ze správce procesů, když správce procesu nasměruje agregaci k provedení akce.

Důležitou vlastností příkazu je, že by měl být zpracován jedním příjemcem jenom jednou. Důvodem je to, že příkaz je jediná akce nebo transakce, kterou chcete v aplikaci provést. Například příkaz pro vytvoření stejné objednávky by neměl být zpracován více než jednou. Jedná se o důležitý rozdíl mezi příkazy a událostmi. Události se můžou zpracovávat víckrát, protože událost může zajímat spousta systémů nebo mikroslužeb.

Kromě toho je důležité, aby byl příkaz zpracován pouze jednou pro případ, že příkaz není idempotentní. Příkaz je idempotentní, pokud jej lze spustit vícekrát, aniž by došlo ke změně výsledku, buď z důvodu povahy příkazu, nebo z důvodu způsobu, jakým systém zpracovává příkaz.

Je vhodné provést příkazy a aktualizovat idempotentní, když to dává smysl v rámci obchodních pravidel a invariant vaší domény. Pokud například chcete použít stejný příklad, pokud z nějakého důvodu (opakování logiky, hacker atd.) stejný příkaz CreateOrder dosáhne vašeho systému několikrát, měli byste být schopni ho identifikovat a zajistit, aby nevytvořili více objednávek. K tomu je třeba v operacích připojit nějaký druh identity a určit, zda byl příkaz nebo aktualizace již zpracována.

Odešlete příkaz jednomu příjemci. nepublikujete příkaz. Publikování je pro události, které jsou ve skutečnosti, že došlo k nějaké situaci a může být zajímavá pro přijímače událostí. V případě událostí Vydavatel nemá žádné obavy o to, které příjemce obdrží událost nebo co k tomu dostanou. Ale události související s doménou nebo integrací jsou již v předchozích oddílech představeny jiným scénářem.

Příkaz je implementován se třídou, která obsahuje datová pole nebo kolekce se všemi informacemi, které jsou potřeba ke spuštění tohoto příkazu. Příkaz je speciální druh objektu Přenos dat (DTO), který se konkrétně používá k vyžádání změn nebo transakcí. Samotný příkaz je založen na přesně informacích, které jsou potřeba ke zpracování příkazu, a nic dalšího.

Následující příklad ukazuje zjednodušenou třídu `CreateOrderCommand`. Toto je neproměnlivý příkaz, který se používá při řazení mikroslužby v eShopOnContainers.

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

V podstatě třída Command obsahuje všechna data, která potřebujete pro provádění obchodní transakce, pomocí objektů doménového modelu. Příkazy jsou tedy jednoduše datové struktury, které obsahují data jen pro čtení, a žádné chování. Název příkazu označuje jeho účel. V mnoha jazycích, C#jako jsou příkazy, jsou reprezentovány jako třídy, ale nejedná se o skutečné třídy v reálném smyslu orientovaném na objekt.

V důsledku dalších charakteristik jsou příkazy neměnné, protože očekávané využití je, že jsou zpracovávány přímo doménovým modelem. Nemusejí se měnit během plánované životnosti. Ve C# třídě lze neměnnosti dosáhnout tak, že neexistují žádné metody setter nebo jiné metody, které mění vnitřní stav.

Je třeba mít na paměti, že Pokud zamýšlíte nebo očekáváte, že se budou provádět příkazy serializace/deserializace, vlastnosti musí mít privátní metodu setter a atribut `[DataMember]` (nebo `[JsonProperty]`), jinak by deserializátor nedokázal rekonstruovat objekt v cíl s požadovanými hodnotami.

Například třída příkazu pro vytvoření objednávky je pravděpodobně podobná z údajů pro pořadí, které chcete vytvořit, ale pravděpodobně nepotřebujete stejné atributy. Například `CreateOrderCommand` nemá ID objednávky, protože objednávka ještě nebyla vytvořena.

Mnoho tříd příkazu může být jednoduché, což vyžaduje pouze několik polí o některém stavu, který je třeba změnit. To by znamenalo, že když měníte stav objednávky z "v procesu" na "placeno" nebo "expedovaných", pomocí příkazu podobného následujícímu:

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

Někteří vývojáři zavedou své objekty žádosti o uživatelské rozhraní oddělené od jejich příkazu DTO, ale to je pouze preference. Je zdlouhavé oddělení, které není mnohem přidané hodnoty, a objekty jsou téměř přesně stejný tvar. Například v eShopOnContainers se některé příkazy přidávají přímo ze strany klienta.

### <a name="the-command-handler-class"></a>Třída obslužné rutiny příkazu

Pro každý příkaz byste měli implementovat konkrétní třídu obslužné rutiny příkazu. To znamená, jak vzor funguje, a je místo, kde budete používat objekt Command, doménové objekty a objekty úložiště infrastruktury. Obslužná rutina příkazu je ve skutečnosti jádrem aplikační vrstvy z podmínek CQRS a DDD. Nicméně všechny doménové logiky by měly být obsaženy v rámci tříd domény – v rámci agregovaných kořenů (kořenové entity), podřízených entit nebo [doménových služeb](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), ale ne v rámci obslužné rutiny příkazu, což je třída z aplikační vrstvy.

Třída obslužné rutiny příkazu nabízí silné kameny v rámci způsobu, jak dosáhnout jediného principu zodpovědnosti (SRP) zmíněného v předchozí části.

Obslužná rutina příkazu obdrží příkaz a získá výsledek z agregace, která je použita. Výsledek by měl být buď úspěšným provedením příkazu, nebo výjimkou. V případě výjimky by stav systému neměl být beze změny.

Obslužná rutina příkazu obvykle provádí následující kroky:

- Přijímá objekt příkazu, jako je DTO (z modulu [prostředníka](https://en.wikipedia.org/wiki/Mediator_pattern) nebo jiného objektu infrastruktury).

- Ověří, jestli je příkaz platný (pokud ho neověřuje zprostředkovatel).

- Vytvoří instanci agregované kořenové instance, která je cílem aktuálního příkazu.

- Spustí metodu na agregované kořenové instanci a získá požadovaná data z příkazu.

- Zachovává nový stav agregace do příslušné databáze. Tato poslední operace je skutečná transakce.

Obvykle obslužná rutina příkazu zpracovává jedinou agregaci založenou na agregačním kořeni (kořenová entita). Pokud by mělo být ovlivněno více agregací přijetím jednoho příkazu, můžete použít události domény k šíření stavů nebo akcí v rámci více agregací.

Důležitým bodem je, že při zpracování příkazu by měla být veškerá logika domény uvnitř doménového modelu (agregace), plně zapouzdřená a připravená pro testování částí. Obslužná rutina příkazu funguje jenom jako způsob, jak získat doménový model z databáze a jako poslední krok, aby bylo možné sdělit vrstvě infrastruktury (úložiště), aby zachovala změny při změně modelu. Výhodou tohoto přístupu je, že můžete logiku domény Refaktorovat v izolovaném, plně zapouzdřeném, bohatým modelu doménového modelu, aniž byste museli měnit kód v vrstevch aplikace nebo infrastruktury, což je úroveň domovní instalace (obslužné rutiny příkazů, webové rozhraní API, úložiště atd.).

Pokud obslužné rutiny příkazu mají složitý, s příliš velkým množstvím logiky, může to být zápach kódu. Přečtěte si je, a pokud najdete logiku domény, refaktorujte kód pro přesun tohoto chování domény do metod doménových objektů (agregovaná kořenová a podřízená entita).

Jako příklad třídy obslužné rutiny příkazu, následující kód ukazuje stejnou třídu `CreateOrderCommandHandler`, kterou jste viděli na začátku této kapitoly. V tomto případě chceme zvýraznit metodu popisovače a operace s objekty nebo agregacemi doménového modelu.

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

- Použijte data příkazu pro práci s metodami a chováním agregačního kořenového adresáře.

- Interně v rámci doménových objektů přivolejte události domény při spuštění transakce, ale to je transparentní z bodu obslužné rutiny příkazu View.

- Pokud je výsledkem operace agregace úspěch a po dokončení transakce, vyvolejte integrační události. (Ty můžou být vyvolány i třídami infrastruktury, jako jsou úložiště.)

#### <a name="additional-resources"></a>Další zdroje informací:

- **Označte Seemann. V hranicích nejsou aplikace orientované na objekt** \.
  <https://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/>

- **Příkazy a události** \
  <http://cqrs.nu/Faq/commands-and-events>

- **Co dělá obslužná rutina příkazu?** \
  <http://cqrs.nu/Faq/command-handlers>

- **Jimmy Bogard. Doménové vzory příkazů – obslužné rutiny** \
  <https://jimmybogard.com/domain-command-patterns-handlers/>

- **Jimmy Bogard. Doménové vzorce příkazů – ověření** \
  <https://jimmybogard.com/domain-command-patterns-validation/>

## <a name="the-command-process-pipeline-how-to-trigger-a-command-handler"></a>Kanál procesu příkazu: Jak aktivovat obslužnou rutinu příkazu

Další otázkou je postup vyvolání obslužné rutiny příkazu. Můžete ji ručně volat z každého souvisejícího kontroleru ASP.NET Core. Nicméně tento přístup by byl příliš spojený a není ideální.

Další dvě hlavní možnosti, které jsou doporučenými možnostmi, jsou:

- Prostřednictvím artefaktu modelu pro zpracování v paměti.

- S asynchronní frontou zpráv mezi řadiči a obslužnými rutinami.

### <a name="use-the-mediator-pattern-in-memory-in-the-command-pipeline"></a>Použití vzoru povýšení (v paměti) v kanálu příkazů

Jak je znázorněno na obrázku 7-25, CQRS přístup k používání inteligentního modulu pro směrování, podobně jako sběrnice v paměti, která je dostatečně inteligentní pro přesměrování na správnou obslužnou rutinu příkazů na základě typu příkazu nebo DTO, který je právě přijímán. Jednoduché šipky mezi komponentami znázorňují závislosti mezi objekty (v mnoha případech vložené přes DI) se souvisejícími interakcemi.

![Přiblíží se k předchozímu obrázku: řadič ASP.NET Core odesílá příkaz do kanálu příkazů MediatR, aby se dostal k příslušné obslužné rutině.](./media/image22.png)

**Obrázek 7-25**. Použití vzoru prostředníka v procesu v jedné mikroslužbě CQRS

Důvodem použití vzorového principu je to, že v podnikových aplikacích můžou požadavky na zpracování dosáhnout složitosti. Chcete být schopni přidat otevřený počet vzájemně se podobných otázek, jako je protokolování, ověření, audit a zabezpečení. V těchto případech můžete spoléhat na kanál prostředníka (viz [vzor zprostředkovatelů](https://en.wikipedia.org/wiki/Mediator_pattern)) a poskytnout tak prostředky pro tato dodatečná chování nebo problémy při průřezu.

Zprostředkovatel je objekt, který zapouzdřuje "How" tohoto procesu: koordinuje spouštění na základě stavu, způsob vyvolání obslužné rutiny příkazu nebo datovou část, kterou poskytnete obslužné rutině. Společně s komponentou pro spoluprůřezy můžete v centralizovaném a transparentním způsobu použít otázky pro průřez, a to použitím dekoratéry (nebo [chování kanálu](https://github.com/jbogard/MediatR/wiki/Behaviors) od [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0)). Další informace najdete v tématu [dekoratér vzor](https://en.wikipedia.org/wiki/Decorator_pattern).

Dekoratéry a chování jsou podobné [programování orientovanému na orientaci (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming), které se používá jenom pro konkrétní kanál procesu spravovaný komponentou prostředníka. Aspekty v AOP, které implementují obavy mezi průřezy, se uplatňují na základě *aspektů Weavers* vložených v době kompilace nebo na základě zachycení volání objektů. Typické přístupy k AOP jsou někdy označovány jako "jako Magic", protože není snadné zjistit, jak AOP funguje. Při řešení vážných problémů nebo chyb může být AOP obtížné ho ladit. Na druhé straně jsou tyto dekoratéry/chování explicitní a použité pouze v kontextu prostředníka, takže ladění je mnohem více předvídatelné a snadné.

Například v eShopOnContainers objednávání mikroslužby jsme implementovali dvě vzorová chování, třídu [LogBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) a třídu [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) . Implementaci chování je vysvětleno v další části zobrazením, jak eShopOnContainers používá [chování](https://github.com/jbogard/MediatR/wiki/Behaviors) [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) .

### <a name="use-message-queues-out-of-proc-in-the-commands-pipeline"></a>Použití front zpráv (out-of-proc) v kanálu příkazu

Další možností je použít asynchronní zprávy založené na zprostředkovatelích nebo frontách zpráv, jak je znázorněno na obrázku 7-26. Tato možnost může být také kombinována s komponentou prostředníka před obslužnou rutinou příkazu.

![Kanál příkazu může být také zpracován frontou zpráv vysoké dostupnosti pro doručení příkazů příslušné obslužné rutině.](./media/image23.png)

**Obrázek 7-26**. Použití front zpráv (mimo procesy a komunikace mezi procesy) pomocí příkazů CQRS

Použití front zpráv k přijetí příkazů může dále zkomplikovat kanál příkazu, protože pravděpodobně budete muset kanál rozdělit do dvou procesů, které jsou připojeny prostřednictvím externí fronty zpráv. Stále byste měli použít, pokud potřebujete mít lepší škálovatelnost a výkon na základě asynchronního zasílání zpráv. Vezměte v úvahu, že v případě obrázku 7-26 tento kontroler pouze odešle příkaz do fronty a vrátí. Potom obslužné rutiny příkazu zpracovávají zprávy vlastním tempem. To je skvělé výhody front: fronta zpráv může fungovat jako vyrovnávací paměť v případech, kdy je potřeba škálovatelnost technologie Hyper-v případě potřeby, jako jsou například akcie nebo jakýkoli jiný scénář s velkým objemem příchozích dat.

Z důvodu asynchronního povaze front zpráv je však nutné zjistit, jak komunikovat s klientskou aplikací o úspěšnosti nebo selhání procesu příkazu. Jako pravidlo byste nikdy neměli používat příkazy "Fire and zapomenout". Každá obchodní aplikace potřebuje zjistit, jestli byl příkaz úspěšně zpracován, nebo alespoň ověřený a přijatý.

Proto schopnost reagovat na klienta po ověření zprávy příkazu, která byla odeslána do asynchronní fronty, představuje složitost systému, jak je popsáno v procesu příkazu procesu, který vrací výsledek operace po spuštění transakce. Pomocí front může být nutné vrátit výsledek příkazového procesu prostřednictvím dalších zpráv výsledků operací, které budou vyžadovat další součásti a vlastní komunikaci ve vašem systému.

Kromě toho asynchronní příkazy jsou jednosměrné příkazy, které v mnoha případech nemusí být potřeba, jak je vysvětleno v následujícím zajímavém Exchangi mezi Burtsev Alexey a Greg Youngem v [online konverzaci](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):

> \[Burtsev Alexey @ no__t-1 najdu spoustu kódu, kde lidé používají zpracování asynchronních příkazů nebo jednosměrné zasílání zpráv bez jakéhokoli důvodu (neprovádí se žádné dlouhé operace) hranice, která bude používat sběrnici zpráv). Proč zavádějí tuto zbytečný složitost? A ve skutečnosti jsem neviděl příklad kódu CQRS s blokujícími obslužnými rutinami příkazů, i když bude ve většině případů fungovat přesně dobře.
>
> \[Greg Young @ no__t-1 \[... \] neexistují asynchronní příkazy; ve skutečnosti se jedná o jinou událost. Pokud je potřeba přijmout, co pošlete, a vyvolat událost, Pokud nesouhlasíte, už Neoznamujeme, že vám @no__t – 0that je, není to příkaz @ no__t-1. Je to vám řekněte mi, že se něco udělalo. Vypadá to jako mírně rozdíl v prvním, ale má mnoho aspektů.

Asynchronní příkazy významně zvyšují složitost systému, protože neexistuje žádný jednoduchý způsob, jak označovat selhání. Proto nejsou asynchronní příkazy jiné doporučovány než při vyžadování požadavků na škálování nebo ve zvláštních případech při komunikaci interních mikroslužeb prostřednictvím zasílání zpráv. V těchto případech je třeba navrhnout samostatné vytváření sestav a systém obnovení pro selhání.

V počáteční verzi eShopOnContainers jsme se rozhodli používat synchronní zpracování příkazů spouštěné z požadavků HTTP a řízených vzorem pro povýšení. To umožňuje snadno vrátit úspěch nebo neúspěch procesu, jako v implementaci [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) .

V každém případě by to mělo být rozhodnutí založené na obchodních požadavcích vaší aplikace nebo mikroslužeb.

## <a name="implement-the-command-process-pipeline-with-a-mediator-pattern-mediatr"></a>Implementace kanálu procesu příkazu pomocí vzoru povedení (MediatR)

V rámci ukázkové implementace tato příručka navrhuje použití kanálu v rámci procesu založeného na vzorci pro řízení příkazů pro příjem příkazů a směrování příkazů v paměti na pravé obslužné rutiny příkazů. Průvodce také navrhuje použití [chování](https://github.com/jbogard/MediatR/wiki/Behaviors) , aby bylo možné oddělit různé aspekty.

Pro implementaci v .NET Core je k dispozici více Open Source knihoven, které implementují vzor povýšení. Knihovna použitá v tomto průvodci je [MediatR](https://github.com/jbogard/MediatR) open source knihovna (vytvořená Jimmy Bogard), ale můžete použít jiný přístup. MediatR je malá a jednoduchá knihovna, která umožňuje zpracovávat zprávy v paměti jako příkaz, a to při použití dekoratéry nebo chování.

Použití vzorového vztahu vám pomůže omezit spojování a izolovat obavy o požadovanou práci a automaticky se připojit k obslužné rutině, která provádí tuto práci – v tomto případě do obslužných rutin příkazů.

Dalším dobrým důvodem pro použití vzoru prostředníka bylo při prohlížení této příručky vysvětleno v Jimmy Bogard:

> Domnívám se, že se tady může poznamenat testování – nabízí skvělé konzistentní okno s chováním systému. Požadavky, reakce. Zjistili jsme, že tento aspekt je poměrně užitečný při sestavování konzistentně se chovajících testů.

Nejprve se podíváme na vzorový kontroler WebAPI, kde byste ve skutečnosti použili objekt prostředníka. Pokud jste nepoužívali objekt prostředníka, je nutné vložit všechny závislosti pro tento kontroler, například objekt protokolovacího nástroje a další. Konstruktor by proto byl poměrně složitý. Na druhou stranu platí, že pokud použijete objekt prostředníkem, může být konstruktor vašeho kontroleru mnohem jednodušší, ale pouze pár závislostí místo mnoha závislostí, pokud jste měli jeden za operaci křížového vyjmutí, jak je uvedeno v následujícím příkladu:

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

Můžete vidět, že zprostředkovatel poskytuje čistý a štíhlý konstruktor webového rozhraní API. Kromě toho v rámci metod kontroleru je kód pro odeslání příkazu do objektu prostředníku skoro jeden řádek:

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

### <a name="implement-idempotent-commands"></a>Implementace příkazů idempotentní

V **eShopOnContainers**, pokročilejší příklad, který je uveden výše, odesílá objekt CreateOrderCommand z řazení mikroslužeb. Ale vzhledem k tomu, že je obchodní proces objednávání trochu složitější a v našem případě se ve skutečnosti zahájí v rámci služby koš, tato akce odeslání objektu CreateOrderCommand je prováděna z obslužné rutiny události Integration-Event s názvem > UserCheckoutAcceptedIntegrationEvent.cs] (https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) namísto jednoduchého kontroleru WebAPI, který se volá z klientské aplikace jako v předchozím jednodušším příkladu.

Nicméně akce odeslání příkazu do MediatR je poměrně podobná, jak je znázorněno v následujícím kódu.

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

Tento případ je ale také trochu pokročilejší, protože implementujeme také idempotentní příkazy. Proces CreateOrderCommand by měl být idempotentní, takže pokud se stejná zpráva bude duplikována prostřednictvím sítě z jakéhokoli důvodu, jako je třeba opakování, stejné obchodní objednávky se zpracují jenom jednou.

To je implementováno zabalením obchodního příkazu (v tomto případě CreateOrderCommand) a jeho vložením do obecného IdentifiedCommandu, které je sledováno ID každé zprávy přicházející přes síť, která musí být idempotentní.

V následujícím kódu vidíte, že IdentifiedCommand není nic více než DTO s a ID plus zabalený objekt Business Command.

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

Pak CommandHandler – pro IdentifiedCommand s názvem [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs) bude v podstatě kontrolovat, zda ID přicházející jako součást zprávy již v tabulce existuje. Pokud již existuje, tento příkaz nebude zpracován znovu, takže se chová jako příkaz idempotentní. Tento kód infrastruktury provádí volání metody `_requestManager.ExistAsync` níže.

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

Vzhledem k tomu, že IdentifiedCommand funguje jako obálka obchodního příkazu, když je potřeba zpracovat obchodní příkaz, protože se nejedná o opakované ID, pak provede interní obchodní příkaz a znovu ho odešle zprostředkovateli, jako v poslední části kódu uvedeného výše. spuštění `_mediator.Send(message.Command)` z [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs).

Při tomto postupu bude probíhat odkazování a spuštění obslužné rutiny obchodního příkazu, v tomto případě [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) , který spouští transakce proti objednávce databáze, jak je znázorněno v následujícím kódu.

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

### <a name="register-the-types-used-by-mediatr"></a>Zaregistrujte typy používané pomocí MediatR

Aby MediatR informace o třídách obslužných rutin příkazů, je nutné zaregistrovat třídy poskytovatele a obslužné rutiny příkazu v kontejneru IoC. Ve výchozím nastavení používá MediatR jako kontejner IoC Autofac, ale můžete použít i integrovaný kontejner ASP.NET Core IoC nebo jakýkoli jiný kontejner podporovaný MediatR.

Následující kód ukazuje, jak registrovat typy a příkazy poskytovatele při použití Autofac modulů.

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

V takovém případě se s MediatR stane "Magic".

Vzhledem k tomu, že každá obslužná rutina příkazu implementuje při registraci sestavení Obecné rozhraní @no__t 0, registruje kód s `RegisteredAssemblyTypes` všechny typy označené jako `IAsyncRequestHandler`, zatímco se vztahuje na `CommandHandlers` s jejich `Commands` díky vztahu uvedenému na Třída `CommandHandler`, jak je uvedeno v následujícím příkladu:

```csharp
public class CreateOrderCommandHandler
  : IAsyncRequestHandler<CreateOrderCommand, bool>
{
```

To je kód, který koreluje příkazy s obslužnými rutinami příkazů. Obslužná rutina je pouze jednoduchá třída, ale dědí z `RequestHandler<T>`, kde T je typ příkazu, a MediatR zajišťuje, že je vyvolána se správnou datovou částí (příkaz).

## <a name="apply-cross-cutting-concerns-when-processing-commands-with-the-behaviors-in-mediatr"></a>Při zpracování příkazů s chováním v MediatR použít různé aspekty při vyjmutí

K dispozici je ještě více věcí: schopnost použít průřezy v rámci kanálu pro proporcování. Můžete také vidět na konci registračního modulu Autofac, jak registruje typ chování, konkrétně vlastní třídu LoggingBehavior a třídu ValidatorBehavior. Můžete ale také přidat další vlastní chování.

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

Tato třída [LoggingBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) může být implementována jako následující kód, který protokoluje informace o spuštěné obslužné rutině příkazu a zda byla úspěšná.

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

Pouze implementací této třídy chování a jejich registrací do kanálu (ve výše uvedeném MediatorModule) budou všechny příkazy zpracované prostřednictvím MediatR protokolovány informace o spuštění.

Mikroslužba řazení eShopOnContainers také používá druhé chování pro základní ověřování, třídu [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) , která spoléhá na knihovnu [FluentValidation](https://github.com/JeremySkinner/FluentValidation) , jak je znázorněno v následujícím kódu:

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

Chování vyvolalo výjimku, pokud se ověření nepovede, ale můžete také vrátit výsledný objekt, který obsahuje výsledek příkazu, pokud byl úspěšný, nebo ověřovací zprávy v případě, že nedošlo k chybě. To by pravděpodobně bylo snazší zobrazit výsledky ověřování uživateli.

V závislosti na knihovně [FluentValidation](https://github.com/JeremySkinner/FluentValidation) jsme vytvořili ověřování pro data předaná pomocí CreateOrderCommand, jak je uvedeno v následujícím kódu:

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

Mohli byste vytvořit další ověření. Jedná se o velmi čistý a elegantní způsob implementace příkazů pro ověřování.

Podobným způsobem můžete implementovat jiné chování pro další aspekty nebo problémy mimo průřez, které chcete použít pro příkazy při jejich zpracování.

#### <a name="additional-resources"></a>Další zdroje informací:

##### <a name="the-mediator-pattern"></a>Vzor zprostředkovatelů

- **Vzor zprostředkovatelů** \
  [https://en.wikipedia.org/wiki/Mediator\_pattern](https://en.wikipedia.org/wiki/Mediator_pattern)

##### <a name="the-decorator-pattern"></a>Vzor dekoratér

- **Dekoratér vzor** \
  [https://en.wikipedia.org/wiki/Decorator\_pattern](https://en.wikipedia.org/wiki/Decorator_pattern)

##### <a name="mediatr-jimmy-bogard"></a>MediatR (Jimmy Bogard)

- **MediatR.** Úložiště GitHub. \
  <https://github.com/jbogard/MediatR>

- **CQRS s MediatR a automapper** \
  <https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/>

- **Vložte své řadiče do diety: příspěvky a příkazy.** \
  <https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/>

- Řešení **potíží v průřezu s použitím kanálu**vedení  \
  <https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/>

- **CQRS a REST: ideální shoda** \
  <https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/>

- **Příklady MediatR kanálu** \
  <https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/>

- **Testovací přípravek pro MediatR a ASP.NET Core** \
  <https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/>

- **Rozšíření MediatR pro vkládání závislostí Microsoft** \
  <https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/>

##### <a name="fluent-validation"></a>Ověření Fluent

- **Jeremy Skinner. FluentValidation.** Úložiště GitHub. \
  <https://github.com/JeremySkinner/FluentValidation>

> [!div class="step-by-step"]
> [Předchozí](microservice-application-layer-web-api-design.md)@no__t – 1 –[Další](../implement-resilient-applications/index.md)
