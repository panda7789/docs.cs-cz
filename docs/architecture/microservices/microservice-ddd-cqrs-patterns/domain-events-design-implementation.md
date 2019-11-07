---
title: Události domény. návrh a implementace
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Získejte podrobné zobrazení událostí domény, klíčový koncept k navázání komunikace mezi agregacemi.
ms.date: 10/08/2018
ms.openlocfilehash: f0dbd6b0e70d825122d319611a327438df065588
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739883"
---
# <a name="domain-events-design-and-implementation"></a>Doménové události: Návrh a implementace

Pomocí událostí domény explicitně implementujte vedlejší účinky změn ve vaší doméně. Jinými slovy a pomocí nástroje DDD, používají události domény k explicitní implementaci vedlejších efektů v rámci více agregací. Volitelně můžete pro lepší škálovatelnost a menší dopad na zámky databáze použít konečnou konzistenci mezi agregacemi v rámci stejné domény.

## <a name="what-is-a-domain-event"></a>Co je doménová událost?

Událost je něco, co se stalo v minulosti. Doménová událost je, něco, co se stalo v doméně, na kterou mají vědět jiné části stejné domény (v procesu). Oznámené části obvykle reagují na události nějakým způsobem.

Důležitou výhodou událostí domény je to, že vedlejší účinky je možné vyjádřit explicitně.

Například pokud používáte pouze Entity Framework a v případě, že je nutné reagovat na nějaké události, pravděpodobně budete kód, který potřebujete, zavřít, abyste mohli událost vyvolala. Takže pravidlo je spojeno, implicitně, do kódu, a musíte se podívat do kódu do, snad a realizovat, že je pravidlo implementováno.

Na druhé straně použití událostí domény dává pojem explicitní, protože existuje `DomainEvent` a nejméně jedna `DomainEventHandler`.

Například v aplikaci eShopOnContainers, když je vytvořena objednávka, se uživatel bude jednat o kupující, takže je vyvoláno `OrderStartedDomainEvent` a bude zpracováno v `ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler`, takže je základní koncept zřejmý.

Krátké události domény vám pomůžou vyjádřit, explicitně a pravidla domény, a to na základě jazyka všudypřítomný poskytovaného odborníky na domény. Události domény také umožňují lepší oddělení otázek mezi třídami v rámci stejné domény.

Je důležité zajistit, aby, stejně jako databázová transakce, buď všechny operace týkající se události domény úspěšně skončily, nebo žádný z nich.

Události domény jsou podobné událostem ve stylu zasílání zpráv s jedním důležitým rozdílem. V případě skutečného zasílání zpráv, služby Řízení front zpráv, zprostředkovatelů zpráv nebo Service Bus pomocí AMQP se zpráva vždy odesílá asynchronně a komunikuje napříč procesy a počítači. To je užitečné pro integraci více ohraničených kontextů, mikroslužeb nebo dokonce různých aplikací. S událostmi domény ale budete chtít vyvolat událost z aktuálně spuštěné operace domény, ale chcete, aby se v rámci stejné domény staly všechny vedlejší účinky.

Události domény a jejich vedlejší účinky (akce aktivované následně, které jsou spravovány obslužnými rutinami událostí) by se měly provádět téměř okamžitě, obvykle v procesu a v rámci stejné domény. Proto mohou být události domény synchronní nebo asynchronní. Události integrace by však měly být vždy asynchronní.

## <a name="domain-events-versus-integration-events"></a>Události v doméně versus integrační události

Sémanticky, události v doméně a integraci jsou stejné: oznámení o něco, co se právě stalo. Nicméně jejich implementace musí být odlišná. Události domény jsou pouze zprávy vložené do dispečeru událostí domény, které by mohly být implementovány jako zprostředkovatel v paměti na základě IoC kontejneru nebo jakékoli jiné metody.

Na druhé straně účelem integračních událostí je rozšířit potvrzené transakce a aktualizace na další subsystémy, ať už se jedná o jiné mikroslužby, ohraničené kontexty nebo dokonce externí aplikace. Proto by se měly vyskytovat pouze v případě, že je entita úspěšně zachovaná, jinak je to, jako kdyby k celé operaci nikdy nedošlo.

