---
title: Návrh doménového modelu mikroslužby
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Seznamte se s klíčovými koncepty při navrhování modelu domény orientovaného na DDD.
ms.date: 01/30/2020
ms.openlocfilehash: 628fb5c76362ec8f48367b3d69d16ea6ebd24f09
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77502322"
---
# <a name="design-a-microservice-domain-model"></a>Návrh modelu domény mikroslužeb

*Definujte jeden model bohaté domény pro každou obchodní mikroslužbu nebo ohraničený kontext.*

Vaším cílem je vytvořit jeden soudržný model domény pro každou obchodní mikroslužbu nebo ohraničený kontext (BC). Mějte však na paměti, že bc nebo obchodní mikroslužby může být někdy skládá z několika fyzických služeb, které sdílejí model jedné domény. Model domény musí zachytit pravidla, chování, obchodní jazyk a omezení jednoho ohraničeného kontextu nebo obchodní mikroslužby, které představuje.

## <a name="the-domain-entity-pattern"></a>Vzor entity domény

Entity představují objekty domény a jsou primárně definovány jejich identitou, kontinuitou a trvalostí v průběhu času, a nikoli pouze atributy, které je tvoří. Jak říká Eric Evans, "objekt primárně definovaný jeho identitou se nazývá entita." Entity jsou velmi důležité v modelu domény, protože jsou základem pro model. Proto byste je měli pečlivě identifikovat a navrhnout.

*Identita entity může procházet více mikroslužeb nebo ohraničené kontexty.*

Stejná identita (to znamená, že stejná `Id` hodnota, i když možná není stejná entita domény) lze modelovat napříč více ohraničené kontexty nebo mikroslužeb. To však neznamená, že stejná entita se stejnými atributy a logikou by byla implementována ve více ohraničených kontextech. Místo toho entity v každém ohraničeném kontextu omezují jejich atributy a chování na ty, které jsou požadovány v doméně ohraničeného kontextu.

Například entita kupujícího může mít většinu atributů osoby, které jsou definovány v entitě uživatele v mikroslužbě profilu nebo identity, včetně identity. Ale entita kupujícív objednávání mikroslužby může mít méně atributů, protože pouze určitá data kupujícího souvisí s procesem objednávky. Kontext každé mikroslužby nebo ohraničený kontext má vliv na jeho model domény.

*Entity domény musí implementovat chování kromě implementace atributů dat.*

Entita domény v DDD musí implementovat logiku domény nebo chování související s daty entity (objekt přístupný v paměti). Například jako součást třídy entity objednávky musíte mít obchodní logiku a operace implementovány jako metody pro úkoly, jako je přidání položky objednávky, ověření dat a celkový výpočet. Metody entity se starají o invarianty a pravidla entity namísto rozložení těchto pravidel na aplikační vrstvu.

Obrázek 7-8 znázorňuje entitu domény, která implementuje nejen atributy dat, ale i operace nebo metody s logikou související domény.

![Diagram znázorňující vzor entity domény.](./media/microservice-domain-model/domain-entity-pattern.png)

**Obrázek 7-8**. Příklad návrhu entity domény implementující data plus chování

Entita modelu domény implementuje chování prostřednictvím metod, to znamená, že není "chudokrevný" model. Samozřejmě někdy můžete mít entity, které neimplementují žádnou logiku jako součást třídy entity. K tomu může dojít v podřízených entitách v rámci agregace, pokud podřízená entita nemá žádnou zvláštní logiku, protože většina logiky je definována v agregačním kořenovém adresáři. Pokud máte komplexní mikroslužbu, která má velké množství logiky implementované ve třídách služby namísto v entitách domény, může být spadají do modelu anemické domény, je vysvětleno v následující části.

### <a name="rich-domain-model-versus-anemic-domain-model"></a>Bohatý model domény versus model chudokrevné domény

