---
title: Přihlášení k odběru událostí
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Seznamte se s podrobnostmi o publikování a předplatném integračních událostí.
ms.date: 01/30/2020
ms.openlocfilehash: 544af8035ed23dd6507dfed4944b0c327c81d943
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77501809"
---
# <a name="subscribing-to-events"></a>Přihlášení k odběru událostí

Prvním krokem pro použití sběrnice Event je přihlášení k odběru mikroslužeb k událostem, které chtějí přijímat. To by mělo být provedeno v mikroslužbách přijímače.

Následující jednoduchý kód ukazuje, co každá mikroslužba přijímače potřebuje implementovat při spuštění služby (to znamená ve třídě `Startup`), aby se přihlásila k odběru událostí, které potřebuje. V takovém případě se `basket-api` mikroslužeb musí přihlásit k odběru `ProductPriceChangedIntegrationEvent` a `OrderStartedIntegrationEvent` zpráv.

Například při přihlášení k odběru události `ProductPriceChangedIntegrationEvent`, která umožňuje, aby mikroslužba koše mohla vědět o jakýchkoli změnách ceny za produkt, a umožňuje uživateli upozornit na změnu v případě, že je tento produkt v koši uživatele.

```csharp
var eventBus = app.ApplicationServices.GetRequiredService<IEventBus>();

eventBus.Subscribe<ProductPriceChangedIntegrationEvent,
                   ProductPriceChangedIntegrationEventHandler>();

eventBus.Subscribe<OrderStartedIntegrationEvent,
                   OrderStartedIntegrationEventHandler>();

```

Po spuštění tohoto kódu bude služba pro předplatitele naslouchat prostřednictvím RabbitMQ kanálů. Při doručení libovolné zprávy typu ProductPriceChangedIntegrationEvent kód vyvolá obslužnou rutinu události, která je předána a zpracovává událost.

## <a name="publishing-events-through-the-event-bus"></a>Publikování událostí prostřednictvím sběrnice událostí

Nakonec odesílatel zprávy (původ mikroslužeb) publikuje události integrace s kódem podobným následujícímu příkladu. (Jedná se o zjednodušený příklad, který nebere v úvahu nedělitelnost.) Podobný kód byste implementovali vždy, když je nutné rozšířit událost napříč několika mikroslužbami, obvykle po potvrzení dat nebo transakcí od původu mikroslužeb.

