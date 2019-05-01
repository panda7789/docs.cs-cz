---
title: Události domény. návrh a implementace
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Získáte podrobné zobrazení událostí domény klíčovým konceptem navázal komunikaci mezi agregace.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: 353e50de65f21930ebe0bef9e239e1e333403676
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62020046"
---
# <a name="domain-events-design-and-implementation"></a>Doménové události: Návrh a implementace

Používejte události domény o explicitní implementaci vedlejší účinky změn v rámci vaší domény. Jiná slova, a pomocí terminologie DDD používejte události domény o explicitní implementaci vedlejší účinky napříč více agregací. Volitelně můžete pro lepší škálovatelnost a menší dopad na zámků databáze pomocí konečné konzistenci mezi agregací ve stejné doméně.

## <a name="what-is-a-domain-event"></a>Co je událost domény?

Událost je něco, ke kterým došlo v minulosti. Událost domény se něco, co se stalo v doméně, který má jiné části stejné domény (v procesu) je potřeba vědět. Části oznámený obvykle nějakým způsobem reagovat na ně události.

Důležitou výhodou metody události domény je, že je explicitně vyjádřené vedlejší účinky.

Například pokud používáte pouze Entity Framework a musí být reakci na nějakou událost, by pravděpodobně kódu, je třeba blízko co aktivuje události. Takže pravidla získá s velkou provázaností, implicitně, kódu, a budete muset prozkoumat kód a doufá, uvědomte si pravidlo je implementováno existuje.

Na druhé straně pomocí události domény umožňuje koncept explicitní, protože je `DomainEvent` a alespoň jednu `DomainEventHandler` zahrnuté.

Například v aplikaci eShopOnContainers aplikace při vytvoření objednávky, uživatel bude kupujících, proto `OrderStartedDomainEvent` je vyvolána a zpracovávány v `ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler`, takže základní koncept je evidentní.

Stručně řečeno události domény můžete vyjádřit explicitně, pravidla domény, na základě v jazyce všudypřítomná poskytované odborníky domény. Události domény také umožňují lepší oddělené oblasti zájmu mezi třídami ve stejné doméně.

Je důležité zajistit, že stejně jako databázové transakce buď všechny operace související s událostí domény úspěšně dokončit nebo žádná z nich proveďte.

Domény události jsou podobné událostem zasílání zpráv ve stylu s jeden důležitý rozdíl. S skutečné zasílání zpráv služby Řízení front zpráv, zprostředkovatele zpráv a služby Service bus pomocí protokolu AMQP zprávu vždy odeslán asynchronně a předávat v rámci procesy a počítače. To je užitečné pro integraci více ohraničených kontextech, mikroslužby nebo dokonce během různých aplikací. S událostmi domény chcete vyvolat událost z operace domény, které jsou aktuálně spuštěné, ale chcete, aby všechny vedlejší účinky na výskyt ve stejné doméně.

Události domény a jejich vedlejších účinků (akce aktivuje později, které se spravují přes obslužné rutiny událostí) se budou objevovat téměř okamžitě, obvykle v rámci procesu a ve stejné doméně. Události domény může proto být synchronní nebo asynchronní. Integrace událostí, ale musí být vždy asynchronní.

## <a name="domain-events-versus-integration-events"></a>Události domény oproti události integrace

Sémanticky, domény a integrace událostí se stejnou věc: oznámení o něco, stačí ke kterým došlo. Jejich provádění však musí být jiný. Události domény jsou pouze zprávy do dispečeru událostí domény, který by mohl implementovat jako zprostředkovatel v paměti založené na kontejner IoC nebo jakékoliv jiné metody.

Na druhé straně účelem integrace událostí je šířit potvrzené transakce a aktualizace pro další subsystémy, ať už jsou ostatní mikroslužeb, ohraničených kontextech nebo dokonce i externích aplikací. Proto by měl nastat pokud entita se úspěšně ukládají, v opačném případě, že je jako celá operace se nikdy stalo.

Jak jsme zmínili, integrace událostí musí vycházet asynchronní komunikaci mezi několika mikroslužbami (omezená kontexty jiných) nebo i externích systémů a aplikací.