Ve svém [příspěvku AnemicDomainModel](https://martinfowler.com/bliki/AnemicDomainModel.html), Martin Fowler popisuje anemický model domény tímto způsobem:

Základním příznakem anemické domény Model je, že na první červenat to vypadá jako skutečná věc. Existují objekty, mnoho pojmenovaných po substivatelech v prostoru domény a tyto objekty jsou spojeny s bohatými vztahy a strukturou, které mají skutečné modely domén. Úlovek přichází, když se podíváte na chování, a uvědomíte si, že tam je téměř žádné chování na tyto objekty, což je o něco více než pytle getters a setters.

Samozřejmě, když použijete model chudokrevné domény, tyto datové modely budou použity ze sady objektů služby (tradičně pojmenovaných *obchodní vrstva),* které zachycují všechny domény nebo obchodní logiku. Obchodní vrstva je na datovém modelu a používá datový model stejně jako data.

Anemický model domény je jen procedurální styl designu. Objekty anemické entity nejsou skutečné objekty, protože postrádají chování (metody). Uchovávají pouze vlastnosti dat, a proto není objektově orientovaným návrhem. Vložením všech chování do objektů služby (obchodní vrstva) v podstatě skončíte s [špagetovým kódem](https://en.wikipedia.org/wiki/Spaghetti_code) nebo [transakčními skripty](https://martinfowler.com/eaaCatalog/transactionScript.html), a proto ztratíte výhody, které poskytuje model domény.

Bez ohledu na to, pokud vaše mikroslužeb nebo ohraničený kontext je velmi jednoduché (služba CRUD), anemické doménové modely ve formě objektů entity s pouze vlastnosti dat může být dost dobré a nemusí být vhodné implementovat složitější vzory DDD. V takovém případě to bude jednoduše model trvalosti, protože jste záměrně vytvořili entitu s pouze daty pro účely CRUD.

To je důvod, proč architektury mikroslužeb jsou ideální pro vícearchitektonický přístup v závislosti na každém ohraničené kontextu. Například v eShopOnContainers objednávání mikroslužby implementuje DDD vzory, ale mikroslužby katalogu, což je jednoduchá služba CRUD, není.

Někteří lidé říkají, že anemický model domény je anti-vzor. To opravdu záleží na tom, co implementujete. Pokud mikroslužbu, kterou vytváříte, je dostatečně jednoduchá (například služba CRUD), po modelu anemické domény není anti-pattern. Pokud však potřebujete řešit složitost domény mikroslužeb, která má mnoho neustále se měnících obchodních pravidel, může být model chudokrevné domény anti-vzor pro tuto mikroslužbu nebo ohraničený kontext. V takovém případě jeho návrh jako bohatý model s entitami obsahujícími data a chování, stejně jako implementace dalších vzorů DDD (agregace, hodnotové objekty atd.) může mít obrovské výhody pro dlouhodobý úspěch takové mikroslužby.

#### <a name="additional-resources"></a>Další zdroje

- **DevIQ. Entita domény** \
  <https://deviq.com/entity/>

- **Martin Fowler. Model domény** \
  <https://martinfowler.com/eaaCatalog/domainModel.html>

- **Martin Fowler. Annemic doménový model** \
  <https://martinfowler.com/bliki/AnemicDomainModel.html>

### <a name="the-value-object-pattern"></a>Vzor Objekt hodnoty

Jak poznamenal Eric Evans: "Mnoho objektů nemá koncepční identitu. Tyto objekty popisují určité vlastnosti věci."

Entita vyžaduje identitu, ale existuje mnoho objektů v systému, které nemají, stejně jako vzor Value Object. Objekt hodnoty je objekt bez konceptuální identity, který popisuje aspekt domény. Jedná se o objekty, které konkretizovat představují prvky návrhu, které se týkají pouze dočasně. Záleží ti na tom, *co* jsou, ne *na tom, kdo* jsou. Příklady zahrnují čísla a řetězce, ale mohou být také koncepty vyšší úrovně, jako jsou skupiny atributů.

Něco, co je entita v mikroslužeb nemusí být entita v jiné mikroslužby, protože v druhém případě ohraničené kontextu může mít jiný význam. Například adresa v aplikaci elektronického obchodu nemusí mít identitu vůbec, protože může představovat pouze skupinu atributů profilu zákazníka pro osobu nebo společnost. V takovém případě by měla být adresa klasifikována jako objekt hodnoty. V aplikaci pro energetickou společnost by však mohla být adresa zákazníka důležitá pro obchodní doménu. Proto musí mít adresa identitu, aby fakturační systém mohl být přímo propojen s adresou. V takovém případě by měla být adresa klasifikována jako entita domény.

Osoba se jménem a příjmením je obvykle subjektem, protože osoba má totožnost, a to i v případě, že se jméno a příjmení shodují s jinou sadou hodnot, například pokud se tato jména vztahují i na jinou osobu.

Hodnotové objekty je obtížné spravovat v relačních databázích a ORM, jako je entity Framework (EF), zatímco v databázích orientovaných na dokumenty se snadněji implementují a používají.

EF Core 2.0 a novější verze zahrnují [funkci Vlastněných entit,](https://devblogs.microsoft.com/dotnet/announcing-entity-framework-core-2-0/#owned-entities-and-table-splitting) která usnadňuje zpracování hodnotových objektů, jak uvidíme podrobně později.

#### <a name="additional-resources"></a>Další zdroje

- **Martin Fowler. Vzor objektu hodnoty** \
  <https://martinfowler.com/bliki/ValueObject.html>

- **Objekt hodnoty** \
  <https://deviq.com/value-object/>

- **Hodnotové objekty ve vývoji řízeném testem** \
  [https://leanpub.com/tdd-ebook/read\#leanpub-auto-value-objects](https://leanpub.com/tdd-ebook/read#leanpub-auto-value-objects)

- **Eric Evans. Návrh řízený doménou: Řešení složitosti v srdci softwaru.** (Kniha; obsahuje diskusi o hodnotových objektech) \
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

### <a name="the-aggregate-pattern"></a>Agregační vzor

Model domény obsahuje clustery různých datových entit a procesů, které mohou řídit významnou oblast funkčnosti, jako je plnění objednávek nebo zásoby. Více jemně odstupňované Jednotky DDD je agregace, která popisuje cluster nebo skupinu entit a chování, které lze považovat za soudržnou jednotku.

Obvykle definujete agregaci na základě transakcí, které potřebujete. Klasickým příkladem je objednávka, která obsahuje také seznam položek objednávky. Zboží objednávky bude obvykle entita. Ale bude podřízená entita v rámci agregace objednávky, která bude také obsahovat entitu objednávky jako její kořenovou entitu, obvykle nazývanou agregační kořen.

Identifikace agregátů může být těžká. Agregace je skupina objektů, které musí být konzistentní dohromady, ale nelze pouze vybrat skupinu objektů a označit je agregaci. Musíte začít s konceptem domény a přemýšlet o entitách, které se používají v nejběžnějších transakcích souvisejících s tímto konceptem. Tyto entity, které musí být transakce konzistentní jsou to, co tvoří agregaci. Přemýšlení o transakčních operacích je pravděpodobně nejlepší způsob, jak identifikovat agregáty.

### <a name="the-aggregate-root-or-root-entity-pattern"></a>Vzor agregované kořenové nebo kořenové entity

Agregace se skládá alespoň z jedné entity: agregační kořen, také nazývaný kořenová entita nebo primární entita. Navíc může mít více podřízených entit a hodnotových objektů, přičemž všechny entity a objekty spolupracují na implementaci požadovaného chování a transakcí.

Účelem agregovaného kořene je zajistit konzistenci agregátu; měl by být jediným vstupním bodem pro aktualizace agregace prostřednictvím metod nebo operací v agregované kořenové třídě. Změny entit v rámci agregace byste měli provádět pouze prostřednictvím agregačního kořenového adresáře. Je agregát konzistence opatrovník, s ohledem na všechny invariants a pravidla konzistence, které budete muset dodržovat v agregátu. Pokud změníte podřízenou entitu nebo objekt hodnoty nezávisle, agregační kořen nemůže zajistit, že agregace je v platném stavu. Bylo by to jako stůl s volnou nohou. Zachování konzistence je hlavním účelem agregačníkořen.

Na obrázku 7-9 můžete vidět ukázkové agregace, jako je agregace kupujícího, která obsahuje jednu entitu (agregační kořenový kupující). Agregace pořadí obsahuje více entit a objekt hodnoty.

![Diagram porovnání agregace kupujícího a agregace objednávky.](./media/microservice-domain-model/buyer-order-aggregate-pattern.png)

**Obrázek 7-9**. Příklad agregací s více nebo jednotlivými entitami

Model domény DDD se skládá z agregace, agregace může mít pouze jednu entitu nebo více a může také obsahovat objekty hodnoty. Všimněte si, že Kupující agregace může mít další podřízené entity, v závislosti na vaší doméně, stejně jako v objednávání mikroslužby v referenční aplikaci eShopOnContainers. Obrázek 7-9 pouze ilustruje případ, ve kterém kupující má jednu entitu, jako příklad agregátu, který obsahuje pouze agregační kořen.

Chcete-li zachovat oddělení agregace a zachovat jasné hranice mezi nimi, je vhodné v modelu domény DDD zakázat přímou navigaci mezi agregacemi a pouze s polem cizího klíče (FK), jak je implementováno v [modelu domény mikroslužeb](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs) v eShopOnContainers. Entita Objednávka má pouze pole FK pro kupujícího, ale ne navigační vlastnost EF Core, jak je znázorněno v následujícím kódu:

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

Identifikace a práce s agregáty vyžaduje výzkum a zkušenosti. Další informace naleznete v následujícím seznamu Další zdroje.

#### <a name="additional-resources"></a>Další zdroje

- **Vaughn Vernon, to je můj zástupce. Efektivní agregační design - část I: Modelování jednoho agregátu** (od <http://dddcommunity.org/>) \
  <http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_1.pdf>

- **Vaughn Vernon, to je můj zástupce. Efektivní agregační design - část II: Tvorba agregáty pracovat společně** (od <http://dddcommunity.org/>) \
  <http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf>

- **Vaughn Vernon, to je můj zástupce. Efektivní agregační design - část III: Získání Insight Prostřednictvím Discovery** (od <http://dddcommunity.org/>) \
  <http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_3.pdf>

- **Sergej Grybniak. DDD Taktické návrhové vzory** \
  <https://www.codeproject.com/Articles/1164363/Domain-Driven-Design-Tactical-Design-Patterns-Part>

- **Chrise Richardsona. Vývoj transakčních mikroslužeb pomocí agregací** \
  <https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-1-richardson>

- **DevIQ. Agregační vzor** \
  <https://deviq.com/aggregate-pattern/>

>[!div class="step-by-step"]
>[Předchozí](ddd-oriented-microservice.md)
>[další](net-core-microservice-domain-model.md)