Nejprve bude objekt implementace sběrnice událostí (založený na RabbitMQ nebo na základě služby Service Bus) vložen do konstruktoru kontroleru, jak je uvedeno v následujícím kódu:

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    private readonly CatalogContext _context;
    private readonly IOptionsSnapshot<Settings> _settings;
    private readonly IEventBus _eventBus;

    public CatalogController(CatalogContext context,
        IOptionsSnapshot<Settings> settings,
        IEventBus eventBus)
    {
        _context = context;
        _settings = settings;
        _eventBus = eventBus;
    }
    // ...
}
```

Pak ho použijete z metod řadiče, jako v metodě UpdateProduct:

```csharp
[Route("items")]
[HttpPost]
public async Task<IActionResult> UpdateProduct([FromBody]CatalogItem product)
{
    var item = await _context.CatalogItems.SingleOrDefaultAsync(
        i => i.Id == product.Id);
    // ...
    if (item.Price != product.Price)
    {
        var oldPrice = item.Price;
        item.Price = product.Price;
        _context.CatalogItems.Update(item);
        var @event = new ProductPriceChangedIntegrationEvent(item.Id,
            item.Price,
            oldPrice);
        // Commit changes in original transaction
        await _context.SaveChangesAsync();
        // Publish integration event to the event bus
        // (RabbitMQ or a service bus underneath)
        _eventBus.Publish(@event);
        // ...
    }
    // ...
}
```

V tomto případě, vzhledem k tomu, že je zdrojem mikroslužeb jednoduchá CRUD, je kód umístěný přímo do kontroleru webového rozhraní API.

V pokročilejších mikroslužbách, například při použití CQRS přístupů, je možné ji implementovat do třídy `CommandHandler` v rámci metody `Handle()`.

### <a name="designing-atomicity-and-resiliency-when-publishing-to-the-event-bus"></a>Návrh atomické a odolnosti při publikování do sběrnice událostí

Když publikujete integrační události prostřednictvím distribuovaného systému zasílání zpráv, jako je vaše sběrnice událostí, máte problém s atomovou aktualizací původní databáze a publikováním události (to znamená, že se buď dokončí obě operace, nebo žádné z nich). Například u zjednodušeného příkladu, který byl výše uveden, kód potvrdí data do databáze při změně ceny produktu a následném publikování zprávy ProductPriceChangedIntegrationEvent. Zpočátku může být důležité, aby tyto dvě operace byly prováděny atomicky. Pokud ale používáte distribuovanou transakci zahrnující databázi a zprostředkovatele zpráv, stejně jako ve starších systémech, jako je služba [Microsoft Message Queuing (MSMQ)](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx), to se nedoporučuje z důvodů popsaných v [věta Cap](https://www.quora.com/What-Is-CAP-Theorem-1).

V podstatě používáte mikroslužby k vytváření škálovatelných systémů s vysokou dostupností. Poněkud větší věta znamená, že nemůžete sestavit (distribuovanou) databázi (nebo mikroslužbu, která vlastní svůj model), která je trvale dostupná, silně konzistentní *a* odolná vůči jakémukoli oddílu. Musíte zvolit dvě z těchto tří vlastností.

V architekturách založených na mikroslužbách byste měli zvolit dostupnost a toleranci a měli byste zdůraznit silnou konzistenci. Ve většině moderních aplikací založených na mikroslužbách většinou nechcete v zasílání zpráv používat distribuované transakce, jako při implementaci [distribuovaných transakcí](https://docs.microsoft.com/previous-versions/windows/desktop/ms681205(v=vs.85)) na základě Windows DTC (DISTRIBUTED Transaction Coordinator) (DTC) pomocí [služby MSMQ](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx).

Pojďme se vrátit k původnímu problému a jeho příkladu. Pokud služba po aktualizaci databáze dojde k chybě (v tomto případě je to hned za řádkem kódu s \_m kontextem. SaveChangesAsync ()), ale před publikováním události integrace, by celkový systém mohl být nekonzistentní. To může být důležité pro podnikání v závislosti na konkrétní obchodní operaci, se kterou se chystáte pracovat.

Jak bylo zmíněno dříve v části architektura, můžete mít několik přístupů k řešení tohoto problému:

- Pomocí vzoru úplných [zdrojů událostí](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing).

- Pomocí [dolování protokolu transakcí](https://www.scoop.it/t/sql-server-transaction-log-mining).

- Pomocí [vzoru pošty k odeslání](https://www.kamilgrzybek.com/design/the-outbox-pattern/). Toto je transakční tabulka pro uložení integračních událostí (rozšíření místní transakce).

V tomto scénáři je jedním z nejlepších přístupů použití vzoru úplných událostí (ES), pokud *to není nejlepší* . V mnoha scénářích aplikací ale nemusí být možné implementovat úplný systém ES. ES znamená ukládání pouze doménových událostí do transakční databáze místo ukládání aktuálních dat o stavu. Ukládání pouze událostí v doméně může mít skvělé výhody, jako je třeba historie vašeho systému a možnost zjistit stav systému v minulosti. Implementace celého systému ES ale vyžaduje, abyste převedli své architekty na většinu systému a předvedli spoustu dalších složitých a požadavků. Například byste chtěli použít databázi specifickou pro daný původ události, jako je například [úložiště událostí](https://eventstore.org/), nebo databáze orientovaný na dokument, například Azure Cosmos DB, MongoDB, Cassandra, CouchDB nebo RavenDB. ES je skvělý přístup k tomuto problému, ale ne nejjednodušší řešení, pokud už neznáte jeho původ.

Možnost použít dolování protokolu transakcí zpočátku vypadá velmi transparentně. Chcete-li však použít tento přístup, musí být mikroslužba spojena s protokolem transakcí RDBMS, jako je například protokol transakcí SQL Server. To pravděpodobně není žádoucí. Další nevýhodou je, že aktualizace nízké úrovně zaznamenané v protokolu transakcí nemusí být na stejné úrovni jako vaše integrační události vysoké úrovně. V takovém případě může být proces zpětného strojírenství těchto operací s protokolem transakcí obtížné.

Vyvážený přístup je kombinací transakční tabulky databáze a zjednodušeného vzoru ES. Můžete použít stav, například "připraveno k publikování události", který jste nastavili v původní události při jejich potvrzení do tabulky integračních událostí. Pak se pokusíte publikovat událost do sběrnice událostí. Pokud je akce publikovat-událost úspěšná, spustíte jinou transakci ve zdrojové službě a přesunete stav z "připraveno k publikování události" do "již publikované události".

Pokud akce publikovat-událost ve sběrnici událostí selže, data stále nebudou v původním mikroslužbě konzistentní – bude stále označena jako "připraveno k publikování události" a s ohledem na zbytek služeb bude nakonec konzistentní. Kdykoli můžete mít úlohy na pozadí, které kontrolují stav transakcí nebo integračních událostí. Pokud úloha najde událost ve stavu "připraveno k publikování události", může se pokusit tuto událost znovu publikovat do sběrnice událostí.

Všimněte si, že s tímto přístupem jste zachovali jenom události integrace pro každou zdrojovou mikroslužbu a jenom události, které chcete komunikovat s dalšími mikroslužbami nebo externími systémy. Na rozdíl od úplného systému ES ukládáte i všechny události domény.

Proto je tento vyvážený přístup zjednodušený systém ES. Budete potřebovat seznam událostí integrace s jejich aktuálním stavem ("připraveno k publikování" versus "Publikováno"). Ale stačí, abyste tyto stavy implementovali pro integrační události. A v tomto přístupu nemusíte ukládat veškerá doménová data jako události do transakční databáze, stejně jako v plném systému ES.

Pokud již používáte relační databázi, můžete k ukládání integračních událostí použít transakční tabulku. Chcete-li dosáhnout nedělitelnost v aplikaci, použijte proces se dvěma kroky, který je založen na místních transakcích. V podstatě máte tabulku IntegrationEvent ve stejné databázi, ve které máte vaše doménové entity. Tato tabulka spolupracuje jako pojištění pro dosažení nedělitelnost, takže zahrnete trvalé integrační události do stejných transakcí, které potvrzují data domény.

Krok za krokem proces bude vypadat takto:

1. Aplikace zahájí místní databázovou transakci.

2. Pak aktualizuje stav entit vaší domény a vloží událost do tabulky integračních událostí.

3. Nakonec potvrdí transakci, takže získáte požadovanou nedělitelnost a pak

4. Událost se publikuje nějakým způsobem (další).

Při implementaci kroků publikování událostí máte tyto možnosti:

- Publikovat událost Integration hned po potvrzení transakce a použít jinou místní transakci k označení událostí v tabulce jako publikovaná. Pak použijte tabulku stejně jako artefakt ke sledování událostí integrace v případě problémů se vzdálenými mikroslužbami a provádění kompenzačních akcí na základě uložených integračních událostí.

- Použijte tabulku jako typ fronty. Samostatné vlákno aplikace nebo zpracovává dotaz na tabulku událostí integrace, zveřejňuje události do sběrnice událostí a poté používá místní transakci k označení událostí jako publikovaných.

Obrázek 6-22 ukazuje architekturu pro první z těchto přístupů.

![Diagram nedělitelnost při publikování bez pracovního mikroslužby.](./media/subscribe-events/atomicity-publish-event-bus.png)

**Obrázek 6-22**. Nedělitelnost při publikování událostí do sběrnice událostí

Při přístupu na obrázku 6-22 chybí další mikroslužba pracovního procesu, která má za následek kontrolu a ověření úspěchu publikovaných integračních událostí. V případě selhání může tato služba Worker Worker z tabulky číst události a znovu je publikovat, to znamená opakovat krok číslo 2.

O druhém přístupu: použijte tabulku EventLog jako frontu a vždy použijte k publikování těchto zpráv pracovní mikroslužbu. V takovém případě se jedná o proces, který je znázorněn na obrázku 6-23. Zobrazí se další mikroslužba a tabulka je jediným zdrojem při publikování událostí.

![Diagram nedělitelnost při publikování pomocí mikroslužby pracovního procesu](./media/subscribe-events/atomicity-publish-worker-microservice.png)

**Obrázek 6-23**. Nedělitelnost při publikování událostí do sběrnice událostí pomocí mikroslužby pracovního procesu

Pro zjednodušení ukázka eShopOnContainers používá první přístup (bez dalších procesů nebo mikroslužeb pro kontrolu) a sběrnice událostí. EShopOnContainers ale nezpracovává všechny možné případy selhání. V reálné aplikaci nasazené do cloudu je nutné zaplnit skutečnost, že k problémům dojde nakonec, a musíte tuto kontrolu implementovat a znovu odeslat. Použití tabulky jako fronty může být efektivnější než první přístup, pokud tuto tabulku máte jako jediný zdroj událostí při jejich publikování (s pracovním procesem) prostřednictvím sběrnice událostí.

### <a name="implementing-atomicity-when-publishing-integration-events-through-the-event-bus"></a>Implementace atomické události při publikování integračních událostí prostřednictvím sběrnice událostí

Následující kód ukazuje, jak lze vytvořit jednu transakci zahrnující více objektů DbContext – jeden kontext související s původními daty, která jsou aktualizována, a druhý kontext vztahující se k tabulce IntegrationEventLog.

Všimněte si, že transakce v následujícím ukázkovém kódu nebude odolná, pokud mají připojení k databázi nějaký problém v době, kdy je kód spuštěný. K tomu může dojít v cloudových systémech, jako je Azure SQL DB, které mohou přesouvat databáze na serverech. Informace o implementaci odolných transakcí napříč více kontexty najdete v části [implementace odolného Entity Framework Core připojení SQL](../implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md) dále v této příručce.

Pro přehlednost následující příklad ukazuje celý proces v jednom kusu kódu. Implementace eShopOnContainers je ale ve skutečnosti refaktorovaná a rozdělí tuto logiku do více tříd, takže ji můžete snáze udržovat.

```csharp
// Update Product from the Catalog microservice
//
public async Task<IActionResult> UpdateProduct([FromBody]CatalogItem productToUpdate)
{
  var catalogItem =
       await _catalogContext.CatalogItems.SingleOrDefaultAsync(i => i.Id ==
                                                               productToUpdate.Id);
  if (catalogItem == null) return NotFound();

  bool raiseProductPriceChangedEvent = false;
  IntegrationEvent priceChangedEvent = null;

  if (catalogItem.Price != productToUpdate.Price)
          raiseProductPriceChangedEvent = true;

  if (raiseProductPriceChangedEvent) // Create event if price has changed
  {
      var oldPrice = catalogItem.Price;
      priceChangedEvent = new ProductPriceChangedIntegrationEvent(catalogItem.Id,
                                                                  productToUpdate.Price,
                                                                  oldPrice);
  }
  // Update current product
  catalogItem = productToUpdate;

  // Just save the updated product if the Product's Price hasn't changed.
  if (!raiseProductPriceChangedEvent)
  {
      await _catalogContext.SaveChangesAsync();
  }
  else  // Publish to event bus only if product price changed
  {
        // Achieving atomicity between original DB and the IntegrationEventLog
        // with a local transaction
        using (var transaction = _catalogContext.Database.BeginTransaction())
        {
           _catalogContext.CatalogItems.Update(catalogItem);
           await _catalogContext.SaveChangesAsync();

           // Save to EventLog only if product price changed
           if(raiseProductPriceChangedEvent)
               await _integrationEventLogService.SaveEventAsync(priceChangedEvent);

           transaction.Commit();
        }

      // Publish the integration event through the event bus
      _eventBus.Publish(priceChangedEvent);

      integrationEventLogService.MarkEventAsPublishedAsync(
                                                priceChangedEvent);
  }

  return Ok();
}

