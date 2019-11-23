---
title: Návrh doménového modelu mikroslužby
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Princip klíčových konceptů při navrhování doménového modelu orientovaného na DDD
ms.date: 10/08/2018
ms.openlocfilehash: 3a02059064305ca148b7909923e2f51e60ee54d5
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73737383"
---
# <a name="design-a-microservice-domain-model"></a>Návrh doménového modelu mikroslužeb

*Definujte jeden model domény s bohatou vazbou pro jednotlivé obchodní mikroslužby nebo ohraničený kontext.*

Vaším cílem je vytvořit jeden soudržný doménový model pro jednotlivé obchodní mikroslužby nebo ohraničený kontext (BC). Mějte na paměti, že v některých případech může být BC nebo obchodní mikroslužba tvořená několika fyzickými službami, které sdílejí jeden doménový model. Model domény musí zachytit pravidla, chování, obchodní jazyk a omezení jednoho vázaného kontextu nebo obchodního mikroslužby, který představuje.

## <a name="the-domain-entity-pattern"></a>Vzor entity domény

Entity představují objekty domény a jsou primárně definovány jejich identitou, kontinuitou a stálostí v průběhu času, a nikoli pouze pomocí atributů, které je tvoří. Eric Evans říká, že "objekt primárně definovaný jeho identitou se nazývá entita." Entity jsou v modelu domény velmi důležité, protože jsou základem pro model. Proto byste je měli pečlivě identifikovat a navrhovat.

*Identita entity může protínat více mikroslužeb nebo ohraničených kontextů.*

Stejná identita (tj. stejná hodnota `Id`, i když možná není stejná doménová entita), může být modelována v rámci několika ohraničených kontextů nebo mikroslužeb. To však neznamená, že stejná entita se stejnými atributy a logikou by byla implementována ve více ohraničených kontextech. Místo toho entity v každém ohraničeném kontextu omezují jejich atributy a chování na ty, které jsou požadovány v doméně daného vázaného kontextu.

Například entita Buyer může mít většinu atributů osoby, které jsou definovány v entitě uživatele v profilu nebo mikroslužbě identity, včetně identity. Entita kupující v rámci řazení mikroslužeb ale může mít méně atributů, protože pouze určitá data nákupčího se vztahují k procesu Order. Kontext každého mikroslužby nebo vázaného kontextu má vliv na svůj doménový model.

*Entity domény musí implementovat chování společně s implementací datových atributů.*

Entita domény v DDD musí implementovat logiku domény nebo chování související s daty entity (objekt, ke kterému se přistupovala v paměti). Například jako součást třídy entity Order musíte mít obchodní logiku a operace implementované jako metody pro úlohy, jako je například přidání položky objednávky, ověření dat a celkový výpočet. Metody entity se postará o invariantování a pravidla entity místo toho, aby se tato pravidla rozšířila napříč aplikační vrstvou.

Obrázek 7-8 ukazuje doménovou entitu, která implementuje nejen atributy dat, ale operace nebo metody s relační logikou domény.

![Diagram znázorňující vzor entity domény](./media/microservice-domain-model/domain-entity-pattern.png)

**Obrázek 7-8**. Příklad návrhu entity domény, který implementuje chování dat a chování

Entita doménového modelu implementuje chování prostřednictvím metod, to znamená, že se nejedná o model "anemic". Samozřejmě, někdy můžete mít entity, které neimplementují žádnou logiku jako součást třídy entity. K tomu může dojít v případě podřízených entit v rámci agregace, pokud podřízená entita nemá žádnou speciální logiku, protože většina logiky je definována v agregačním kořenu. Pokud máte složitou mikroslužbu, která má spoustu logiky implementovanou v třídách služby místo v doménových entitách, mohli byste být do modelu domény anemic, který je vysvětlen v následující části.

### <a name="rich-domain-model-versus-anemic-domain-model"></a>Model domény s bohatou doménou vs anemic

