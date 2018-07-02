---
title: Přihlášení k odběru událostí
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Přihlášení k odběru událostí
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: 6cc5563f93915d1516e5a5f22a104012c1bb85d6
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106574"
---
# <a name="subscribing-to-events"></a>Přihlášení k odběru událostí

Prvním krokem pro používání sběrnici událostí je přihlášení k odběru mikroslužeb k událostem, které chtějí přijímat. Která se má provést v mikroslužeb příjemce.

Následující jednoduchý kód ukazuje, co každý příjemce mikroslužbu musí implementovat při spouštění služby (který je v `Startup` třída), přihlásí se k událostem, které se vyžaduje. V takovém případě `basket.api` mikroslužbu musí přihlásit k odběru `ProductPriceChangedIntegrationEvent` a `OrderStartedIntegrationEvent` zprávy. 

Například když se přihlásíte k odběru `ProductPriceChangedIntegrationEvent` událost, která umožňuje mikroslužbu košík vědět, všechny změny cena produktu a umožňuje ji upozornit uživatele o změnu, pokud tento produkt je v koši uživatele.

```csharp
var eventBus = app.ApplicationServices.GetRequiredService<IEventBus>();

eventBus.Subscribe<ProductPriceChangedIntegrationEvent, 
                   ProductPriceChangedIntegrationEventHandler>();

eventBus.Subscribe<OrderStartedIntegrationEvent, 
                   OrderStartedIntegrationEventHandler>();

```

Po spuštění tohoto kódu mikroslužbu odběratele se naslouchání prostřednictvím RabbitMQ kanálů. Pokud dorazí jakékoli zprávy typu ProductPriceChangedIntegrationEvent, vyvolá kód obslužné rutiny události, který je předán a zpracovává událost.

## <a name="publishing-events-through-the-event-bus"></a>Publikování události prostřednictvím sběrnici událostí

Nakonec odesílatele zprávy (počátek mikroslužbu) publikuje události integrace s kódem podobně jako v následujícím příkladu. (Toto je zjednodušená příklad, který nevyžaduje nedělitelnost v úvahu). Podobný kód by implementovat vždy, když událost musí být rozšířena napříč více mikroslužeb, obvykle hned po potvrzení dat nebo transakcí z počátku mikroslužby.

V konstruktoru řadiče, jako v následujícím kódu by nejprve vložit objekt implementace sběrnice událostí (podle RabbitMQ nebo v závislosti na služby service bus):

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

Můžete ho pak použít z vašeho řadiče metod, jako metodu UpdateProduct:

