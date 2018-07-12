---
title: Navržení modelu mikroslužbu domény
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Navržení modelu mikroslužbu domény
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/09/2017
ms.openlocfilehash: e672685666c846ea63bcd9cdb713af58f5e6fb1b
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106249"
---
# <a name="designing-a-microservice-domain-model"></a>Navržení modelu mikroslužbu domény

*Definovat jeden model bohaté domény pro každou obchodní mikroslužbu nebo ohraničenou kontextu*

Vaším cílem je pro vytvoření modelu získá na ucelenosti jednu doménu pro každou obchodní mikroslužbu nebo ohraničenou kontextu (BC). Mějte na paměti, ale který BC nebo obchodní mikroslužbu může někdy skládat několik fyzických služeb, které sdílí jedinou doménu modelu. Model domény nutné zaznamenat pravidla, chování, obchodní jazyk a omezení jednotlivý kontext ohraničenou nebo mikroslužbu firmy, která reprezentuje.

## <a name="the-domain-entity-pattern"></a>Entita domény vzor

Entity reprezentaci objektů domény a jejich identitu, kontinuitu a trvalost v čase a ne jenom atributy, které tvoří jejich jsou primárně definováno. Jako zařízení Evans Erica informacemi o tom, "objekt primárně definováno svou identitu se nazývá Entity." Entity jsou velmi důležité v modelu domény, protože jsou základ pro model. Proto musí identifikovat a je pečlivě návrhu.

*Entity identity můžete mezi více mikroslužeb nebo ohraničenou kontextů.*

Stejnou identitu (i když není stejná entita) můžete modelován mezi více ohraničenou kontexty nebo mikroslužeb. Nicméně, neznamená ve více ohraničenou kontexty by být implementována stejné entity se stejným atributy a logiku. Místo toho entity v kontextu jednotlivých ohraničenou omezte jejich atributů a chování pro tyto požadované v tomto ohraničenou kontextu domény.

Pro instanci entity kupujících pravděpodobně většinu atributů osoby, které jsou definovány v entity uživatele v profilu nebo identita mikroslužbu, včetně identity. Ale kupujících entity v řazení mikroslužbu pravděpodobně méně atributů, protože je jenom určité kupujících data související s procesem pořadí. Kontext každý mikroslužbu nebo ohraničenou kontextu ovlivňuje jeho modelu domény.

*Domény entit musí implementovat chování kromě implementace atributy dat*

Entita domény v DDD musí implementovat logiku domény nebo chování týkající se dat entity (objekt získat přístup do paměti). Jako součást třídu entity pořadí je třeba musí mít operace implementované jako metody pro úlohy, jako je například přidávání pořadí položek, ověřování dat a celkový počet výpočtu a obchodní logiku. Metody entity postará výstupních podmínek a pravidel entity místo nutnosti tato pravidla rozloženy aplikační vrstvu.

Obrázek 9 – 8 znázorňuje entita domény, která implementuje nejen atributy datového ale operace nebo metody s logiku související domény.

![](./media/image9.png)

**Obrázek 9 – 8**. Příklad implementace data plus chování entit návrhu domény

Samozřejmě v některých případech může mít entit, které neimplementují veškeré logiky v rámci třídy entity. To může nastat v podřízených entit v rámci agregace, když se entita na podřízené nemá žádné speciální logiku, protože většina logiku je definováno v kořenu agregační. Pokud máte komplexní mikroslužbu, který má spoustu logiku implementaci třídy služeb místo v entity domény, může být spadajících do modelu anemic domény, popsané v následující části.

### <a name="rich-domain-model-versus-anemic-domain-model"></a>Bohaté domény modelu a modelu anemic domény

