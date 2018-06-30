---
title: Události domény. návrh a implementaci
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Události domény, návrhu a implementace
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: 44fbe79c9ed7cfd4a79daf6ee9b3d39afd33a910
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106022"
---
# <a name="domain-events-design-and-implementation"></a>Události domény: návrhu a implementace

Explicitní implementace vedlejší účinky změn ve vaší doméně pomocí události domény. V jiná slova a používá terminologie DDD používejte domény události explicitní implementace vedlejší účinky napříč více agregace. Volitelně můžete pro účely lepší škálovatelnosti a menší dopad na uzamčení databáze pomocí konzistence typu případné mezi agregace ve stejné doméně.

## <a name="what-is-a-domain-event"></a>Co je událost domény?

Událost je něco, co došlo v minulosti. Událost domény, logicky, něco, co se stalo v určité doméně, a něco chcete jiných součástí stejné domény (v procesu), aby mít na paměti a potenciálně reagovat na ně.

Důležité výhodou události domény je, že vedlejší účinky po se něco stalo v doméně, může být vyjádřený explicitně místo implicitně. Tyto straně důsledky musí být konzistentní, proto dojít buď všechny operace související s obchodní úlohy, nebo žádná z nich. Kromě toho události domény umožňuje lepší oddělené oblasti zájmu v rámci třídy ve stejné doméně.

Například pokud právě používáte rozhraní Entity Framework a entity nebo i agregace, pokud musí existovat vedlejší účinky provoked případem použití, ty budou prováděny jako implicitní koncept v párované kódu po se něco stalo. Ale pokud se zobrazí pouze tento kód, možná nevíte, pokud tento kód (vedlejším účinkem) je součástí hlavní operaci, nebo pokud se ve skutečnosti je vedlejším účinkem. Na druhé straně pomocí události domény mohou koncept explicitní a součástí všudypřítomný jazyk. Například v aplikaci eShopOnContainers vytváření pořadí není jenom o pořadí; aktualizací nebo vytvoří kupujících agregační na základě původního uživatele, protože uživatel není kupující dokud pořadí na místě. Pokud používáte události domény, můžete explicitně express pravidlo této domény založené na všudypřítomný jazyk zadaný odborníky domény.

Události domény jsou trochu podobné události zasílání zpráv ve stylu s jeden podstatným rozdílem. S skutečné zasílání zpráv služby Řízení front zpráv, zpráv zprostředkovatelé nebo služby service bus pomocí AMPQ se zprávu vždy odesílají asynchronně a předávat v rámci procesy a počítače. To je užitečné pro integraci více ohraničenou kontexty, mikroslužeb nebo i jiné aplikace. S událostmi domény chcete vyvolat událost z operace domény, které jsou aktuálně spuštěné, ale chcete, aby žádné vedlejší účinky v rámci stejné domény.

Události domény a jejich vedlejší efekty (akce aktivuje později spravovaná obslužné rutiny událostí) provedeno téměř okamžitě, obvykle v rámci procesu a v rámci stejné domény. Proto události domény může být synchronní nebo asynchronní. Události integrace, ale musí být vždy asynchronní.

## <a name="domain-events-versus-integration-events"></a>Události domény oproti události integrace

Sémanticky, domény a integrace události jsou samé: oznámení o něco, které právě došlo. Implementace však musí být jiný. Události domény jsou jenom zpráv nabídnutých do dispečeru událostí domény, který by mohl implementovaný jako zprostředkovatel v paměti na základě kontejner IoC nebo jiným způsobem.

Na druhé straně účelem události integrace je potřebný k šíření potvrzené transakce a aktualizace další subsystémy, jestli jsou v jiné mikroslužeb nebo ohraničenou kontextu i externími aplikacemi. Proto má vzniknout jen pokud entita je úspěšně jako trvalé, od v mnoha scénářích Pokud se to nezdaří, celou operaci efektivně nikdy došlo.