```csharp
[Route("update")]
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

V takovém případě je tento kód jednoduché mikroslužbu CRUD totiž mikroslužbu počátek umístěna vpravo do kontroleru webového rozhraní API. 
 
V pokročilejší mikroslužeb, jako při použití CQRS přístupy, můžou se implementovat v `CommandHandler` třídy uvnitř `Handle()` metoda. 


### <a name="designing-atomicity-and-resiliency-when-publishing-to-the-event-bus"></a>Navrhování nedělitelnost a odolnost proti chybám při publikování ke sběrnici událostí

Při publikování události integrace pomocí distribuované zasílání zpráv systému jako vaše sběrnice událostí, budete mít problém atomicky aktualizace původní databáze a publikování události. Například z zjednodušené příkladu výše, kód potvrdí data do databáze při cena produktu se změní a pak publikuje zprávu ProductPriceChangedIntegrationEvent. Na začátku může vypadat základní těchto dvou operací atomicky provést. Ale pokud používáte distribuované transakce zahrnující databáze a zprávy zprostředkovatel, stejně jako ve starších systémů jako [Microsoft služby Řízení front zpráv (MSMQ)](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx), to není doporučeno důvodů popsaného [Věta CAP](https://www.quora.com/What-Is-CAP-Theorem-1).

V podstatě použijete mikroslužeb k sestavení systémy škálovatelné a vysoce dostupné. Ke zjednodušení poněkud, věta CAP uvádí nemůže vytvořit databázi (nebo mikroslužbu, který vlastní svůj model), se průběžně k dispozici, důrazně konzistentní *a* odolný vůči chybám pro libovolný oddíl. Musíte zvolit dva z těchto tří vlastností.

V případě architektur se na základě mikroslužeb měli byste vybrat dostupnost a odolnost proti a měli omezit silnou konzistenci. Proto v většina moderních aplikací na základě mikroslužbu, obvykle nechcete používat distribuovaných transakcí v zasílání zpráv, stejně jako při implementaci [distribuované transakce](https://msdn.microsoft.com/library/ms978430.aspx#bdadotnetasync2_topic3c) založené na distribuovanou transakci Windows Koordinátor (DTC) s [MSMQ](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx).

Přejděte zpět do počáteční problému a jeho příklad. Pokud po aktualizaci databáze dojde k chybě služby (v tomto případě pravým po řádku kódu pomocí \_kontextu. SaveChangesAsync()), ale před publikováním události integrace celého systému může být nekonzistentní. To může být kritické, v závislosti na konkrétní firemní operaci, kterou chcete pracovat s firmy.

Jak je uvedeno výše v části architektura, může mít několik přístupů pro s řešením tohoto problému:

-   Pomocí kompletní [Sourcing událostí vzor](https://msdn.microsoft.com/library/dn589792.aspx).

-   Pomocí [transakce protokolu dolování](https://www.scoop.it/t/sql-server-transaction-log-mining).

-   Pomocí [pošta k odeslání vzoru](http://gistlabs.com/2014/05/the-outbox/). Toto je transakcí tabulku pro ukládání událostí integrace (rozšíření místní transakce).

Pro tento scénář pomocí úplné vzoru událostí Sourcing (ES) je jedním z osvědčených postupů, není-li *nejlepší*. V mnoha scénářích aplikace, ale nemusí být schopen implementovat úplnou ES operace. ES znamená ukládání jenom události domény v transakční databáze, místo ukládání dat v aktuálním stavu. Ukládání jenom události domény může mít velký výhod, jako je například s historii vašeho systému, které jsou k dispozici a schopnost určit stav systému v každém okamžiku v minulosti. Ale implementace úplnou ES vyžaduje, abyste rearchitect většinu systému a představuje mnoho složité kroky a požadavky. Například by chcete použít databázi vytvořené speciálně pro událost sourcing, například [událostí úložiště](https://geteventstore.com/), nebo databázi orientované dokumentu například Azure Cosmos DB, MongoDB, Cassandra, CouchDB nebo RavenDB. ES je skvělým přístup pro tento problém, ale není Nejsnazším řešením, pokud jste již obeznámeni s sourcing událostí.

Možnost použít transakčního protokolu dolování původně vypadá velmi transparentní. Pro tento postup, ale mikroslužbu má pro spojení protokolu RDBMS transakce, jako je například protokolu transakcí serveru SQL Server. To je pravděpodobně není žádoucí. Další nevýhodou je, že nízké úrovně aktualizací zaznamenávají v protokolu transakcí nemusí být na stejné úrovni jako vysoké úrovně integrace události. Pokud ano, proces zpětnou tyto operace transakce protokolu může být obtížné.

Vyrovnáváním přístup je směs tabulku transakcí databáze a zjednodušená ES vzor. Můžete použít stav, jako je například "připravené k publikování událostí,", které se nastavují v původní událost v případě potvrzení události tabulky integrace. Potom se pokusíte publikovat událost ke sběrnici událostí. Pokud akce publikování událostí úspěšné, spustit jinou transakcí v rámci služby původu a přesun stavu z "připravena k publikování události" do "událost již zveřejněny."

Pokud akce publikování událostí události sběrnici selže, data stále nebudou konzistentní v rámci mikroslužbu počátek – stále je označena jako "připravené k publikování události", a s ohledem na zbytek služby, případně bude konzistentní. Vždycky můžete mít kontrolu stavu transakce nebo události integrace úlohy na pozadí. Pokud úloha nalezne událost ve stavu "připraveno k publikování události", můžete zkusit znovu publikovat tuto událost ke sběrnici událostí.

Všimněte si, že s tímto přístupem uchováváte jenom události integrace pro každý mikroslužbu původ a jenom události, které chcete sdělit další mikroslužeb nebo externími systémy. Naopak v rámci systému ES ukládat všechny události domény také.

Proto tento vyrovnáváním přístup je zjednodušená ES systému. Je třeba seznam události integrace s jejich aktuální stav ("je připravena k publikování" a "publikovat"). Ale potřebujete implementovat tyto stavy pro události integrace. A v tento přístup, není nutné ukládat všechny domény data jako události v databázi transakcí, stejně jako v úplnou ES.

Pokud už používáte relační databázi, můžete k uložení událostí integrace transakčních tabulku. K dosažení nedělitelnost ve vaší aplikaci, můžete použít ve dvou krocích založené na místní transakce. V podstatě máte tabulku IntegrationEvent ve stejné databázi, kdy máte entity vaší domény. Tato tabulka funguje jako pojištění k dosažení nedělitelnost tak, aby zahrnete trvalé události integrace do stejné transakcí, které se potvrzují data vaší domény.

Krok za krokem procesu přejde takto: aplikace začne transakce místní databáze. Pak aktualizuje stav entity vaší domény a vloží do tabulky události integrace událost. Nakonec potvrdí transakce. Zobrazí požadovanou nedělitelnost.

Při implementaci kroky publikování události, máte tyto možnosti:

-   Publikování události integrace hned po potvrzení transakce a k označení události v tabulce jako publikovanému použijte jinou místní transakcí. Pak pomocí tabulky stejně jako artefakt sledovat události integrace v případě problémů v vzdálené mikroslužeb a provádět vyrovnávací akce založené na události uložené integrace.

-   Tabulku použijte jako typ fronty. Vlákno samostatné aplikace nebo proces dotazuje tabulku událostí integrace, publikuje události ke sběrnici událostí a pak použije místní transakce označit události jako publikovaná.

Obrázek 8 do 22 ukazuje architekturu pro první z těchto přístupů.

![](./media/image23.png)

**Obrázek 8 do 22**. Nedělitelnost při publikování události ke sběrnici událostí

Přístup zobrazené v obrázek 8 do 22 chybí mikroslužbu další pracovního procesu, který má na starosti kontrole a potvrzení úspěch události publikované integrace. V případě selhání můžete tuto další kontrolu pracovní mikroslužbu číst události z tabulky a znovu publikovat.

O druhý přístup: protokolu událostí tabulku použijte jako fronty a k publikování zpráv vždycky používat mikroslužbu pracovního procesu. Proces v takovém případě se zobrazí jako je například v obrázek 8 – 23. Zobrazí se další mikroslužbu a tabulka je jediným zdrojem při publikování události.

![](./media/image24.png)

**Obrázek 8 – 23**. Nedělitelnost při publikování události ke sběrnici událostí s mikroslužbu pracovního procesu

Pro jednoduchost používá ukázka eShopOnContainers prvním přístupem (bez dalších procesů nebo kontrolu mikroslužeb) plus sběrnici událostí. Však není eShopOnContainers zpracování všech možných selhání případech. V reálné aplikaci nasadit do cloudu musíte použít skutečnost, že se vyskytnout potíže se nakonec a musí implementovat, zkontrolujte a opakujte odeslání logiky. Pokud máte tato tabulka jako jednoho zdroje událostí, pokud je publikování přes sběrnici událostí může být efektivnější než prvním přístupem pomocí tabulky jako fronty.

### <a name="implementing-atomicity-when-publishing-integration-events-through-the-event-bus"></a>Implementace nedělitelnost při publikování události integrace přes sběrnici událostí

Následující kód ukazuje, jak můžete vytvořit jeden transakce zahrnující víc objektů DbContext – jeden kontext související s původní data aktualizují a druhý kontext související s IntegrationEventLog tabulky.

Všimněte si, že transakce v následujícím příkladu kódu nebude odolné, pokud připojení k databázi jakýkoli problém v době, kdy kód běží. K tomu dochází v cloudových systémech jako databázi SQL Azure, který může přesunutí databází mezi servery. Implementace odolné transakce napříč více kontexty, najdete v článku [implementace odolné připojení Entity Framework Core SQL](#implementing_resilient_EFCore_SQL_conns) dále v této příručce.

Pro přehlednost následující příklad ukazuje celého procesu v jeden úsek kódu. Implementace eShopOnContainers ale ve skutečnosti je teď vyčleněný a rozdělení této logiky do více tříd, takže je snazší správa.

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
  if !(raiseProductPriceChangedEvent) 
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

      // Publish the intergation event through the event bus
      _eventBus.Publish(priceChangedEvent); 

      integrationEventLogService.MarkEventAsPublishedAsync(
                                                priceChangedEvent); 
  }

  return Ok();
}

```

