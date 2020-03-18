---
title: Události domény. návrh a realizace
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Získejte podrobný přehled událostí domény, což je klíčový koncept pro navázání komunikace mezi agregacemi.
ms.date: 10/08/2018
ms.openlocfilehash: 3bba18d4a77b47abee55c16bae8a64ed27ac9aba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74884225"
---
# <a name="domain-events-design-and-implementation"></a>Doménové události: Návrh a implementace

Události domény slouží k explicitní implementaci vedlejších účinků změn v rámci domény. Jinými slovy a pomocí terminologie DDD použijte události domény explicitně implementovat vedlejší účinky napříč více agregacemi. Volitelně pro lepší škálovatelnost a menší dopad na uzamčení databáze, použijte konečnou konzistenci mezi agregacemi v rámci stejné domény.

## <a name="what-is-a-domain-event"></a>Co je událost domény?

Událost je něco, co se stalo v minulosti. Událost domény je něco, co se stalo v doméně, které chcete, aby ostatní části stejné domény (v procesu) být vědomi. Oznámené části obvykle nějak reagují na události.

Důležitou výhodou událostí domény je, že vedlejší účinky mohou být vyjádřeny explicitně.

Například pokud právě používáte Entity Framework a musí být reakce na některé události, pravděpodobně kód, co potřebujete blízko co spouští událost. Takže pravidlo dostane spojen, implicitně, do kódu a budete muset podívat do kódu, doufejme, že si uvědomit, že pravidlo je implementováno tam.

Na druhou stranu pomocí události domény je koncept explicitní, protože je `DomainEvent` a alespoň jeden `DomainEventHandler` zapojených.

Například v aplikaci eShopOnContainers při vytvoření objednávky se uživatel stane `OrderStartedDomainEvent` kupujícím, takže `ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler`je aktivována a zpracována v , takže základní koncept je evidentní.

Stručně řečeno, události domény vám pomohou explicitně vyjádřit pravidla domény založená v všudypřítomném jazyce poskytovaném odborníky domény. Události domény také umožňují lepší oddělení obav mezi třídy v rámci stejné domény.

Je důležité zajistit, že stejně jako databázová transakce, buď všechny operace související s událostí domény úspěšně dokončit nebo žádný z nich dělat.

Události domény jsou podobné události ve stylu zasílání zpráv, s jedním důležitým rozdílem. Při skutečném zasílání zpráv, frontách zpráv, zprostředkovatelích zpráv nebo službě Service Bus pomocí služby AMQP je zpráva vždy odesílána asynchronně a komunikována mezi procesy a počítači. To je užitečné pro integraci více ohraničené kontexty, mikroslužeb nebo dokonce různé aplikace. S událostmi domény však chcete vyvolat událost z operace domény, kterou právě sbíháte, ale chcete, aby se v rámci stejné domény vyskytly jakékoli vedlejší účinky.

Události domény a jejich vedlejší účinky (akce aktivované později, které jsou spravovány obslužnými rutinami událostí) by se měly objevit téměř okamžitě, obvykle v procesu a v rámci stejné domény. Události domény tedy mohou být synchronní nebo asynchronní. Události integrace by však měly být vždy asynchronní.

## <a name="domain-events-versus-integration-events"></a>Události domény versus události integrace

Sémanticky, domény a integrace události jsou totéž: oznámení o něčem, co se právě stalo. Jejich provádění však musí být odlišné. Události domény jsou pouze zprávy odeslané dispečerovi událostí domény, které mohou být implementovány jako mediátor v paměti založené na kontejneru IoC nebo jiné metodě.

Na druhé straně účelem události integrace je šířit potvrzené transakce a aktualizace dalších subsystémů, ať už jsou jiné mikroslužby, ohraničené kontexty nebo dokonce externí aplikace. Proto by k nim mělo dojít pouze v případě, že entita je úspěšně trvalá, jinak je to, jako by se celá operace nikdy neuskutečnila.

Jak již bylo zmíněno dříve, události integrace musí být založeny na asynchronní komunikaci mezi více mikroslužeb (jiné ohraničené kontexty) nebo dokonce externí systémy/aplikace.