Kromě toho a jako uvedených, integrace události musí být založená na asynchronní komunikaci mezi více mikroslužeb (jiných kontextech s ohraničenou) nebo i externími systémy nebo aplikacemi. Proto musí rozhraní sběrnice událostí některé infrastrukturu, která umožňuje mezi proces a distribuovaných komunikace mezi potenciálně vzdálené. Ho může být založen na komerční služby service bus, fronty, sdílenou databázi použít jako poštovní schránku nebo jakékoliv distribuované a v ideálním případě push založené na systému zasílání zpráv.

## <a name="domain-events-as-a-preferred-way-to-trigger-side-effects-across-multiple-aggregates-within-the-same-domain"></a>Události domény jako upřednostňovaný způsob, jak aktivovat vedlejší účinky napříč více agregace ve stejné doméně

Pokud spuštění příkazu vztahující se k jednomu agregační instance vyžaduje další domény pravidla ke spuštění na jeden nebo více dalších agregace, by měl navrhujete a implementujete tyto vedlejší účinky, aby se spouštěly domény událostmi. Jak je uvedené v obrázek 9-14 a jako jeden z nejdůležitějších případy použití, domény událostí se používá k rozšíří změny stavu na více agregace v rámci stejného modelu domény.

![](./media/image15.png)

**Obrázek 9-14**. Události domény chcete zajistit konzistenci mezi několika agregace ve stejné doméně

Na obrázku když uživatel spustí pořadí, aktivuje událost domény OrderStarted vytvoření objektu kupujících v řazení mikroslužbu, založené na původní informace o uživateli z mikroslužbu identity (pomocí informací uvedených v příkazu CreateOrder). Událost domény je generován agregace pořadí při vytvoření na prvním místě.

Alternativně můžete mít kořenu agregační předplatné pro události vyvolané službou členy jeho agregace (podřízených entit). Každá entita podřízené OrderItem pro instanci může vyvolat událost, když cena zboží je vyšší než určitou velikostí, nebo když množství položek produktu je příliš vysoká. Agregační kořenové můžete přijímat tyto události a provádět globální výpočtu nebo agregace.

Je důležité si uvědomit, že tato komunikace na základě událostí není implementována přímo v rámci agregace; je nutné implementovat domény obslužné rutiny. Zpracování událostí domény je aplikace. Vrstva modelu domény měli jenom zaměřit na logiku domény – věcí, které by pochopit odborník z domény, ne aplikace infrastruktury, jako jsou obslužné rutiny a vedlejším účinkem trvalost akce s použitím úložiště. Úroveň vrstvy aplikace je proto, kde byste měli mít spuštění akce při domény událost se vyvolá, obslužné rutiny událostí domény.

Události domény lze také použít k aktivaci libovolného počtu akcí aplikace a co je důležitější, musí být otevřený a odpojeného způsobem zvýšit počet v budoucnu. Například při spuštění pořadí, můžete chtít publikování domény událostí k šíření této informací o jiné agregace nebo i pro vyvolání akce aplikace jako oznámení.