Po vytvoření události integrace ProductPriceChangedIntegrationEvent transakce, která ukládá původní operace domény (aktualizace položka katalogu, kterou) také zahrnuje trvalost události v protokolu událostí tabulce. Díky tomu jedné transakci a vždy bude moct zkontrolovat, zda byly odeslány zprávy o událostech.

V tabulce v protokolu událostí se aktualizuje atomicky původní databáze, pomocí operace místní transakce proti stejné databáze. Pokud selžou všechny operace, je vyvolána výjimka, a transakce se vrátí zpět všechny dokončené operace, a proto zachování konzistence mezi domény operace a zprávy událostí odeslané.

### <a name="receiving-messages-from-subscriptions-event-handlers-in-receiver-microservices"></a>Přijímání zpráv z předplatných: obslužné rutiny událostí v mikroslužeb příjemce

Kromě logice odběru událostí potřebujete implementovat vnitřní kód pro obslužné rutiny událostí integrace (jako metody zpětného volání). Obslužné rutiny události je, kde můžete určit, kde přijme a zpracuje zprávy o událostech určitého typu.

Obslužné rutiny události nejprve obdrží instanci události z události sběrnice. Pak je možné vyhledat součásti, které mají být zpracovány vztahující se k této události integrace, šíření a zachování událost jako ke změně stavu v mikroslužbu příjemce. Například pokud ProductPriceChanged událost pochází v katalogu mikroslužbu, ho je zpracována v košíku mikroslužbu a změní stav v košíku mikroslužbu tento příjemce i, jak je znázorněno v následujícím kódu.

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