Jak již bylo zmíněno dříve, události integrace musí být založeny na asynchronní komunikaci mezi několika mikroslužbami (dalšími ohraničenými kontexty) nebo i s externími systémy nebo aplikacemi.

Proto rozhraní sběrnice událostí potřebuje určitou infrastrukturu, která umožňuje meziprocesovou a distribuovanou komunikaci mezi potenciálně vzdálenými službami. Může vycházet z komerční služby Service Bus, front, sdílené databáze používané jako poštovní schránky nebo jakéhokoli jiného distribuovaného a ideálního systému zasílání zpráv.

## <a name="domain-events-as-a-preferred-way-to-trigger-side-effects-across-multiple-aggregates-within-the-same-domain"></a>Události domény jako preferovaný způsob, jak aktivovat vedlejší účinky napříč více agregacemi v rámci stejné domény

Pokud provádění příkazu, který souvisí s jednou agregací instance, vyžaduje, aby byla na jednom nebo více dalších agregacích spuštěna další pravidla domény, měli byste navrhnout a implementovat tyto vedlejší účinky, které budou aktivovány událostmi domény. Jak je znázorněno na obrázku 7-14 a jako jeden z nejdůležitějších případů použití by měla být k šíření změn stavu mezi několika agregacemi v rámci stejného doménového modelu používána doménová událost.

![Diagram znázorňující událost v doméně, která řídí data pro agregaci nákupčího.](./media/domain-events-design-implementation/domain-model-ordering-microservice.png)

**Obrázek 7-14**. Události domény pro vymáhání konzistence mezi několika agregacemi v rámci stejné domény

Obrázek 7-14 ukazuje, jak je dosaženo konzistence mezi agregacemi v doménových událostech. Když uživatel zahájí objednávku, objednávka Aggregate odešle událost `OrderStarted` domény. Událost OrderStarted domény je zpracována agregací Buyercollection za účelem vytvoření objektu Buyer v mikroslužbě řazení na základě původních informací o uživateli z mikroslužby identity (s informacemi, které jsou k dispozici v příkazu CreateOrder).

Alternativně můžete mít agregovaný kořenový adresář pro události vyvolané členy svých agregací (podřízené entity). Například každá podřízená entita OrderItem může vyvolat událost, pokud je cena položky vyšší než konkrétní hodnota nebo když je hodnota položky produktu příliš vysoká. Agregovaný kořen může následně přijímat tyto události a provádět globální výpočet nebo agregaci.

Je důležité pochopit, že tato komunikace založená na událostech není implementována přímo v agregacích. je nutné implementovat obslužné rutiny událostí domény.

Zpracování událostí domény se týká aplikace. Vrstva doménového modelu by se měla zaměřit jenom na doménovou logiku – věci, které by znalec domény porozuměl, nikoli aplikační infrastrukturu, jako jsou obslužné rutiny a akce trvalosti vedlejšího účinku pomocí úložišť. Proto je úroveň vrstvy aplikace, kde byste měli mít obslužné rutiny událostí domény aktivované akce při vyvolání události domény.

Události domény lze také použít k aktivaci libovolného počtu akcí aplikace a o tom, co je důležitější, musí být otevřeny, aby bylo možné toto číslo v budoucnu v případě oddálení zvýšit. Například při zahájení objednávky můžete chtít publikovat událost domény a rozšířit tyto informace na jiné agregace nebo dokonce vyvolat akce aplikace, jako je oznámení.

Klíčovým bodem je otevřený počet akcí, které se mají provést, když dojde k události domény. Nakonec se budou rozšiřovat akce a pravidla v doméně a aplikaci. Složitost nebo počet akcí vedlejšího účinku, když se něco stane, ale pokud byl váš kód spojený s "lepidlem" (tj. vytváření specifických objektů s `new`), pak pokaždé, když jste potřebovali přidat novou akci, byste také museli změnit práci a testovaný kód.