Rozhraní události Service bus proto potřebuje určitou infrastrukturu, která umožňuje mezi procesu a distribuovat mezi potenciálně vzdálené komunikace. Může být založen na komerční služby Service bus, front, sdílené databáze používaná jako poštovní schránku nebo jakékoli jiné distribuované a v ideálním případě push založené na systému zasílání zpráv.

## <a name="domain-events-as-a-preferred-way-to-trigger-side-effects-across-multiple-aggregates-within-the-same-domain"></a>Události domény jako upřednostňovaný způsob, jak spouštět vedlejší účinky napříč více agregací ve stejné doméně

Pokud spuštění příkazu vztahující se k jednomu agregace instance vyžaduje další doménu pravidel ke spuštění na jeden nebo více dalších agregace, by měl navrhujte a implementujte tyto vedlejší účinky bude aktivovat události domény. Jak je znázorněno v obrázek 7-14 a jako jeden z vašich nejdůležitějších případy použití, událost domény by měla sloužit k šíření změn stavu napříč více agregace v rámci stejného modelu domény.

![Konzistenci mezi agregace se dosahuje prostřednictvím události domény, agregační pořadí odešle událost OrderStarted domény, který je zpracován aktualizovat agregační odběratele. ](./media/image15.png)

**Obrázek 7-14**. Události domény k vynucení konzistence mezi více agregací ve stejné doméně

Obrázek když uživatel zahájí objednávky, aktivuje událost domény OrderStarted vytvoření objektu kupujících v pořadí mikroslužeb, založené na původní informace o uživateli z mikroslužeb identity (pomocí informací uvedených v příkazu CreateOrder). Agregace pořadí vygeneruje událost domény při vytváření na prvním místě.

Alternativně můžete mít agregační kořenové přihlášený(á) k odběru události vyvolané službou členy jeho agregace (podřízené entity). Každé podřízené entity OrderItem například může vyvolat událost při větším než určitou velikostí cena zboží, nebo když částka položka produktu je příliš vysoká. Agregační kořenové můžete přijímat události a provádět globální výpočtu nebo agregace.

Je důležité pochopit, že tato komunikace založené na události není implementovaná přímo v rámci agregace; budete muset implementovat obslužné rutiny událostí domény.

Zpracování událostí domény je aplikace. Vrstvě doménového modelu byste se zaměřit jenom na logiku domény – věcí, které by pochopit doménu, není aplikační infrastruktury jako vedlejší efekt trvalost akce pomocí úložišť a obslužné rutiny. Na úrovni vrstvy aplikace je proto, ve kterém byste měli mít obslužné rutiny událostí domény Aktivace akce, když je vyvolána událost domény.

Domény události lze také spustit libovolný počet akcí aplikace a co je důležitější, musí být otevřený, aby toto číslo v budoucnu zvýšit oddělující způsobem. Například při spuštění příkazu můžete publikovat událost domény, šíření tyto informace do jiné agregace nebo dokonce, aby se vyvolala se akce aplikace jako oznámení.

Zásadním aspektem je otevřít počet akce, které se spustí při výskytu události domény. Nakonec se zvětší akce a pravidla v doméně a aplikace. Složitost nebo počet akcí vedlejší efekt při určité události, které se zvýší, ale pokud se váš kód spolu s "spojovací" (to znamená, vytváří se specifickými objekty s `new`), pak pokaždé, když je potřeba přidat novou akci je také třeba změnit pracovní a testovaný kód.