Klíče bod je otevřené počet akce má být proveden při výskytu události domény. Nakonec se zvýší akce a pravidla v doméně a aplikace. Složitost nebo počet vedlejším účinkem akcí, když se stane něco se zvýší, ale pokud se váš kód kombinaci s "spojovací" (který je právě vytváření instancí objektů s new – klíčové slovo v jazyce C\#), pokaždé, když je potřeba přidat novou akci je nutné, aby Původní kód změňte. Výsledkem by mohlo nové chyby, protože se každý nový požadavek by potřebujete změnit původní toku kódu. To má význam proti [otevřete/uzavřeno Princip](https://en.wikipedia.org/wiki/Open/closed_principle) z [plnou](https://en.wikipedia.org/wiki/SOLID_(object-oriented_design)). Ne, pouze to, že, původní třídu, která byla Orchestrace operace by růst a růst, která přejde na [jedné zásadě odpovědnost (SRP)](https://en.wikipedia.org/wiki/Single_responsibility_principle).

Na druhé straně Pokud používáte události domény, můžete vytvořit podrobné a odpojeného implementace oddělováním odpovědnosti použití tohoto přístupu:

1.  Odeslání příkazu (například CreateOrder).
2.  Zobrazí příkaz v obslužná rutina příkazu.
    -   Spusťte jeden agregace transakce.
    -   (Volitelné) Vyvolávání událostí domény pro vedlejší efekty (například OrderStartedDomainEvent).
1.  Zpracování událostí domény (v rámci aktuální proces), které budou spuštěny otevřete počet vedlejší účinky v několika agregace nebo se akce aplikace. Příklad:
    -   Ověřte nebo vytvořte kupujících a způsobu platby.
    -   Vytvoření a odeslání událostí související integrace ke sběrnici událostí k rozšíří stavy na mikroslužeb nebo aktivační událost externí akcí jako odběratel odesílání e-mailu.
    -   Zpracujte jiné vedlejší účinky.

Jak znázorňuje obrázek 9 – 15, od stejné domény události, může zpracovávat několik akcí souvisejících s jiné agregace v doméně nebo akce další aplikace, které je potřeba provést přes připojení s integrace události a události sběrnice mikroslužeb.

![](./media/image16.png)

**Obrázek 9 až 15**. Zpracování více akcí v každé doméně

Obslužné rutiny událostí jsou obvykle v aplikační vrstvě, protože objektů infrastruktury, jako jsou úložiště nebo rozhraní API aplikace bude používat mikroslužbu chování. V tomto smysl jsou podobné obslužné rutiny příkazů, obslužné rutiny událostí, tak jak jsou součástí aplikační vrstvu. Důležitý rozdíl je, že příkaz má být zpracován pouze jednou. Událost domény může být zpracována nula nebo *n* krát, protože ho lze přijímat pomocí několika příjemci nebo obslužných rutin událostí pomocí k jinému účelu pro každou obslužnou rutinu.

Možnost Otevřít počet obslužných rutin na událost domény umožňuje přidat mnoho další pravidla domény bez dopadu na váš aktuální kód. Implementace následující obchodní pravidlo, které se má provést vpravo po konkrétní události, například může být stejně snadná jako přidávání několik obslužné rutiny událostí (nebo i pouze jeden):

Pokud celková velikost koupili zákazníka v úložišti, napříč jakékoli číslo objednávky, překročí $6000, platí pro všechny nové pořadí 10 % vypnout slevu a upozorňovat zákazník s e-mailu o tomto slevy pro budoucí objednávky.

## <a name="implementing-domain-events"></a>Implementace události domény

V jazyce C# domény událostí je jednoduše data za ruku struktura nebo třídy, jako je DTO, všechny informace související s co se právě stalo v doméně, jak je znázorněno v následujícím příkladu:

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

Toto je v podstatě třídu, která obsahuje všechna data související s OrderStarted události.

Z hlediska všudypřítomný jazyka domény vzhledem k tomu, že událost je něco, co se stalo v minulosti, název třídy události by měl být reprezentován jako minulost operace, jako je OrderStartedDomainEvent nebo OrderShippedDomainEvent. To je, jak je implementovaná událost domény v řazení mikroslužbu v eShopOnContainers.

Jak již bylo uvedeno dříve, důležitou vlastností událostí je, že vzhledem k tomu, že událost je něco, co se stalo v minulosti, neměli měnit. Proto musí být třídu neměnné. Zobrazí se v předchozí kód, který vlastnosti jsou jen pro čtení z mimo objekt. Jediný způsob, jak aktualizovat objekt je pomocí konstruktoru, při vytváření objektu události.

### <a name="raising-domain-events"></a>Vyvolání událostí domény

Další otázka se vyvolat událost domény, takže se dosáhne jeho obslužné rutiny událostí související postupy. Můžete použít několik přístupů.

Původně navrhované UDI Dahan (například v několika související s příspěvky, jako například [události domény – trvat 2](http://udidahan.com/2008/08/25/domain-events-take-2/)) pomocí statická třída pro správu a vyvolávání událostí. To může zahrnovat statické třídy s názvem DomainEvents, který by vyvolávání událostí domény okamžitě, když je volána, pomocí syntaxe jako DomainEvents.Raise (MyEvent má mít událostí). Jimmy Bogard napsali blogový příspěvek ([posílení vaší domény: domény události](https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/)), doporučuje podobný postup.

Ale když statické třídy události domény se také odešle do obslužné rutiny okamžitě. Díky testování a ladění obtížnější, protože obslužných rutin událostí pomocí logiky vedlejší účinky jsou vykonány ihned po vyvolání události. Když jsou testování a ladění, chcete zaměřit na to, a stejně, co se děje v aktuální agregační třídy; nechcete náhle přesměrovat na ostatních obslužných rutin událostí pro vedlejší účinky související do jiných agregací nebo aplikační logiku. Z tohoto důvodu vyvinuly jiné postupy, jak je popsáno v následující části.

#### <a name="the-deferred-approach-for-raising-and-dispatching-events"></a>Odložené přístup pro vyvolání a odeslání události

Místo odeslání na obslužnou rutinu události domény okamžitě, je lepší způsob přidání události domény do kolekce a potom k odesílání událostí tyto domény *bezprostředně před* nebo *správné*  *Po* potvrzení transakce (stejně jako u SaveChanges v EF). (Tento přístup byl Jimmy Bogard popsaného v tomto blogu [lepší vzor události domény](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/).)

Při rozhodování o tom, pokud je odeslat události domény hned před nebo správné za potvrzení transakce je důležité, protože určuje, zda bude obsahovat vedlejší účinky v rámci stejné transakci nebo jinou transakcí. V takovém případě budete muset řešit případné konzistence napříč více agregace. Toto téma je popsané v další části.

Odložené přístup je, jaké eShopOnContainers používá. Nejprve přidejte události děje ve vašem entity do kolekce nebo seznamu událostí za entity. Tento seznam musí být součástí objektu entity, nebo i lépe součástí třídy základní entitu, jak je znázorněno v následujícím příkladu základní třídy Entity:

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
        if (_domainEvents is null) return;
        _domainEvents.Remove(eventItem);
    }
    // ...
}
```

Když chcete vyvolat událost, stačí ho přidáte do kolekce událostí z kódu v jakékoli metody objektu entity agregace root.

Následující kód, součástí [pořadí agregace root na eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs), ukazuje příklad:

```csharp
var orderStartedDomainEvent = new OrderStartedDomainEvent(this, //Order object
                                                          cardTypeId, cardNumber,
                                                          cardSecurityNumber,
                                                          cardHolderName,
                                                          cardExpiration);
this.AddDomainEvent(orderStartedDomainEvent);
```

Všimněte si, že je jediné, co dělají metodu AddDomainEvent přidání události do seznamu. Žádná událost je odeslána ještě a ještě volána žádná obslužná rutina události.

Chcete skutečně později na odeslání události při potvrzení transakce do databáze. Pokud používáte Entity Framework Core, znamená to v metodě SaveChanges vaší EF DbContext, jako v následujícím kódu:

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
        // event handlers) performed through the DbContext will be commited
        var result = await base.SaveChangesAsync();
    }
}
```

S tímto kódem odeslání události entity k svým obslužným příslušné události.

Celkové výsledkem je, že budete mít odpojené vyvolání události domény (jednoduchou přidat do seznamu v paměti) od odeslání do obslužné rutiny události. Kromě toho v závislosti na tom, jaký druh dispečera používáte, může odeslat události synchronně nebo asynchronně.

Mějte na paměti zde přehrání transakční hranice začalo významné. Pokud je vaše jednotka práce a transakce může mít rozsah více než jeden agregace (stejně jako při používání jádra EF a relační databáze), to může fungovat správně. Ale pokud transakce nelze span agregace, jako je například při použití databáze NoSQL, jako je Azure DocumentDB, je nutné implementovat další kroky k zajištění konzistence. To je další důvod, proč trvalost které není universal; To závisí na systému úložiště, které používáte.

### <a name="single-transaction-across-aggregates-versus-eventual-consistency-across-aggregates"></a>Jediné transakce napříč agregace versus konzistence typu případné napříč agregace

Dotaz, zda provést jediné transakce napříč agregace versus spoléhat na konzistence typu případné mezi tyto agregace je sporná. Mnoho DDD autoři jako zařízení Evans Erica a Vaughn Vernon doporučují pravidlo této jednu transakci = jeden agregace a proto uvádějí pro konzistence typu případné napříč agregace. Například v jeho kniha *Domain-Driven návrhu*, zařízení Erica Evans uvádí toto:

Jakékoli pravidlo, které zahrnuje agregace nebude možné očekává aktuální za všech okolností. Prostřednictvím zpracování událostí, dávkové zpracování nebo jiných mechanismů aktualizace může být další závislosti vyřešen v určité chvíli. (stránka 128)

Vaughn Vernon uvádí následující [efektivní návrh agregace. Část II: Provádění agreguje pracovní společně](https://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf):

Proto pokud spouštění příkazu na jednom agregační instance vyžaduje, že další obchodní pravidla spustit na jeden nebo více agregace, použijte konzistence typu případné \[...\] Je praktický způsob, jak podporovat konzistence typu případné ve DDD model. Agregační metoda publikuje domény událost, která je v čase se doručí na jeden nebo více asynchronní odběratele.

Tato odůvodnění je založena na přijetí podrobných transakce místo transakce mnoho agregace nebo entity. Cílem je, že v druhém případě počtu uzamčení databáze bude výrazně v aplikace ve velkém měřítku s vysokou škálovatelnost požadavky. Přijetí skutečnost, že vysoce škálovatelné aplikace potřebují nemá rychlých transakční konzistence mezi více agregace pomáhá s přijetím koncept konzistence typu případné. Atomic firmy často není potřebné změny, a je v žádném případě odpovědnost domény odborníků. Tím vyjádříte, jestli konkrétní operace musí jednotlivé transakce, nebo ne. Pokud operace vždy potřebuje transakcích mezi více agregace, může požádat, jestli vaše agregace musí být větší nebo nebyl navržen správně.

Ostatní vývojáři a architektům jako Jimmy Bogard jsou však nevadí pokrývání uzlů jediné transakce napříč několika agregace – ale jenom, když jsou tyto další agregace relaci k vedlejší účinky pro stejný původní příkaz. Například v [lepší vzor události domény](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/), Bogard uvádí toto:

Obvykle chci vedlejší účinky domény události dochází v rámci stejné logické transakci, ale nemusí nutně jít ve stejném oboru z vyvolá událost domény \[...\] Těsně před jsme potvrzení naše transakce, jsme dispatch naše události na jejich odpovídající obslužné rutiny.

Pokud dispatch právo události domény *před* potvrzování původní transakce, je to proto, chcete-li vedlejší účinky těchto událostí, které mají být zahrnuty ve stejné transakci. Například pokud metoda EF DbContext SaveChanges selže, transakce se vrátit zpět všechny změny, včetně výsledek žádné vedlejším účinkem operace implementované obslužné rutiny událostí související domény. To je protože oboru životnosti DbContext je ve výchozím nastavení definovaný jako "vymezen." Proto je objekt DbContext sdílet mezi více objektů úložiště vytváření instancí v rámci stejného oboru nebo grafu objektu. To se shoduje s oboru požadavku HTTP při vývoji aplikace webového rozhraní API nebo MVC.

Ve skutečnosti může být správné obou přístupů (jedné atomic transakce a konzistence typu případné). Ve skutečnosti závisí na vaší domény nebo organizační požadavky a co se odborníka domény zjistíte. Také závisí na tom, jak škálovatelné musí až bude služba (podrobnější transakce mají menší dopad s ohledem na uzamčení databáze). A závisí na tom, kolik investice jste ochotni proveďte v kódu, protože konzistence typu případné vyžaduje složitější kód zjistit možné nekonzistence mezi agregace a není nutné k implementaci vyrovnávací akce. Vezměte v úvahu, že pokud provedete změny původní agregace a později, když jsou události distribuovanou, nastane problém a obslužné rutiny událostí nelze potvrdit jejich vedlejší účinky, budete mít nekonzistence mezi agregace.

Způsob, jak povolit vyrovnávací akce by k uložení událostí domény v tabulkách další databáze, aby mohly být součástí původní transakce. Později může mít batch proces, který zjistí nekonzistence a spustí vyrovnávací akce tak, že porovnáte seznam událostí s aktuálním stavem agregací. Vyrovnávací akce, které jsou součástí komplexní téma, které bude vyžadovat hloubkovou analýzu z vaší strany, včetně diskuse s business uživatelů a domény odborníky.

V každém případě můžete přístupů, které potřebujete. Počáteční odložení přístup, ale – vyvolání události před potvrzením, takže můžete použít jen jednu transakci – je nejjednodušším přístupem při použití EF jádra a relační databáze. Je usnadnil a v mnoha případech firmy. Je také metoda používaná v řazení mikroslužbu v eShopOnContainers.

Ale jak je ve skutečnosti odeslání události, k jejich obslužné rutiny událostí odpovídajících? Co je \_zprostředkovatel objekt, který se zobrazí v předchozím příkladu? Který má dělat s technik a artefaktů, které můžete použít pro mapování mezi událostí a jejich obslužných rutin.

### <a name="the-domain-event-dispatcher-mapping-from-events-to-event-handlers"></a>Dispečer událostí domény: mapování z událostí na obslužné rutiny událostí

Jakmile budete moct odeslat nebo publikovat události, je nutné nějaký druh artefaktů, která bude publikovat události, tak, aby každý související rutiny můžete ho získat a zpracovat vedlejší účinky na základě této události.

Jeden z přístupů je skutečně zasílání zpráv systému nebo i událostí sběrnici, případně založená na služby service bus a události v paměti. Pro první případ skutečných zasílání zpráv by však bylo přehnaně pro zpracování události domény, protože stačí ke zpracování těchto událostí v rámci stejného procesu (to znamená, v rámci stejné vrstvě domény a aplikace).

Dalším způsobem se mapují události do více obslužných rutin událostí je prostřednictvím registrace typy v kontejner IoC, takže můžete dynamicky odvození kde odeslání události. Jinými slovy budete muset vědět, jaké obslužné rutiny událostí je potřeba získat konkrétní události. Obrázek 9 až 16 ukazuje zjednodušený přístup k této.

![](./media/image17.png)

**Obrázek 9 až 16**. Dispečer událostí domény pomocí technologie IoC

Můžete vytvořit všechny vložení a artefaktů k implementaci tohoto přístupu podle sami. Však můžete použít také k dispozici knihovny jako [MediatR](https://github.com/jbogard/MediatR), který pod pozadí používá vaše kontejner IoC. Proto přímo můžete vytvořit předdefinované rozhraní a metody publikování nebo odeslání objekt zprostředkovatel.

V kódu, je nutné nejprve zaregistrovat typy obslužných rutin událostí v vaší kontejner IoC, jak je znázorněno v následujícím příkladu v [eShopOnContainers řazení mikroslužbu](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/MediatorModule.cs):

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

Kód nejprve identifikuje sestavení, které obsahuje obslužné rutiny událostí domény tím, že je sestavení, které obsahuje všechny obslužné rutiny (pomocí typeof(ValidateOrAddBuyerAggregateWhenXxxx), ale by vybrány žádné jiné obslužné rutiny události k nalezení sestavení). Vzhledem k tomu, že všechny obslužné rutiny událostí implementovat rozhraní IAsyncNotificationHandler, kód pak vyhledá jenom ty typy a zaregistruje všechny obslužné rutiny událostí.

### <a name="how-to-subscribe-to-domain-events"></a>Tom, jak se přihlásit k odběru událostí domény

Při použití MediatR každý obslužné rutiny události musí používat typ události, který je k dispozici na obecný parametr INotificationHandler rozhraní, jak můžete vidět v následujícím kódu:

```csharp
public class ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler
  : IAsyncNotificationHandler<OrderStartedDomainEvent>
```

Na základě vztahu mezi událostí a obslužná rutina události, která lze považovat za předplatné, artefaktů MediatR zjistit všechny obslužné rutiny události pro všechny události a aktivuje každý z těchto obslužných rutin událostí.

### <a name="how-to-handle-domain-events"></a>Postupy: zpracování události domény

Nakonec obslužné rutiny události obvykle implementuje aplikační vrstvy kód, který používá infrastrukturu úložiště získat požadovaná další agregace a provést logiku domény vedlejším účinkem. Následující [domény kód obslužné rutiny událostí v eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/DomainEventHandlers/OrderStartedEvent/ValidateOrAddBuyerAggregateWhenOrderStartedDomainEventHandler.cs), ukazuje příklad implementace.

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

Předchozí kód obslužné rutiny událostí domény považuje za vrstvy kódu aplikace protože ji používá infrastrukturu úložiště, jak je vysvětleno v další části na vrstvě infrastruktury trvalost. Obslužné rutiny událostí může také použít další součásti infrastruktury.

#### <a name="domain-events-can-generate-integration-events-to-be-published-outside-of-the-microservice-boundaries"></a>Události domény může generovat události integrace publikována mimo hranice mikroslužbu

Nakonec je důležité zmínili, může někdy chcete rozšíří události na více mikroslužeb. Který považuje za událost integrace a může být publikován přes sběrnici událostí z obslužné rutiny události žádné konkrétní doméně.

## <a name="conclusions-on-domain-events"></a>Závěrů na události domény

Jak jsme uvedli, pomocí události domény explicitní implementace vedlejší účinky změn ve vaší doméně. Terminologie DDD, použití události domény explicitně implementovat vedlejší účinky přes jeden nebo více agregace. Kromě toho a lepší škálovatelnost a menší dopad na uzamčení databáze použijte konzistence typu případné mezi agregace ve stejné doméně.

## <a name="additional-resources"></a>Další zdroje

-   **Gregu Young. Co je událost domény?**
    [*http://codebetter.com/gregyoung/2010/04/11/what-is-a-domain-event/*](http://codebetter.com/gregyoung/2010/04/11/what-is-a-domain-event/)

-   **Jan Stenberg. Události domény a konzistence typu případné**
    [*https://www.infoq.com/news/2015/09/domain-events-consistency*](https://www.infoq.com/news/2015/09/domain-events-consistency)

-   **Jimmy Bogard. Lepší vzor události domény**
    [*https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/*](https://lostechies.com/jimmybogard/2014/05/13/a-better-domain-events-pattern/)

-   **Vaughn Vernon. Efektivní návrh agregace část II: Provádění agregací pracovní společně**
    [*http://dddcommunity.org/wp-content/uploads/files/pdf\_articles/Vernon\_2011\_2.pdf*](https://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf)

-   **Jimmy Bogard. Posílení vaší domény: domény události**
    *<https://lostechies.com/jimmybogard/2010/04/08/strengthening-your-domain-domain-events/> *

-   **ADAM Truong. Příklad vzoru události domény**
    [*https://www.tonytruong.net/domain-events-pattern-example/*](https://www.tonytruong.net/domain-events-pattern-example/)

-   **Udi Dahan. Postup vytvoření plně zapouzdřené domény modely**
    [*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)

-   **Udi Dahan. Události domény – trvat 2**
    [*http://udidahan.com/2008/08/25/domain-events-take-2/*](http://udidahan.com/2008/08/25/domain-events-take-2/%20)

-   **Udi Dahan. Události domény – Salvation**
    [*http://udidahan.com/2009/06/14/domain-events-salvation/*](http://udidahan.com/2009/06/14/domain-events-salvation/)

-   **Jan Kronquist. Nemáte publikovat události domény, obnoví v nich!**
    [*https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/*](https://blog.jayway.com/2013/06/20/dont-publish-domain-events-return-them/)

-   **Cesaru členka Torre. Domény události vs. Integrace události v případě architektur se DDD a mikroslužeb**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/02/07/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/02/07/domain-events-vs-integration-events-in-domain-driven-design-and-microservices-architectures/)


>[!div class="step-by-step"]
[Předchozí](client-side-validation.md)
[další](infrastructure-persistence-layer-design.md)