```

Po vytvoření události integrace ProductPriceChangedIntegrationEvent bude transakce, která obsahuje operaci původní domény (aktualizovat položku katalogu), zahrnovat také trvalost události v tabulce EventLog. Díky tomu bude jediná transakce a vždy budete moci ověřit, zda byly zasílány zprávy o událostech.

Tabulka protokolu událostí je aktualizována atomicky s původní databázovou operací pomocí místní transakce se stejnou databází. Pokud dojde k selhání některé z operací, je vyvolána výjimka a transakce vrátí zpět všechny dokončené operace, čímž se zachovává konzistence mezi doménovými operacemi a zprávami událostí uloženými do tabulky.

### <a name="receiving-messages-from-subscriptions-event-handlers-in-receiver-microservices"></a>Příjem zpráv z předplatných: obslužné rutiny událostí v mikroslužbách přijímače

Kromě logiky odběru událostí je nutné implementovat interní kód pro obslužné rutiny událostí integrace (jako metoda zpětného volání). Obslužná rutina události je tam, kde určíte, kde budou přijaty a zpracovány zprávy událostí určitého typu.

Obslužná rutina události nejprve přijme instanci události ze sběrnice událostí. Pak vyhledá komponentu, která se má zpracovat v souvislosti s touto integrační událostí, šíří a uchovává událost jako změnu stavu ve službě přijímače. Pokud například událost ProductPriceChanged vznikla v katalogu služby Catalog, je zpracována v mikroslužbě koše a mění stav v této mikroslužbě koše přijímače, jak je znázorněno v následujícím kódu.

```csharp
namespace Microsoft.eShopOnContainers.Services.Basket.API.IntegrationEvents.EventHandling
{
    public class ProductPriceChangedIntegrationEventHandler :
        IIntegrationEventHandler<ProductPriceChangedIntegrationEvent>
    {
        private readonly IBasketRepository _repository;

        public ProductPriceChangedIntegrationEventHandler(
            IBasketRepository repository)
        {
            _repository = repository;
        }

        public async Task Handle(ProductPriceChangedIntegrationEvent @event)
        {
            var userIds = await _repository.GetUsers();
            foreach (var id in userIds)
            {
                var basket = await _repository.GetBasket(id);
                await UpdatePriceInBasketItems(@event.ProductId, @event.NewPrice, basket);
            }
        }

        private async Task UpdatePriceInBasketItems(int productId, decimal newPrice,
            CustomerBasket basket)
        {
            var itemsToUpdate = basket?.Items?.Where(x => int.Parse(x.ProductId) ==
                productId).ToList();
            if (itemsToUpdate != null)
            {
                foreach (var item in itemsToUpdate)
                {
                    if(item.UnitPrice != newPrice)
                    {
                        var originalPrice = item.UnitPrice;
                        item.UnitPrice = newPrice;
                        item.OldUnitPrice = originalPrice;
                    }
                }
                await _repository.UpdateBasket(basket);
            }
        }
    }
}
```

Obslužná rutina události musí ověřit, zda produkt existuje v žádné z instancí koše. Také aktualizuje cenu položky pro každou související položku řádku košíku. Nakonec se vytvoří výstraha, která uživateli zobrazí informace o změně ceny, jak je znázorněno na obrázku 6-24.

![Snímek obrazovky prohlížeče znázorňujícího oznámení o změně ceny na uživatelském košíku](./media/subscribe-events/display-item-price-change.png)

**Obrázek 6-24**. Zobrazení změny ceny položky v košíku, jak se sdělují událostmi integrace

## <a name="idempotency-in-update-message-events"></a>Idempotence v událostech zprávy Update

Důležitým aspektem událostí aktualizace zpráv je to, že selhání v jakémkoli bodě komunikace by mělo způsobit opakování zprávy. Jinak se úloha na pozadí může pokusit publikovat událost, která už je publikovaná, a vytvořit tak konflikt časování. Je nutné zajistit, aby byly aktualizace buď idempotentní, nebo aby poskytovaly dostatek informací, aby bylo možné zjistit, zda je duplicitní, zahozena a odeslána zpět pouze jedna odpověď.

Jak bylo uvedeno dříve, idempotence znamená, že operaci lze provést několikrát, aniž by došlo ke změně výsledku. V prostředí pro zasílání zpráv, jako při komunikaci událostí, je událost idempotentní, pokud se dá doručit víckrát, aniž by se změnil výsledek pro mikroslužbu přijímače. To může být nutné z důvodu povahy samotné události nebo z důvodu způsobu, jakým systém událost zpracovává. Zpráva idempotence je důležitá v jakékoli aplikaci, která používá zasílání zpráv, nejen v aplikacích, které implementují model sběrnice událostí.

Příkladem operace idempotentní je příkaz SQL, který vkládá data do tabulky pouze v případě, že tato data v tabulce ještě nejsou. Nezáleží na tom, kolikrát spustíte příkaz Insert jazyka SQL. výsledek bude stejný, tabulka bude obsahovat tato data. Idempotence podobným způsobem může být také nutné při práci se zprávami, pokud je možné zprávy potenciálně odeslat, a proto je zpracovat více než jednou. Pokud například logika opakování způsobí, že odesílatel pošle přesně stejnou zprávu více než jednou, musíte se ujistit, že je idempotentní.

Je možné navrhnout zprávy idempotentní. Můžete například vytvořit událost s informacemi "nastavit cenu produktu na $25" místo "Přidat $5 k ceně produktu". První zprávu můžete bezpečně zpracovat několikrát a výsledek bude stejný. Ta není pro druhou zprávu pravdivá. Ale i v prvním případě nebudete chtít zpracovat první událost, protože systém mohl také odeslat novou událost změny ceny a za novou cenu byste přepsali.

Dalším příkladem může být událost dokončená v pořadí, která se šíří více odběratelům. Je důležité, aby se informace o objednávkách aktualizovaly v jiných systémech, a to i v případě, že existují duplicitní události zpráv pro stejnou událost – dokončeno.

Je vhodné mít nějaký druh identity na událost, abyste mohli vytvořit logiku, která vynutila, že každá událost je zpracována pouze jednou pro každého příjemce.

Některé zpracování zpráv je ze své podstaty idempotentní. Například pokud systém vygeneruje miniatury obrázků, může to být bez ohledu na to, kolikrát je zpracována zpráva o vygenerované miniatuře; Výsledkem je, že jsou vygenerovány miniatury a jsou vždy stejné. Na druhé straně operace, jako je například volání brány pro platby za účelem účtování platební karty, nemusí být idempotentní vůbec. V těchto případech je potřeba zajistit, aby zpracování zprávy bylo ve více časech.

### <a name="additional-resources"></a>Další zdroje

- **Dodržuje se zpráva idempotence** \
  <https://docs.microsoft.com/previous-versions/msp-n-p/jj591565(v=pandp.10)#honoring-message-idempotency>

## <a name="deduplicating-integration-event-messages"></a>Odstraňování duplicitních zpráv událostí integrace

Můžete zajistit, aby byly události zpráv odesílány a zpracovávány pouze jednou pro předplatitele na různých úrovních. Jedním ze způsobů je použít funkci odstranění duplicit nabízenou infrastrukturou zasílání zpráv, kterou používáte. Další je implementace vlastní logiky v cílové mikroslužbě. Nejlepším řešením je použití ověření na úrovni přenosu i na úrovni aplikace.

### <a name="deduplicating-message-events-at-the-eventhandler-level"></a>Odstranění duplicit událostí zpráv na úrovni EventHandler

Jedním ze způsobů, jak zajistit, že událost je zpracovávána pouze jednou příjemcem, je implementace určité logiky při zpracování událostí zpráv v obslužných rutinách událostí. Například to je přístup, který se používá v aplikaci eShopOnContainers, jak můžete vidět ve [zdrojovém kódu třídy UserCheckoutAcceptedIntegrationEventHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) , když přijme událost integrace UserCheckoutAcceptedIntegrationEvent. (V tomto případě jsme CreateOrderCommand pomocí IdentifiedCommand, pomocí eventMsg. RequestId jako identifikátoru, před odesláním obslužné rutině příkazu).

### <a name="deduplicating-messages-when-using-rabbitmq"></a>Odstranění duplicit zpráv při použití RabbitMQ

Dojde-li k přerušovanému výpadku sítě, mohou být zprávy duplikovány a přijímač zpráv musí být připraven na zpracování duplicitních zpráv. Pokud je to možné, přijímače by měly zpracovávat zprávy idempotentní způsobem, který je lepší, než je výslovně zpracovává odstranění duplicit.

Podle [dokumentace RabbitMQ](https://www.rabbitmq.com/reliability.html#consumer)se zobrazí zpráva o tom, že pokud se pošle zpráva příjemci a pak se znovu zařadila do fronty (protože nebyla potvrzena před zahozením připojení k uživateli), pak RabbitMQ nastaví příznak opětovného doručení na něj, když se znovu doručí (ať už u stejného příjemce nebo na jiný).

Pokud je nastaven příznak "", příjemce musí brát v úvahu, protože zpráva již mohla být zpracována. Ale to není zaručené; Zpráva by nikdy nebyla přes příjemce po ukončení služby Zprostředkovatel zpráv, možná kvůli problémům se sítí. Na druhé straně, pokud není nastaven příznak "", je zaručeno, že zpráva nebyla odeslána více než jednou. Proto přijímač potřebuje k odstranění duplicitních zpráv nebo zpracování zpráv v idempotentní způsobem pouze v případě, že je ve zprávě nastaven příznak "předáno".

### <a name="additional-resources"></a>Další zdroje

- **Rozvětvené eShopOnContainers s použitím NServiceBus (konkrétní software)**  \
    <https://go.particular.net/eShopOnContainers>

-  \ **zpráv řízených událostmi**
    <https://patterns.arcitura.com/soa-patterns/design_patterns/event_driven_messaging>

- **Jimmy Bogard. Refaktoring směrem k odolnosti: vyhodnocování \ spojovacích zařízení**
    <https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/>

-  \ **kanálu pro publikování a odběr**
    <https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html>

- **Komunikace mezi ohraničenými kontexty** \
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591572(v=pandp.10)>

- Konečné \ **konzistence**
    <https://en.wikipedia.org/wiki/Eventual_consistency>

- **Philip Brown. Strategie pro integraci ohraničených kontextů** \
    <https://www.culttt.com/2014/11/26/strategies-integrating-bounded-contexts/>

- **Chris Richardson. Vývoj transakčních mikroslužeb pomocí agregací, zdroje událostí a CQRS – část 2** \
    <https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson>

- **Chris Richardson. \ vzorového zdroje událostí**
    <https://microservices.io/patterns/data/event-sourcing.html>

- **Představujeme \ zdrojů událostí**
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591559(v=pandp.10)>

- **Databáze úložiště událostí** Oficiální lokalita. \
    <https://geteventstore.com/>

- **NeNommensený. Správa dat řízená událostmi pro mikroslužby** \
    <https://dzone.com/articles/event-driven-data-management-for-microservices-1>

- **Limit věta** \
    <https://en.wikipedia.org/wiki/CAP_theorem>

- **Co je CAP věta?** \
    <https://www.quora.com/What-Is-CAP-Theorem-1>

- **Úvod do konzistence dat** \
    <https://docs.microsoft.com/previous-versions/msp-n-p/dn589800(v=pandp.10)>

- **Rick Saling. CAP věta: Proč "vše je jiné" s cloudem a Internet** \
    <https://docs.microsoft.com/archive/blogs/rickatmicrosoft/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/>

- **Eric pivovar. LIMIT 12 let později: způsob, jakým se změnila pravidla** \
    <https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed>

- **Azure Service Bus. Zprostředkované zasílání zpráv:  \ zjišťování duplicit**
    <https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25>

- **Průvodce spolehlivostí** (dokumentace RabbitMQ) \
    <https://www.rabbitmq.com/reliability.html#consumer>

> [!div class="step-by-step"]
> [Předchozí](rabbitmq-event-bus-development-test-environment.md)
> [Další](test-aspnet-core-services-web-apps.md)
