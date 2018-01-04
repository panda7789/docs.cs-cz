---
title: "Implementace modelu mikroslužbu domény s .NET Core"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Implementace modelu mikroslužbu domény s .NET Core"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/09/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 07a79f3d52db400d1539fb4172166cccf8905fb8
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="implementing-a-microservice-domain-model-with-net-core"></a>Implementace modelu mikroslužbu domény s .NET Core 

V předchozí části byly vysvětlené základní principy a vzory návrhu modelu domény. Nyní je čas na vyzkoušení možné způsoby, jak implementovat modelu domény pomocí .NET Core (prostý C\# kódu) a základní EF. Všimněte si, že váš model domény bude skládat jednoduše vašeho kódu. Na EF bude mít jenom základní EF modelu požadavky, ale ne skutečné závislosti. Pevné závislosti nebo odkazy na základní EF nebo jiných ORM by neměl mít v modelu domény.

## <a name="domain-model-structure-in-a-custom-net-standard-library"></a>Doménovou strukturu modelu v knihovně vlastní .NET Standard

Složka organizace používá pro odkaz na aplikaci eShopOnContainers ukazuje DDD modelu pro danou aplikaci. Můžete se setkat jinou složku organizace více jasně komunikuje možnosti návrhu, které jsou vytvářeny pro vaši aplikaci. Jak vidíte v obrázek 9 – 10, v řazení modelu domény existují dvě agregace, agregace pořadí a kupujících agregace. Každý agregace je skupina domény entity a hodnota objekty, i když můžete mít agregace také skládá z jedné domény entity (agregační kořenové nebo kořenové entity).

![](./media/image11.png)

**Obrázek 9 – 10**. Doménovou strukturu modelu pro řazení mikroslužbu v eShopOnContainers

Kromě toho vrstva modelu domény zahrnuje smlouvy úložiště (rozhraní), které jsou požadavky na infrastrukturu modelu domény. Jinými slovy, tyto rozhraní express jaké úložiště vrstvě infrastruktury musí implementovat a jak. Je důležité, aby implementace úložišť umístit mimo vrstva modelu domény, v knihovně infrastruktury vrstvy tak vrstva modelu domény není "napadeny" rozhraní API nebo třídy z infrastruktury technologie, jako je rozhraní Entity Framework.

Můžete také zjistit [SeedWork](https://martinfowler.com/bliki/Seedwork.html) složku, která obsahuje vlastní základní třídy, které můžete použít jako základ pro entity domény a hodnota objekty, takže není nutné redundantní kódu v každé doméně třída objektu.

## <a name="structuring-aggregates-in-a-custom-net-standard-library"></a>Strukturování agregací ve vlastní knihovna .NET Standard

Agregace odkazuje na clusteru s podporou objektů domény tak, aby odpovídaly transakční konzistence seskupeny dohromady. Tyto objekty může být instancí entit (z nichž jeden je agregační kořenový server WSUS nebo kořenové entity) plus všechny objekty další hodnotu.

Transakční konzistence znamená, že agregace záruku, že se konzistentní a aktuální na konci obchodní akce. Například agregace pořadí z eShopOnContainers řazení mikroslužbu modelu domény se skládá, jak ukazuje obrázek 9 – 11.

![](./media/image12.png)

**Obrázek 9-11**. Pořadí agregační v řešení sady Visual Studio

Otevřete-li některý ze souborů ve složce aplikace agregační, uvidíte jak je označen jako vlastní základní třídu nebo rozhraní, jako je entity nebo hodnota objektu, jak jsou implementované ve [Seedwork](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork) složky.

## <a name="implementing-domain-entities-as-poco-classes"></a>Implementace entity domény jako třídy objektů POCO

Implementaci modelu domény v rozhraní .NET a vytváření tříd objektů POCO, které implementují entity vaší domény. V následujícím příkladu je třída pořadí definovaná jako entity a také jako agregovaná kořenového adresáře. Protože pořadí třída odvozena z třídy base entita, můžete znovu použít společný kód související s entitami. Berte v úvahu, že tyto základní třídy a rozhraní jsou definované uživatelem v projektu modelu domény, tak, aby byl kód, není infrastruktury kód z ORM jako EF.

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

Je důležité si uvědomit, že toto je entita domény, implementovaný jako třídu objektů POCO. Nástroj nemá žádné přímé závislost na Entity Framework Core nebo jiné infrastruktury framework. Tato implementace je jako by měl být v DDD, právě C\# kód implementace modelu domény.

Kromě toho je třída označených pomocí rozhraní s názvem IAggregateRoot. Toto rozhraní je prázdný rozhraní, někdy nazývané *rozhraní značek*, která je použít jenom k označení, že tato třída entity je také agregační kořenové.

Rozhraní značek se někdy považuje za proti vzor; je však také čistou způsob, jak označit třídu, zejména v případě, že rozhraní může být vyvíjející se. Atribut může být volba pro značky, ale je rychlejší najdete v části základní třídy (entita) vedle rozhraní IAggregate místo vložení agregační atribut značky nad třídu. Je metter preference, v každém případě.

S agregační kořenové znamená, že většinu kódu související s konzistence a obchodní pravidla na agregaci entit by měla být implementována jako metody ve třídě agregační kořenové pořadí (například AddOrderItem při přidávání objektu OrderItem do agregace) . Nesmí vytvořit nebo aktualizovat objekty OrderItems, samostatně nebo přímo. Třída AggregateRoot musí je udržovat v řízení a konzistence všechny operace aktualizace proti podřízených entit.

## <a name="encapsulating-data-in-the-domain-entities"></a>Zapouzdření dat v doméně entity

Častých problémů v modelech entity je, že jejich vystavit navigační vlastnosti kolekce jako veřejně přístupný seznamu typy. To umožňuje vývojáři žádné spolupracovník manipulovat s obsahem tyto kolekce typů, které mohou obejít zásadní obchodní pravidla pro kolekci, pravděpodobně nechat objekt v neplatném stavu. Toto řešení je vystavit přístup jen pro čtení k související kolekce a explicitně zadat metody, které definují způsoby, ve kterém můžete upravit klientů je.

V předchozí kód Všimněte si, že mnoho atributů jsou jen pro čtení nebo privátní a jsou pouze aktualizovat pomocí metody třídy, takže všechny aktualizace trvat do výstupních podmínek domény účtů business a logiku určenou v rámci metody třídy.

Například následující vzory DDD, měli byste *není* udělejte z libovolné příkaz obslužná rutina metoda nebo aplikaci vrstvy třídy:

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

Metodu Add. v takovém případě je čistě operace přidání dat s přímým přístupem ke kolekci OrderItems. Proto většinu logiku domény, pravidel nebo ověření související se, že operace podřízenými položkami, bude možné rozdělit do aplikační vrstvu (obslužné rutiny příkazů a řadičů webového rozhraní API).

Pokud přejdete kolem agregační kořenové, nemůže zaručit kořenu agregační jeho výstupních podmínek, jeho platnost nebo jeho konzistence. Nakonec bude mít špagety kód nebo kód transakční skriptu.

Podle vzorů DDD, nesmí mít entity v libovolné vlastnosti entity, veřejné setter. Změny v entitě by měl být doprovází explicitní metody s explicitní všudypřítomný jazyk o změny, které se provádí v entitě.

Kromě toho kolekce v rámci entity (např. pořadí položek) by měla být vlastnosti jen pro čtení (metoda AsReadOnly vysvětleno dále). Nyní byste měli mít pouze z aktualizovat v rámci metody třídy agregační kořenové nebo podřízené metody entity.

Jak můžete vidět v kódu pro kořenovou agregační pořadí, všechny setter musí být privátní nebo alespoň oprávnění jen pro čtení externě, tak, aby všechny operace proti entity data nebo jeho podřízených entit musí být provedena prostřednictvím metody ve třídě entity. Tím se zachová konzistence řízené a objektově orientované způsobem místo implementace kód transakční skriptu.

Následující fragment kódu ukazuje správný způsob, jak můžete kód úkolu přidávání objekt OrderItem k agregaci pořadí.

```csharp
// RIGHT ACCORDING TO DDD--CODE AT THE APPLICATION LAYER OR COMMAND HANDLERS
// The code in command handlers or WebAPI controllers, related only to application stuff
// There is NO code here related to OrderItem object’s business logic
myOrder.AddOrderItem(productId, productName, pictureUrl, unitPrice, discount, units);

// The code related to OrderItem params validations or domain rules should
// be WITHIN the AddOrderItem method.

//...
```

V tento fragment kódu, bude většina ověření nebo logiku související vytvoření objektu OrderItem pod kontrolou agregační kořenu pořadí – v metodě AddOrderItem – zejména ověření a logiku související s další prvky v souhrnném. Například může získat položce produktu v důsledku několik volání AddOrderItem. V dané metody můžete prozkoumat položky produktu a konsolidovat stejné položek produktu do jednoho objektu OrderItem u několik jednotek. Kromě toho pokud existují různé slevu objemy, ale ID produktu je stejný, by pravděpodobně použijete vyšší slevy. Tato zásada se vztahuje na další logiku domény OrderItem objektu.

Kromě toho nové OrderItem(params) operaci rovněž se řídí a provádí metodu AddOrderItem z kořene agregační pořadí. Proto většinu logiky nebo ověření související se, že operace, (zejména všechno, co má dopad na konzistenci mezi dalšími subjekty, podřízené) bude na jednom místě v kořenu agregační. Toto je ultimate účel agregační kořenové vzoru.

Pokud používáte Entity Framework Core 1.1 nebo novější, DDD entita může být lépe vyjádřený protože umožňuje [mapování polí](https://docs.microsoft.com/ef/core/modeling/backing-field) kromě vlastností. To je užitečné, když chráníte kolekcí podřízených entit nebo hodnota objekty. Toto vylepšení můžete použít jednoduchý privátním polím místo vlastnosti a můžete implementovat žádné aktualizace ke kolekci pole v veřejné metody a poskytovat přístup jen pro čtení prostřednictvím metody AsReadOnly.

V DDD chcete entitu aktualizovat pouze prostřednictvím metody v entitě (nebo konstruktoru), aby bylo možné řídit všechny neutrální a konzistence dat takže vlastnosti jsou definované pouze s přistupující objekt get. Vlastnosti jsou zajišťované privátním polím. Soukromé členy pouze přístupná v rámci třídy. Ale zde jedna výjimka: základní EF je třeba nastavit také těchto polí.


### <a name="mapping-properties-with-only-get-accessors-to-the-fields-in-the-database-table"></a>Mapování vlastností s pouze získat přístupové objekty na pole v tabulce databáze

Mapování vlastností na sloupce tabulky databáze není odpovědnost domény, ale součást vrstvě infrastruktury a trvalost. Jsme zmínili, tento tady jednoduše tak, že víte o nové funkce v EF základní 1.1 nebo později související na tom, jak můžete modelu entity. Další informace o tomto tématu jsou vysvětleny v sekci infrastruktury a trvalost.

Při použití EF základní 1.0, v rámci DbContext, budete muset mapy – vlastnosti, které jsou definovány pouze s mechanismy získání skutečné pole v tabulce databáze. To se provádí pomocí metody HasField PropertyBuilder třídy.

### <a name="mapping-fields-without-properties"></a>Mapování polí bez vlastností

Funkce s EF základní 1.1 nebo novější k mapování sloupců na pole je také možné nepoužívat vlastnosti. Místo toho můžete namapovat jenom sloupce z tabulky na pole. Běžně používá pro tento je privátním polím pro vnitřní stav, který nemusí být subjekty mimo entity.

Například v předchozím příkladu kódu OrderAggregate neexistují několik privátní pole, jako je třeba `_paymentMethodId` pole, které mají žádné související vlastnost pro nastavení nebo getter. Toto pole může být také vypočítat v rámci obchodní logiku pořadí a použít z metod pořadí, ale je potřeba nastavit jako trvalý, v databázi také. Proto v EF jádra (od verze 1.1) je způsob, jak mapování pole bez související vlastnosti na sloupec v databázi. To je také podrobně [vrstvě infrastruktury](#the-infrastructure-layer) části této příručky.

### <a name="additional-resources"></a>Další zdroje

-   **Vaughn Vernon. Modelování agregace s DDD a Entity Framework.** Všimněte si, že toto je *není* Entity Framework Core.
    [*https://vaughnvernon.co/?p=879*](https://vaughnvernon.co/?p=879)

-   **Julie Lerman. Kódování řízené domény návrh: tipy pro zaměřené na Data Devs**
    [*https://msdn.microsoft.com/en-us/magazine/dn342868.aspx*](https://msdn.microsoft.com/en-us/magazine/dn342868.aspx)

-   **UDI Dahan. Postup vytvoření plně zapouzdřené domény modely**
    [*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)


>[!div class="step-by-step"]
[Předchozí] (mikroslužbu domain-model.md) [Další] (seedwork-domain-model-base-classes-interfaces.md)
