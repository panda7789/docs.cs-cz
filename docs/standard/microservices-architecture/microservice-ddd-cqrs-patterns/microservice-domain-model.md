---
title: Návrh doménového modelu mikroslužby
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Při návrhu modelu domény orientované na DDD porozumět klíčovým koncepcím.
ms.date: 10/08/2018
ms.openlocfilehash: c6d2e84189ff542a2ed4c584c4a47bf7bf0e946a
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644206"
---
# <a name="design-a-microservice-domain-model"></a>Návrh doménového modelu mikroslužby

*Definujte jeden bohaté doménový model pro každou obchodní mikroslužeb nebo ohraničená kontextu.*

Vaším cílem je vytvořit jeden získá na ucelenosti doménový model pro každou obchodní mikroslužeb nebo ohraničená kontextu (BC). Mějte na paměti, ale který BC nebo obchodní mikroslužeb může někdy skládá z několika fyzických služeb, které sdílejí jeden doménový model. Doménový model nutné zaznamenat pravidla, chování, obchodní jazyka a omezení jednotlivý kontext ohraničená nebo obchodní mikroslužeb, která představuje.

## <a name="the-domain-entity-pattern"></a>Vzor entita domény

Entity reprezentaci objektů domény a jsou jejich identitu, kontinuity podnikových procesů a přetrvávání v čase a ne jenom atributy, které tvoří je primárně definováno. Jak říká Eric Evans "primárně definováno svoji identitu objektu je volána Entity." Entity jsou velmi důležité pro doménový model, protože jsou základ pro model. Proto byste identifikovat a je pečlivě Navrhněte.

*Entity identity můžete napříč několika mikroslužbami nebo ohraničených kontextech.*

Stejnou identitu (to znamená, že stejné `Id` hodnoty, i když možná není stejné domény entity) můžete modelovat napříč více ohraničených kontextech nebo mikroslužeb. Ale, neznamená, že stejnou entitu, se stejnými atributy a logiky by implementovat v několika kontextech omezená. Místo toho entity v jednotlivých ohraničených kontextech omezit jejich atributy a chování na tyto požadované v tomto ohraničená kontextu domény.

Kupující může obsahovat většinu atributů osoby, které jsou definovány v entitě uživatele v profilu nebo identity mikroslužeb, včetně identitu. Ale kupujících entita v pořadí mikroslužeb může mít méně atributy, protože pouze určité kupujících dat má vztah k proces zpracování objednávky. Kontext jednotlivých mikroslužeb nebo ohraničená kontext ovlivňuje jeho doménový model.

*Domény entity musí implementovat chování kromě provádění atributy data.*

Entita domény v DDD musí implementovat logiku domény nebo chování týkající se dat entity (objekt, kterého v paměti). Například jako součást třídu entity pořadí potřebujete obchodní logiky a implementovat jako metody pro úlohy, jako je přidání objednávky položku, ověření dat a výpočet celkového počtu operací. Metody entity zajistíme výstupních podmínek a pravidla entity namísto toho, aby tato pravidla rozloženy aplikační vrstvu.

Obrázek 7 – 8 ukazuje domény entity, která implementuje nejen datové atributy, ale operací a metod s logikou související domény.

![Entity model domény implementuje chování pomocí metod, tedy není "anemic" modelu.](./media/image9.png)

**Obrázek 7. a 8**. Příklad implementace data a chování entit návrhu domény

Samozřejmě někdy může mít entity, které nejsou implementovat jakoukoli logiku v rámci třídy entity. V podřízené entity v rámci agregace tomu může dojít, pokud podřízené entity nemá nějakou zvláštní logiku, protože většina logiku je definováno v kořenu agregace. Pokud máte složité mikroslužeb, která má spoustu logiky implementovány v třídách service místo v entitách domény, může být spadající do anemic doménový model, je vysvětleno v následující části.

### <a name="rich-domain-model-versus-anemic-domain-model"></a>Model domény ve formátu RTF oproti anemic doménový model

