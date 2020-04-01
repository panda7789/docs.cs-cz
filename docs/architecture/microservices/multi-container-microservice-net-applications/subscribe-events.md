---
title: Přihlášení k odběru událostí
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Seznamte se s podrobnostmi publikování a předplatného integračních událostí.
ms.date: 01/30/2020
ms.openlocfilehash: 3bfcdb1766a15b1a8e8deab46055f14e1791c2cc
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523594"
---
# <a name="subscribing-to-events"></a>Přihlášení k odběru událostí

Prvním krokem pro použití sběrnice událostí je přihlásit mikroslužeb k události, které chcete přijímat. To by mělo být provedeno v mikroslužbách přijímače.

Následující jednoduchý kód ukazuje, co každý přijímač mikroslužby potřebuje implementovat `Startup` při spuštění služby (to znamená, že ve třídě), takže se přihlásí k odběru událostí, které potřebuje. V takovém případě `basket-api` mikroslužby musí `ProductPriceChangedIntegrationEvent` přihlásit k odběru a `OrderStartedIntegrationEvent` zprávy.

Například při přihlášení k odběru `ProductPriceChangedIntegrationEvent` události, který dělá mikroslužbu košíku vědomi jakékoli změny ceny produktu a umožňuje upozornit uživatele o změně, pokud je tento produkt v košíku uživatele.

```csharp
var eventBus = app.ApplicationServices.GetRequiredService<IEventBus>();

eventBus.Subscribe<ProductPriceChangedIntegrationEvent,
                   ProductPriceChangedIntegrationEventHandler>();

eventBus.Subscribe<OrderStartedIntegrationEvent,
                   OrderStartedIntegrationEventHandler>();

```

Po spuštění tohoto kódu bude mikroslužba odběratele naslouchat prostřednictvím kanálů RabbitMQ. Při doručení jakékoli zprávy typu ProductPriceChangedIntegrationEvent kód vyvolá obslužnou rutinu události, která je mu předána, a zpracuje událost.

## <a name="publishing-events-through-the-event-bus"></a>Publikování událostí prostřednictvím sběrnice událostí

Nakonec odesílatel zprávy (původ mikroslužby) publikuje události integrace s kódem podobný následujícímu příkladu. (Toto je zjednodušený příklad, který nebere v úvahu nedělitost.) Podobný kód byste implementovali vždy, když událost musí být šířena ve více mikroslužbách, obvykle hned po potvrzení dat nebo transakcí z mikroslužby původu.

Nejprve objekt implementace sběrnice událostí (na základě RabbitMQ nebo na základě sběrnice) by být vložen a konstruktoru řadiče, jako v následujícím kódu:

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

Potom jej použijete z metod ovladače, například v metodě UpdateProduct:

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

V tomto případě vzhledem k tomu, že původ mikroslužby je jednoduchý crud mikroslužby, tento kód je umístěn přímo do řadiče webového rozhraní API.

V pokročilejší mikroslužeb, jako při použití přístupů CQRS, `CommandHandler` může být `Handle()` implementována ve třídě v rámci metody.

### <a name="designing-atomicity-and-resiliency-when-publishing-to-the-event-bus"></a>Navrhování nedělitosti a odolnosti při publikování na sběrnici událostí

