---
title: Implementace doménového modelu mikroslužby pomocí .NET Core
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Získejte podrobnosti implementace modelu domény orientovaného na DDD.
ms.date: 10/08/2018
ms.openlocfilehash: bff9cbda08e519038056268151a1721427f0ac01
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73972048"
---
# <a name="implement-a-microservice-domain-model-with-net-core"></a>Implementace modelu domény mikroslužeb pomocí jádra .NET Core

V předchozí části byly vysvětleny základní principy návrhu a vzory pro návrh modelu domény. Nyní je čas prozkoumat možné způsoby implementace modelu domény pomocí\# .NET Core (prostý kód C) a EF Core. Všimněte si, že váš model domény se bude skládat pouze z vašeho kódu. Bude mít pouze požadavky modelu EF Core, ale ne skutečné závislosti na EF. Neměli byste mít pevné závislosti nebo odkazy na EF Core nebo jiné ORM v modelu domény.

## <a name="domain-model-structure-in-a-custom-net-standard-library"></a>Struktura modelu domény ve vlastní standardní knihovně .NET

Organizace složek použitá pro referenční aplikaci eShopOnContainers demonstruje model DDD pro aplikaci. Možná zjistíte, že jiná organizace složek jasněji sděluje volby návrhu provedené pro vaši aplikaci. Jak můžete vidět na obrázku 7-10, v modelu objednávací domény existují dvě agregace, agregace objednávky a agregace kupujícího. Každý agregace je skupina entit domény a hodnotové objekty, i když můžete mít agregát složený z jedné entity domény (agregační kořenová nebo kořenová entita) také.

:::image type="complex" source="./media/net-core-microservice-domain-model/ordering-microservice-container.png" alt-text="Snímek obrazovky projektu Ordering.Domain v Průzkumníku řešení":::
Zobrazení Průzkumník řešení pro projekt Ordering.Domain, zobrazující složku AggregatesModel obsahující složky BuyerAggregate a OrderAggregate, z nichž každá obsahuje třídy entit, soubory objektů hodnoty a tak dále.
:::image-end:::

**Obrázek 7-10**. Struktura modelu domény pro objednávání mikroslužeb v eShopOnContainers

Kromě toho vrstva modelu domény zahrnuje kontrakty úložiště (rozhraní), které jsou požadavky na infrastrukturu modelu domény. Jinými slovy tato rozhraní vyjadřují, jaké repozitáře a metody vrstvy infrastruktury musí implementovat. Je důležité, aby implementace úložišť byla umístěna mimo vrstvu modelu domény v knihovně vrstvy infrastruktury, takže vrstva modelu domény není "kontaminována" rozhraním API nebo třídami z infrastrukturních technologií, jako je entity Framework.

