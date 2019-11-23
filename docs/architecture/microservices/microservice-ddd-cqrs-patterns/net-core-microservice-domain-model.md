---
title: Implementace doménového modelu mikroslužby pomocí .NET Core
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Získejte informace o implementaci doménového modelu orientovaného na DDD.
ms.date: 10/08/2018
ms.openlocfilehash: bff9cbda08e519038056268151a1721427f0ac01
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73972048"
---
# <a name="implement-a-microservice-domain-model-with-net-core"></a>Implementace modelu domény mikroslužeb pomocí .NET Core

V předchozí části byly vysvětleny základní principy návrhu a vzory pro návrh doménového modelu. Nyní je čas prozkoumat možné způsoby implementace doménového modelu pomocí .NET Core (prostý kód v jazyce C\#) a EF Core. Všimněte si, že váš doménový model se skládá jednoduše z vašeho kódu. Bude mít pouze požadavky na model EF Core, ale ne skutečné závislosti na EF. Neměli byste mít pevné závislosti nebo odkazy na EF Core nebo jiné ORM ve vašem doménovém modelu.

## <a name="domain-model-structure-in-a-custom-net-standard-library"></a>Struktura doménového modelu ve vlastní knihovně .NET Standard

Organizace, která se používá pro referenční aplikaci eShopOnContainers, ukazuje model DDD pro aplikaci. Může se stát, že jiná organizace bude jasně informovat o tom, jaké možnosti návrhu aplikace udělaly. Jak vidíte na obrázku 7-10, v modelu domény řazení existují dvě agregace, pořadí agregace a agregace nákupčího. Každá agregace je skupina doménových entit a hodnotových objektů, i když můžete mít agregaci tvořenou jedinou doménovou entitou (agregovanou kořenovou nebo kořenovou entitou).

:::image type="complex" source="./media/net-core-microservice-domain-model/ordering-microservice-container.png" alt-text="Snímek projektu objednávky. Domain v Průzkumník řešení.":::
Průzkumník řešení zobrazení pro projekt objednávání. Domain, ve kterém je zobrazená složka AggregatesModel obsahující složky BuyerAggregate a OrderAggregate, každou z nich obsahující třídy entit, hodnotové soubory a tak dále.
:::image-end:::

**Obrázek 7-10**. Struktura doménového modelu pro řazení mikroslužby v eShopOnContainers

Vrstva doménového modelu navíc zahrnuje kontrakty úložiště (rozhraní), které jsou požadavky na infrastrukturu vašeho doménového modelu. Jinými slovy, tato rozhraní vyjadřují úložiště a metody, které vrstva infrastruktury musí implementovat. Je velmi důležité, aby se implementace úložišť na úrovni doménového modelu, v knihovně vrstev infrastruktury, nastavila mimo vrstvu doménového modelu, takže vrstva modelu domény není "kontaminována" rozhraním API nebo třídami z technologií infrastruktury, jako je Entity Framework.

Můžete také zobrazit složku [SeedWork](https://martinfowler.com/bliki/Seedwork.html) s vlastními základními třídami, které můžete použít jako základ pro vaše doménové entity a objekty hodnot, takže nemáte redundantní kód ve třídě objektu v každé doméně.

## <a name="structure-aggregates-in-a-custom-net-standard-library"></a>Agregace struktur ve vlastní knihovně .NET Standard

Agregace odkazuje na cluster objektů domény seskupených dohromady, aby odpovídaly konzistenci transakcí. Těmito objekty můžou být instance entit (jedna z nich je agregovaná kořenová nebo kořenová entita) a všechny další objekty hodnot.

Transakční konzistence znamená, že agregace je zaručená tak, aby byla na konci obchodní akce konzistentní a aktuální. Například pořadí agregace z eShopOnContainersho doménového modelu pro řazení mikroslužeb se skládá jak je znázorněno na obrázku 7-11.

:::image type="complex" source="./media/net-core-microservice-domain-model/vs-solution-explorer-order-aggregate.png" alt-text="Snímek obrazovky se složkou OrderAggregate a jejími třídami":::
Podrobné zobrazení složky OrderAggregate: Address.cs je objekt hodnoty, IOrderRepository je rozhraní úložiště, Order.cs je agregovaným kořenem, OrderItem.cs je podřízenou entitou a OrderStatus.cs je třída výčtu.
:::image-end:::

**Obrázek 7-11**. Pořadí agregace v řešení Visual Studio

Pokud otevřete kterýkoli ze souborů v agregační složce, můžete zjistit, jak je označen jako vlastní základní třída nebo rozhraní, jako je objekt entity nebo hodnota, jak je implementováno ve složce [SeedWork](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork) .

## <a name="implement-domain-entities-as-poco-classes"></a>Implementace doménových entit jako tříd POCO

Model domény v rozhraní .NET implementujete tak, že vytvoříte třídy POCO, které implementují vaše doménové entity. V následujícím příkladu je třída Order definovaná jako entita a také jako agregovaný kořen. Vzhledem k tomu, že třída Order je odvozena od základní třídy entity, může znovu použít společný kód související s entitami. Pamatujte, že tyto základní třídy a rozhraní jsou definovány v projektu modelu domény, takže se jedná o váš kód, nikoli kód infrastruktury z ORM jako EF.

```csharp
// COMPATIBLE WITH ENTITY FRAMEWORK CORE 2.0
// Entity is a custom base class with the ID
public class Order : Entity, IAggregateRoot
{
    private DateTime _orderDate;
    public Address Address { get; private set; }
    private int? _buyerId;

    public OrderStatus OrderStatus { get; private set; }
    private int _orderStatusId;

    private string _description;
    private int? _paymentMethodId;

    private readonly List<OrderItem> _orderItems;
    public IReadOnlyCollection<OrderItem> OrderItems => _orderItems;

    public Order(string userId, Address address, int cardTypeId, string cardNumber, string cardSecurityNumber,
            string cardHolderName, DateTime cardExpiration, int? buyerId = null, int? paymentMethodId = null)
    {
        _orderItems = new List<OrderItem>();
        _buyerId = buyerId;
        _paymentMethodId = paymentMethodId;
        _orderStatusId = OrderStatus.Submitted.Id;
        _orderDate = DateTime.UtcNow;
        Address = address;

        // ...Additional code ...
    }

    public void AddOrderItem(int productId, string productName,
                            decimal unitPrice, decimal discount,
                            string pictureUrl, int units = 1)
    {
        //...
        // Domain rules/logic for adding the OrderItem to the order
        // ...

        var orderItem = new OrderItem(productId, productName, unitPrice, discount, pictureUrl, units);

        _orderItems.Add(orderItem);

    }
    // ...
    // Additional methods with domain rules/logic related to the Order aggregate
    // ...
}
```

Je důležité si uvědomit, že se jedná o entitu domény implementovanou jako třídu POCO. Nemá žádnou přímou závislost na Entity Framework Core ani žádné jiné architektury infrastruktury. Tato implementace je tak, jak by měla být v DDD, jenom C\# kód implementující doménový model.

Kromě toho třída je upravena s rozhraním s názvem IAggregateRoot. Toto rozhraní je prázdné rozhraní, někdy označované jako *rozhraní značky*, které se používá pouze k označení toho, že tato třída entity je také agregovaným kořenem.

Rozhraní značek se někdy považuje za anti-Pattern; je však také čistý způsob, jak označit třídu, zejména v případě, že se toto rozhraní může vyvíjejí. Atribut může být jinou volbou pro značku, ale je rychlejší zobrazit základní třídu (entity) vedle rozhraní IAggregate místo vložení značky agregovaného atributu nad třídu. V každém případě je to v souvislosti s preferencemi.

Výsledkem agregovaného kořene znamená, že většina kódu souvisejícího s konzistencí a obchodními pravidly entit agregace by měla být implementována jako metody v pořadí agregované kořenové třídy (například AddOrderItem při přidávání objektu OrderItem do agregace). . Nemusíte vytvářet ani aktualizovat OrderItems objekty nezávisle nebo přímo; Třída AggregateRoot musí zachovat kontrolu a konzistenci jakékoli operace aktualizace s jejími podřízenými entitami.

## <a name="encapsulate-data-in-the-domain-entities"></a>Zapouzdřit data v doménových entitách

Běžným problémem v modelech entit je, že zveřejňují vlastnosti navigace kolekce jako veřejně přístupné typy seznamů. To umožňuje vývojářům spolupracovníkům manipulovat s obsahem těchto typů kolekcí, což může obejít důležité obchodní pravidla související s kolekcí, což může opustit objekt v neplatném stavu. Řešením je vystavit přístup jen pro čtení k souvisejícím kolekcím a explicitně poskytnout metody, které definují způsoby, kterými je můžou klienti manipulovat.

V předchozím kódu si všimněte, že mnoho atributů je pouze pro čtení nebo je soukromé a lze je aktualizovat pouze metodami třídy, takže jakákoli aktualizace bere v úvahu invariantní v podnikové doméně a logiku zadanou v rámci metod třídy.

Například následující vzory DDD **byste neměli provádět**  z jakékoli metody obslužné rutiny příkazu nebo třídy vrstvy aplikace (ve skutečnosti by to nemělo být možné):

```csharp
// WRONG ACCORDING TO DDD PATTERNS – CODE AT THE APPLICATION LAYER OR
// COMMAND HANDLERS
// Code in command handler methods or Web API controllers
//... (WRONG) Some code with business logic out of the domain classes ...
OrderItem myNewOrderItem = new OrderItem(orderId, productId, productName,
    pictureUrl, unitPrice, discount, units);

//... (WRONG) Accessing the OrderItems collection directly from the application layer // or command handlers
myOrder.OrderItems.Add(myNewOrderItem);
//...
```

V tomto případě je metoda Add čistě operací pro přidání dat s přímým přístupem ke kolekci OrderItems. Proto se většina doménové logiky, pravidel nebo ověření souvisejících s touto operací s podřízenými entitami rozprostře napříč aplikační vrstvou (obslužné rutiny příkazů a řadiče webového rozhraní API).

Pokud překročíte agregovanou kořenovou hodnotu, nemůže agregovaný kořen zaručit jeho invariantní, jeho platnost nebo konzistenci. Nakonec budete mít Spaghetti kód nebo transakční kód skriptu.

Aby bylo možné sledovat vzory DDD, nesmí entity mít veřejné metody setter v žádné vlastnosti entity. Změny v entitě by měly být ovládány explicitními metodami s explicitním všudypřítomným jazykem o změně, kterou provádějí v entitě.

Kolekce v rámci entity (jako například položky objednávky) by měly být také vlastnosti jen pro čtení (metoda AsReadOnly je vysvětlena později). Měli byste být schopni ho aktualizovat pouze v rámci metod agregace kořenové třídy nebo z metod podřízené entity.

Jak vidíte v kódu pro kořen pořadí agregace, všechny metody nastavení by měly být privátní nebo alespoň jen pro čtení, aby bylo možné všechny operace s daty entity nebo jejími podřízenými entitami probíhat prostřednictvím metod ve třídě entity. Tím se udržuje konzistence řízeným a objektově orientovaným způsobem namísto implementace transakčního kódu skriptu.

Následující fragment kódu ukazuje správný způsob, jak kódovat úlohu přidání objektu OrderItem do agregace pořadí.

```csharp
// RIGHT ACCORDING TO DDD--CODE AT THE APPLICATION LAYER OR COMMAND HANDLERS
// The code in command handlers or WebAPI controllers, related only to application stuff
// There is NO code here related to OrderItem object’s business logic
myOrder.AddOrderItem(productId, productName, pictureUrl, unitPrice, discount, units);

// The code related to OrderItem params validations or domain rules should
// be WITHIN the AddOrderItem method.

//...
```

V tomto fragmentu kódu je většina ověření nebo logiky související s vytvořením objektu OrderItem pod ovládacím prvkem pořadí agregovaného kořene – v metodě AddOrderItem – obzvláště ověření a logika související s jinými prvky v agregaci. Například můžete získat stejnou položku produktu jako výsledek více volání AddOrderItem. V této metodě můžete prozkoumávat položky produktu a konsolidovat stejné položky produktu do jednoho OrderItem objektu s několika jednotkami. Pokud navíc existují různé částky slev, ale ID produktu je stejné, pravděpodobně použijete vyšší slevu. Tento princip platí pro jakoukoliv jinou logiku domény pro objekt OrderItem.

Kromě toho bude také kontrolována a provedena nová operace OrderItem (parami) metodou AddOrderItem z kořenového adresáře Order Aggregate. Proto většina logiky nebo ověření souvisejících s touto operací (zejména cokoli, co se týká konzistence mezi ostatními podřízenými entitami) bude na jednom místě v rámci agregovaného kořene. To je konečný účel agregovaného kořenového vzoru.

Pokud používáte Entity Framework Core 1,1 nebo novější, může být vhodnější vyjádřit entitu DDD, protože umožňuje [mapování na pole](https://docs.microsoft.com/ef/core/modeling/backing-field) kromě vlastností. To je užitečné při ochraně kolekcí podřízených entit nebo objektů hodnot. S tímto vylepšením můžete použít jednoduchá soukromá pole namísto vlastností a můžete implementovat jakoukoli aktualizaci kolekce polí ve veřejných metodách a poskytnout přístup jen pro čtení prostřednictvím metody AsReadOnly.

V DDD chcete entitu aktualizovat pouze prostřednictvím metod v entitě (nebo konstruktoru), aby bylo možné řídit jakékoli invariantní a konzistenci dat, takže vlastnosti jsou definovány pouze pomocí přístupového objektu Get. Vlastnosti jsou zálohovány soukromými poli. K soukromým členům lze přistupovat pouze v rámci třídy. Existuje však jedna výjimka: EF Core musí nastavit i tato pole (takže může vrátit objekt se správnými hodnotami).

### <a name="map-properties-with-only-get-accessors-to-the-fields-in-the-database-table"></a>Mapovat vlastnosti pouze přistupující objekty get k polím v tabulce databáze

Mapování vlastností na sloupce tabulky databáze není zodpovědností domény, ale součástí infrastruktury a vrstvy trvalosti. Zde uvádíme, abychom si vědomi nových funkcí v EF Core 1,1 nebo novějších, které souvisejí s tím, jak můžete modelovat entity. Další podrobnosti k tomuto tématu jsou vysvětleny v části infrastruktura a trvalost.

Pokud používáte EF Core 1,0 nebo novější, v rámci DbContext potřebujete namapovat vlastnosti, které jsou definované pouze pomocí mechanismů getter, na skutečná pole v tabulce databáze. To se provádí pomocí metody HasField třídy PropertyBuilder.

### <a name="map-fields-without-properties"></a>Mapování polí bez vlastností

S funkcí v EF Core 1,1 nebo novějším pro mapování sloupců na pole je také možné nepoužívat vlastnosti. Místo toho můžete mapovat sloupce z tabulky na pole. Běžným případem použití pro toto je soukromá pole pro vnitřní stav, ke kterému nemusíte přicházet z oblasti mimo entitu.

Například v předchozím příkladu kódu OrderAggregate je k dispozici několik privátních polí, například pole `_paymentMethodId`, které nemá žádnou související vlastnost pro metodu setter nebo getter. Toto pole je také možné vypočítat v obchodní logice objednávky a použít je v metodách objednávky, ale je potřeba je zachovat i v databázi. Takže v EF Core (od verze 1.1) existuje způsob, jak namapovat pole bez související vlastnosti na sloupec v databázi. To je také vysvětleno v části [vrstva infrastruktury](ddd-oriented-microservice.md#the-infrastructure-layer) tohoto průvodce.

### <a name="additional-resources"></a>Další materiály a zdroje informací

- **Vaughn Vernon. Modelování agreguje pomocí DDD a Entity Framework.** Všimněte si, že to *není* Entity Framework Core. \
  <https://kalele.io/blog-posts/modeling-aggregates-with-ddd-and-entity-framework/>

- **Julie Lerman. Datové body – kódování pro návrh založený na doméně: Tipy pro vývojáři, která se zaměřuje na data** \
  <https://docs.microsoft.com/archive/msdn-magazine/2013/august/data-points-coding-for-domain-driven-design-tips-for-data-focused-devs>

- **UDI Dahan. Vytvoření plně zapouzdřených doménových modelů** \
  <http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/>

> [!div class="step-by-step"]
> [Předchozí](microservice-domain-model.md)
> [Další](seedwork-domain-model-base-classes-interfaces.md)