Tato změna může mít za následek nové chyby a tento přístup se také přesměruje na [otevřený/uzavřený princip](https://en.wikipedia.org/wiki/Open/closed_principle) z [Solid](https://en.wikipedia.org/wiki/SOLID). Nejen to, původní třída, která prováděla orchestraci operací, by mohla růst a růst, což vede k [jedné zásadě zodpovědnosti (SRP)](https://en.wikipedia.org/wiki/Single_responsibility_principle).

Na druhé straně, pokud používáte události domény, můžete vytvořit jemně odstupňovanou a oddělenou implementaci tím, že oddělíte zodpovědnosti pomocí tohoto přístupu:

1. Odešlete příkaz (například CreateOrder).
2. Přijmout příkaz v obslužné rutině příkazu.
   - Provede jednu agregační transakci.
   - Volitelné Vyvolat události domény pro vedlejší účinky (například OrderStartedDomainEvent).
3. Zpracování událostí domény (v rámci aktuálního procesu), který spustí otevřený počet vedlejších účinků v několika agregacích nebo akcích aplikace. Příklad:
   - Ověřte nebo vytvořte metodu Buyer a platby.
   - Vytvoření a odeslání související integrační události do sběrnice událostí pro šíření stavů napříč mikroslužbami nebo Aktivace externích akcí, jako je odeslání e-mailu kupujícímu.
   - Zpracovat jiné vedlejší účinky.

Jak je znázorněno na obrázku 7-15 od stejné domény, můžete zpracovávat více akcí souvisejících s ostatními agregacemi v doméně nebo dalšími akcemi aplikace, které potřebujete provést v rámci mikroslužeb, které se připojují k integračním událostem a sběrnici událostí.

![Diagram znázorňující událost domény, která předává data do několika obslužných rutin událostí.](./media/domain-events-design-implementation/aggregate-domain-event-handlers.png)

**Obrázek 7-15**. Zpracování více akcí na doménu

Může existovat několik obslužných rutin pro stejnou událost domény v aplikační vrstvě, jedna obslužná rutina může vyhodnotit konzistenci mezi agregacemi a jiná obslužná rutina může publikovat událost integrace, aby s ní mohli ostatní mikroslužby pracovat. Obslužné rutiny událostí jsou obvykle umístěny v aplikační vrstvě, protože budete používat objekty infrastruktury jako úložiště nebo aplikační rozhraní API pro chování mikroslužeb. V takovém smyslu jsou obslužné rutiny událostí podobné obslužným rutinám příkazů, takže obě jsou součástí aplikační vrstvy. Důležitým rozdílem je, že by se měl příkaz zpracovat jen jednou. Událost domény může být zpracována nula nebo *n* krát, protože může být přijata více přijímači nebo obslužnými rutinami událostí s jiným účelem pro každou obslužnou rutinu.

Otevřený počet obslužných rutin na jednu doménu umožňuje přidat libovolný počet pravidel domény podle potřeby, aniž by to ovlivnilo aktuální kód. Například implementace následujícího obchodního pravidla může být stejně snadné jako přidání několika obslužných rutin událostí (nebo dokonce jenom jednoho):

> Pokud celková částka zakoupená zákazníkem v obchodě v rámci libovolného počtu objednávek přesáhne $6 000, použijte pro každou novou objednávku 10% slevu a upozorněte zákazníka e-mailem o této slevě na budoucí objednávky.

## <a name="implement-domain-events"></a>Implementace událostí domény

V C#nástroji je doménová událost jednoduše strukturou datového hospodářství nebo třídy, jako je DTO, se všemi informacemi souvisejícími s tím, co se právě stalo v doméně, jak je znázorněno v následujícím příkladu:

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

To je v podstatě třída, která obsahuje všechna data související s událostí OrderStarted.

V souvislosti s všudypřítomný jazykem domény, vzhledem k tomu, že událost je něco, co se stalo v minulosti, by měl být název třídy události reprezentován jako poslední vhodné příkaz, jako je OrderStartedDomainEvent nebo OrderShippedDomainEvent. To je způsob, jakým je událost domény implementována v eShopOnContainers při řazení mikroslužeb.

Jak bylo uvedeno dříve, důležitou charakteristikou událostí je, že vzhledem k tomu, že událost je něco, co se stalo v minulosti, by nemělo dojít ke změně. Proto musí být neměnné třídy. Můžete vidět v předchozím kódu, ke kterému jsou vlastnosti jen pro čtení. Neexistuje žádný způsob, jak objekt aktualizovat, můžete hodnoty nastavit pouze při jeho vytváření.

Je důležité zdůraznit, že pokud byly události domény zpracovány asynchronně, pomocí fronty, která vyžadovala serializaci a deserializaci objektů událostí, by vlastnost musela být "soukromá sada" místo "jen pro čtení", proto by byl deserializace dokáže přiřadit hodnoty při vyřazování z fronty. Nejedná se o problém ve službě řazení mikroslužeb, protože událost/sub v doméně je implementovaná synchronně pomocí MediatR.

### <a name="raise-domain-events"></a>Vyvolat události domény

Další otázkou je postup, jak vyvolat událost domény, aby dosáhla souvisejících obslužných rutin událostí. Můžete použít více přístupů.

UDI Dahan původně navržen (například v několika souvisejících příspěvcích, například v případě [událostí domény – Vezměte 2](http://udidahan.com/2008/08/25/domain-events-take-2/)) pomocí statické třídy pro správu a vyvolávání událostí. To může zahrnovat statickou třídu s názvem DomainEvents, která by mohla vyvolat události domény hned po jejím volání, a to pomocí syntaxe, jako je `DomainEvents.Raise(Event myEvent)`. Jimmy Bogard zapsal Blogový příspěvek ([posilováním domény](https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/)domén), která doporučuje podobný přístup.

Nicméně pokud je třída událostí domény statická, také odesílá obslužné rutiny okamžitě. Díky tomu je testování a ladění obtížnější, protože obslužné rutiny událostí s logikou vedlejších účinků jsou spouštěny ihned po vyvolání události. Při testování a ladění se chcete zaměřit na a co se děje v aktuálních agregačních třídách; nechcete náhle přesměrovat na jiné obslužné rutiny událostí pro vedlejší účinky související s jinými agregacemi nebo logikou aplikace. To je důvod, proč se vyvinuly další přístupy, jak je vysvětleno v další části.

#### <a name="the-deferred-approach-to-raise-and-dispatch-events"></a>Odložený přístup k událostem vyvolání a odeslání

Místo přímého odeslání do obslužné rutiny události domény lepším přístupem je přidání událostí domény do kolekce a následné odeslání těchto událostí domény *přímo* do nebo *hned* *po* potvrzení transakce (jako u SaveChanges v EF). (Tento přístup byl popsán v Jimmy Bogard v tomto příspěvku [pro lepší vzorec doménových událostí](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/).)

Rozhodnutí o tom, jestli odesíláte události domény přímo před nebo hned po potvrzení transakce, je důležité, protože určuje, jestli se mají zahrnout vedlejší účinky jako součást stejné transakce nebo v různých transakcích. V druhém případě je nutné se zabývat s konečnou konzistencí napříč více agregacemi. Toto téma je popsáno v další části.

Odvoditelné přístupu je to, co eShopOnContainers používá. Nejprve do kolekce nebo seznamu událostí na entitu přidejte události, které se děje ve svých entitách. Tento seznam by měl být součástí objektu entity, nebo dokonce i lépe, který je součástí základní třídy entity, jak je znázorněno v následujícím příkladu základní třídy entity:

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

V případě, že chcete vyvolat událost, stačí ji přidat do kolekce událostí z kódu v libovolné metodě agregační – kořenová entita.

Následující kód, část [Order Aggregate-root na eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs), ukazuje příklad:

```csharp
var orderStartedDomainEvent = new OrderStartedDomainEvent(this, //Order object
                                                          cardTypeId, cardNumber,
                                                          cardSecurityNumber,
                                                          cardHolderName,
                                                          cardExpiration);
this.AddDomainEvent(orderStartedDomainEvent);
```

Všimněte si, že jediná věc, kterou metoda AddDomainEvent provádí, je přidání události do seznamu. Zatím není odeslaná žádná událost a zatím se nevyvolá žádná obslužná rutina události.

Opravdu chcete později odeslat události, když transakci odešlete do databáze. Pokud používáte Entity Framework Core, to znamená v metodě SaveChanges DbContext EF, jak je uvedeno v následujícím kódu:

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

S tímto kódem odesíláte události entit do příslušných obslužných rutin událostí.

Celkový výsledek je, že jste odkázali vyvolání události domény (jednoduchým přidáním do seznamu v paměti) od jejich odeslání obslužné rutině události. V závislosti na tom, jaký typ dispečera používáte, můžete události odesílat synchronně nebo asynchronně.

Počítejte s tím, že hranice transakcí přicházejí do značného množství. Pokud vaše pracovní jednotka a transakce mohou rozbírat více než jednu agregaci (jako při použití EF Core a relační databáze), může to dobře fungovat. Pokud však transakce nemůže zahrnovat agregace, například pokud používáte databázi NoSQL jako Azure CosmosDB, je nutné implementovat další kroky, abyste dosáhli konzistence. Toto je další důvod, proč ignorování trvalosti není univerzální; závisí na používaném úložném systému.

### <a name="single-transaction-across-aggregates-versus-eventual-consistency-across-aggregates"></a>Jedna transakce napříč agregacemi a konečná konzistence napříč agregacemi

Otázka, zda provést jednu transakci napříč agregacemi a spoléhácí se na konečnou konzistenci napříč těmito agregacemi, je kontroverzním jedna. Řada DDD autorů, jako je Eric Evans a Vaughn Vernon, doporučuje pravidlo, že jedna transakce = jedna agregovaná a proto tvrdí pro konečnou konzistenci napříč agregacemi. V případě návrhu založeného na *doméně*například Eric Evans uvádí toto:

> Všechna pravidla, která jsou nad agregacemi, by neměla být vždy aktuální. Pomocí zpracování událostí, dávkového zpracování nebo jiných mechanismů aktualizace je možné jiné závislosti vyřešit v určitou dobu. (stránka 128)

Vaughn Vernon uvádí následující v [účinném agregovaném návrhu. Část II: vytváření agregačních prvků společně](https://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf):

> Proto pokud provádění příkazu u jedné agregační instance vyžaduje, aby další obchodní pravidla běžela v jedné nebo více agregacích, použijte konečnou \[...\] existuje praktický způsob, jak podporovat konečnou konzistenci v modelu DDD. Agregační metoda publikuje událost domény, která je v čase Doručená jednomu nebo více asynchronním předplatitelům.

Tato odůvodnění je založena na přechodu jemně odstupňovaných transakcí namísto transakcí, které pokrývá mnoho agregací nebo entit. Výsledkem je, že v druhém případě bude počet zámků databáze podstatný v rozsáhlých aplikacích s vysokými nároky na škálovatelnost. Přechodu se skutečnost, že vysoce škálovatelné aplikace nepotřebují okamžitou transakční konzistenci mezi několika agregacemi, což pomáhá přijmout koncept konečné konzistence. Tyto atomické změny často nejsou potřebné pro firmu a jsou v každém případě odpovědné odborníky na domény, kteří říkají, jestli konkrétní operace potřebují atomické transakce, nebo ne. Pokud operace vždy potřebuje atomovou transakci mezi více agregacemi, můžete se zeptat, zda má být agregace větší nebo nebyla správně navržena.

Další vývojáři a architekty, jako je Jimmy Bogard, jsou v pořádku, pokud pokrývá jednu transakci napříč několika agregacemi, ale pouze v případě, že tyto další agregace souvisejí s vedlejšími účinky pro stejný původní příkaz. Například v [lepším vzoru doménových událostí](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/)Bogard říká toto:

> Obvykle chci, aby došlo k vedlejším účinkům události domény v rámci stejné logické transakce, ale ne nutně ve stejném rozsahu vyvolání události domény \[...\] těsně před potvrzením naší transakce, odesíláme naše události do jejich příslušné obslužné rutiny.

Pokud odesíláte události domény přímo *před* potvrzením původní transakce, je to proto, že chcete, aby se vedlejší účinky těchto událostí zahrnuly do stejné transakce. Například pokud metoda EF DbContext SaveChanges selže, transakce vrátí všechny změny, včetně výsledku všech operací vedlejších účinků implementovaných souvisejícími obslužnými rutinami událostí domény. Důvodem je to, že rozsah životnosti DbContext je ve výchozím nastavení definovaný jako "obor". Proto je objekt DbContext sdílen mezi více objektů úložiště, které jsou vytvořeny v rámci stejného oboru nebo grafu objektů. Při vývoji webových rozhraní API nebo aplikací MVC se to bude shodovat s oborem HttpRequest.

Ve skutečnosti může být napravo obě přístupy (jedna atomická transakce a konečná konzistence). Ve skutečnosti záleží na vašich požadavcích vaší domény nebo podniku a na tom, co vás odborníci na doménu říkají. Záleží taky na tom, jak škálovatelná služba vyžaduje (podrobnější transakce mají méně vliv na zámky databáze). A závisí na tom, kolik investic jste ochotni ve svém kódu. vzhledem k tomu, že jakákoli konzistence vyžaduje složitější kód, aby se zjistily možné nekonzistence napříč agregacemi a nutnost implementovat kompenzační akce. Vezměte v úvahu, že pokud zadáte změny do původní agregace a následně při odeslání událostí, pokud dojde k problému a obslužné rutiny události nemohou potvrdit své vedlejší účinky, budete mít nekonzistence mezi agregacemi.

Způsob, jak umožnit kompenzační akce, by měl ukládat události domény do dalších databázových tabulek, aby mohly být součástí původní transakce. Následně můžete mít dávkový proces, který detekuje nekonzistence a spouští kompenzační akce porovnáním seznamu událostí s aktuálním stavem agregací. Kompenzační akce jsou součástí komplexního tématu, které bude vyžadovat hloubkovou analýzu z vaší strany, která zahrnuje jejich diskuzi s odborníky z obchodních uživatelů a domén.

V každém případě můžete zvolit přístup, který potřebujete. Ale počáteční odložený přístup – vyvolal události před potvrzením, takže používáte jedinou transakci – je nejjednodušší přístup při použití EF Core a relační databáze. Implementaci a platnost je snazší v mnoha obchodních případech. Je to také přístup k použití při řazení mikroslužby v eShopOnContainers.

Ale jak skutečně odesíláte tyto události do příslušných obslužných rutin událostí? Jaký je objekt `_mediator`, který vidíte v předchozím příkladu? Je nutné, abyste provedli postupy a artefakty, které používáte k mapování mezi událostmi a jejich obslužnými rutinami událostí.

### <a name="the-domain-event-dispatcher-mapping-from-events-to-event-handlers"></a>Dispečer událostí domény: mapování událostí na obslužné rutiny událostí

Jakmile budete moci odeslat nebo publikovat události, budete potřebovat nějaký typ artefaktu, který bude publikovat událost, aby každá související obslužná rutina mohla získat a zpracovat vedlejší účinky na základě této události.

Jedním z přístupů je skutečný systém zasílání zpráv nebo dokonce i sběrnice událostí, která je možná založená na službě Service Bus, a to na rozdíl od událostí v paměti. Pro první případ se ale skutečná výměna zpráv přehnaně důkladné pro zpracování událostí domény, protože stačí tyto události zpracovat v rámci stejného procesu (to znamená v rámci stejné domény a aplikační vrstvy).

Další způsob, jak mapovat události na více obslužných rutin událostí, je použití registračních typů v kontejneru IoC, takže můžete dynamicky odvodit, kam se mají události odesílat. Jinými slovy, potřebujete zjistit, jaké obslužné rutiny události potřebují získat konkrétní událost. Obrázek 7-16 ukazuje zjednodušený přístup k tomuto přístupu.

![Diagram znázorňující dispečera událostí domény odesílající události do příslušných obslužných rutin.](./media/domain-events-design-implementation/domain-event-dispatcher.png)

**Obrázek 7-16**. Dispečer událostí domény pomocí IoC

Můžete sestavit všechny instalace a artefakty k implementaci tohoto přístupu sami sebe. Můžete ale také použít dostupné knihovny, jako je [MediatR](https://github.com/jbogard/MediatR) , které používají kontejner IOC v rámci pokrývání. Proto můžete přímo použít předdefinovaná rozhraní a metody publikování/odeslání objektu poskytovatele.

V kódu je nejprve nutné zaregistrovat typy obslužných rutin událostí v kontejneru IoC, jak je znázorněno v následujícím příkladu v [EShopOnContainers řazení mikroslužby](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/MediatorModule.cs):

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

Kód nejprve identifikuje sestavení, které obsahuje obslužné rutiny události domény, umístěním sestavení, které obsahuje některý z obslužných rutin (pomocí typeof (ValidateOrAddBuyerAggregateWhenXxxx), ale můžete zvolit jakoukoli jinou obslužnou rutinu události pro vyhledání sestavení). Vzhledem k tomu, že všechny obslužné rutiny událostí implementují rozhraní IAsyncNotificationHandler, pak kód jednoduše vyhledá tyto typy a zaregistruje všechny obslužné rutiny událostí.

### <a name="how-to-subscribe-to-domain-events"></a>Přihlášení k odběru událostí domény

Při použití MediatR musí každá obslužná rutina události použít typ události, který je k dispozici na obecném parametru rozhraní INotificationHandler, jak vidíte v následujícím kódu:

```csharp
public class ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler
  : IAsyncNotificationHandler<OrderStartedDomainEvent>
```

Na základě vztahu mezi událostí a obslužnou rutinou události, kterou lze považovat za odběr, artefakt MediatR může zjistit všechny obslužné rutiny událostí pro každou událost a aktivovat každou z těchto obslužných rutin událostí.

### <a name="how-to-handle-domain-events"></a>Postup zpracování událostí domény

Nakonec obslužná rutina události obvykle implementuje kód vrstvy aplikace, který používá úložiště infrastruktury k získání požadovaných dalších agregací a k provedení logiky domény s vedlejšími účinky. Následující [kód obslužné rutiny události domény v eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/DomainEventHandlers/OrderStartedEvent/ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler.cs)ukazuje příklad implementace.

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

Předchozí kód obslužné rutiny události domény se považuje za kód vrstvy aplikace, protože používá úložiště infrastruktury, jak je vysvětleno v další části vrstvy trvalosti infrastruktury. Obslužné rutiny událostí mohou také používat jiné součásti infrastruktury.

#### <a name="domain-events-can-generate-integration-events-to-be-published-outside-of-the-microservice-boundaries"></a>Události v doméně mohou generovat události integrace, které budou publikovány mimo hranice mikroslužeb.

Nakonec je důležité si všimnout, že někdy budete chtít rozšířit události napříč více mikroslužbami. Tato propagace je integrační událost a mohla by být publikována prostřednictvím sběrnice událostí z jakékoli konkrétní obslužné rutiny události domény.

## <a name="conclusions-on-domain-events"></a>Závěry o událostech domény

Jak je uvedeno, pomocí událostí domény explicitně implementujte vedlejší účinky změn ve vaší doméně. Chcete-li použít DDD, použijte k explicitní implementaci vedlejších efektů v rámci jednoho nebo více agregací události domény. Navíc a kvůli lepší škálovatelnosti a menšímu dopadu na zámky databáze používejte konečnou konzistenci mezi agregacemi v rámci stejné domény.

## <a name="additional-resources"></a>Další zdroje

- **Greg Young. Co je doménová událost?** \
  <https://cqrs.files.wordpress.com/2010/11/cqrs_documents.pdf#page=25>

- **Stenberg LED. Události domény a konečná konzistence** \
  <https://www.infoq.com/news/2015/09/domain-events-consistency>

- **Jimmy Bogard. Lepší vzor událostí domény** \
  <https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/>

- **Vaughn Vernon. Efektivní agregovaná část návrhu II: vytváření agregačních prvků společně** \
  [https://dddcommunity.org/wp-content/uploads/files/pdf\_articles/Vernon\_2011\_2.pdf](https://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf)

- **Jimmy Bogard. Posílení vaší domény: události domény** \
  <https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/>

- **Adam Truong. Příklad vzorce pro události domény** \
  <https://www.tonytruong.net/domain-events-pattern-example/>

- **UDI Dahan. Vytvoření plně zapouzdřených doménových modelů** \
  <http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/>

- **UDI Dahan. Události domény – Vezměte 2** \
  <http://udidahan.com/2008/08/25/domain-events-take-2/>

- **UDI Dahan. Události domény – Salvation** \
  <http://udidahan.com/2009/06/14/domain-events-salvation/>

- **Kronquist LED. Nepublikujte události domény, vraťte je!** \
  <https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/>

- **Cesar de la Torre. Události v doméně vs. integrační události v architekturách DDD a mikroslužeb** \
  <https://devblogs.microsoft.com/cesardelatorre/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/>

>[!div class="step-by-step"]
>[Předchozí](client-side-validation.md)
>[Další](infrastructure-persistence-layer-design.md)