Obslužné rutiny události musí ověřit, zda v některém z instancí košík existuje produktu. Aktualizuje také cena zboží pro každou položku řádku související nákupní košík. Nakonec vytvoří výstrahu, který se má zobrazit uživateli o změně ceny, jak ukazuje obrázek 8 – 24.

![](./media/image25.png)

**Obrázek 8 – 24**. Zobrazení o změnu cena zboží v košíku, oznámené události integrace

## <a name="idempotency-in-update-message-events"></a>Idempotenci v události zpráva aktualizace

Důležitým aspektem události zpráva aktualizace je, že selhání v libovolném bodě komunikace by nemělo způsobit zpráva, která má být opakována. Úlohy na pozadí v opačném případě může pokusit publikovat událost, která už se publikovala, vytváření časování. Můžete potřebovat a ujistěte se, že aktualizace jsou idempotent nebo že poskytují dostatek informací k zajištění, že můžete zjistit duplicitní, ji zrušit a odeslání odpovědi zpět jenom jeden.

Jak již bylo uvedeno dříve, idempotenci znamená, že operaci lze provést několikrát beze změny výsledek. V prostředí zasílání zpráv jako při komunikaci události, je událost idempotent, pokud ho může doručit víckrát beze změny výsledek pro příjemce mikroslužby. To může být způsobeno povaha samotné události nezbytné nebo z důvodu způsob, jakým systém zpracovává událost. Zpráva idempotenci je důležité v jakékoli aplikaci, která používá zasílání zpráv, ne jenom v aplikacích, které implementovat vzor sběrnice událostí.