Rozhraní sběrnice událostí tedy potřebuje určitou infrastrukturu, která umožňuje meziprocesovou a distribuovanou komunikaci mezi potenciálně vzdálenými službami. Může být založen na komerční sběrnici, frontách, sdílené databázi používané jako poštovní schránka nebo jiném distribuovaném a ideálně nabízeném systému zasílání zpráv.

## <a name="domain-events-as-a-preferred-way-to-trigger-side-effects-across-multiple-aggregates-within-the-same-domain"></a>Události domény jako upřednostňovaný způsob, jak vyvolat vedlejší účinky napříč více agregacemi v rámci stejné domény

Pokud spuštění příkazu souvisejícího s jednou agregační instancí vyžaduje spuštění dalších pravidel domény na jednom nebo více dalších agregacích, měli byste tyto vedlejší účinky navrhnout a implementovat tak, aby byly spuštěny událostmi domény. Jak je znázorněno na obrázku 7-14 a jako jeden z nejdůležitějších případů použití, událost domény by měla být použita k šíření změn stavu napříč více agregacemi v rámci stejného modelu domény.

![Diagram znázorňující událost domény ovládající data do agregace Kupujícího.](./media/domain-events-design-implementation/domain-model-ordering-microservice.png)

**Obrázek 7-14**. Události domény k vynucení konzistence mezi více agregacemi v rámci stejné domény

Obrázek 7-14 ukazuje, jak je dosaženo konzistence mezi agregacemi podle událostí domény. Když uživatel zahájí objednávku, agregace objednávky odešle `OrderStarted` událost domény. Událost domény OrderStarted je zpracována agregací kupujícího k vytvoření objektu Buyer v objednávající mikroslužbě na základě původních informací o uživateli z mikroslužby identity (s informacemi poskytnutými v příkazu CreateOrder).

Alternativně můžete mít agregované root objednané události vyvolané členy jeho agregace (podřízené entity). Například každá podřízená entita OrderItem může vyvolat událost, když je cena položky vyšší než určitá částka nebo pokud je částka položky produktu příliš vysoká. Agregační kořen pak můžete přijímat tyto události a provést globální výpočet nebo agregaci.

Je důležité si uvědomit, že tato komunikace založená na událostech není implementována přímo v rámci agregací; je třeba implementovat obslužné rutiny událostí domény.

Zpracování událostí domény je problém aplikace. Vrstva modelu domény by se měla zaměřit pouze na logiku domény – věci, které by znalec domény pochopil, nikoli aplikační infrastruktury, jako jsou obslužné rutiny a akce trvalosti vedlejších účinků pomocí úložišť. Úroveň aplikační vrstvy je proto místo, kde byste měli mít obslužné rutiny událostí domény, které spouštějí akce při vyvolání události domény.

Události domény lze také použít k aktivaci libovolného počtu akcí aplikace a co je důležitější, musí být otevřené zvýšit toto číslo v budoucnu odděleným způsobem. Například při spuštění objednávky můžete chtít publikovat událost domény k šíření těchto informací do jiných agregací nebo dokonce zvýšit akce aplikace, jako jsou oznámení.

Klíčovým bodem je otevřený počet akcí, které mají být provedeny při výskytu události domény. Nakonec akce a pravidla v doméně a aplikaci poroste. Složitost nebo počet akcí vedlejších účinků, když se něco stane, se zvýší, ale pokud byl váš `new`kód spojen s "lepidlem" (to znamená vytvářením konkrétních objektů s ), pak pokaždé, když potřebujete přidat novou akci, budete také muset změnit pracovní a testovaný kód.