Tato změna by mohla vést k nové chyby a tento přístup také proti přejde [Princip Open/uzavřeno](https://en.wikipedia.org/wiki/Open/closed_principle) z [SOLID](https://en.wikipedia.org/wiki/SOLID). Not, nejen to, původní třídy, která byla Orchestrace operace by růst i při pozdějším růstu a ten se ukládá proti [jedné zásadě odpovědnost (SRP)](https://en.wikipedia.org/wiki/Single_responsibility_principle).

Na druhé straně Pokud používáte události domény, můžete vytvořit podrobné a samostatné implementace podle oddělení odpovědností tento přístup:

1. Poslat příkaz (například CreateOrder).
2. Zobrazit příkaz v obslužná rutina příkazu.
   - Spuštění jedné agregace transakce.
   - (Volitelné) Vyvolávání událostí domény pro vedlejší účinky (například OrderStartedDomainEvent).
3. Popisovač události domény (v rámci aktuální proces), které spustí otevřít počet vedlejší účinky ve více agregace nebo akce aplikací. Příklad:
   - Ověřit nebo vytvořit odběratele a způsobu platby.
   - Vytvoření a odeslání událostí související integrace do sběrnice událostí šíření stavů mezi mikroslužbami nebo aktivační událost externí akce, jako je odesílání e-mailu do odběratele.
   - Zpracování vedlejší efekty.

Jak je znázorněno v obrázek 7-15, od stejné událost domény, můžete zpracovávat několik akcí souvisejících s jiné agregace v doméně nebo akce další aplikace, které je potřeba provést přes připojení pomocí integrace událostí a sběrnice událostí mikroslužeb.

![Může existovat několik obslužných rutin pro stejnou událost domény v aplikační vrstvě, jedna obslužná rutina může vyřešit konzistenci mezi agregace a jinou obslužnou rutinu událost můžete publikovat integraci, takže můžete s ním něco udělat další mikroslužeb.](./media/image16.png)

**Obrázek 7 – 15**. Zpracování více akcí pro doménu

Obslužné rutiny událostí jsou obvykle v aplikační vrstvě, protože objektů infrastruktury, jako jsou úložiště nebo rozhraní API aplikace bude používat pro chování mikroslužbách. V tomto smyslu obslužné rutiny událostí jsou podobně jako obslužné rutiny příkazů, tak jak jsou součástí aplikačního. Důležitý rozdíl je, že příkaz by se měly zpracovat pouze jednou. Událost domény může být zpracována nula nebo *n* vícekrát, protože může být přijata několik příjemců nebo obslužné rutiny události s jiným způsobem pro každou obslužnou rutinu.

Otevřít počet obslužné rutiny na událost domény umožňuje přidat tolik domény pravidla bez podle potřeby, aniž by to ovlivnilo stávajícího kódu. Implementace následující obchodní pravidlo například může být stejně jednoduché jako přidání několik obslužných rutin událostí (nebo dokonce jen jeden):

> Pokud celková částka zakoupené ze strany zákazníka v úložišti, napříč libovolným počtem objednávky, překročí 6 000 $, platí pro každou novou objednávku 10 % sleva na produkt slevy a informovat zákazníka s e-mailu o tuto slevu pro budoucí objednávky.

## <a name="implement-domain-events"></a>Implementace událostí domény

V jazyce C# událost domény je jednoduše ruku datové struktury nebo třídy, jako je objekt DTO, všechny informace související s co se právě stalo v doméně, jak je znázorněno v následujícím příkladu:

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

Toto je v podstatě třída, která obsahuje všechna data související s OrderStarted událostí.

Z hlediska všudypřítomná jazyk domény, protože událost je něco, co se stalo v minulosti, název třídy události by měly být zastoupeny jako minulý čas operace, jako je OrderStartedDomainEvent nebo OrderShippedDomainEvent. Je to, jak je v pořadí mikroslužeb v aplikaci eShopOnContainers implementovaná událost domény.

Jak je uvedeno výše, je důležitou vlastnost událostí, že vzhledem k tomu, že událost je něco, co se stalo v minulosti by neměly měnit. Proto musí být neměnné třídy. Zobrazí se v předcházejícím kódu, že jsou vlastnosti jen pro čtení. Neexistuje žádný způsob, jak aktualizovat objekt, hodnoty lze nastavit pouze při jeho vytvoření.

Je důležité, abyste měli na očích sem, pokud události domény zpracovávány asynchronně, použití fronty jako povinné serializace a deserializace objektů událostí, vlastnosti by mohl být "soukromé sada" místo jen pro čtení, takže bude deserializátor můžete přiřadit hodnoty při vyřazování z fronty. To není problém v mikroslužbě řazení, protože domény události publikování a odběr je implementováno synchronně pomocí MediatR.

### <a name="raise-domain-events"></a>Vyvolávání událostí domény

Další otázkou je postup vyvolat událost domény, tak se dosáhne své obslužné rutině související události. Můžete použít několik přístupů.

Původně navrhl UDI Dahan (například v několika souvisejících příspěvků, jako například [události domény – trvat 2](http://udidahan.com/2008/08/25/domain-events-take-2/)) pomocí statické třídy pro správu a vyvolávání událostí. To může zahrnovat statickou třídu s názvem DomainEvents, který by vyvolat události domény okamžitě, když je volána, pomocí syntaxe jako `DomainEvents.Raise(Event myEvent)`. Blogový příspěvek napsal Jimmy Bogard ([posílení vaší domény: Události domény](https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/)), která doporučuje podobný přístup.

Ale když doménová třída událostí je statická, také odešle do obslužné rutiny okamžitě. To umožňuje testování a ladění obtížnější, protože obslužných rutin událostí pomocí logiky vedlejší účinky jsou spouštěny ihned poté, co se vyvolá událost. Při testování a ladění, chcete zaměřit se na a právě, co se děje v aktuální agregační třídy; nechcete náhle přesměrováni na jiné obslužné rutiny událostí pro vedlejší účinky související s jinými agregace nebo aplikaci logiky. To je důvod, proč se vyvinula další přístupy, jak je vysvětleno v další části.

#### <a name="the-deferred-approach-to-raise-and-dispatch-events"></a>Odložené přístup ke zvýšení a odeslání události

Místo agresivnějším odesláním do obslužné rutiny události domény okamžitě, lepším řešením je přidat do kolekce událostí domény a pak k odeslání události domény *bezprostředně před* nebo *správné*  *Po* potvrzování transakcí (stejně jako u SaveChanges v EF). (Tento přístup se v tomto příspěvku popsal Jimmy Bogard [lepší vzor události domény](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/).)

Rozhodování o tom, pokud budete události odesílat na domény hned před nebo pravou za potvrzování transakcí je důležité, protože určuje, zda bude obsahovat vedlejší účinky v rámci stejné transakce nebo v jiné transakce. V takovém případě budete muset pracovala s konečnou konzistencí napříč více agregací. V tomto tématu jsou popsány v následující části.

Odložené přístup je, jaké aplikaci eShopOnContainers používá. Nejprve přidejte události děje ve vaše entity do kolekce nebo seznamu událostí za entity. Tento seznam by měl být součástí objektu entity, nebo ještě lepší část třídy základní entitu, jak je znázorněno v následujícím příkladu základní třída Entity:

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

Pokud chcete vyvolat událost, stačí přidat jej do kolekce událostí z kódu v jakékoli metody objektu agregace kořenové entity.

Následující kód, součástí [pořadí kořenové agregace v aplikaci eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs), ukazuje příklad:

```csharp
var orderStartedDomainEvent = new OrderStartedDomainEvent(this, //Order object
                                                          cardTypeId, cardNumber,
                                                          cardSecurityNumber,
                                                          cardHolderName,
                                                          cardExpiration);
this.AddDomainEvent(orderStartedDomainEvent);
```

Všimněte si, že pouze jednu metodu AddDomainEvent probíhající činnosti je přidání události do seznamu. Žádná událost je odeslána ještě a žádná obslužná rutina události je vyvolána ještě.

Ve skutečnosti budete chtít později při odeslání události při potvrzení transakce v databázi. Pokud používáte Entity Framework Core, která znamená, že metoda SaveChanges vaše EF DbContext, stejně jako v následujícím kódu:

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

S tímto kódem odeslání události entity na jejich odpovídající událost obslužné rutiny.

Celkový výsledek je, že můžete mít oddělení vyvolání události domény (jednoduchý přidat do seznamu v paměti) od agresivnějším odesláním do obslužné rutiny události. Kromě toho v závislosti na tom, jaký druh dispečer používáte, může odesílat události synchronně nebo asynchronně.

Mějte na paměti zde přehrát transakční začne významné hranice. Pokud jednotka práce a transakce může zahrnovat více než jeden agregace (stejně jako při použití EF Core a relační databáze), to dobře fungovat. Ale pokud transakce nemůžou zahrnovat agregace, jako je například při použití databáze NoSQL, jako jsou služby Azure cosmos DB, je nutné implementovat další kroky k zajištění konzistence. To je další důvod, proč není univerzální; neznalosti trvalosti To závisí na úložný systém, který používáte. 

### <a name="single-transaction-across-aggregates-versus-eventual-consistency-across-aggregates"></a>Jediné transakce napříč agregace oproti konečné konzistence napříč agregace

Na otázku, jestli se má provést jedné transakce napříč agregace oproti spoléhat na konečnou konzistenci napříč těmito agregace je kontroverzním. Mnoho DDD autoři jako Eric Evans a Vaughn Vernon pomocníků pro pravidlo jednu transakci = jedné agregace a proto tvrdí pro konečnou konzistenci napříč agregace. Například ve své knize *Domain-Driven Design*, Eric Evans uvádí, že toto:

> Jakékoli pravidlo, které zahrnuje agregace se očekává se aktuální za všech okolností. Zpracování událostí, dávkové zpracování nebo jiných mechanismů aktualizace může být další závislosti přeložit v určité chvíli. (stránka 128)

Vaughn Vernon říká takto [efektivní návrh agregace. Část II: Provádění agreguje pracovní společně](https://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf):

> Proto pokud spuštění příkazu v jednom agregace instance vyžaduje další obchodní pravidla můžete spustit na jeden nebo více agregace, použijte konečné konzistence \[...\] Existuje praktický způsob, jak v modelu DDD podporu konečné konzistence. Agregační metoda publikuje domény událost, která je v čase se doručí do jednoho nebo více asynchronních předplatitele.

Tato důvody vychází středu podrobných transakce místo transakce zahrnující mnoho agregace nebo entity. Cílem je, že v druhém případě počtu uzamčení databáze bude podstatný rozsáhlé aplikace s požadavky na vysokou škálovatelnost. Středu skutečnost, že vysoce škálovatelných aplikací nemusí mít okamžitý transakční konzistenci mezi více agregace pomáhá s přijetím koncept konečné konzistence. Atomic změny jsou často není potřeba podnikání a je v žádném případě odpovědnost odborníků domény říct, jestli konkrétní operace potřebovat atomické transakce, nebo ne. Pokud je operace vždy nutné jednu atomickou transakci mezi více agregace, můžete pokládat, jestli vaše agregace by měla být větší nebo nebyl správně určen.

Další vývojářům a architektům jako Jimmy Bogard ale pořádku, pokud je pokrývání uzlů jedné transakce napříč několika agregace, ale pouze pokud tyto další agregace souvisejí s vedlejší účinky pro stejný příkaz původní. Například v [lepší vzor události domény](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/), Bogard uvádí, že toto:

> Obvykle chci vedlejší účinky domény události dojde v rámci jedné logické transakce, ale nemusí nutně jít v rámci stejné vyvolání události domény k \[...\] Těsně před plánovaným začátkem potvrzení jsme naše transakce, jsme odeslání náš událostí do jejich odpovídajících obslužné rutiny.

Pokud odeslání události vpravo domény *před* potvrzování původní transakce, je proto vedlejším účinkům tyto události mají být zahrnuty v rámci jedné transakce. Například pokud metoda EF DbContext SaveChanges selže, transakce se vrátit zpět všechny změny, včetně výsledku žádné vedlejší účinek operace implementované obslužné rutiny událostí související domény. Toto je vzhledem k tomu, že obor života DbContext je ve výchozím nastavení definován jako "v oboru." Proto objekt DbContext je sdílen mezi více objektů úložiště instance v rámci stejného oboru nebo grafu objektů. To se shoduje s rozsahem HttpRequest při vývoji aplikace webového rozhraní API nebo MVC.

Oba přístupy (jediné atomické transakce a konečné konzistence) ve skutečnosti může být správné. Tato skutečnost závisí na vaší domény nebo obchodní požadavky a co odborníky na domény zjistíte. Také závisí na způsobu škálovatelné, je třeba služba bude (podrobnější transakce mít menší dopad s ohledem na zámků databáze). A závisí na tom, kolik investice jste natolik, aby ve vašem kódu, protože konečné konzistence vyžaduje složitější kód k detekci případným nekonzistencím napříč agregace a není nutné implementovat vyrovnávací akce. Vezměte v úvahu, že pokud změny potvrdíte do původní agregaci a později, když události se odešlou, pokud dochází k potížím a obslužné rutiny událostí nelze potvrdit jejich vedlejších účinků, budete mít nekonzistence mezi agregace.

Způsob, jak povolit vyrovnávací akce by k uložení událostí domény v tabulkách další databáze, tak můžou být součástí původní transakce. Později může mít dávkové zpracování, která nekonzistence a spouští akce vyrovnávací porovnáním seznam událostí s aktuálním stavem agregací. Náhradní akce, které jsou součástí složité téma, které se vyžadují hlubší analýzy z vaší strany, která zahrnuje diskutovat s obchodnímu uživateli a odborníky na domény.

V každém případě můžete zvolit přístup, které potřebujete. Počáteční odložené přístup, ale – vyvolání události před potvrzením, takže pomocí jedné transakce – je nejjednodušším přístupem při používání EF Core a relační databáze. Je snadněji implementovat a platný v mnoha obchodních případů. Je také použitý v pořadí mikroslužeb v aplikaci eShopOnContainers přístup.

Ale jak je ve skutečnosti odeslání těchto událostí na jejich obslužné rutiny událostí odpovídajících? Co je `_mediator` objektu se zobrazí v předchozím příkladu? Má se techniky a artefakty, které můžete použít k mapování mezi událostmi a jejich obslužné rutiny událostí.

### <a name="the-domain-event-dispatcher-mapping-from-events-to-event-handlers"></a>Dispečer události domény: mapování z událostí k obslužné rutiny událostí

Když budete moct odesílat ani publikovat události, je potřeba nějaký druh artefaktu, která bude publikovat událost, tak, aby každý související obslužnou rutinu můžete získat a zpracovávat vedlejší účinky na základě této události.

Jedním z přístupů je systém reálné zasílání zpráv nebo dokonce sběrnice událostí, případně podle služby Service bus, na rozdíl od události v paměti. První případu skutečném zasílání zpráv by však bylo přehnaně pro zpracování události domény, protože potřebujete jenom pro zpracování těchto událostí v rámci stejného procesu (to znamená, že v rámci stejné vrstvy domény a aplikace).

Dalším způsobem, jak namapovat více obslužných rutin událostí události je pomocí registrace typů v kontejner IoC tak může dynamicky odvodit where k odeslání události. Jinými slovy je potřeba vědět, co obslužné rutiny událostí musel určité události. Obrázek 7 – 16 ukazuje zjednodušený postup pro tento přístup.

![Injektáž závislostí lze použít pro přidružení událostí k obslužné rutiny událostí, které je tento přístup používá MediatR](./media/image17.png)

**Obrázek 7 – 16**. Dispečer události domény pomocí technologie IoC

Můžete vytvářet zajistí funkčnost systému a artefakty k implementaci tohoto přístupu sami. Však můžete také použít dostupných knihoven jako [MediatR](https://github.com/jbogard/MediatR) , který používá váš kontejner IoC pod pokličkou. Můžete proto přímo použít předdefinované rozhraní a metody publikování/odeslání zprostředkovatel objektu.

V kódu, musíte nejprve zaregistrovat typy obslužných rutin událostí ve vašem kontejneru IoC, jak je znázorněno v následujícím příkladu v [aplikaci eShopOnContainers řazení mikroslužeb](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/MediatorModule.cs):

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

Kód nejprve identifikuje sestavení, které obsahuje obslužné rutiny událostí domény vyhledáním sestavení, které obsahuje některý z obslužné rutiny (pomocí typeof(ValidateOrAddBuyerAggregateWhenXxxx), ale může vybrali jakékoli jiné obslužné rutiny události pro nalezení sestavení). Protože všechny obslužné rutiny událostí implementovat rozhraní IAsyncNotificationHandler, kód a hledání jenom pro ty typy a zaregistruje všechny obslužné rutiny událostí.

### <a name="how-to-subscribe-to-domain-events"></a>Postup přihlášení k odběru událostí domény

Při použití MediatR Každá obslužná rutina události musí používat typ události, která je k dispozici pro obecný parametr INotificationHandler rozhraní, jak je vidět v následujícím kódu:

```csharp
public class ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler
  : IAsyncNotificationHandler<OrderStartedDomainEvent>
```

Na základě vztahu mezi událostí a obslužnou rutinu události, která lze považovat za předplatné, artefaktů MediatR zjistit všechny obslužné rutiny události pro každou jednotlivou událost a aktivovat jedna z těchto obslužných rutin událostí.

### <a name="how-to-handle-domain-events"></a>Zpracování události domény

A konečně obslužná rutina události obvykle implementuje aplikace vrstvu kódu, který používá infrastrukturu úložiště získat požadované další agregace a spustit logiku domény vedlejší efekt. Následující [domény kód obslužné rutiny událostí v aplikaci eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/DomainEventHandlers/OrderStartedEvent/ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler.cs), ukazuje příklad implementace.

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

Předchozí kód obslužné rutiny události domény se považuje za vrstvu kódu aplikace vzhledem k tomu používá infrastrukturu úložiště, jak je vysvětleno v další části vrstvy trvalosti infrastruktury. Obslužné rutiny události použít i další komponenty infrastruktury.

#### <a name="domain-events-can-generate-integration-events-to-be-published-outside-of-the-microservice-boundaries"></a>Události domény může generovat události integrace zveřejnit mimo hranic mikroslužby

Nakonec je důležité zmínit, že můžete někdy chtít rozšířit události napříč různými mikroslužbami. Tohoto rozšíření je integrace událostí a může být zveřejněna prostřednictvím sběrnice událostí z libovolné obslužné rutiny události konkrétní doménu.

## <a name="conclusions-on-domain-events"></a>Závěry domény událostí

Jak jsme uvedli, používejte události domény o explicitní implementaci vedlejší účinky změn v rámci vaší domény. Použití terminologie DDD, používejte události domény o explicitní implementaci vedlejší účinky přes jeden nebo více agregací. Kromě toho a pro lepší škálovatelnost a menší dopad na zámků databáze pomocí konečné konzistenci mezi agregací ve stejné doméně.

## <a name="additional-resources"></a>Další zdroje

- **Grega Younga:. Co je událost domény?** \
  <http://codebetter.com/gregyoung/2010/04/11/what-is-a-domain-event/>

- **Jan Stenberg. Události domény a konečné konzistence** \
  <https://www.infoq.com/news/2015/09/domain-events-consistency>

- **Jimmy Bogard. Lepší události modelu domény** \
  <https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/>

- **Vaughn Vernon. Efektivní návrh agregace část II: Provádění agregací spolupracují** \
  [https://dddcommunity.org/wp-content/uploads/files/pdf\_articles/Vernon\_2011\_2.pdf](https://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf)

- **Jimmy Bogard. Posílení vaší domény: Domain Events** \
  <https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/>

- **ADAM Truong. Příklad události modelu domény** \
  <https://www.tonytruong.net/domain-events-pattern-example/>

- **Udi Dahan. Vytvoření plně zapouzdřené doménových modelů** \
  <http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/>

- **Udi Dahan. Události domény – trvat 2** \
  <http://udidahan.com/2008/08/25/domain-events-take-2/>

- **Udi Dahan. Události domény – Salvation** \
  <http://udidahan.com/2009/06/14/domain-events-salvation/>

- **Jan Kronquist. Není publikovat události domény, vraťte je!** \
  <https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/>

- **De la Torre Cesarovi. Domain Events vs. Integrace událostí v architektur mikroslužeb a DDD** \
  <https://blogs.msdn.microsoft.com/cesardelatorre/2017/02/07/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/>

>[!div class="step-by-step"]
>[Předchozí](client-side-validation.md)
>[další](infrastructure-persistence-layer-design.md)