Příkaz SQL, který vkládá data do tabulky, pouze pokud tato data již není v tabulce je například idempotent operace. Není důležité, kolik časy spuštění, které vložte příkaz jazyka SQL; Výsledkem bude stejná – tabulka bude obsahovat data. Idempotenci jako to může být také nezbytné při plánování práce s zprávy, pokud se zprávy může potenciálně odeslat a proto zpracování více než jednou. Například pokud logika opakovaných pokusů způsobí, že odesílatel přesně stejnou zprávu odeslat více než jednou, musíte zajistit, že se jedná o idempotent.

Je možné návrhu idempotent zprávy. Například můžete vytvořit událost, která uvádí, že "nastavit cena produktu na \$25" místo "Přidat \$5 a cena produktu." Vám může bezpečně první zprávu zpracovat libovolný počet časy a výsledkem bude stejná. Který není pro druhou zprávu na hodnotu true. Ale i v prvním případě možná nebudete chtít zpracovat první událost, protože v systému může také odeslali novější událostí změna ceny a by přepsal nového ceníku.

Dalším příkladem může být událost dokončit pořadí nebyl rozšířen do více odběrateli. Je důležité, aby informace o objednávce pouze jednou, aktualizovat v ostatních systémech i v případě, že existují duplicitní zpráva události pro jednu událost dokončit pořadí.

Je vhodné používat nějaký druh identity na událost, takže můžete vytvořit logiku, která vynucuje, že každá událost je jenom jednou zpracovaných za příjemce.

Některé zpracování zprávy je ze své podstaty idempotent. Například pokud systém vygeneruje miniatur bitové kopie, je nemusí důležité, kolikrát je zpracovat zprávu o generovaného miniaturu; výsledek je, že jsou generovány miniatur a jsou stejné pokaždé, když. Operace, jako například volání platební brány účtují platební karty na druhé straně, nemusí být idempotent vůbec. V těchto případech je potřeba zajistit, že zpracování zprávy několikrát má vliv očekáváte, že.

### <a name="additional-resources"></a>Další zdroje