Tato změna by mohla vést k novým chybám a tento přístup je také v rozporu s [principem otevření/uzavření](https://en.wikipedia.org/wiki/Open/closed_principle) z [SOLID](https://en.wikipedia.org/wiki/SOLID). Nejen to, původní třída, která byla orchestrating operace by růst a růst, což je v rozporu s [jednotnou odpovědnost i (SRP)](https://en.wikipedia.org/wiki/Single_responsibility_principle).

Na druhou stranu, pokud používáte události domény, můžete vytvořit jemně odstupňované a oddělené implementace oddělením odpovědnosti pomocí tohoto přístupu:

1. Odeslat příkaz (například CreateOrder).
2. Přijměte příkaz v obslužné rutině příkazu.
   - Proveďte transakci jednoho agregace.
   - (Nepovinné) Raise domain events for side effects (například OrderStartedDomainEvent).
3. Zpracování událostí domény (v rámci aktuálního procesu), který provede otevřený počet vedlejších účinků ve více agregaci nebo akce aplikace. Například:
   - Ověřte nebo vytvořte kupujícího a způsob platby.
   - Vytvořte a odešlete související integrační událost do sběrnice událostí, abyste rozšířili stavy napříč mikroslužbami nebo spustili externí akce, jako je odeslání e-mailu kupujícímu.
   - Zvládejte další nežádoucí účinky.

Jak je znázorněno na obrázku 7-15, počínaje stejnou událostí domény, můžete zpracovat více akcí souvisejících s jinými agregacemi v doméně nebo dalšími akcemi aplikace, které je třeba provést napříč mikroslužbami, které se připojují k událostem integrace a sběrnici událostí.

![Diagram znázorňující událost domény, která předává data několika obslužným rutinám událostí.](./media/domain-events-design-implementation/aggregate-domain-event-handlers.png)

**Obrázek 7-15**. Zpracování více akcí na doménu

Může existovat několik obslužných rutin pro stejnou událost domény v aplikační vrstvě, jedna obslužná rutina může vyřešit konzistenci mezi agregacemi a jinou obslužnou rutinou může publikovat integrační událost, takže s ní mohou jiné mikroslužby něco udělat. Obslužné rutiny událostí jsou obvykle ve vrstvě aplikace, protože budete používat objekty infrastruktury, jako jsou úložiště nebo rozhraní API aplikace pro chování mikroslužby. V tomto smyslu jsou obslužné rutiny událostí podobné obslužným rutinám příkazů, takže obě jsou součástí aplikační vrstvy. Důležitým rozdílem je, že příkaz by měl být zpracován pouze jednou. Událost domény může být zpracována nula nebo *n* krát, protože může být přijata více příjemců nebo obslužné rutiny událostí s jiným účelem pro každou obslužnou rutinu.

S otevřeným počtem obslužných rutin na událost domény umožňuje přidat tolik pravidel domény podle potřeby, aniž by to ovlivnilo aktuální kód. Například implementace následujícího obchodního pravidla může být stejně snadná jako přidání několika obslužných rutin událostí (nebo dokonce jen jednoho):

> Pokud celková částka zakoupená zákazníkem v obchodě v libovolném počtu objednávek přesáhne 6 000 USD, použijte slevu 10% na každou novou objednávku a informujte zákazníka e-mailem o této slevě pro budoucí objednávky.

## <a name="implement-domain-events"></a>Implementace událostí domény

V C#, událost domény je jednoduše struktura nebo třída pro držení dat, jako je DTO, se všemi informacemi týkajícími se toho, co se právě stalo v doméně, jak je znázorněno v následujícím příkladu:

```csharp
public class OrderStartedDomainEvent : INotification
{
    public string UserId { get; }
    public int CardTypeId { get; }
    public string CardNumber { get; }
    public string CardSecurityNumber { get; }
    public string CardHolderName { get; }
    public DateTime CardExpiration { get; }
    public Order Order { get; }

    public OrderStartedDomainEvent(Order order,
                                   int cardTypeId, string cardNumber,
                                   string cardSecurityNumber, string cardHolderName,
                                   DateTime cardExpiration)
    {
        Order = order;
        CardTypeId = cardTypeId;
        CardNumber = cardNumber;
        CardSecurityNumber = cardSecurityNumber;
        CardHolderName = cardHolderName;
        CardExpiration = cardExpiration;
    }
}
```

Toto je v podstatě třída, která obsahuje všechna data související s OrderStarted události.

Pokud jde o všudypřítomný jazyk domény, protože událost je něco, co se stalo v minulosti, název třídy události by měl být reprezentován jako sloveso v minulém řádu, jako orderstarteddomainevent nebo OrderShippedDomainEvent. Tak je událost domény implementována v objednávání mikroslužby v eShopOnContainers.

Jak již bylo uvedeno dříve, důležitou charakteristikou událostí je, že vzhledem k tomu, že událost je něco, co se stalo v minulosti, nemělo by se to měnit. Proto musí být neměnné třídy. V předchozím kódu se zobrazí, že vlastnosti jsou jen pro čtení. Neexistuje žádný způsob, jak aktualizovat objekt, můžete nastavit hodnoty pouze při jeho vytvoření.

Je důležité zdůraznit, že pokud by události domény byly zpracovány asynchronně pomocí fronty, která vyžadovala serializaci a deserializaci objektů události, vlastnosti by musely být "soukromé sady" namísto jen pro čtení, takže by byl deserializátor mohou přiřadit hodnoty při dequeuing. To to není problém v objednávání mikroslužby, jako domain event pub/sub je implementována synchronně pomocí MediatR.

### <a name="raise-domain-events"></a>Zvýšit události domény

Další otázkou je, jak vyvolat událost domény tak, aby dosáhla související chod ní obslužné rutiny události. Můžete použít více přístupů.

Udi Dahan původně navrhl (například v několika souvisejících pracovních míst, jako je [například domain events - Take 2](http://udidahan.com/2008/08/25/domain-events-take-2/)) pomocí statické třídy pro správu a zvyšování událostí. To může zahrnovat statickou třídu s názvem DomainEvents, která by `DomainEvents.Raise(Event myEvent)`okamžitě vyvolala události domény, když je volána, pomocí syntaxe jako . Jimmy Bogard napsal blogový příspěvek[(Posílení vaší domény: Domain Events),](https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/)který doporučuje podobný přístup.

Však při třídy událostí domény je statická, také odešle obslužné rutiny okamžitě. To ztěžuje testování a ladění, protože obslužné rutiny událostí s logikou vedlejších účinků jsou spuštěny ihned po vyvolání události. Při testování a ladění, chcete zaměřit na a jen to, co se děje v aktuální agregační třídy; nechcete být náhle přesměrováni na jiné obslužné rutiny událostí pro vedlejší účinky související s jinými agregacemi nebo aplikační logikou. To je důvod, proč se vyvinuly jiné přístupy, jak je vysvětleno v další části.

#### <a name="the-deferred-approach-to-raise-and-dispatch-events"></a>Odložený přístup ke zvýšení a odeslání událostí

Místo okamžitého odeslání do obslužné rutiny události domény je lepším přístupem přidání událostí domény do kolekce a následné odeslání těchto událostí domény *přímo před* nebo *bezprostředně* *po* potvrzení transakce (jako u SaveChanges v EF). (Tento přístup byl popsán Jimmy Bogard v tomto [příspěvku lepší doména události vzor](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/).)

Rozhodování o tom, zda odešlete události domény přímo před nebo přímo po potvrzení transakce je důležité, protože určuje, zda bude zahrnovat vedlejší účinky jako součást stejné transakce nebo v různých transakcích. V druhém případě je třeba řešit konečnou konzistenci mezi více agregáty. Toto téma je popsáno v další části.

Odložený přístup je to, co používá eShopOnContainers. Nejprve přidáte události, ke kterých dochází ve vašich entitách, do kolekce nebo seznamu událostí na entitu. Tento seznam by měl být součástí objektu entity nebo ještě lépe součástí základní třídy entity, jak je znázorněno v následujícím příkladu základní třídy Entity:

```csharp
public abstract class Entity
{
     //...
     private List<INotification> _domainEvents;
     public List<INotification> DomainEvents => _domainEvents;

     public void AddDomainEvent(INotification eventItem)
     {
         _domainEvents = _domainEvents ?? new List<INotification>();
         _domainEvents.Add(eventItem);
     }

     public void RemoveDomainEvent(INotification eventItem)
     {
         _domainEvents?.Remove(eventItem);
     }
     //... Additional code
}
```

Pokud chcete vyvolat událost, stačí ji přidat do kolekce událostí z kódu v libovolné metodě entity agregační kořenové.

Následující kód, který je součástí [agregačního kořene objednávky v eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs), ukazuje příklad:

```csharp
var orderStartedDomainEvent = new OrderStartedDomainEvent(this, //Order object
                                                          cardTypeId, cardNumber,
                                                          cardSecurityNumber,
                                                          cardHolderName,
                                                          cardExpiration);
this.AddDomainEvent(orderStartedDomainEvent);
```

Všimněte si, že jediná věc, kterou metoda AddDomainEvent dělá, je přidání události do seznamu. Zatím není odeslána žádná událost a dosud není vyvolána žádná obslužná rutina události.

Ve skutečnosti chcete odeslat události později, když potvrdíte transakci do databáze. Pokud používáte core entity framework, znamená to v SaveChanges metoda EF DbContext, jako v následujícím kódu:

```csharp
// EF Core DbContext
public class OrderingContext : DbContext, IUnitOfWork
{
    // ...
    public async Task<bool> SaveEntitiesAsync(CancellationToken cancellationToken = default(CancellationToken))
    {
        // Dispatch Domain Events collection.
        // Choices:
        // A) Right BEFORE committing data (EF SaveChanges) into the DB. This makes
        // a single transaction including side effects from the domain event
        // handlers that are using the same DbContext with Scope lifetime
        // B) Right AFTER committing data (EF SaveChanges) into the DB. This makes
        // multiple transactions. You will need to handle eventual consistency and
        // compensatory actions in case of failures.
        await _mediator.DispatchDomainEventsAsync(this);

        // After this line runs, all the changes (from the Command Handler and Domain
        // event handlers) performed through the DbContext will be committed
        var result = await base.SaveChangesAsync();
    }
}
```

Pomocí tohoto kódu odešlete události entity do příslušných obslužných rutin událostí.

Celkovývýsledek je, že jste oddělili zvýšení události domény (jednoduché přidání do seznamu v paměti) od odeslání do obslužné rutiny události. Kromě toho v závislosti na tom, jaký druh dispečera používáte, můžete odeslat události synchronně nebo asynchronně.

Uvědomte si, že transakční hranice přicházejí do významné hry zde. Pokud vaše jednotka práce a transakce může span více než jeden agregace (jako při použití EF Core a relační databáze), to může fungovat dobře. Ale pokud transakce nemůže span agregace, například při použití databáze NoSQL, jako je Azure CosmosDB, budete muset implementovat další kroky k dosažení konzistence. To je další důvod, proč neznalost vytrvalosti není univerzální; závisí na úložném systému, který používáte.

### <a name="single-transaction-across-aggregates-versus-eventual-consistency-across-aggregates"></a>Jednotlivá transakce mezi agregáty versus konečná konzistence mezi agregáty

Otázka, zda provést jednu transakci napříč agregáty versus spoléhat se na konečnou konzistenci mezi těmito agregáty, je kontroverzní. Mnoho Autorů DDD jako Eric Evans a Vaughn Vernon obhajovat pravidlo, že jedna transakce = jeden agregát, a proto argumentují pro případné konzistence napříč agregáty. Například, ve své knize *Domain-Driven Design*, Eric Evans říká toto:

> Jakékoli pravidlo, které zahrnuje agregace, nebude očekáváno, že bude vždy aktuální. Prostřednictvím zpracování událostí, dávkového zpracování nebo jiných aktualizačních mechanismů lze v určitém čase vyřešit jiné závislosti. (strana 128)

Vaughn Vernon říká následující v [efektivní agregační design. Část II: Tvorba agregáty pracovat společně](https://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf):

> Pokud tedy provedení příkazu na jedné agregované instanci vyžaduje, aby se \[na jednom nebo více agregacích prováděla další obchodní pravidla, použijte konečnou konzistenci ... \] Existuje praktický způsob, jak podpořit konečnou konzistenci v modelu DDD. Agregační metoda publikuje událost domény, která je doručena v čase dojednoho nebo více asynchronních odběratelů.

Toto zdůvodnění je založeno na přijetí jemně odstupňovaných transakcí namísto transakcí zahrnujících mnoho agregací nebo entit. Myšlenka je, že v druhém případě počet uzamčení databáze bude značný v rozsáhlých aplikacích s vysokými potřebami škálovatelnosti. Přijetí skutečnost, že vysoce škálovatelné aplikace nemusí mít okamžitou transakční konzistenci mezi více agregace mi pomáhá s přijetím konceptu konečné konzistence. Atomové změny často nejsou potřebné pro podnikání, a to je v každém případě odpovědnost odborníků domény říci, zda konkrétní operace potřebují atomické transakce, nebo ne. Pokud operace vždy potřebuje atomické transakce mezi více agregace, můžete se zeptat, zda agregace by měla být větší nebo nebyla správně navržena.

Nicméně, ostatní vývojáři a architekti jako Jimmy Bogard jsou v pořádku s kondrování jedné transakce přes několik agregátů-ale pouze v případě, že tyto další agregáty souvisejí s vedlejšími účinky pro stejný původní příkaz. Například, v [lepší doména události vzor](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/), Bogard říká toto:

> Obvykle chci, aby vedlejší účinky události domény nastat v rámci stejné logické transakce, ale \[ne nutně ve stejném rozsahu zvyšování domény události ... \] Těsně předtím, než potvrdíme naši transakci, odešleme naše události jejich příslušným obslužným rutinám.

Pokud odešlete události domény přímo *před* potvrzením původní transakce, je to proto, že chcete vedlejší účinky těchto událostí, které mají být zahrnuty do stejné transakce. Například pokud EF DbContext SaveChanges metoda selže, transakce vrátí zpět všechny změny, včetně výsledku všech operací vedlejších účinků implementovaných obslužné rutiny události související domény. Důvodem je, že dbContext životnost oboru je ve výchozím nastavení definován jako "s vymezeným oborem." Proto DbContext objekt je sdílena přes více objektů úložiště jsou vytvářeny v rámci stejného oboru nebo objektgrafu. To se shoduje s rozsahem HttpRequest při vývoji webových rozhraní API nebo aplikací MVC.

Ve skutečnosti oba přístupy (jedna atomová transakce a konečná konzistence) může být správné. To opravdu záleží na vaší oblasti nebo obchodní požadavky a to, co doména odborníci vám. Závisí také na tom, jak škálovatelné potřebujete službu být (podrobnější transakce mají menší dopad s ohledem na uzamčení databáze). A záleží na tom, kolik investic jste ochotni provést ve vašem kódu, protože konečná konzistence vyžaduje složitější kód, aby bylo možné zjistit možné nesrovnalosti mezi agregáty a potřebu implementovat kompenzační akce. Zvažte, že pokud potvrdíte změny původní agregace a po odeslání události, pokud je problém a obslužné rutiny událostí nelze potvrdit jejich vedlejší účinky, budete mít nekonzistence mezi agregace.

Způsob, jak povolit kompenzační akce by bylo ukládat události domény v dalšídatabázové tabulky, takže mohou být součástí původní transakce. Poté můžete mít dávkový proces, který zjistí nekonzistence a spustí kompenzační akce porovnáním seznamu událostí s aktuálním stavem agregací. Kompenzační akce jsou součástí komplexního tématu, které bude vyžadovat hloubkovou analýzu z vaší strany, což zahrnuje diskusi s odborníky na obchodní uživatele a doménu.

V každém případě si můžete vybrat přístup, který potřebujete. Ale počáteční odložené přístup – vyvolání události před potvrzením, takže použít jednu transakci – je nejjednodušší přístup při použití EF Core a relační databáze. Je jednodušší implementovat a platit v mnoha obchodních případech. Je to také přístup používaný v objednávání mikroslužby v eShopOnContainers.

Ale jak se skutečně odeslat tyto události na jejich příslušné obslužné rutiny událostí? Jaký je `_mediator` objekt, který vidíte v předchozím příkladu? Má co do činění s techniky a artefakty, které používáte k mapování mezi událostmi a jejich obslužné rutiny událostí.

### <a name="the-domain-event-dispatcher-mapping-from-events-to-event-handlers"></a>Dispečer událostí domény: mapování z událostí na obslužné rutiny událostí

Jakmile budete moci odeslat nebo publikovat události, budete potřebovat nějaký artefakt, který bude publikovat událost, takže každý související obslužná rutina může získat a zpracovat vedlejší účinky na základě této události.

Jedním z přístupů je skutečný systém zasílání zpráv nebo dokonce sběrnice událostí, případně na základě sběrnice na rozdíl od událostí v paměti. Však pro první případ skutečné zasílání zpráv by bylo přehnané pro zpracování událostí domény, protože stačí zpracovat tyto události v rámci stejného procesu (to znamená, že ve stejné doméně a aplikační vrstvy).

Dalším způsobem, jak mapovat události na více obslužných rutin událostí, je použití registrace typů v kontejneru IoC, takže můžete dynamicky odvodit, kam mají být události odeslány. Jinými slovy, musíte vědět, jaké obslužné rutiny událostí potřebují získat konkrétní událost. Obrázek 7–16 ukazuje zjednodušený přístup k tomuto přístupu.

![Diagram znázorňující dispečera událostí domény odesílající události příslušným obslužným rutinám.](./media/domain-events-design-implementation/domain-event-dispatcher.png)

**Obrázek 7-16**. Dispečer událostí domény používající ioC

Můžete vytvořit všechny instalatérské a artefakty k provedení tohoto přístupu sami. Můžete však také použít dostupné knihovny, jako [je MediatR,](https://github.com/jbogard/MediatR) který používá kontejner IoC pod kryty. Proto můžete přímo použít předdefinovaná rozhraní a metody publikování a odeslání objektu mediátora.

V kódu musíte nejprve zaregistrovat typy obslužné rutiny událostí v kontejneru IoC, jak je znázorněno v následujícím příkladu na [eShopOnContainers Objednávání mikroslužby](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/MediatorModule.cs):

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        // Other registrations ...
        // Register the DomainEventHandler classes (they implement IAsyncNotificationHandler<>)
        // in assembly holding the Domain Events
        builder.RegisterAssemblyTypes(typeof(ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler)
                                       .GetTypeInfo().Assembly)
                                         .AsClosedTypesOf(typeof(IAsyncNotificationHandler<>));
        // Other registrations ...
    }
}
```

Kód nejprve identifikuje sestavení, které obsahuje obslužné rutiny události domény vyhledáním sestavení, které obsahuje některý z obslužných rutin (pomocí typeof(ValidateOrAddBuyerAggregateWhenXxxx), ale můžete zvolit jakoukoli jinou obslužnou rutinu události k vyhledání sestavení). Vzhledem k tomu, že všechny obslužné rutiny událostí implementují rozhraní IAsyncNotificationHandler, kód pak pouze vyhledá tyto typy a zaregistruje všechny obslužné rutiny událostí.

### <a name="how-to-subscribe-to-domain-events"></a>Jak se přihlásit k odběru událostí domény

Při použití MediatR musí každá obslužná rutina události použít typ události, který je k dispozici na obecném parametru rozhraní INotificationHandler, jak je vidět v následujícím kódu:

```csharp
public class ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler
  : IAsyncNotificationHandler<OrderStartedDomainEvent>
```

Na základě vztahu mezi obslužnou rutinou události a obslužnou rutinou události, kterou lze považovat za odběr, může artefakt MediatR zjistit všechny obslužné rutiny událostí pro každou událost a aktivovat každou z těchto obslužných rutin událostí.

### <a name="how-to-handle-domain-events"></a>Jak zpracovat události domény

Nakonec obslužná rutina události obvykle implementuje kód aplikační vrstvy, který používá úložiště infrastruktury k získání požadovaných dalších agregací a ke spuštění logiky domény s vedlejším účinkem. Následující [kód obslužné rutiny události domény na eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/DomainEventHandlers/OrderStartedEvent/ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler.cs)ukazuje příklad implementace.

```csharp
public class ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler
                   : INotificationHandler<OrderStartedDomainEvent>
{
    private readonly ILoggerFactory _logger;
    private readonly IBuyerRepository<Buyer> _buyerRepository;
    private readonly IIdentityService _identityService;

    public ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler(
        ILoggerFactory logger,
        IBuyerRepository<Buyer> buyerRepository,
        IIdentityService identityService)
    {
        // ...Parameter validations...
    }

    public async Task Handle(OrderStartedDomainEvent orderStartedEvent)
    {
        var cardTypeId = (orderStartedEvent.CardTypeId != 0) ? orderStartedEvent.CardTypeId : 1;
        var userGuid = _identityService.GetUserIdentity();
        var buyer = await _buyerRepository.FindAsync(userGuid);
        bool buyerOriginallyExisted = (buyer == null) ? false : true;

        if (!buyerOriginallyExisted)
        {
            buyer = new Buyer(userGuid);
        }

        buyer.VerifyOrAddPaymentMethod(cardTypeId,
                                       $"Payment Method on {DateTime.UtcNow}",
                                       orderStartedEvent.CardNumber,
                                       orderStartedEvent.CardSecurityNumber,
                                       orderStartedEvent.CardHolderName,
                                       orderStartedEvent.CardExpiration,
                                       orderStartedEvent.Order.Id);

        var buyerUpdated = buyerOriginallyExisted ? _buyerRepository.Update(buyer)
                                                                      : _buyerRepository.Add(buyer);

        await _buyerRepository.UnitOfWork
                .SaveEntitiesAsync();

        // Logging code using buyerUpdated info, etc.
    }
}
```

Předchozí kód obslužné rutiny události domény je považován za kód aplikační vrstvy, protože používá úložiště infrastruktury, jak je vysvětleno v další části vrstvy trvalost v infrastruktuře. Obslužné rutiny událostí mohou také používat jiné součásti infrastruktury.

#### <a name="domain-events-can-generate-integration-events-to-be-published-outside-of-the-microservice-boundaries"></a>Události domény mohou generovat události integrace, které mají být publikovány mimo hranice mikroslužeb.

Nakonec je důležité zmínit, že někdy můžete chtít šířit události napříč více mikroslužeb. Toto šíření je událost integrace a může být publikována prostřednictvím sběrnice událostí z jakékoli obslužné rutiny události konkrétní domény.

## <a name="conclusions-on-domain-events"></a>Závěry o událostech domény

Jak je uvedeno, použijte události domény explicitně implementovat vedlejší účinky změn v rámci domény. Chcete-li použít terminologii DDD, použijte události domény explicitně implementovat vedlejší účinky v rámci jednoho nebo více agregací. Navíc a pro lepší škálovatelnost a menší dopad na uzamčení databáze, použijte konečnou konzistenci mezi agregacemi v rámci stejné domény.

Referenční aplikace používá [MediatR](https://github.com/jbogard/MediatR) k šíření událostí domény synchronně napříč agregacemi v rámci jedné transakce. Můžete však také použít některé implementace AMQP jako [RabbitMQ](https://www.rabbitmq.com/) nebo [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview) k šíření událostí domény asynchronně pomocí konečné konzistence, ale jak je uvedeno výše, musíte zvážit potřebu kompenzačníakce v případě selhání.

## <a name="additional-resources"></a>Další zdroje

- **Greg Young. Co je událost domény?** \
  <https://cqrs.files.wordpress.com/2010/11/cqrs_documents.pdf#page=25>

- **Jan Stenberg. Události domény a konečná konzistence** \
  <https://www.infoq.com/news/2015/09/domain-events-consistency>

- **Jimmyho Bogarda. Lepší vzor událostí domény** \
  <https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/>

- **Vaughn Vernon, to je můj zástupce. Efektivní agregační design část II: Tvorba agregáty spolupracovat** \
  [https://dddcommunity.org/wp-content/uploads/files/pdf\_articles/Vernon\_2011\_2.pdf](https://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf)

- **Jimmyho Bogarda. Posílení vaší domény: Domain Events** \
  <https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/>

- **Tonytruong. Příklad vzoru událostí domény** \
  <https://www.tonytruong.net/domain-events-pattern-example/>

- **Udi Dahan. Jak vytvořit plně zapouzdřené modely domény** \
  <http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/>

- **Udi Dahan. Události domény – take 2** \
  <http://udidahan.com/2008/08/25/domain-events-take-2/>

- **Udi Dahan. Události domény – spása** \
  <http://udidahan.com/2009/06/14/domain-events-salvation/>

- **Jan Kronquist. Nepublikujte domain události, vraťte je!** \
  <https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/>

- **Cesar de la Torre. Události domény vs. Události integrace v architekturách DDD a mikroslužeb** \
  <https://devblogs.microsoft.com/cesardelatorre/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/>

>[!div class="step-by-step"]
>[Předchozí](client-side-validation.md)
>[další](infrastructure-persistence-layer-design.md)