Můžete také zobrazit složku [SeedWork,](https://martinfowler.com/bliki/Seedwork.html) která obsahuje vlastní základní třídy, které můžete použít jako základ pro entity domény a objekty hodnot, takže nemáte redundantní kód v třídě objektů každé domény.

## <a name="structure-aggregates-in-a-custom-net-standard-library"></a>Struktura agregací ve vlastní knihovně .NET Standard

Agregace odkazuje na cluster objektů domény seskupených dohromady tak, aby odpovídaly transakční konzistenci. Tyto objekty mohou být instance entit (z nichž jeden je agregační kořenová nebo kořenová entita) plus všechny další hodnoty objektů.

Transakční konzistence znamená, že agregát je zaručeno, že bude konzistentní a aktuální na konci obchodní akce. Například agregace objednávky z modelu domény eShopOnContainers objednávající mikroslužby se skládá, jak je znázorněno na obrázku 7-11.

:::image type="complex" source="./media/net-core-microservice-domain-model/vs-solution-explorer-order-aggregate.png" alt-text="Snímek obrazovky složky OrderAggregate a jejích tříd.":::
Podrobné zobrazení složky OrderAggregate: Address.cs je objekt hodnoty, IOrderRepository je repo rozhraní, Order.cs je agregační kořen, OrderItem.cs je podřízená entita a OrderStatus.cs je třída výčtu.
:::image-end:::

**Obrázek 7-11**. Agregace objednávek v řešení Sady Visual Studio

Pokud otevřete některý ze souborů v agregované složce, můžete vidět, jak je označen jako vlastní základní třídy nebo rozhraní, jako entita nebo objekt hodnoty, jak je implementováno ve složce [SeedWork.](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork)

## <a name="implement-domain-entities-as-poco-classes"></a>Implementovat entity domény jako třídy POCO

Model domény implementujete v rozhraní .NET vytvořením tříd POCO, které implementují entity domény. V následujícím příkladu order třída je definována jako entita a také jako agregační kořen. Vzhledem k tomu, že order třída pochází ze základní třídy Entity, můžete znovu použít společný kód vztahující se k entitám. Mějte na paměti, že tyto základní třídy a rozhraní jsou definovány v projektu modelu domény, takže je váš kód, nikoli kód infrastruktury z ORM jako EF.

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

Je důležité si uvědomit, že se jedná o entitu domény implementovanou jako třída POCO. Nemá žádnou přímou závislost na jádru entity frameworku nebo jiném rozhraní infrastruktury. Tato implementace je, jak by měla být\# v DDD, jen C kód implementace modelu domény.

Kromě toho je třída zdobena rozhraním s názvem IAggregateRoot. Toto rozhraní je prázdné rozhraní, někdy nazývané *rozhraní značky*, které se používá pouze k označení, že tato třída entity je také agregační kořen.

Rozhraní značky je někdy považováno za anti-pattern; je však také čistý způsob, jak označit třídu, zejména v případě, že rozhraní může být vyvíjející se. Atribut může být další volbou pro značku, ale je rychlejší zobrazit základní třídu (entitu) vedle rozhraní IAggregate namísto umístění značky atributu Aggregate nad třídu. Je to otázka preferencí, v každém případě.

S agregační kořen znamená, že většina kódu týkající se konzistence a obchodní pravidla entity agregace by měly být implementovány jako metody v pořadí agregační kořenové třídy (například AddOrderItem při přidávání OrderItem objektu agregovat) . Neměli byste vytvářet nebo aktualizovat Objekty OrderItems nezávisle nebo přímo; Třída AggregateRoot musí zachovat kontrolu a konzistenci všech operací aktualizace vůči svým podřízeným entitam.

## <a name="encapsulate-data-in-the-domain-entities"></a>Zapouzdření dat v entitách domény

Běžným problémem v modelech entit je, že zveřejňují navigační vlastnosti kolekce jako veřejně přístupné typy seznamů. To umožňuje všechny vývojáře spolupracovník manipulovat s obsahem těchto typů kolekce, které mohou obejít důležitá obchodní pravidla týkající se kolekce, případně ponechat objekt v neplatném stavu. Řešením je vystavit přístup jen pro čtení k související kolekce a explicitně poskytnout metody, které definují způsoby, ve kterém klienti mohou manipulovat s nimi.

V předchozím kódu si všimněte, že mnoho atributů je jen pro čtení nebo soukromé a jsou aktualizovatelné pouze metodami třídy, takže každá aktualizace bere v úvahu invarianty a logiku obchodní domény zadanou v rámci metod třídy.

Například následující vzory DDD **byste *neměli* dělat následující kroky** z žádné metody obslužné rutiny příkazu nebo třídy aplikační vrstvy (ve skutečnosti by to mělo být nemožné):

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

V tomto případě Add Metoda je čistě operace pro přidání dat, s přímým přístupem k OrderItems kolekce. Proto většina logiky domény, pravidla nebo ověření související s této operace s podřízenými entitami budou rozloženy do aplikační vrstvy (obslužné rutiny příkazů a řadiče webového rozhraní API).

Pokud půjdete kolem agregační kořen, agregační kořen nemůže zaručit jeho invariants, jeho platnost nebo jeho konzistence. Nakonec budete mít špagety kód nebo transakční skript kód.

Chcete-li sledovat vzory DDD, entity nesmí mít veřejné nastavení v žádné vlastnosti entity. Změny v entitě by měly být řízeny explicitními metodami s explicitním všudypřítomným jazykem o změně, kterou v entitě provádějí.

Kromě toho kolekce v rámci entity (jako položky objednávky) by měly být vlastnosti jen pro čtení (AsReadOnly metoda vysvětlena později). Měli byste být schopni aktualizovat pouze z v rámci metody agregované kořenové třídy nebo metody podřízené entity.

Jak můžete vidět v kódu pro kořenový kořen objednávky, všechny nastavení by měly být soukromé nebo alespoň pro čtení externě, takže všechny operace proti datům entity nebo její podřízené entity musí být provedeny prostřednictvím metod ve třídě entity. To udržuje konzistenci řízeným a objektově orientovaným způsobem namísto implementace transakčního kódu skriptu.

Následující fragment kódu ukazuje správný způsob, jak kód ovat úkol přidání OrderItem objektu pořadí agregace.

```csharp
// RIGHT ACCORDING TO DDD--CODE AT THE APPLICATION LAYER OR COMMAND HANDLERS
// The code in command handlers or WebAPI controllers, related only to application stuff
// There is NO code here related to OrderItem object’s business logic
myOrder.AddOrderItem(productId, productName, pictureUrl, unitPrice, discount, units);

// The code related to OrderItem params validations or domain rules should
// be WITHIN the AddOrderItem method.

//...
```

V tomto fragmentu bude většina ověření nebo logiky související s vytvořením objektu OrderItem pod kontrolou agregačního kořenu Order – v metodě AddOrderItem – zejména ověření a logiky související s jinými prvky v agregaci. Například můžete získat stejnou položku produktu v důsledku více volání AddOrderItem. V této metodě můžete prozkoumat položky produktu a konsolidovat stejné položky produktu do jednoho objektu OrderItem s několika jednotkami. Navíc, pokud existují různé částky slevy, ale ID produktu je stejný, pravděpodobně použít vyšší slevu. Tento princip platí pro všechny ostatní logiky domény pro OrderItem objektu.

Kromě toho nové OrderItem (params) operace bude také řízena a provedena AddOrderItem metoda z Order agregační kořen. Proto většina logiky nebo ověření související s této operace (zejména cokoli, co má vliv na konzistenci mezi jinými podřízenými entitami) bude na jednom místě v rámci agregační kořen. To je konečný účel souhrnného kořenového vzoru.

Při použití entity Framework Core 1.1 nebo novější, entita DDD může být lépe vyjádřena, protože umožňuje [mapování na pole](https://docs.microsoft.com/ef/core/modeling/backing-field) kromě vlastností. To je užitečné při ochraně kolekce podřízených entit nebo hodnotových objektů. S tímto vylepšením můžete použít jednoduchá soukromá pole namísto vlastností a můžete implementovat libovolnou aktualizaci kolekce polí ve veřejných metodách a poskytnout přístup jen pro čtení prostřednictvím metody AsReadOnly.

V DDD chcete aktualizovat entitu pouze prostřednictvím metod v entitě (nebo konstruktoru) za účelem řízení jakékoli invarianty a konzistence dat, takže vlastnosti jsou definovány pouze pomocí přistupujícího objektu get. Vlastnosti jsou zálohovány soukromými poli. Soukromé členy lze přistupovat pouze z v rámci třídy. Existuje však jedna výjimka: EF Core musí také nastavit tato pole (tak, aby může vrátit objekt se správnými hodnotami).

### <a name="map-properties-with-only-get-accessors-to-the-fields-in-the-database-table"></a>Mapování vlastností pouze s přístupovými objekty k polím v databázové tabulce

Mapování vlastností na sloupce databázové tabulky není odpovědností domény, ale součástí vrstvy infrastruktury a trvalosti. Zmíníme se zde jen proto, abyste si byli vědomi nových funkcí v EF Core 1.1 nebo novějších, které souvisejí s tím, jak můžete modelovat entity. Další podrobnosti k tomuto tématu jsou vysvětleny v části infrastruktury a trvalosti.

Při použití EF Core 1.0 nebo novější, v rámci DbContext je třeba mapovat vlastnosti, které jsou definovány pouze s getters na skutečná pole v databázové tabulce. To se provádí metodou HasField třídy PropertyBuilder.

### <a name="map-fields-without-properties"></a>Mapování polí bez vlastností

Pomocí funkce v EF Core 1.1 nebo novější mapovat sloupce na pole, je také možné nepoužívat vlastnosti. Místo toho můžete pouze mapovat sloupce z tabulky na pole. Běžnýpřípad použití pro toto je privátní pole pro vnitřní stav, který není nutné přistupovat z mimo entitu.

Například v předchozím příkladu orderaggregate kódu existuje několik soukromých polí, jako je `_paymentMethodId` pole, které nemají žádnou související vlastnost pro setter nebo getter. Toto pole lze také vypočítat v rámci obchodní logiky objednávky a použít z metod objednávky, ale musí být také trvalé v databázi. Takže v EF Core (od verze 1.1) existuje způsob, jak mapovat pole bez související vlastnosti na sloupec v databázi. To je také vysvětleno v části [Vrstva infrastruktury](ddd-oriented-microservice.md#the-infrastructure-layer) v této příručce.

### <a name="additional-resources"></a>Další zdroje

- **Vaughn Vernon, to je můj zástupce. Modelování agregace s DDD a entity framework.** Všimněte si, že *toto není* jádro entity frameworku. \
  <https://kalele.io/blog-posts/modeling-aggregates-with-ddd-and-entity-framework/>

- **Julie Lermanová. Datové body - Kódování pro návrh řízený doménou: Tipy pro data-zaměřené devs** \
  <https://docs.microsoft.com/archive/msdn-magazine/2013/august/data-points-coding-for-domain-driven-design-tips-for-data-focused-devs>

- **Udi Dahan. Jak vytvořit plně zapouzdřené modely domény** \
  <http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/>

> [!div class="step-by-step"]
> [Předchozí](microservice-domain-model.md)
> [další](seedwork-domain-model-base-classes-interfaces.md)