-   **Aby byla dodržena idempotenci zpráva** (Podtitulek na této stránce) [*https://msdn.microsoft.com/library/jj591565.aspx*](https://msdn.microsoft.com/library/jj591565.aspx)

## <a name="deduplicating-integration-event-messages"></a>Odstranění duplicit dat zprávy o událostech integrace

Zajistit odesílání a zpracuje jenom jednou za odběratele na různých úrovních zpráva události. Jedním ze způsobů je použít funkci odstranění duplicitních dat, které nabízí infrastrukturu zasílání zpráv, které používáte. Jiné je implementace vlastní logiky ve vaší cílové mikroslužby. Ověření na úrovni přenosu i na úrovni aplikace je nejlepším řešením.

### <a name="deduplicating-message-events-at-the-eventhandler-level"></a>Odstranění duplicit dat události zpráv na úrovni obslužná rutina události

Jedním ze způsobů, abyste měli jistotu, že událost pouze jednou zpracovává libovolné receiver je implementace určité logiku při zpracování zprávy událostí v obslužné rutiny událostí. Například, je metoda používaná v aplikaci eShopOnContainers, jak můžete vidět v [zdrojový kód](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Controllers/OrdersController.cs) třídy OrdersController při přijetí příkazu CreateOrderCommand. (V tomto případě používáme příkaz požadavku HTTP není na základě zpráv příkaz, ale logiku, budete muset udělat na základě zpráv příkaz idempotent je podobný.)

### <a name="deduplicating-messages-when-using-rabbitmq"></a>Při použití RabbitMQ odstranění duplicit dat zprávy

Pokud dochází k občasným chybám sítě, zprávy mohou být duplicitní a příjemce zprávy musí být připravené pro zpracování těchto duplicitní zpráv. Pokud je to možné příjemci by měla řídit zprávy idempotent způsobem, který je lepší, než je explicitně zpracovávat s odstraněním duplicit.

Podle požadavků [RabbitMQ dokumentace](https://www.rabbitmq.com/reliability.html#consumer), "Pokud zpráva je doručen k příjemce a pak zařazena (protože nebyla potvrzena, před ztrátě připojení k příjemce, například), pak RabbitMQ nastaví příznak redelivered na je po doručení znovu (jestli k příjemce stejný nebo jiný).

Pokud je nastavený příznak "redelivered", příjemce, vyžaduje v úvahu, protože zpráva může již byly zpracovány. Ale který není zaručena; zpráva může nikdy dosáhli příjemce po jeho levé zprostředkovatele zpráv, možná z důvodu problémů se sítí. Na druhé straně Pokud není nastavený příznak "redelivered", tak, aby zajistil, že zpráva nebyla odeslána více než jednou. Proto musí příjemce k odstranění duplicit zprávy nebo zpracování zpráv způsobem idempotent pouze v případě, že je "redelivered" nastavený příznak ve zprávě.

### <a name="additional-resources"></a>Další zdroje

-   **Forked eShopOnContainers pomocí NServiceBus (určitého softwaru)**
    [*http://go.particular.net/eShopOnContainers*](http://go.particular.net/eShopOnContainers)

-   **Událost řízené zasílání zpráv**
    [*http://soapatterns.org/design\_patterns/event\_driven\_messaging*](http://soapatterns.org/design_patterns/event_driven_messaging)

-   **Jimmy Bogard. Refaktoring směrem odolnost: Vyhodnocení párování**
    [*https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/*](https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/)

-   **Publikování a odběru kanálu**
    [*http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html*](http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html)

-   **Komunikace mezi ohraničené kontexty**
    [*https://msdn.microsoft.com/library/jj591572.aspx*](https://msdn.microsoft.com/library/jj591572.aspx)

-   **Konzistence typu případné**
    [*https://en.wikipedia.org/wiki/Eventual\_consistency*](https://en.wikipedia.org/wiki/Eventual_consistency)

-   **Hnědá Philip. Kontexty ohraničenou strategií pro integraci**
    [*http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/*](http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/)

-   **Jan Ryšánková. Vývoj transakční Mikroslužeb pomocí agregace, Sourcing událostí a CQRS - část 2**
    [*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson)

-   **Jan Ryšánková. Vzor Sourcing událostí**
    [*https://microservices.io/patterns/data/event-sourcing.html*](https://microservices.io/patterns/data/event-sourcing.html)

-   **Představení Sourcing událostí**
    [*https://msdn.microsoft.com/library/jj591559.aspx*](https://msdn.microsoft.com/library/jj591559.aspx)

-   **Databáze úložiště událostí**. Oficiální web.
    [*https://geteventstore.com/*](https://geteventstore.com/)

-   **Patrik Nommensen. Správa dat založeného na událostech pro Mikroslužeb**
    *<https://dzone.com/articles/event-driven-data-management-for-microservices-1> *

-   **Věta Zakončení**
    [*https://en.wikipedia.org/wiki/CAP\_theorem*](https://en.wikipedia.org/wiki/CAP_theorem)

-   **Co je Zakončení věta?**
    [*https://www.quora.com/What-Is-CAP-Theorem-1*](https://www.quora.com/What-Is-CAP-Theorem-1)

-   **Úvod do konzistence dat**
    [*https://msdn.microsoft.com/library/dn589800.aspx*](https://msdn.microsoft.com/library/dn589800.aspx)

-   **Rick Saling. Věta Zakončení: Proč "Vše, co je různé" s cloudu a Internet**
    [*https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/*](https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/)

-   **Erica Brewer. Zakončení 12 letech později: jak změnily "Pravidla"**
    [*https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed*](https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed)

-   **Účastní transakcí (DTC) externí** (MSMQ) [*https://msdn.microsoft.com/library/ms978430.aspx\#bdadotnetasync2\_topic3c*](https://msdn.microsoft.com/library/ms978430.aspx%23bdadotnetasync2_topic3c)

-   **Azure Service Bus. Zprostředkované zasílání zpráv: Detekce duplicitních**
    [*https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25*](https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25)

-   **Průvodce spolehlivost** (RabbitMQ dokumentace) [*https://www.rabbitmq.com/reliability.html\#consumer*](https://www.rabbitmq.com/reliability.html%23consumer)




>[!div class="step-by-step"]
[Předchozí](rabbitmq-event-bus-development-test-environment.md)
[další](test-aspnet-core-services-web-apps.md)