V jeho příspěvku [AnemicDomainModel](https://martinfowler.com/bliki/AnemicDomainModel.html), Martina Fowlera popisuje anemic doménový model tímto způsobem:

Základní příznakem Anemic doménový Model je, že v první blush to vypadá Opravdová věc. Existují objekty, řada s názvem po podstatných jmen v oboru domény a tyto objekty jsou spojeny s formátovaným vztahy a struktury, která má hodnotu true doménových modelů. Catch spolu, když se podíváte na chování a zjistíte, že je na tyto objekty téměř jakékoli chování, takže je trochu více než kontejnery objektů a dat z metody getter a setter.

Samozřejmě, při použití anemic doménový model tyto datové modely se použije ze sady objektů služeb (tradičně pojmenované *vrstvy obchodní*) který zachytit všechny domény nebo obchodní logiku. Vrstva business umístěná na datový model a používá model dat stejně jako data.

Anemic doménový model je právě návrh procedurální stylu. Objekty anemic entit nejsou skutečné objekty, protože nemají chování (metody). Drží vlastnosti dat a proto není objektově orientovaný návrh. Vložením všech chování ven do objektů služby (vrstva business) v podstatě skončíte se [špagety kód](https://en.wikipedia.org/wiki/Spaghetti_code) nebo [transakce skripty](https://martinfowler.com/eaaCatalog/transactionScript.html), a proto ztratit výhody modelu domény poskytuje.

Bez ohledu na to, pokud je velmi jednoduché mikroslužby nebo ohraničená kontextu (CRUD služby), může být dostatečné anemic doménový model ve formě objektů entit s pouze vlastnosti dat a nemusí být vhodné implementovat složitější vzorů DDD. V takovém případě bude jednoduše modelu trvalost, protože se pouze data pro účely CRUD záměrně jste vytvořili entitu.

To je důvod, proč jsou ideální pro více architektonický přístup v závislosti na jednotlivých ohraničených kontextech architekturu mikroslužeb. Například v aplikaci eShopOnContainers, pořadí mikroslužba implementuje vzorů DDD, ale katalogu mikroslužeb, což je jednoduchá služba CRUD, nikoli.

Někteří lidé říkají, že je anemic doménový model proti vzor. Tato skutečnost závisí na co při implementaci. Pokud je mikroslužeb, kterou vytváříte jednoduchou dostatečně (například služba CRUD), po anemic doménový model není proti vzor. Ale pokud potřebujete překonávání složitosti v mikroslužbě domény, který má spoustu neustále se měnící obchodní pravidla, může být anemic doménový model proti vzor pro mikroslužby nebo ohraničená kontextu. V takovém případě navrhování jako bohaté model s entitami, který obsahuje data a chování, stejně jako implementace dalších vzorů DDD (agregace, hodnota objekty atd.) může mít velké výhody pro dlouhodobá úspěšnost těchto mikroslužeb.

#### <a name="additional-resources"></a>Další zdroje

- **DevIQ. Domain Entity** \
  <https://deviq.com/entity/>

- **Martina Fowlera. Doménový Model** \
  <https://martinfowler.com/eaaCatalog/domainModel.html>

- **Martina Fowlera. Anemic doménový Model** \
  <https://martinfowler.com/bliki/AnemicDomainModel.html>

### <a name="the-value-object-pattern"></a>Vzor hodnota objektu

Má poznamenali Eric Evans "velký počet objektů nebudou mít koncepční identitu. Tyto objekty popisují některé vlastnosti objektu."

Entita vyžaduje identitu, ale existuje mnoho objektů v systému, který se nepodporují, jako vzor hodnota objektu. Hodnota objektu je objekt s žádná koncepční identita, která popisuje aspekty domény. Jedná se o objekty, které můžete vytvořit instanci k reprezentaci prvků návrhu, které se vztahuje pouze na vás dočasně. Vás zajímají *co* nejsou, *kdo* jsou. Příklady zahrnují čísly a textovými řetězci, ale může být také vyšší úrovně koncepty, jako jsou skupiny atributů.

Něco, co je entita v mikroslužbě nemusí být entitu v jiném mikroslužeb, protože v druhém případě může být omezená kontextu mají různý význam. Například adresa v aplikaci elektronického obchodování nemusí mít identitu vůbec, protože to může představovat pouze skupiny atributů zákazníka profilu osoby nebo společnosti. V takovém případě by měly být klasifikované adrese jako objekt hodnoty. V žádosti o společnosti nástroj elektrické energie, může být důležité pro obchodní domény adresu zákazníka. Proto adresu musí mít identitu, tak ve fakturačním systému lze přímo propojit na adresu. V takovém případě adresy by měly být klasifikované jako entita domény.

Osoba s jméno a příjmení je obvykle entity vzhledem k tomu, že uživatel má identitu, i v případě, že jméno a příjmení shoduje s jinou sadu hodnot, například když tyto názvy také odkazuje na jinou osobu.

Hodnota objekty jsou náročná na správu v relačních databází a ORMs, jako je EF, zatímco v dokumentu orientovaného databázích, které jsou snadněji implementovat a používat.

EF Core 2.0 obsahuje [vlastní entity](https://devblogs.microsoft.com/dotnet/announcing-entity-framework-core-2-0/#owned-entities-and-table-splitting) funkce, která usnadňuje zpracování hodnotu objektů, jak uvidíme podrobně později.

#### <a name="additional-resources"></a>Další zdroje

- **Martina Fowlera. Vzor hodnota objektu** \
  <https://martinfowler.com/bliki/ValueObject.html>

- **Hodnota objektu** \
  <https://deviq.com/value-object/>

- **Hodnota objektů v vývoj řízený testováním** \
  [https://leanpub.com/tdd-ebook/read\#leanpub-auto-value-objects](https://leanpub.com/tdd-ebook/read#leanpub-auto-value-objects)

- **Eric Evans. Návrhy řízené doménou: Použití složitosti srdce softwaru.** (Kniha; obsahuje diskusi hodnotu objektů) \
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

### <a name="the-aggregate-pattern"></a>Agregační vzor

Doménový model obsahuje cluster různých datových entit a procesy, které můžete řídit důležité oblasti funkcí, jako je například vyřizování objednávek nebo z inventáře. Další detailnější DDD jednotka je agregace, který popisuje cluster nebo skupinu entit a chování, které lze považovat za získá na ucelenosti jednotky.

Obvykle definujete agregace podle transakcí, které potřebujete. Klasickým příkladem je pořadí, které obsahuje také seznam pořadí položek. Objednávky položku, bude obvykle entity. Ale budou podřízené entity v rámci pořadí agregaci, která bude obsahovat také entitě objednávka jako jeho kořenové entity, obvykle nazývá kořen agregace.

Určení agregace může být obtížné. Agregace je skupiny objektů, které musí být konzistentní vzhledem k aplikacím společně, ale nemůže stačí vybrat skupinu objektů a označte je agregace. Musí začínat koncept domény a přemýšlet o entitách, které se používají v nejběžnějších transakce související pro daný koncept. Tyto entity, které musí být transakčně konzistentní se, co tvoří agregace. Přemýšlení o operacích transakce je pravděpodobně nejlepším způsobem, jak identifikovat agregace.

### <a name="the-aggregate-root-or-root-entity-pattern"></a>Model agregace kořenové nebo Kořenová entita

Agregace se skládá z alespoň jedné entity: agregační kořenový adresář, označovaný taky jako kořenová entita nebo primární entity. Kromě toho může mít více podřízených entit a hodnota objekty, se všechny entity a objekty vzájemně spolupracuje při provádění požadované chování a transakce.

Agregační kořenové slouží k zajištění konzistence agregace; měla by být pouze vstupní bod pro aktualizace agregaci prostřednictvím metody nebo operace v agregované kořenová třída. Entity v rámci agregace pouze pomocí agregační kořenové by měl provádět změny. Je strážce konzistence agregaci, vzhledem k tomu výstupních podmínek a pravidla konzistence, které možná budete muset v souladu s vaší agregovaně. Pokud změníte podřízený objekt entity nebo hodnota nezávisle na sobě, agregační kořen nelze zkontrolujte, že agregace v platném stavu. Bylo by jako tabulka s dojde ke ztrátě větev. Udržování konzistentnosti je hlavním účelem agregace root.

V obrázku 7. až 9, zobrazí se agreguje ukázkové jako kupujících, agregace, která obsahuje jednu entitu (kořen agregační kupujících). Agregace pořadí obsahuje více entit a hodnoty objektu.

![Doménový model DDD se skládá z agregace, agregaci může mít pouze jednu entitu nebo více a může obsahovat také objekty hodnotu.](./media/image10.png)

**Obrázek 7. až 9**. Příklad agregace s několika neboli jednotlivých entit

Stejně jako v pořadí mikroslužeb v aplikaci eShopOnContainers odkaz na aplikaci, mějte na paměti, že agregace kupujících může mít další podřízené entity, v závislosti na vaší domény. Obrázek 7. až 9 právě ukazuje případ, ve kterém má kupující jedna entita, například agregaci, která obsahuje jenom agregační kořenové.

Aby bylo možné udržovat oddělení agregací a ponechat zřetelnými hranicemi mezi nimi, je vhodné v modelu domény DDD tak jak je implementován v s přímým přístupem navigace mezi agregace a pouze s poli cizí klíč (Cizíklíč) [ Řazení doménového modelu mikroslužby](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Order.cs) v aplikaci eShopOnContainers. Entity pořadí pouze má pole cizího klíče pro odběratele, ale ne EF Core navigační vlastnost, jak je znázorněno v následujícím kódu:

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

Identifikace a práce s agregacemi vyžaduje výzkum a prostředí. Další informace naleznete v seznamu následující další prostředky.

#### <a name="additional-resources"></a>Další zdroje

- **Vaughn Vernon. Efektivní návrh agregace – část I: Modelování jedné agregace** (z <http://dddcommunity.org/>) \
  <http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_1.pdf>

- **Vaughn Vernon. Efektivní agregační návrh – část II: Provádění agreguje pracovní společně** (z <http://dddcommunity.org/>) \
  <http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_2.pdf>

- **Vaughn Vernon. Efektivní agregační návrh – část III: Získání přehled díky zjišťování** (z <http://dddcommunity.org/>) \
  <http://dddcommunity.org/wp-content/uploads/files/pdf_articles/Vernon_2011_3.pdf>

- **Sergeje Grybniak. Návrh taktických vzorů DDD** \
  <https://www.codeproject.com/Articles/1164363/Domain-Driven-Design-Tactical-Design-Patterns-Part>

- **Chris Richardson. Vývoj transakční Mikroslužeb pomocí agregace** \
  <https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-1-richardson>

- **DevIQ. Agregační vzor** \
  <https://deviq.com/aggregate-pattern/>

>[!div class="step-by-step"]
>[Předchozí](ddd-oriented-microservice.md)
>[další](net-core-microservice-domain-model.md)
