---
title: Přihlášení k odběru událostí
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Zjistěte podrobnosti o publikování a přihlášení k odběru událostí integrace.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/02/2018
ms.openlocfilehash: 962d12c054bed3b2623283e17f83b8466ab2811b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61864594"
---
# <a name="subscribing-to-events"></a>Přihlášení k odběru událostí

Prvním krokem pro používání událostí Service bus je odběru mikroslužeb k událostem, které chtějí dostávat. Který se má počítat v mikroslužbách příjemce.

Následující jednoduchý kód ukazuje, co každá mikroslužba příjemce musí implementovat při spuštění služby (to znamená v `Startup` třídy), přihlásí se k události se vyžaduje. V takovém případě `basket.api` mikroslužeb je potřeba se přihlásit k odběru `ProductPriceChangedIntegrationEvent` a `OrderStartedIntegrationEvent` zprávy.

Například při přihlášení k odběru `ProductPriceChangedIntegrationEvent` události, která provádí mikroslužeb nákupní košík znát některé změny cena produktu a umožňuje ji upozornit uživatele o změnu, je-li tento produkt je v koši uživatele.

```csharp
var eventBus = app.ApplicationServices.GetRequiredService<IEventBus>();

eventBus.Subscribe<ProductPriceChangedIntegrationEvent,
                   ProductPriceChangedIntegrationEventHandler>();

eventBus.Subscribe<OrderStartedIntegrationEvent,
                   OrderStartedIntegrationEventHandler>();

```

Po spuštění tohoto kódu mikroslužeb odběratele se naslouchání prostřednictvím RabbitMQ kanálů. Všechny zprávy typu ProductPriceChangedIntegrationEvent dorazí kód vyvolá obslužnou rutinu události, která je předána a zpracovává události.

## <a name="publishing-events-through-the-event-bus"></a>Publikování událostí prostřednictvím událostí Service bus

Nakonec odesílatele zprávy (mikroslužeb původu) publikuje události integrace s kódem, podobně jako v následujícím příkladu. (Toto je zjednodušený příklad, který nemá atomicitu v úvahu). Podobný kód by implementovat pokaždé, když událost musí být šířena napříč několika mikroslužeb, obvykle hned po potvrzení dat nebo transakcí z mikroslužeb původu.

Objekt implementace sběrnice událostí (podle RabbitMQ nebo podle služby Service bus) by nejprve vloženy v konstruktoru řadič, stejně jako v následujícím kódu:

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

Pak použijete jej z metody vašeho kontroleru, stejně jako v metodě UpdateProduct:

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

V takovém případě původu mikroslužeb je jednoduché mikroslužby CRUD, tento kód nachází vpravo do kontroleru webového rozhraní API.

V pokročilejších mikroslužeb, stejně jako při použití modelu CQRS přístupy, se dá implementovat v `CommandHandler` třídy v rámci `Handle()` metody.

### <a name="designing-atomicity-and-resiliency-when-publishing-to-the-event-bus"></a>Navrhování atomicitu a odolnost proti chybám při publikování událostí Service bus