V jeho post [AnemicDomainModel](https://martinfowler.com/bliki/AnemicDomainModel.html), Martin Fowler popisuje model anemic domény takto:

Základní příznakem Model Anemic domény je, že v první blush to vypadá Opravdová věc. Existují objekty, řada s názvem po podstatná jména v oboru domény a tyto objekty jsou spojeny s bohatou vztahy a struktury, která má hodnotu true domény modely. Catch pochází, když se podíváte na chování a zjistíte, zda je na tyto objekty špatně žádné chování přitom něco více než sáčky mechanismy získání a nastavení.

Samozřejmě, pokud používáte model anemic domény, tyto datové modely se použije ze sady objektů služby (tradičně s názvem *vrstvě podnikání*) který zaznamenat všechny domény nebo obchodní logiku. Obchodní vrstva je umístěna nad datový model a používá datový model stejně jako data.

Model anemic domény je právě návrh procedurální stylu. Objekty anemic entity nejsou skutečné objekty tím, že neobsahují chování (metody). Drží vlastnosti dat, a proto není objektově orientované návrhu. Vložením všechny chování odhlašování do služby objektů (business layer) v podstatě skončili s [špagety kódu](https://en.wikipedia.org/wiki/Spaghetti_code) nebo [transakce skripty](https://martinfowler.com/eaaCatalog/transactionScript.html), a proto ztratit výhod modelu domény poskytuje.

Bez ohledu na to, pokud je velmi jednoduchý mikroslužbu nebo ohraničenou kontextu (CRUD služby), modelu anemic domény v podobě objektů entity se jenom vlastnosti dat může být dostatečně funkční a nemusí být vhodné implementace složitější DDD vzorů. V takovém případě bude jednoduše trvalost modelu, protože se pouze data pro účely CRUD záměrně vytvoření entity.

To je důvod, proč jsou ideální pro více architektury přístup v závislosti na kontextu jednotlivých ohraničenou mikroslužeb architektury. Například v eShopOnContainers, řazení mikroslužbu implementuje vzory DDD, ale mikroslužbu katalog, který je jednoduchý služba CRUD, nemá.

Někteří uživatelé říkají, že model anemic domény je proti vzor. Ve skutečnosti závisí na co jsou implementace. Pokud je mikroslužbu vytvoříte jednoduchou dostatečně (například služba CRUD), následující modelu anemic domény není proti vzor. Ale pokud budete potřebovat řešení složitost mikroslužbu domény, který má spoustu proměnlivých obchodní pravidla, modelu anemic domény může být proti vzor pro dané mikroslužbu nebo ohraničenou kontextu. V takovém případě je navrhování jako s formátováním model, který obsahuje entity obsahující data plus chování a také implementace další DDD vzorů (agregace, hodnota objekty atd.) může mít velký výhody pro dlouhodobý úspěch takové mikroslužby.

#### <a name="additional-resources"></a>Další zdroje

-   **DevIQ. Entita domény**
    [*http://deviq.com/entity/*](http://deviq.com/entity/)

-   **Martin Fowler. Model domény**
    [*https://martinfowler.com/eaaCatalog/domainModel.html*](https://martinfowler.com/eaaCatalog/domainModel.html)

-   **Martin Fowler. Model Anemic domény**

    <https://martinfowler.com/bliki/AnemicDomainModel.html>

### <a name="the-value-object-pattern"></a>Vzor hodnota objektu

Jak je uvedeno zařízení Evans Erica, "mnoho objektů nemají koncepční identity. Tyto objekty popisují některé charakteristiky co".

Entita vyžaduje identity, ale v systému, které nepodporují, existuje mnoho objektů, jako vzor objektu hodnotu. Objekt hodnoty je objekt s žádná koncepční identita, která popisuje aspekt domény. Tyto jsou objekty, které můžete vytvořit instanci představují prvků návrhu, které se týkají pouze můžete dočasně. Kterých vám nejvíc záleží *co* nejsou, *kdo* jsou. Příklady zahrnují čísla a řetězce, ale může být také vyšší úrovně koncepty jako skupiny atributů.

Vzhledem k tomu, že v druhém případě kontext ohraničenou může mít jiný význam něco, co je entita v mikroslužbu nemusí být entity v jiné mikroslužby. Například adresu v aplikaci elektronického obchodování nemusí mít identity vůbec, protože ho může jenom představují skupinu atributů zákazníka profilu pro uživatele nebo společnosti. V takovém případě adresu by se měly klasifikovat jako objekt hodnoty. V aplikaci pro firmu nástroj elektrické energie, může být důležité pro doménu firmy adresa zákazníka. Adresu proto musí mít identity, takže fakturační systém může být přímo spojeny s adresu. V takovém případě adresu by se měly klasifikovat jako entita domény.

Osoba s jméno a příjmení je obvykle entita, protože uživatel má identitu, i v případě, že jméno a příjmení shoduje s jinou sadu hodnot, jako třeba když tyto názvy také odkazuje na jinou osobu.

Hodnota objekty jsou obtížné spravovat v relačních databází a ORMs jako EF, zatímco v dokumentu zaměřené na konkrétní databáze, které jsou jednodušší k implementaci a použití.

#### <a name="additional-resources"></a>Další zdroje

-   **Martin Fowler. Vzor hodnota objektu**
    [*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)

-   **Hodnota objektu**
    [*http://deviq.com/value-object/*](http://deviq.com/value-object/)

-   **Hodnota objekty v vývoje řízeného testováním**
    [*https://leanpub.com/tdd-ebook/read\#leanpub-auto-value-objects*](https://leanpub.com/tdd-ebook/read#leanpub-auto-value-objects)

-   **Zařízení Evans Erica. Řízené domény návrhu: Boji se složitostí při vysílat softwaru.** (Sešit; zahrnuje diskuzi o hodnotu objekty) [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

### <a name="the-aggregate-pattern"></a>Agregační vzor

Model domény obsahuje clustery různých datových entit a procesy, které můžete řídit důležité oblasti funkce, například pořadí platbu nebo z inventáře. Podrobnějšího jednotka DDD je agregaci, která popisuje cluster nebo skupinu entit a chování, které mohou být považovány za získá na ucelenosti jednotku.

Obvykle definujete agregaci podle transakcí, které potřebujete. Classic příkladem je pořadí, které obsahuje také pořadí položek seznamu. Položku pořadí bude obvykle entity. Ale bude podřízené entity v rámci pořadí agregace, který bude také obsahovat entity pořadí jako jeho kořenový entitu, obvykle nazývá agregační root.

Identifikace agregace může být složité. Agregace je pro skupinu objektů, které musí být konzistentní společně, ale nemůže právě vyberte skupinu objektů a označovat je agregace. Musí začínat koncept domény a vezměte v úvahu entitami, které se používají v nejběžnější transakce související pro daný koncept. Tyto entity, které musí být stavu transakční konzistence se, co tvoří agregace. Zamyšlení operací transakce je pravděpodobně nejlepší způsob, jak identifikovat agregace.

### <a name="the-aggregate-root-or-root-entity-pattern"></a>Vzor agregační kořenovou nebo kořenové Entity

Agregace se skládá z nejméně jedna entita: agregační kořenový adresář, označovaný taky jako kořenové entity nebo primární entity. Kromě toho může mít více podřízených entit a hodnota objekty s všechny entity a objekty, které pracují společně k implementaci požadované chování a transakce.

Účelem agregační kořenové je zajištění konzistence agregace; je nutné pouze vstupní bod pro aktualizace agregace prostřednictvím metody nebo operace v souhrnném kořenová třída. Entity v rámci agregace pouze prostřednictvím kořenu agregační měli provádět změny. Je na agregaci konzistence ochrany, vezme v úvahu výstupních podmínek a konzistence pravidla, která může být nutné v souladu se ve vašem agregace. Pokud změníte podřízený objekt entity nebo hodnota nezávisle, kořenu agregační nelze zajistěte, aby byl agregace v platném stavu. Je jako tabulku s přijít větev. Údržba konzistence je hlavním účelem agregační kořenu.

Obrázek 9 – 9 uvidíte ukázka agregace jako kupujících agregační, která obsahuje jednu entitu (Kořenová agregační kupujících). Agregace pořadí obsahuje více entit a objekt hodnoty.

![](./media/image10.png)

**Obrázek 9 – 9**. Příklad agregace s více neboli jednotlivých entit

Všimněte si, že agregace kupujících může mít další podřízené entity, v závislosti na vaší domény, stejně jako v řazení mikroslužbu v eShopOnContainers odkaz na aplikaci. Obrázek 9 – 9 právě znázorňuje případ, ve kterém má kupující jedna entita, jako příklad agregaci, která obsahuje jenom agregační root.

Abyste mohli udržovat oddělené agregací a zachovat zřetelnými hranicemi mezi nimi, je dobrým zvykem v modelu DDD domény tak, aby zakázala přímé navigace mezi agregace, které mají pouze pole cizí klíč (Cizíklíč), jak jsou implementované ve [ Řazení modelu domény mikroslužbu](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs) v eShopOnContainers. Entity pořadí pouze obsahuje pole, cizího klíče pro odběratele, ale ne základní EF navigační vlastnost, jak je znázorněno v následujícím kódu:

```csharp
public class Order : Entity, IAggregateRoot
{
    private DateTime _orderDate;
    public Address Address { get; private set; }
    private int? _buyerId; //FK pointing to a different aggregate root
    public OrderStatus OrderStatus { get; private set; }
    private readonly List<OrderItem> _orderItems;
    public IReadOnlyCollection<OrderItem> OrderItems => _orderItems;
    // ... Additional code
}
```

Identifikace a práci s agregace vyžaduje výzkum a prostředí. Další informace najdete v seznamu následující další prostředky.

#### <a name="additional-resources"></a>Další zdroje

-   **Vaughn Vernon. Efektivní návrh agregace - část I: modelování jeden agregace**
    [*https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD\_COMMUNITY\_ESSAY\_AGGREGATES\_PART\_1.pdf*](https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_1.pdf)

-   **Vaughn Vernon. Efektivní agregační návrh – část II: Provádění agregací pracovní společně**
    *<https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_2.pdf> *

-   **Vaughn Vernon. Efektivní agregační návrh – část III: Získání přehledu prostřednictvím zjišťování**
    *<https://vaughnvernon.co/wordpress/wp-content/uploads/2014/10/DDD_COMMUNITY_ESSAY_AGGREGATES_PART_3.pdf> *

-   **Sergey Grybniak. Vzory návrhu taktické DDD**
    [*https://www.codeproject.com/Articles/1164363/Domain-Driven-Design-Tactical-Design-Patterns-Part*](https://www.codeproject.com/Articles/1164363/Domain-Driven-Design-Tactical-Design-Patterns-Part)

-   **Jan Ryšánková. Vývoj transakční Mikroslužeb používající agregované hodnoty**
    [*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-1-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-1-richardson)

-   **DevIQ. Agregační vzor**
    [*http://deviq.com/aggregate-pattern/*](http://deviq.com/aggregate-pattern/)


>[!div class="step-by-step"]
[Předchozí](ddd-oriented-microservice.md)
[další](net-core-microservice-domain-model.md)
