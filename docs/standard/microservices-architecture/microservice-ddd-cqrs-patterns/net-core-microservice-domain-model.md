---
title: Implementace doménového modelu mikroslužby pomocí .NET Core
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Implementace doménového modelu mikroslužby pomocí .NET Core
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/09/2017
ms.openlocfilehash: bb11d87cacf5bb6cbc980c879b0c42fae76f6246
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44272277"
---
# <a name="implementing-a-microservice-domain-model-with-net-core"></a>Implementace doménového modelu mikroslužby pomocí .NET Core 

V předchozí části byly vysvětlení principů návrhu základní a vzory pro navrhování modelu domény. Teď můžete prozkoumat možnosti, jak implementovat doménový model s využitím .NET Core (plain C\# kódu) a EF Core. Všimněte si, že doménový model se skládá pouze z kódu. Jenom požadavky modelu EF Core, ale ne skutečné závislosti bude mít na EF. Pevné závislosti nebo odkazy na EF Core nebo jiných ORM by neměl mít v doménovém modelu.

## <a name="domain-model-structure-in-a-custom-net-standard-library"></a>Doménovou strukturu modelu ve vlastní knihovny .NET Standard

Složka organizaci použít aplikaci eShopOnContainers referenční aplikace ukazuje DDD modelů pro aplikaci. Můžete zjistit, že organizace jinou složku jasněji komunikuje návrhu volby provedené pro vaši aplikaci. Jak je vidět v obrázek 9-10, v pořadí doménový model existují dvě agregace, agregace pořadí a agregace odběratele. Každou agregaci je skupina domény entity a objekty hodnotu, i když jste mohli agregace také skládá z jedné domény entity (agregační kořenové nebo Kořenová entita).

![](./media/image11.png)

**Obrázek 9-10**. Doménovou strukturu modelu pro objednávání mikroslužeb v aplikaci eShopOnContainers

Kromě toho zahrnuje vrstvě doménového modelu smlouvy úložiště (rozhraní), které jsou požadavky na infrastrukturu modelu domény. Jinými slovy, tato rozhraní express jaké úložiště vrstvy infrastruktury musí implementovat a jak. Je velmi důležité, že implementace úložišť umístit mimo vrstvě doménového modelu, v knihovně infrastruktury vrstvu tak vrstvě doménového modelu není "napadeny" rozhraní API nebo třídy z infrastruktury technologie, jako jsou rozhraní Entity Framework.

Můžete také zobrazit [SeedWork](https://martinfowler.com/bliki/Seedwork.html) složku, která obsahuje vlastní základní třídy, které můžete použít jako základ pro entity domény a hodnota objekty, takže není nutné redundantní kód ve třídě objektu každé domény.

## <a name="structuring-aggregates-in-a-custom-net-standard-library"></a>Strukturování agregace ve vlastní knihovny .NET Standard

Agregace odkazuje na clusteru objektů domény seskupené dohromady tak, aby odpovídaly transakční konzistence. Tyto objekty může být instancí entit (z nichž jeden je agregační kořenový server WSUS nebo Kořenová entita) plus všechny objekty další hodnotu.

Transakční konzistence znamená, že agregace je zaručeno, že byly konzistentní a aktuální na konci obchodní akce. Například pořadí agregace v aplikaci eShopOnContainers řazení doménového modelu mikroslužby se skládá, jak je znázorněno v obrázek 9 – 11.

![](./media/image12.png)

**Obrázek 9 – 11**. Pořadí agregace v řešení sady Visual Studio

Otevřete-li některý ze souborů ve složce aplikace agregace, zobrazí se jak je označen jako vlastní základní třídu nebo rozhraní, jako entity nebo hodnotu objektu, jak je implementován v [Seedwork](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork) složky.

## <a name="implementing-domain-entities-as-poco-classes"></a>Implementace entity domény jako třídy POCO

Doménový model se implementovat v rozhraní .NET tak, že vytvoříte POCO třídy, které implementují entity domény. V následujícím příkladu je definována třída pořadí jako entity a také jako kořen agregace. Protože pořadí třída je odvozena ze základní třídy Entity, můžete znovu použít společný kód související s entitami. Berte v úvahu, že tyto základní třídy a rozhraní jsou definované uživatelem v projektu s modelem domény, tak, aby byl váš kód, ne infrastruktury kód z ORM jako je EF.

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

Je důležité si uvědomit, že se entita domény implementován jako třída POCO. Nemá přímou závislost na Entity Framework Core nebo libovolné jiné architektury infrastruktury. Tato implementace je jako by měl být v DDD, stačí C\# kód implementace modelu domény.

Kromě toho je třída upravena pomocí rozhraní s názvem IAggregateRoot. Toto rozhraní je prázdné rozhraní, říká se jim *rozhraní značky*, která je slouží jenom k označení, že tato třída entity je také agregační kořenové.

Rozhraní značky někdy považovat odolnou proti vzor; je však také čistý způsob, jak označit třídu, zejména v případě, že toto rozhraní může být vyvíjejí. Atribut může být volba pro značky, ale je rychlejší zobrazíte základní třídy (entita) vedle rozhraní IAggregate namísto vložení hodnoty značku agregační atribut nad třídu. Je na vás předvolby, v každém případě.

Máte agregační kořenové znamená, že většinu kódu související s konzistence a obchodních pravidel agregaci entit by měla být implementována jako metody ve třídě kořenové agregační pořadí (například AddOrderItem při přidávání objektu OrderItem agregaci) . By neměl vytvořit nebo aktualizovat objekty OrderItems, nezávisle na sobě nebo přímo. Třída AggregateRoot uchovává ovládacího prvku a konzistence, všechny operace aktualizace s jeho podřízených entit.

## <a name="encapsulating-data-in-the-domain-entities"></a>Zapouzdření dat v entitách domény

Běžný problém v modelech entity je, aby zveřejňovaly navigační vlastnosti kolekce jako seznam veřejně přístupné typy. To umožňuje vývojáři ocení spolupracovníka manipulovat s obsahem těchto kolekci typů, které mohou obejít důležitá obchodní pravidla pro kolekci, možná byste museli opustit objektu v neplatném stavu. Řešení, aby to je a vystavovat přístup jen pro čtení k souvisejících kolekcích explicitně poskytující metody, které definují způsoby, ve které klienty můžete s nimi manipulovat.

V předchozím kódu mějte na paměti, že mnoho atributů jsou jen pro čtení nebo privátní a jsou pouze aktualizovatelné metody třídy tak všechny aktualizace trvá do výstupních účet obchodní domény podmínek a logiku určenou v rámci metod tříd.

Například následující vzorů DDD, měli byste *není* udělejte z libovolné příkaz rutinu metody nebo aplikace vrstvy třídy:

```csharp
// WRONG ACCORDING TO DDD PATTERNS – CODE AT THE APPLICATION LAYER OR
// COMMAND HANDLERS
// Code in command handler methods or Web API controllers
//... (WRONG) Some code with business logic out of the domain classes ...
OrderItem myNewOrderItem = new OrderItem(orderId, productId, productName,
    pictureUrl, unitPrice, discount, units);

//... (WRONG) Accessing the OrderItems colletion directly from the application layer // or command handlers
myOrder.OrderItems.Add(myNewOrderItem);
//...
```

Metoda Add v tomto případě je čistě operace přidání dat s přímým přístupem do kolekce OrderItems. Proto se většina logiku domény, pravidla nebo ověření související se, že operace s podřízených entit bude možné rozdělit do aplikační vrstvy (obslužné rutiny příkazů a kontrolerů rozhraní Web API).

Budete-li kolem agregační kořenové, agregační kořenové nemůže zaručit jeho výstupních podmínek, jeho platnost nebo jeho konzistence. Nakonec je třeba špagety kód nebo kód transakční skriptu.

Pokud chcete postupovat podle vzorů DDD, nesmí mít entity veřejné metody setter v jakékoli vlastnosti entity. Změny v entitě by měl vycházet explicitní metody explicitní všudypřítomná jazyk o změny, které provádějí v dané entitě.

Kromě toho kolekce v rámci entity (například položky objednávky) by měl být vlastnosti jen pro čtení (metoda AsReadOnly vysvětleno dále). Je třeba aktualizovat pouze z v rámci metody agregační kořenové třídy nebo metody podřízené entity.

Jak je vidět v kódu pro kořenový agregační pořadí, všechny metody setter by měla být privátní nebo alespoň oprávnění jen pro čtení externě, tak, aby žádné operace proti entity dat nebo její podřízené entity se provádí prostřednictvím metody ve třídě entity. To udržuje konzistenci způsobem řízeným a objektově orientované namísto implementace kódu transakční skriptu.

Následující fragment kódu ukazuje správný způsob, jak kód úkolu přidávání objekt OrderItem agregaci pořadí.

```csharp
// RIGHT ACCORDING TO DDD--CODE AT THE APPLICATION LAYER OR COMMAND HANDLERS
// The code in command handlers or WebAPI controllers, related only to application stuff
// There is NO code here related to OrderItem object’s business logic
myOrder.AddOrderItem(productId, productName, pictureUrl, unitPrice, discount, units);

// The code related to OrderItem params validations or domain rules should
// be WITHIN the AddOrderItem method.

//...
```

V tomto fragmentu kódu, bude většinu ověření nebo logiky týkající se vytvoření objektu OrderItem pod kontrolou agregační kořenové pořadí – v metodě AddOrderItem – zejména ověření a logiku související s další prvky v agregaci. Například se mohou zobrazovat jako výsledek z více volání AddOrderItem jedné položce produktu. V této metodě můžete zkontrolovat položky produktu a konsolidovat do jediného objektu OrderItem s více jednotkami stejné položky produktu. Kromě toho pokud existují jiné slevy objemy, ale ID produktu je stejný, by pravděpodobně použijete vyšší slevy. Tento princip platí pro další logiku domény OrderItem objektu.

Kromě toho novou operaci OrderItem(params) také být řízený a provádí metoda AddOrderItem z kořene agregační pořadí. Proto většinu logiku nebo ověření související se, že operace (zejména cokoli, co má vliv na konzistenci mezi ostatní podřízené entity) bude na jednom místě v kořenu agregace. To je účel ultimate agregační kořenové vzoru.

Pokud používáte Entity Framework Core 1.1 nebo později, DDD entity můžete lépe vyjádřit protože umožňuje [mapování na pole](https://docs.microsoft.com/ef/core/modeling/backing-field) kromě vlastností. To je užitečné, když chráníte kolekce podřízených entit nebo hodnota objekty. Toto vylepšení místo vlastnosti můžete použít jednoduchý privátní pole a můžete implementovat jakýmkoli aktualizacím kolekce pole ve veřejné metody a prostřednictvím metody AsReadOnly poskytují přístup jen pro čtení.

V DDD, které chcete aktualizovat entitu pouze prostřednictvím metod v entity (nebo konstruktoru), aby bylo možné řídit všechny invariantní a konzistenci dat takže vlastnosti jsou definovány pouze s přistupující objekt get. Vlastnosti se zálohují na soukromé pole. Soukromé členy lze přistupovat pouze z v rámci třídy. Nicméně tady jedna výjimka: EF Core je potřeba nastavit také tato pole.


### <a name="mapping-properties-with-only-get-accessors-to-the-fields-in-the-database-table"></a>Mapování vlastností pomocí pouze získat přístupové objekty do polí v tabulce databáze

Mapování vlastnosti na sloupce tabulky databáze není odpovědnost domény, ale součástí infrastruktury a stálost vrstvu. Jsme zmínili, tento tady jenom, abyste měli přehled o novinkách v EF Core 1.1 nebo novější týkajících se jak lze modelovat entity. Další podrobnosti o tomto tématu jsou vysvětlené v oblasti infrastruktury a trvalost.

Při použití EF Core 1.0, v rámci uvolněn objekt DbContext, budete muset mapy – vlastnosti, které jsou definovány pouze pomocí metody getter skutečné polí v tabulce databáze. To se provádí pomocí metody HasField PropertyBuilder třídy.

### <a name="mapping-fields-without-properties"></a>Mapování polí bez vlastností

S funkcí v EF Core 1.1 nebo vyšší sloupce mapovat na pole je také možné používat vlastnosti. Místo toho můžete namapovat pouze sloupce z tabulky na pole. Je běžným případem použití pro tento privátní pole pro vnitřní stav, který není potřeba přistupovat z mimo entitu.

Například v předchozím příkladu kódu OrderAggregate existují několik privátní pole, jako je třeba `_paymentMethodId` pole, které mají žádné související vlastnost setter nebo getter. Toto pole také může vypočítá v rámci obchodní logiku pořadí a použití z metody pořadí, ale je potřeba nastavit jako trvalý, v databázi i. Takže v EF Core (od verze 1.1) je způsob, jak mapovat pole bez související vlastnost sloupec v databázi. To je také jsou vysvětlené v [vrstvy infrastruktury](#the-infrastructure-layer) části této příručky.

### <a name="additional-resources"></a>Další zdroje

-   **Vaughn Vernon. Modelování agregace s DDD a Entity Framework.** Všimněte si, že toto je *není* Entity Framework Core.
    [*https://vaughnvernon.co/?p=879*](https://vaughnvernon.co/?p=879)

-   **Julie Lerman. Kódování pro návrhy řízené doménou: tipy pro vývojáře, zaměřuje dat**
    [*https://msdn.microsoft.com/en-us/magazine/dn342868.aspx*](https://msdn.microsoft.com/en-us/magazine/dn342868.aspx)

-   **Udi Dahan. Vytvoření plně zapouzdřené doménových modelů**
    [*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)


>[!div class="step-by-step"]
[Předchozí](microservice-domain-model.md)
[další](seedwork-domain-model-base-classes-interfaces.md)