Při publikování události integrace prostřednictvím distribuované zasílání zpráv systému, jako je vaše událostí Service bus, budete mít problém atomicky aktualizuje původní databáze a publikování události (to znamená, jak dokončení operace nebo žádná z nich). Například v zjednodušený příklad je uvedeno výše, kód potvrdí data do databáze při cena produktu se změnilo a pak publikuje zprávu ProductPriceChangedIntegrationEvent. Na začátku může vypadat základní atomicky provést tyto dvě operace. Ale pokud používáte distribuovaných transakcí týkajících se databáze a zprávy zprostředkovatele, stejně jako v starší systémy, jako je [Microsoft Message Queuing (MSMQ)](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx), toto nastavení nedoporučujeme důvodů popsaného [Věty](https://www.quora.com/What-Is-CAP-Theorem-1).

V podstatě mikroslužeb použijete k sestavení škálovatelné a vysoce dostupné systémy. Zjednodušení trochu, věty říká, že nemůže vytvořit databázi (distribuovaným) (nebo mikroslužeb, který vlastní svůj model), který je neustále k dispozici, silně konzistentních *a* vůči žádný oddíl. Musíte zvolit dvě z těchto tří vlastností.

V architekturách založených na mikroslužbách byste měli zvolit dostupnost a odolnost a měli omezit silnou konzistenci. Proto se ve většině moderních aplikací založených na mikroslužbách, obvykle nechcete používat distribuovaných transakcí v zasílání zpráv, stejně jako při implementaci [distribuované transakce](https://docs.microsoft.com/previous-versions/windows/desktop/ms681205(v=vs.85)) založené na Windows distribuované transakce Koordinátor (DTC) s [MSMQ](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx).

Vraťme se k počáteční problému a jeho příklad. Pokud po aktualizaci databáze dojde k chybě služby (v tomto případě klikněte pravým tlačítkem za řádkem kódu pomocí \_kontextu. SaveChangesAsync()), ale před publikováním integrace událostí může nekonzistenci celého systému. To může být pro důležité obchodní informace, v závislosti na konkrétní obchodní operace, které se zabývají.

Jak je uvedeno výše v části architektura, může mít několik přístupů pro řešení tohoto problému:

- Použití úplného [model Event Sourcing](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing).

- Pomocí [protokol transakcí dolování](https://www.scoop.it/t/sql-server-transaction-log-mining).

- Použití [pošta k odeslání vzoru](http://gistlabs.com/2014/05/the-outbox/). Toto je transakční tabulku pro ukládání událostí integrace (rozšíření místní transakce).

V tomto scénáři použití úplné modelu Event Sourcing (ES) je jedním z osvědčených postupů, není-li *nejlepší*. V mnoha scénářích aplikací, ale nemusí být schopni implementovat úplnou ES operace. ES znamená, že ukládání pouze události domény v transakční databáze, místo uložení aktuální data o stavu. Uložení pouze událostí domény může mít skvělé výhody, jako je například s historii vašeho systému, které jsou k dispozici a nebudou moct určení stavu systému v každém okamžiku v minulosti. Ale implementace úplnou ES vyžaduje, abyste úprava architektury většina vašeho systému a přináší mnoho dalších složitosti a požadavky. Například můžete chcete použít databázi vytvořené speciálně pro model event sourcing, například [události Store](https://eventstore.org/), nebo databáze dokumentově orientované, jako je Azure Cosmos DB, MongoDB, Cassandra, CouchDB nebo RavenDB. ES je skvělé přístup k tomuto problému, ale ne Nejjednodušším řešením, pokud jste již obeznámeni s modelem event sourcing.

Možnost použití transakční protokol dolování zpočátku vypadá velmi transparentní. Ale pro tuto metodu použijte mikroslužbách musí být vázány na protokol transakce relační databázový systém, jako je například protokolu transakcí serveru SQL Server. To je pravděpodobně není žádoucí. Jiné nevýhodou je, že nízké úrovně aktualizací zaznamenaných v transakčním protokolu nemusí být na stejné úrovni jako základní integrace událostí. Pokud ano, proces zpětnou tyto operace protokolu transakcí může být obtížné.

Vyvážený přístup je kombinace zjednodušený model ES a tabulku transakcí databáze. Můžete použít stav, jako je například "připraveno k publikování událostí,", které jste nastavili v původní událost, když ji zapište do tabulky událostí integrace. Pak se pokusí publikovat událost událostí Service bus. Pokud události publikování akce proběhne úspěšně, můžete spustit jinou transakcí ve službě původu a přesouvat stavu "připraveno k publikování události" na "událost již publikována."

Pokud akce události publikování událostí Service bus se nezdaří, data stále budou konzistentní v rámci původu mikroslužeb, stále je označen jako "připraveno k publikování události", a s ohledem na ostatní služby, nakonec bude konzistentní vzhledem k aplikacím. Vždy máte úlohy na pozadí kontroluje se stav transakce nebo integrace událostí. Pokud úloha nalezne událost ve stavu "připraveno k publikování události", můžete zkusit znovu publikovat tuto událost do událostí Service bus.

Všimněte si, že s tímto přístupem uchováváte pouze události integrace u jednotlivých mikroslužeb původu a pouze události, které chcete komunikovat s jinými mikroslužby nebo externí systémy. Naproti tomu v rámci systému ES ukládat všechny události domény i.

Proto tento vyvážené přístup je zjednodušené ES. Potřebujete seznam integrace událostí s jejich aktuální stav ("připraveno k publikování" a "publikováno"). Ale potřebujete implementovat tyto stavy pro události integrace. A v takovém případě nepotřebujete k uložení všech vašich dat domény jako události v transakční databází, jako byste to udělali v plném ES systému.

Pokud už používáte relační databáze, můžete transakční tabulku pro ukládání událostí integrace. K dosažení atomicitu ve vaší aplikaci, použít dvoustupňový proces založené na místní transakce. V podstatě máte tabulku IntegrationEvent ve stejné databázi, ve které máte doménu entity. Tuto tabulku funguje jako pojištění pro dosažení atomicitu tak, že zahrnete trvalé události integrace do stejné transakce, které se potvrzují data vaší domény.

Krok za krokem procesu prochází tímto způsobem:

1. Aplikace spustí místní databázové transakce.

2. Pak aktualizuje stav entity domény a vloží do tabulky události integrace událost.

3. Nakonec svého potvrzení transakce, tak, abyste dosáhli požadovaného atomicitu a pak

4. Nějakým způsobem publikovat událost (Další).

Při implementaci kroky k publikování událostí, máte tyto možnosti:

- Publikování události integrace hned po potvrzení transakce a k označení události v tabulce jako publikování použijte jinou místní transakcí. Potom použijte tabulce stejně jako artefakt pro sledování události integrace v případě problémů v vzdálené mikroslužeb a provádět vyrovnávací akce na základě událostí uložených integrace.

- Tabulku použijte jako typ fronty. Vlákna samostatné aplikace nebo proces dotazuje tabulku události integrace, publikuje události pro události Service bus a pak používá k označení události publikování místní transakce.

Obrázek 6 – 22 ukazuje architekturu první z těchto přístupů.

![Jeden ze způsobů zpracování atomicitu při publikování události: pomocí jedné transakce na potvrzení události do protokolu událostí tabulky a pak opět transakce publikovat (používané v aplikaci eShopOnContainers)](./media/image23.png)

**Obrázek 6 – 22**. Atomicitu při publikování událostí do událostí Service bus

Přístup znázorněný v obrázku 6 – 22 chybí pracovní mikroslužeb, který má na starosti kontrole a potvrzení úspěšné publikované integrace událostí. V případě selhání můžete tuto další kontrolu pracovního procesu mikroslužeb číst události z tabulky a znovu publikovat, tedy číslo opakujte krok 2.

O druhým přístupem: protokol událostí tabulku použijte jako fronty a vždy použijte mikroslužbě pracovního procesu k publikování zpráv. V takovém případě proces se tímto způsobem zobrazí obrázek 6 – 23. Zobrazí se další mikroslužeb a v tabulce je jediným zdrojem při publikování události.

![Další možností pro zpracování atomicitu: Publikovat do tabulky protokolu událostí a pak další mikroslužeb (pracovník na pozadí) publikování události.](./media/image24.png)

**Obrázek 6 – 23**. Atomicitu při publikování událostí do sběrnice událostí pomocí mikroslužeb pracovního procesu

Pro zjednodušení používá ukázková aplikaci eShopOnContainers první přístup (s žádné další procesy nebo prerequisite checker mikroslužeb) plus událostí Service bus. Aplikaci eShopOnContainers však neošetřuje všechny případy možného selhání. V reálné aplikaci nasadit do cloudu musí si osvojí skutečnost, že bude vzniku nakonec a je nutné implementovat, zkontrolujte a znovu odeslat logiku. Pokud máte danou tabulku jako jediný zdroj událostí při jejich publikování přes Service bus události (s pracovním procesem) může být efektivnější než první přístup pomocí tabulky jako do fronty.

### <a name="implementing-atomicity-when-publishing-integration-events-through-the-event-bus"></a>Implementace atomicitu při publikování události integrace přes Service bus události

Následující kód ukazuje, jak můžete vytvořit jeden transakce zahrnující více objektů DbContext – jeden kontext související s původní data aktualizují a kontextu druhé související tabulce IntegrationEventLog.

Všimněte si, že transakce ve níže uvedeného ukázkového kódu nesmí být odolné pro případ, připojení k databázi mít jakýkoli problém v době, kdy kód běží. To může nastat v cloudové systémy, jako je Azure SQL DB, která může přesun databází mezi servery. Implementace odolných transakce napříč několika kontextech, najdete v článku [implementace odolnost připojení Entity Framework Core SQL](../implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md) dále v tomto průvodci.

Pro přehlednost následující příklad ukazuje celý proces v každé z kódu. Implementace aplikaci eShopOnContainers ale je ve skutečnosti teď vyčleněný a rozdělit tuto logiku na víc tříd tak, aby byl snazší Údržba.

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

Po vytvoření události integrace ProductPriceChangedIntegrationEvent transakce, která ukládá původní operace domény (aktualizace položky katalogu) také zahrnuje trvalou dostupnost události v tabulce protokolu událostí. Díky tomu jedné transakce a bude vždy možné zkontrolovat, zda byly odesílány zprávy o událostech.

Tabulka protokolu událostí se aktualizuje atomicky původní databáze, pomocí operace místní transakce na stejnou databázi. Pokud všechny operace selžou, je vyvolána výjimka a transakce vrátí zpět všechny dokončené operace, proto zachování konzistence mezi operacemi domény a zprávy o událostech uloží do tabulky.

### <a name="receiving-messages-from-subscriptions-event-handlers-in-receiver-microservices"></a>Příjem zpráv z předplatného: obslužných rutin událostí v mikroslužbách příjemce

Kromě logiky odběr událostí budete muset implementovat vnitřní kód pro integraci obslužné rutiny událostí (např. metoda zpětného volání). Obslužná rutina události je, kde zadáte kde přijme a zpracuje zprávy o událostech určitého typu.

Obslužná rutina události nejprve obdrží instanci události z události Service bus. Potom je možné vyhledat součásti, které mají být zpracovány týkající se této události integrace, šíření a při zachování události jako změnu stavu v mikroslužbě příjemce. Například pokud ProductPriceChanged události mohou být v katalogu mikroslužeb, to probíhá v košíku mikroslužeb a změní stav v košíku mikroslužeb tento příjemce i, jak je znázorněno v následujícím kódu.

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

Obslužná rutina události je potřeba ověřit, zda existuje produktu v některé z instancí nákupní košík. Aktualizuje také ceny položky pro každou položku řádku související nákupního košíku. Nakonec vytvoří výstrahu, který se má zobrazit uživateli o změny cen, jak je znázorněno v obrázek 6 – 24.

![Zobrazit v prohlížeči procesu změnit oznámení v košíku uživatele.](./media/image25.png)

**Obrázek 6 – 24**. Zobrazení o změnu cena zboží v košíku, oznámené události integrace

## <a name="idempotency-in-update-message-events"></a>Idempotence v události zpráva aktualizace

Důležitou součástí událostí zpráva aktualizace je, že selhání v libovolném bodě komunikace by nemělo způsobit zprávu, která se zopakuje. V opačném případě úlohy na pozadí může pokusit o publikovat událost, která se už publikoval, vytváření časování. Potřebujete zajistit, že aktualizace jsou idempotentní nebo, že poskytuje dostatek informací k zajištění, že můžete detekovat duplicitní, ho zrušit a odeslání odpovědi back pouze jeden.

Jak bylo uvedeno dříve, idempotence znamená, že operaci lze provést více než jednou beze změny výsledek. V prostředí zasílání zpráv protože při komunikaci události, události je idempotentní, pokud se více než jednou mohl být doručován beze změny výsledek pro mikroslužby příjemce. To může být vzhledem k povaze samotné události nutné nebo kvůli způsobu, jakým systém zpracovává událost. Zpráva idempotence je důležité v jakékoli aplikaci, která se používá pro přenos zpráv, ne jenom v aplikacích, které implementují vzor událostí Service bus.

Příklad idempotentní operace je příkaz jazyka SQL, který vkládá data do tabulky pouze v případě, že data, která už není v tabulce. Není důležité, kolikrát spuštění, které vkládají příkaz SQL Výsledkem bude stejná – tabulce bude obsahovat data. Idempotence tímto způsobem může být také nezbytné při práci s zprávy, pokud se zprávy můžou potenciálně a tudíž zpracovanými více než jednou. Například pokud logika opakovaných pokusů způsobí, že odesílatel odesílat přesně stejné zprávy více než jednou, budete muset Ujistěte se, že je idempotentní.

Je možné návrhu idempotentní zprávy. Můžete například vytvořit událost, která uvádí, že "určovali ceny produktu do 25 USD" místo "Přidání $5 s cenou při produktu." Vám může bezpečně první zprávu zpracovat libovolný počet pokusů a výsledky budou stejné. To není PRAVDA pro druhé zprávy. Ale i v prvním případě nebudete chtít zpracovat první událost, protože systém může také odeslali novější události Změna ceny a by přepsání nová cena.

Dalším příkladem můžou být objednávka dokončena událost se rozšíří na několik předplatitelů. Je důležité, že informace o objednávkách aktualizují v jiných systémech pouze jednou, i v případě, že existují duplicitní zpráva události pro stejnou událost objednávka dokončena.

Je vhodné mít nějaký druh identity na událost, aby mohl vytvořit logiku, která vynutí, že každé události budou zpracovány pouze jednou za příjemce.

Některé zpracování zprávy je ze své podstaty idempotentní. Například pokud systém vygeneruje obrázek miniatury, je pravděpodobně důležité, kolikrát se zpracovává zpráva o vygenerované miniatury; Výsledkem je, že jsou generovány miniatury a jsou stejné pokaždé, když. Operace, jako je volání platební brány platby prostřednictvím platební karty na druhé straně, nemusí být idempotentní vůbec. V těchto případech je potřeba zajistit, že zpracování zprávy více než jednou má účinek, které jste očekávali.

### <a name="additional-resources"></a>Další zdroje

- **Aby byla dodržena zpráv, idempotence** <br/>
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591565(v=pandp.10)#honoring-message-idempotency>

## <a name="deduplicating-integration-event-messages"></a>Odstranění duplicit dat zprávy o událostech integrace

Zajistíte, že události zprávy odeslané a zpracuje jenom jednou na předplatitele na různých úrovních. Jedním ze způsobů je použití funkce odstranění duplicitních dat, které nabízí infrastruktura zasílání zpráv, které používáte. Další je implementovat vlastní logiku ve vaší cílové mikroslužeb. Ověření na úrovni přenosu i na úrovni aplikace, je nejlepším řešením.

### <a name="deduplicating-message-events-at-the-eventhandler-level"></a>Odstranění duplicit dat v události zpráv na úrovni obslužná rutina události

Jedním ze způsobů, abyste měli jistotu, že události budou zpracovány pouze jednou všechny příjemce je implementace určité logiky při zpracování zprávy událostí v obslužných rutinách událostí. Například, který je použitý v aplikaci eShopOnContainers aplikaci přístup jak je vidět v [zdrojový kód třídy UserCheckoutAcceptedIntegrationEventHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) při přijetí UserCheckoutAcceptedIntegrationEvent integrace událostí. (V tomto případě jsme zalamování CreateOrderCommand s IdentifiedCommand pomocí eventMsg.RequestId jako identifikátor, před odesláním obslužná rutina příkazu).

### <a name="deduplicating-messages-when-using-rabbitmq"></a>Při používání RabbitMQ odstranění duplicit dat zprávy

Pokud dochází k chybám sítě, mohou být duplicitní zprávy a příjemce zprávy musí být připravena ke zpracování těchto duplicitní zprávy. Pokud je to možné příjemce by měl zpracovávat zprávy jako idempotentní, což je lepší než explicitně je zpracování odstranění duplicit.

Podle [RabbitMQ dokumentaci](https://www.rabbitmq.com/reliability.html#consumer), "Pokud zpráva je Doručená příjemce a pak znovu zařadit do fronty (protože nebyla potvrzena, před připojení consumer vyřazeno, například), pak RabbitMQ nastaví příznak redelivered na to při doručení znovu (, zda se má stejný příjemce nebo jiný).

Pokud je nastavený příznak "redelivered", příjemce, který přijme v úvahu, protože zpráva může již byly zpracovány. Není zaručeno,, ale zpráva může mít nedospělo příjemce poté, co je třeba ponechat zprostředkovatele zpráv z důvodu problémů se sítí. Na druhé straně Pokud není nastaven příznak "redelivered", není zaručeno, že zpráva nebyla odeslána více než jednou. Příjemce proto potřebuje k odstranění duplicit zprávy nebo zprávy procesu způsobem idempotentní, pouze pokud příznak "redelivered" je nastavena ve zprávě.

### <a name="additional-resources"></a>Další zdroje

- **Rozvětveného aplikaci eShopOnContainers pomocí NServiceBus (určitého softwaru)** \
    <https://go.particular.net/eShopOnContainers>

- **Řízené zasílání zpráv** \
    [http://soapatterns.org/design\_patterns/event\_driven\_messaging](http://soapatterns.org/design_patterns/event_driven_messaging)

- **Jimmy Bogard. Refaktoring směrem k odolnosti: Vyhodnocení párování** \
    <https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/>

- **Publikování a odběru kanálu** \
    <https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html>

- **Komunikace mezi ohraničené kontexty** \
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591572(v=pandp.10)>

- **Konzistence typu případné** \
    [https://en.wikipedia.org/wiki/Eventual\_consistency](https://en.wikipedia.org/wiki/Eventual_consistency)

- **Philip Brown. Strategie pro integraci ohraničených kontextech** \
    <https://www.culttt.com/2014/11/26/strategies-integrating-bounded-contexts/>

- **Chris Richardson. Vývoj transakční Mikroslužeb pomocí agregace, modelu Event Sourcing a CQRS – část 2** \
    <https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson>

- **Chris Richardson. Model Event Sourcing** \
    <https://microservices.io/patterns/data/event-sourcing.html>

- **Úvod do modelu Event Sourcing** \
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591559(v=pandp.10)>

- **Událost Store databáze**. Oficiální web. \
    <https://geteventstore.com/>

- **Patrick Nommensen. Správa dat založené na událostech pro Mikroslužby** \
    <https://dzone.com/articles/event-driven-data-management-for-microservices-1>

- **Věty** \
    [https://en.wikipedia.org/wiki/CAP\_theorem](https://en.wikipedia.org/wiki/CAP_theorem)

- **Co je věty?** \
    <https://www.quora.com/What-Is-CAP-Theorem-1>

- **Úvod do konzistence dat** \
    <https://docs.microsoft.com/previous-versions/msp-n-p/dn589800(v=pandp.10)>

- **Rick Saling. Věty: Proč "všechno, co jsou různé" bez cloudu a Internetu** \
    <https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/>

- **Eric Bureš. Zakončení 12 letech později: Jak se mění "Pravidla"** \
    <https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed>

- **Azure Service Bus. Zprostředkované zasílání zpráv: Vyhledávání duplicit**  \
    <https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25>

- **Průvodce spolehlivost** (RabbitMQ dokumentace) \
    [https://www.rabbitmq.com/reliability.html\#consumer](https://www.rabbitmq.com/reliability.html#consumer)

- **Azure Service Bus. Zprostředkované zasílání zpráv: Vyhledávání duplicit** \
    <https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25>

- **Průvodce spolehlivost** (RabbitMQ dokumentace) \
    [https://www.rabbitmq.com/reliability.html\#consumer](https://www.rabbitmq.com/reliability.html%23consumer)

> [!div class="step-by-step"]
> [Předchozí](rabbitmq-event-bus-development-test-environment.md)
> [další](test-aspnet-core-services-web-apps.md)