V jeho příspěvku [AnemicDomainModel](https://martinfowler.com/bliki/AnemicDomainModel.html)Novák Fowlera popisuje model domény anemic tímto způsobem:

Základním příznakem doménového modelu Anemic je, že první růžová vypadá jako skutečná věc. K dispozici jsou objekty, které jsou pojmenovány po podstatných podstatných prostorech v doméně, a tyto objekty jsou propojeny s bohatými vztahy a strukturou, které mají skutečné doménové modely. K zachycení dojde, když se podíváte na chování a zjistíte, že se špatně jakékoliv chování na těchto objektech, což znamená, že je málo více než penalty mechanismů getter a setter.

Když použijete doménový model anemic, budou se tyto datové modely používat ze sady objektů služby (tradičně pojmenované *obchodní vrstvy*), které zachytí veškerou doménu nebo obchodní logiku. Obchodní vrstva je umístěná nad datovým modelem a používá datový model stejně jako data.

Model domény anemic je jenom návrhem procedurálního stylu. Objekty entit Anemic nejsou reálné objekty, protože nemají chování (metody). Uchovávají pouze vlastnosti dat, takže se nejedná o objektově orientovaný návrh. Vložením veškerého chování do objektů služby (obchodní vrstva), které v podstatě končí [Spaghetti kódem](https://en.wikipedia.org/wiki/Spaghetti_code) nebo [skripty transakcí](https://martinfowler.com/eaaCatalog/transactionScript.html), a proto ztratíte výhody, které poskytuje doménový model.

Bez ohledu na to, jestli je váš mikroslužba nebo ohraničený kontext velmi jednoduchý (služba CRUD), model domény anemic ve formě objektů entity, které mají pouze vlastnosti dat, může být dostatečně dobrý a nemusí se jednat o implementaci složitějších vzorů DDD. V takovém případě bude jednoduše model trvalosti, protože jste záměrně vytvořili entitu s pouze daty pro účely CRUD.

To je důvod, proč architektury mikroslužeb jsou ideální pro přístup s více architekturami v závislosti na jednotlivých ohraničených kontextech. Například v eShopOnContainers pořadí mikroslužeb implementuje vzory DDD, ale katalogová služba, která je jednoduchou službou CRUD, ne.

Někteří lidé říkají, že model domény anemic je anti-Pattern. Ve skutečnosti záleží na tom, co implementujete. Pokud je mikroslužba, kterou vytváříte, dostatečně jednoduchá (například služba CRUD), pak za doménovým modelem anemic se nejedná o anti-Pattern. Pokud ale potřebujete řešit složitost domény mikroslužeb, která má mnoho stále se měnících obchodních pravidel, model domény anemic může být antipattern pro daný kontext mikroslužeb nebo vázaného kontextu. V takovém případě může mít návrh jako bohatý model s entitami, které obsahují data a chování, i implementaci dalších vzorků DDD (agregované hodnoty, objekty hodnot atd.) pro dlouhodobou úspěšnost této mikroslužby.

#### <a name="additional-resources"></a>Další materiály a zdroje informací

- **DevIQ. \ doménových entit**
  <https://deviq.com/entity/>

- **Martin Fowlera. \ doménového modelu**
  <https://martinfowler.com/eaaCatalog/domainModel.html>

- **Martin Fowlera. \ Anemic doménového modelu**
  <https://martinfowler.com/bliki/AnemicDomainModel.html>

### <a name="the-value-object-pattern"></a>Vzorec objektu hodnoty

Jak si poznamenal Eric Evans, "mnoho objektů nemá koncepční identitu. Tyto objekty popisují určité charakteristiky věci. "

Entita vyžaduje identitu, ale v systému existuje mnoho objektů, které nefungují jako vzor objektu Value. Objekt hodnoty je objekt bez koncepční identity, který popisuje aspekt domény. Jedná se o objekty, které vytváříte, aby představovaly prvky návrhu, které se jen dočasně týkají. Záleží na *tom, co* jsou, bez toho, *kdo* jsou. Příklady zahrnují čísla a řetězce, ale mohou být také koncepty vyšší úrovně, jako jsou skupiny atributů.

Něco, co je entita v mikroslužbě, nemusí být entitou v jiné mikroslužbě, protože v druhém případě může mít ohraničený kontext jiný význam. Například adresa v aplikaci elektronického obchodování nemusí mít vůbec identitu, protože může představovat jenom skupinu atributů profilu zákazníka pro osobu nebo firmu. V takovém případě by měla být adresa klasifikována jako objekt hodnoty. V aplikaci pro elektrickou společnost Power Utility ale může být adresa zákazníka pro obchodní doménu důležitá. Adresa proto musí mít identitu, aby se fakturační systém mohl přímo propojit s adresou. V takovém případě by měla být adresa klasifikována jako entita domény.

Osoba, která má jméno a příjmení, je obvykle entita, protože osoba má identitu, a to i v případě, že se název a příjmení shodují s jinou sadou hodnot, například pokud se tyto názvy vztahují také na jinou osobu.

Objekty hodnot jsou obtížné spravovat v relačních databázích a ORMs jako EF, zatímco v dokumentu orientovaném na dokumenty se snadněji implementují a používají.

EF Core 2,0 obsahuje funkci [vlastněné entity](https://devblogs.microsoft.com/dotnet/announcing-entity-framework-core-2-0/#owned-entities-and-table-splitting) , která usnadňuje zpracování hodnotových objektů, jak se dozvíme později v podrobnostech.

#### <a name="additional-resources"></a>Další materiály a zdroje informací

- **Martin Fowlera. \ – vzor objektu hodnoty**
  <https://martinfowler.com/bliki/ValueObject.html>

- **Hodnota objektu** \
  <https://deviq.com/value-object/>

- **Objekty hodnot v \ vývoje řízených testem**
  [https://leanpub.com/tdd-ebook/read\#leanpub-auto-value-objects](https://leanpub.com/tdd-ebook/read#leanpub-auto-value-objects)

- **Eric Evans. Návrh založený na doméně: řešení složitosti na srdce softwaru.** (Kniha; obsahuje diskuzi o objektech hodnot) \
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

### <a name="the-aggregate-pattern"></a>Agregovaný vzor

Doménový model obsahuje clustery různých datových entit a procesů, které mohou řídit významnou oblast funkčnosti, jako je například plnění objednávky nebo inventarizace. Podrobná jednotka DDD je agregovaná, která popisuje cluster nebo skupinu entit a chování, které lze považovat za soudržnou jednotku.

Agregaci obvykle definujete v závislosti na transakcích, které potřebujete. Klasický příklad je objednávka, která obsahuje také seznam položek objednávek. Položka objednávky obvykle bude entitou. Ale bude podřízenou entitou v rámci agregace pořadí, která bude také obsahovat entitu Order jako její kořenovou entitu, která se obvykle označuje jako agregovaná kořenová.

Identifikace agregací může být pevná. Agregace je skupina objektů, které musí být konzistentní společně, ale nelze vybrat pouze skupinu objektů a označit ji jako agregaci. Musíte začít s konceptem domény a zamyslete se nad entitami, které se používají v nejběžnějších transakcích souvisejících s tímto konceptem. Ty entity, které je potřeba vyhodnotit jako nevhodné, jsou, které tvoří agregaci. Nejlepším způsobem, jak identifikovat agregace, je pravděpodobně myslím na operace s transakcemi.

### <a name="the-aggregate-root-or-root-entity-pattern"></a>Model agregované kořenové nebo kořenové entity

Agregace se skládá z aspoň jedné entity: agregační kořen, označovaný také jako kořenová entita nebo primární entita. Kromě toho může mít více podřízených entit a objektů hodnot se všemi entitami a objekty, které pracují společně pro implementaci požadovaných chování a transakcí.

Účelem agregovaného kořene je zajistit konzistenci agregace; měl by být jediným vstupním bodem pro aktualizace agregace prostřednictvím metod nebo operací v agregační kořenové třídě. Změny entit v rámci agregace byste měli provádět pouze prostřednictvím agregovaného kořene. Je to modul pro sjednocení konzistence agregace a zvažuje všechna pravidla invariantní a konzistence, která může být potřeba splnit v agregaci. Pokud změníte podřízenou entitu nebo objekt hodnoty nezávisle, agregovaný kořen nemůže zajistit, aby agregace byla v platném stavu. Vypadá to, že tabulka s volnou nožkou. Zachování konzistence je hlavním účelem agregovaného kořene.

Na obrázku 7-9 vidíte agregace ukázek, jako je agregace nákupčího, která obsahuje jednu entitu (agregovaný kořenový nákupčí). Agregace objednávky obsahuje více entit a objektů hodnot.

![Diagram, který porovnává agregaci kupující a agregaci objednávky](./media/microservice-domain-model/buyer-order-aggregate-pattern.png)

**Obrázek 7-9**. Příklad agregací s více nebo jednou entitou

Doménový model DDD se skládá z agregací, agregace může mít pouze jednu entitu a může obsahovat také objekty hodnot. Počítejte s tím, že agregace nákupčího může mít další podřízené entity v závislosti na vaší doméně, stejně jako při řazení mikroslužby v referenční aplikaci eShopOnContainers. Obrázek 7-9 pouze ukazuje případ, ve kterém má kupující jednu entitu, jako příklad agregace, která obsahuje pouze agregovanou kořenovou hodnotu.

Aby se zachovalo oddělení agregací a mělo mezi nimi jasné hranice, je dobrým zvykem, aby se zakázala přímá navigace mezi agregacemi a měla by se používat pole cizího klíče (FK), [jak je implementované](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs) v eShopOnContainers. Entita Order má pouze pole FK pro kupující, ale ne EF Core navigační vlastnost, jak je znázorněno v následujícím kódu:

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

Identifikace a práce s agregacemi vyžaduje výzkum a možnosti. Další informace najdete v následujících dalších seznamech prostředků.

#### <a name="additional-resources"></a>Další materiály a zdroje informací

- **Vaughn Vernon. Účinný agregovaný návrh – část I: modelování jedné agregace** (z <http://dddcommunity.org/>) \
  <http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_1.pdf>

- **Vaughn Vernon. Účinný agregovaný návrh – část II: vytváření agregačních prvků společně** (z <http://dddcommunity.org/>) \
  <http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf>

- **Vaughn Vernon. Efektivní agregovaná Návrhová část III: získání přehledu prostřednictvím zjišťování** (z <http://dddcommunity.org/>) \
  <http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_3.pdf>

- **Sergeje Grybniak. Vzory návrhu DDD taktické** \
  <https://www.codeproject.com/Articles/1164363/Domain-Driven-Design-Tactical-Design-Patterns-Part>

- **Chris Richardson. Vývoj transakčních mikroslužeb pomocí agregací** \
  <https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-1-richardson>

- **DevIQ. Agregační vzor** \
  <https://deviq.com/aggregate-pattern/>

>[!div class="step-by-step"]
>[Předchozí](ddd-oriented-microservice.md)
>[Další](net-core-microservice-domain-model.md)