Při publikování událostí integrace prostřednictvím systému distribuovaného zasílání zpráv, jako je sběrnice událostí, máte problém atomicky aktualizovat původní databázi a publikování události (to znamená, že obě operace dokončena nebo žádná z nich). Například ve zjednodušeném příkladu zobrazeném dříve kód potvrdí data do databáze při změně ceny produktu a poté publikuje zprávu ProductPriceChangedIntegrationEvent. Zpočátku může vypadat nezbytné, aby tyto dvě operace byly provedeny atomicky. Pokud však používáte distribuovanou transakci zahrnující databázi a zprostředkovatele zpráv, stejně jako ve starších systémech, jako je [služba Microsoft Message Queuing (MSMQ),](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx)nedoporučujeme to z důvodů popsaných [teorém emistorem CAP](https://www.quora.com/What-Is-CAP-Theorem-1).

V podstatě můžete použít mikroslužeb k vytváření škálovatelných a vysoce dostupných systémů. Zjednodušení poněkud, cap teorém říká, že nelze vytvořit (distribuované) databáze (nebo mikroslužbu, která vlastní svůj model), který je neustále k dispozici, silně konzistentní *a* tolerantní k libovolnému oddílu. Je nutné zvolit dvě z těchto tří vlastností.

V architekturách založených na mikroslužbách byste měli zvolit dostupnost a toleranci a měli byste deemphasize silné konzistence. Proto ve většině moderních aplikací založených na mikroslužbách obvykle nechcete používat distribuované transakce ve zasílání zpráv, stejně jako při implementaci [distribuovaných transakcí](https://docs.microsoft.com/previous-versions/windows/desktop/ms681205(v=vs.85)) založených na koordinátoru DTC (Windows Distributed Transaction Coordinator) se [službou MSMQ](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx).

Vraťme se k původnímu problému a jeho příkladu. Pokud dojde k chybě služby po aktualizaci databáze (v tomto \_případě hned za řádek kódu s kontextem. SaveChangesAsync()), ale před publikováním události integrace může být celkový systém nekonzistentní. To může být důležité pro podnikání, v závislosti na konkrétní obchodní operace, kterou máte co do činění s.

Jak již bylo zmíněno dříve v části architektura, můžete mít několik přístupů pro řešení tohoto problému:

- Použití úplného [vzoru získávání událostí](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing).

- Použití [dolování transakční protokol](https://www.scoop.it/t/sql-server-transaction-log-mining).

- Použití [vzoru Pošta k poště k poště k poště .](https://www.kamilgrzybek.com/design/the-outbox-pattern/) Toto je transakční tabulka pro uložení událostí integrace (rozšíření místní transakce).

V tomto scénáři pomocí úplné události Sourcing (ES) vzor je *the* jedním z nejlepších přístupů, ne-li nejlepší. V mnoha scénářích aplikace však nemusí být možné implementovat úplný systém ES. ES znamená ukládání pouze události domény v transakční databázi, namísto ukládání aktuálních dat stavu. Ukládání pouze události domény může mít velké výhody, jako je například mít historii vašeho systému k dispozici a je schopen určit stav systému v každém okamžiku v minulosti. Implementace úplného systému ES však vyžaduje, abyste přezákladňovali většinu systému a zavedli mnoho dalších složitostí a požadavků. Například byste chtěli použít databázi speciálně vyrobenou pro získávání událostí, jako je [například úložiště událostí](https://eventstore.org/), nebo databázi orientovanou na dokumenty, jako je Azure Cosmos DB, MongoDB, Cassandra, CouchDB nebo RavenDB. ES je skvělý přístup k tomuto problému, ale není nejjednodušší řešení, pokud jste již obeznámeni s event sourcing.

Možnost použít dolování transakční protokol zpočátku vypadá velmi transparentní. Chcete-li však použít tento přístup, mikroslužby musí být spojeny s protokolem transakcí RDBMS, jako je například protokol transakcí serveru SQL Server. To pravděpodobně není žádoucí. Další nevýhodou je, že aktualizace nižší úrovně zaznamenané v transakčním protokolu nemusí být na stejné úrovni jako události integrace na vysoké úrovni. Pokud ano, proces zpětného inženýrství těchto operací transakční protokol může být obtížné.

Vyvážený přístup je kombinací transakční databázové tabulky a zjednodušeného vzoru ES. Můžete použít stav, jako je například "připraven o publikování události", který nastavíte v původní události, když ji potvrdíte do tabulky událostí integrace. Potom se pokusíte publikovat událost do sběrnice událostí. Pokud akce publikování události úspěšné, spustíte jinou transakci ve službě původu a přesunout stav z "připraven o publikování události" na "událost již byla publikována."

Pokud akce publikování události v sběrnici události selže, data stále nebude nekonzistentní v rámci mikroslužby původu – je stále označenjako "připraven k publikování události" a s ohledem na ostatní služby nakonec bude konzistentní. Vždy můžete mít úlohy na pozadí, které kontrolují stav transakcí nebo událostí integrace. Pokud úloha najde událost ve stavu "připraveno k publikování události", může se pokusit znovu publikovat tuto událost do sběrnice událostí.

Všimněte si, že s tímto přístupem přetrvává pouze události integrace pro každou mikroslužbu původu a pouze události, které chcete komunikovat s jinými mikroslužbami nebo externími systémy. Naproti tomu v úplném systému ES ukládáte také všechny události domény.

Tento vyvážený přístup je proto zjednodušeným systémem ES. Potřebujete seznam integračních událostí s jejich aktuálním stavem ("připraveno k publikování" versus "publikováno"). Ale stačí implementovat tyto stavy pro události integrace. A v tomto přístupu není nutné ukládat všechna data domény jako události v transakční databázi, jako byste v úplném systému ES.

Pokud již používáte relační databázi, můžete použít transakční tabulku k ukládání událostí integrace. K dosažení nedělitelnosti v aplikaci, použijte dvoustupňový proces založený na místní transakce. V podstatě máte Tabulku IntegrationEvent ve stejné databázi, kde máte entity domény. Tato tabulka funguje jako pojištění pro dosažení nedělitosti, takže zahrnete trvalé události integrace do stejných transakcí, které posuzují data domény.

Krok za krokem, proces jde takto:

1. Aplikace spustí transakci místní databáze.

2. Potom aktualizuje stav entit domény a vloží událost do tabulky událostí integrace.

3. Nakonec potvrdí transakci, takže získáte požadovanou nedělitost a pak

4. Událost publikujete nějak (další).

Při implementaci kroků publikování událostí máte tyto možnosti:

- Publikovat událost integrace hned po potvrzení transakce a použít jinou místní transakci označit události v tabulce jako publikována. Potom použijte tabulku stejně jako artefakt ke sledování událostí integrace v případě problémů ve vzdálených mikroslužeb a provádět kompenzační akce na základě událostí uložené integrace.

- Použijte tabulku jako druh fronty. Samostatné vlákno aplikace nebo proces dotazuje tabulku událostí integrace, publikuje události do sběrnice událostí a pak použije místní transakci k označení událostí jako publikovaných.

Obrázek 6-22 ukazuje architekturu pro první z těchto přístupů.

![Diagram nedělitosti při publikování bez mikroslužby pracovníka.](./media/subscribe-events/atomicity-publish-event-bus.png)

**Obrázek 6-22**. Nedělitost při publikování událostí do sběrnice událostí

Přístup znázorněný na obrázku 6-22 chybí další mikroslužeb pracovníka, který má na starosti kontrolu a potvrzení úspěchu publikovaných událostí integrace. V případě selhání, že další kontrolovky pracovní mikroslužby můžete číst události z tabulky a znovu publikovat, to znamená, opakujte krok číslo 2.

O druhý přístup: použijete Tabulka EventLog jako fronty a vždy použít pracovní mikroslužbu k publikování zpráv. V takovém případě je proces podobný tomu, který je znázorněn na obrázku 6-23. To ukazuje další mikroslužbu a tabulka je jeden zdroj při publikování událostí.

![Diagram nedělitosti při publikování s mikroslužbou pracovního procesu.](./media/subscribe-events/atomicity-publish-worker-microservice.png)

**Obrázek 6-23**. Nedělitnost při publikování událostí do sběrnice událostí s mikroslužbou pracovního procesu

Pro jednoduchost eShopOnContainers ukázka používá první přístup (bez dalších procesů nebo kontrolní mikroslužeb) plus sběrnice událostí. EShopOnContainers však nezpracovává všechny možné případy selhání. V reálné aplikaci nasazené do cloudu, musíte přijmout skutečnost, že problémy nakonec vzniknou a musíte implementovat tuto logiku kontroly a opětovného odeslání. Použití tabulky jako fronty může být efektivnější než první přístup, pokud máte tuto tabulku jako jediný zdroj událostí při jejich publikování (s pracovníkem) prostřednictvím sběrnice událostí.

### <a name="implementing-atomicity-when-publishing-integration-events-through-the-event-bus"></a>Implementace nedělitosti při publikování událostí integrace prostřednictvím sběrnice událostí

Následující kód ukazuje, jak můžete vytvořit jednu transakci zahrnující více objektů DbContext – jeden kontext související s původní data jsou aktualizovány a druhý kontext související s integrationeventlog tabulky.

Všimněte si, že transakce v ukázkovém kódu níže nebude odolná, pokud připojení k databázi mají nějaký problém v době, kdy je spuštěn kód. K tomu může dojít v cloudových systémech, jako je Azure SQL DB, které můžou přesouvat databáze mezi servery. Implementace odolných transakcí ve více kontextech najdete v [části Implementing resilient Entity Framework Core SQL connections](../implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md) dále v této příručce.

Pro přehlednost následující příklad ukazuje celý proces v jedné části kódu. Implementace eShopOnContainers je však ve skutečnosti refaktorována a rozdělí tuto logiku do více tříd, takže je snadnější udržovat.

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

      _integrationEventLogService.MarkEventAsPublishedAsync(
                                                priceChangedEvent);
  }

  return Ok();
}

```

Po ProductPriceChangedIntegrationEvent integrační událost zahrnuje transakce, která ukládá původní operace domény (aktualizace položky katalogu) také trvalost události v tabulce EventLog. Díky tomu je jedna transakce a vždy budete moci zkontrolovat, zda byly odeslány zprávy o událostech.

Tabulka protokolu událostí je atomicky aktualizována původní databázovou operací pomocí místní transakce proti stejné databázi. Pokud některá z operací selže, je vyvolána výjimka a transakce vrátí zpět všechny dokončené operace, čímž se zachová konzistence mezi operacemi domény a zprávami událostí uloženými do tabulky.

### <a name="receiving-messages-from-subscriptions-event-handlers-in-receiver-microservices"></a>Příjem zpráv z předplatných: obslužné rutiny událostí v mikroslužbách příjemce

Kromě logiky odběru událostí je třeba implementovat interní kód pro obslužné rutiny událostí integrace (jako je metoda zpětného volání). Obslužná rutina události je místo, kde určíte, kde budou přijímány a zpracovány zprávy o událostech určitého typu.

Obslužná rutina události nejprve obdrží instanci události z sběrnice událostí. Pak vyhledá součást, která má být zpracována související s událostí integrace, šíření a trvalé události jako změna stavu v mikroslužbě příjemce. Například pokud ProductPriceChanged událost pochází z mikroslužby katalogu, je zpracována v mikroslužbě košíku a změní stav v tomto košíku příjemce mikroslužeb také, jak je znázorněno v následujícím kódu.

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

Obslužná rutina události musí ověřit, zda produkt existuje v některé z instancí košíku. Aktualizuje také cenu zboží pro každou související řádkovou položku košíku. Nakonec vytvoří výstrahu, která se zobrazí uživateli o změně ceny, jak je znázorněno na obrázku 6-24.

![Snímek obrazovky s prohlížečem zobrazujícím oznámení o změně ceny v uživatelském košíku](./media/subscribe-events/display-item-price-change.png)

**Obrázek 6-24**. Zobrazení změny ceny položky v košíku, jak je sděleno událostmi integrace

## <a name="idempotency-in-update-message-events"></a>Idempotence v událostech zpráv aktualizace

Důležitým aspektem události zprávy aktualizace je, že selhání v libovolném okamžiku v komunikaci by měla způsobit zprávu opakovat. V opačném případě se úloha na pozadí může pokusit publikovat událost, která již byla publikována, a vytvořit tak spor. Musíte se ujistit, že aktualizace jsou idempotentní nebo že poskytují dostatek informací, abyste zajistili, že můžete zjistit duplikát, zahodit je a odeslat zpět pouze jednu odpověď.

Jak již bylo uvedeno dříve, idempotence znamená, že operace může být provedena vícekrát bez změny výsledku. V prostředí zasílání zpráv, jako při komunikaci událostí, událost je idempotentní, pokud může být doručena vícekrát beze změny výsledku pro mikroslužbu příjemce. To může být nezbytné z důvodu povahy samotné události nebo z důvodu způsobu, jakým systém zpracovává událost. Idempotence zprávy je důležité v každé aplikaci, která používá zasílání zpráv, nikoli pouze v aplikacích, které implementují vzor sběrnice událostí.

Příkladem idempotentní operace je příkaz SQL, který vkládá data do tabulky pouze v případě, že tato data ještě nejsou v tabulce. Nezáleží na tom, kolikrát spustíte, že vložit příkaz SQL; výsledek bude stejný – tabulka bude tato data obsahovat. Idempotence, jako je tato může být také nezbytné při práci se zprávami, pokud zprávy mohou být potenciálně odeslány a proto zpracovány více než jednou. Například pokud logika opakování způsobí, že odesílatel odeslat přesně stejnou zprávu více než jednou, je třeba se ujistit, že je idempotentní.

Je možné navrhnout idempotentní zprávy. Můžete například vytvořit událost s nápisem "nastavit cenu produktu na 25 USD" namísto "přidat 5 USD k ceně produktu". Můžete bezpečně zpracovat první zprávu libovolný počet opakování a výsledek bude stejný. To neplatí pro druhou zprávu. Ale i v prvním případě možná nebudete chtít zpracovat první událost, protože systém mohl také odeslat novější událost změny ceny a novou cenu byste přepsali.

Dalším příkladem může být událost dokončená pořadí, která se šíří více odběratelům. Je důležité, aby informace o objednávce byly aktualizovány v jiných systémech pouze jednou, i když existují duplicitní události zprávy pro stejnou událost dokončení objednávky.

Je vhodné mít nějaký druh identity na událost, takže můžete vytvořit logiku, která vynucuje, že každá událost je zpracována pouze jednou na příjemce.

Některé zpracování zpráv je ze své podstaty idempotentní. Pokud například systém generuje miniatury obrázků, nemusí záležet na tom, kolikrát bude zpráva o generované miniaturě zpracována; Výsledkem je, že miniatury jsou generovány a jsou pokaždé stejné. Na druhou stranu operace, jako je volání platební brány k platbě z kreditní karty, nemusí být vůbec idempotentní. V těchto případech je třeba zajistit, že zpracování zprávy vícekrát má účinek, který očekáváte.

### <a name="additional-resources"></a>Další zdroje

- **Ctít idempotenci zprávy** \
  <https://docs.microsoft.com/previous-versions/msp-n-p/jj591565(v=pandp.10)#honoring-message-idempotency>

## <a name="deduplicating-integration-event-messages"></a>Odstranění duplicitních zpráv událostí integrace

Můžete se ujistit, že události zprávy jsou odesílány a zpracovávány pouze jednou na odběratele na různých úrovních. Jedním ze způsobů je použití funkce odstranění duplicit, kterou nabízí infrastruktura zasílání zpráv, kterou používáte. Dalším je implementovat vlastní logiku v cílové mikroslužeb. S ověřením na úrovni přenosu i na úrovni aplikace je vaše nejlepší sázka.

### <a name="deduplicating-message-events-at-the-eventhandler-level"></a>Odstranění duplicitních událostí zpráv na úrovni EventHandler

Jedním ze způsobů, jak zajistit, že událost je zpracována pouze jednou libovolným příjemcem je implementací určité logiky při zpracování událostí zprávy v obslužných rutinách událostí. Například to je přístup používaný v aplikaci eShopOnContainers, jak můžete vidět ve [zdrojovém kódu třídy UserCheckoutAcceptedIntegrationEventHandler,](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) když obdrží událost integrace UserCheckoutAcceptedIntegrationEvent. (V tomto případě jsme zabalit CreateOrderCommand s IdentifiedCommand, pomocí eventMsg.RequestId jako identifikátor, před odesláním do obslužné rutiny příkazu).

### <a name="deduplicating-messages-when-using-rabbitmq"></a>Odstranění duplicitzpráv při používání funkce RabbitMQ

Dojde-li k občasnému selhání sítě, mohou být zprávy duplikovány a příjemce zprávy musí být připraven ke zpracování těchto duplicitních zpráv. Pokud je to možné, příjemci by měli zpracovávat zprávy idempotentním způsobem, což je lepší než explicitní zpracování s deduplikací.

Podle [dokumentace RabbitMQ](https://www.rabbitmq.com/reliability.html#consumer), "Pokud je zpráva doručena spotřebiteli a pak requeued (protože nebyla potvrzena před připojení spotřebitele maže, například), pak RabbitMQ nastaví znovu doručena příznak na něj, když je doručena znovu (zda ke stejnému spotřebiteli nebo jiný).

Pokud je nastaven příznak "redelivered", příjemce musí vzít v úvahu, protože zpráva již mohla být zpracována. To však není zaručeno; zpráva pravděpodobně nikdy nedosáhlpříjemce poté, co opustil zprostředkovatele zpráv, pravděpodobně z důvodu problémů se sítí. Na druhou stranu, pokud "redelivered" příznak není nastaven, je zaručeno, že zpráva nebyla odeslána více než jednou. Příjemce proto potřebuje deduplikovat zprávy nebo zpracovat zprávy idempotentním způsobem pouze v případě, že je ve zprávě nastaven příznak "redelivered".

### <a name="additional-resources"></a>Další zdroje

- **Vidlicí eShopOnKontejnery používající NServiceBus (konkrétní software)** \
    <https://go.particular.net/eShopOnContainers>

- **Zasílání zpráv řízených událostmi** \
    <https://patterns.arcitura.com/soa-patterns/design_patterns/event_driven_messaging>

- **Jimmyho Bogarda. Refaktoring směrem k odolnosti: Hodnocení spojky** \
    <https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/>

- **Kanál publikování a odběru** \
    <https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html>

- **Komunikace mezi ohraničené kontexty** \
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591572(v=pandp.10)>

- **Konečná konzistence** \
    <https://en.wikipedia.org/wiki/Eventual_consistency>

- **Philipbrown, to je můj otec. Strategie pro integraci ohraničených kontextů** \
    <https://www.culttt.com/2014/11/26/strategies-integrating-bounded-contexts/>

- **Chrise Richardsona. Vývoj transakčních mikroslužeb pomocí agregátů, zdrojů událostí a CQRS - část 2** \
    <https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson>

- **Chrise Richardsona. Vzor získávání událostí** \
    <https://microservices.io/patterns/data/event-sourcing.html>

- **Představujeme získávání událostí** \
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591559(v=pandp.10)>

- **Databáze úložiště událostí**. Oficiální stránky. \
    <https://geteventstore.com/>

- **Patrik Nommensen. Správa dat řízená událostmi pro mikroslužby** \
    <https://dzone.com/articles/event-driven-data-management-for-microservices-1>

- **Teorém SZP** \
    <https://en.wikipedia.org/wiki/CAP_theorem>

- **Co je cap teorém?** \
    <https://www.quora.com/What-Is-CAP-Theorem-1>

- **Základní nátěr konzistence dat** \
    <https://docs.microsoft.com/previous-versions/msp-n-p/dn589800(v=pandp.10)>

- **Rick Saling. Teorém SZP: Proč je "Všechno je jiné" s cloudem a internetem** \
    <https://docs.microsoft.com/archive/blogs/rickatmicrosoft/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/>

- **Eric Brewer, to je ono. SZP o dvanáct let později: Jak se změnila "pravidla"** \
    <https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed>

- **Azure Service Bus. Zprostředkované zasílání zpráv: vyhledávání duplicit**  \
    <https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25>

- **Průvodce spolehlivostí** (dokumentace RabbitMQ) \
    <https://www.rabbitmq.com/reliability.html#consumer>

> [!div class="step-by-step"]
> [Předchozí](rabbitmq-event-bus-development-test-environment.md)
> [další](test-aspnet-core-services-web-apps.md)
