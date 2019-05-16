---
title: Návrh mikroslužby orientované na DDD
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Pochopte návrh pořadí mikroslužby orientované na DDD a jeho vrstvy aplikace.
ms.date: 10/08/2018
ms.openlocfilehash: 303f8909d12dddef93b20604a00b9ea8e8493ee5
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65639674"
---
# <a name="design-a-ddd-oriented-microservice"></a>Návrh mikroslužby orientované na DDD

Návrhy řízené doménou (DDD) nejzávažnějších modelování podle ve skutečnosti je množství firmy jako relevantní pro vaše případy použití. V rámci vytváření aplikací DDD hovoří o problémech jako domény. Popisuje nezávislé problémových oblastí jako ohraničených kontextech (jednotlivých ohraničených kontextech souvisí s mikroslužbě) a zvýrazní společný jazyk mluvit o tyto problémy. Rovněž navrhuje mnoho technické koncepty a vzory, stejně jako domény entity s formátovaným modely (žádné [anemic doménový model](https://martinfowler.com/bliki/AnemicDomainModel.html)), hodnota objekty, agregace a agregační kořenové (nebo Kořenová entita) pravidla pro podporu interní implementace. Tato část představuje návrh a implementaci těchto interní vzorce.

Někdy jsou tyto technické pravidla DDD a vzory považován za překážky, které mají strmé křivky učení pro implementaci DDD přístupy. Ale je důležitou součástí není vzorky sami, ale uspořádání kód, takže je umístěno na obchodní problémy a pomocí stejného obchodní termíny (všudypřítomná language). Kromě toho DDD přístupy bude použito pouze v případě, že při implementaci komplexní mikroslužby s důležité obchodní pravidla. Jednodušší odpovědnosti, například ke službě CRUD lze spravovat pomocí jednodušší přístupy.

Kde stanovit hranice je klíčové úlohy při návrhu a definování mikroslužby. Vzorů DDD vám pomůže pochopit složitosti v doméně. Pro doménový model pro jednotlivých ohraničených kontextech identifikovat a definují entity, hodnota objekty a agregace, které modelují vaší domény. Vytváření a zpřesňování doménový model, který je obsažený v hranici, která definuje váš kontext. A to je velmi explicitní ve formě mikroslužby. Komponenty v rámci těchto hranicích skončit se mikroslužby, i když v některých případech a BC nebo obchodní mikroslužeb se může skládat z několika fyzických služeb. Proto jsou to mikroslužby DDD je o hranice.

## <a name="keep-the-microservice-context-boundaries-relatively-small"></a>Zachovat mikroslužbách hranic kontextu za poměrně málo početnému

Určení, kam umístit hranice mezi ohraničených kontextech vyrovnává dvě konkurenční cíle. Nejprve chcete k úvodnímu vytvoření nejmenší možné mikroslužeb, i když, který by neměl být hlavní ovladač; měli byste vytvořit hranicí kolem věcí, které je třeba soudržnosti. Za druhé budete chtít zabránit přetížení komunikace mezi mikroslužbami. Těchto cílů můžete si vzájemně odporují. Měl by je vyvážit podle rozložení systému do tolik malé mikroslužeb, jako je možné, dokud se nezobrazí komunikace hranice rychle rostoucí s další pokus oddělení nový kontext omezená. Klíčem v rámci jednoho ohraničený kontext je soudržnosti.

Se podobá [nevhodný Intimacy kód pach](https://sourcemaking.com/refactoring/smells/inappropriate-intimacy) při implementaci třídy. Pokud potřebujete vzájemně spolupracovat mnohem dvě mikroslužeb, by měl pravděpodobně být stejné mikroslužeb.

Dalším způsobem, jak podívejte se na to je autonomie. Pokud mikroslužeb musíte spoléhat na jiné služby pro žádost o službu, přímo, není skutečně autonomní.

## <a name="layers-in-ddd-microservices"></a>Vrstvy v DDD mikroslužeb

Většina podnikových aplikací s důležité obchodní a technické složitost jsou definovány více vrstev. Vrstvy jsou logické artefaktů a nejsou spojené s nasazením služby. Existují, což vývojářům umožňuje zvládnout složité v kódu. Různé vrstvy (např. vrstvě doménového modelu a prezentační vrstvy, atd.) může mít různé typy, který zmocňuje převody mezi typy.

Například entita nešlo načíst z databáze. Součástí těchto informací nebo agregované informace, včetně další data z jiných entit, můžete pak odešlou do klienta uživatelského rozhraní pomocí webového rozhraní API REST. Tady je bod je, že entita domény je obsažen ve vrstvě doménového modelu a by neměl být předány další oblasti, které nepatří, jako je třeba do prezentační vrstvy.

Kromě toho musíte mít vždy platné entity (najdete v článku [návrh ověřování ve vrstvě doménového modelu](domain-model-layer-validations.md) části) řídí agregační kořeny (kořenové entity). Proto entity by neměl být vázána na zobrazení klienta, protože na úrovni uživatelského rozhraní nemusí stále ověřit některá data. Toto je, co ViewModel je. ViewModel je datový model výhradně pro potřeby prezentační vrstvy. Entity domény nepatří přímo do ViewModel. Místo toho musíte k převodu mezi entitami modely ViewModels a domény a naopak.

Při řešení složitost, je důležité mít modelu domény řídí agregační kořeny, ujistěte se, že výstupních podmínek a pravidla týkající se do této skupiny entit (agregace) se provádí prostřednictvím jedním vstupním bodem nebo brány, agregační kořenové.

Obrázek 7 – 5 ukazuje, jak je implementována vrstvený návrh v aplikaci eShopOnContainers aplikace.

![Tři vrstvy v mikroslužbě DDD, jako jsou řazení. Každá vrstva je projekt VS: Aplikační vrstva je Ordering.API, vrstvy domény je Ordering.Domain a vrstvy infrastruktury je Ordering.Infrastructure.](./media/image6.png)

**Obrázek 7 – 5**. Vrstvy DDD v pořadí mikroslužeb v aplikaci eShopOnContainers

Chcete Navrhněte systém tak, aby každá vrstva komunikuje jenom s určitým vrstvy. Který může být jednodušší vynutit Pokud vrstvy jsou implementovány jako jinou třídu knihovny, protože můžete jasně určit, jaké závislosti jsou nastaveny mezi knihovnami. Vrstvě doménového modelu, neměla by mít závislost na jinou vrstvu (tříd modelu domény by měl být prostý starší objekty CLR nebo [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object), třídy). Jak ukazuje obrázek 7 – 6 **Ordering.Domain** knihovny vrstvy má závislosti pouze na knihovny .NET Core nebo balíčky NuGet, ale ne na jiných vlastní knihovny, jako je například knihovnu dat nebo trvalost.

![Zobrazení Průzkumníka řešení Ordering.Domain závislostí, abych ho pouze závisí na knihovny .NET Core.](./media/image7.png)

**Obrázek 7 – 6**. Implementováno jako knihovny umožňují lepší kontrolu nad závislostech mezi vrstvami, vrstvy

### <a name="the-domain-model-layer"></a>Vrstvě doménového modelu

Eric Evans vynikající knihy [domény Driven Design](https://domainlanguage.com/ddd/) říká následující informace o vrstvě doménového modelu a aplikační vrstvy.

**Vrstvě doménového modelu**: Za představující koncepty firmy, informace o situaci a obchodní pravidla. Stav, který odráží obchodní situaci řídí a se tady použít, i když jsou delegovanými technické podrobnosti o jeho uložení do infrastruktury. Tato vrstva je srdcem obchodního softwaru.

Vrstvě doménového modelu je, kde je vyjádřena podniku. Při implementaci vrstvě doménového modelu mikroslužby v rozhraní .NET je, že vrstva kódovat jako knihovny tříd s entitami domény, které zaznamenávají data a chování (metody s logikou).

Následující [trvalost neznalosti](https://deviq.com/persistence-ignorance/) a [neznalosti infrastruktury](https://ayende.com/blog/3137/infrastructure-ignorance) zásady, tato vrstva musí být zcela ignorovat podrobnosti trvalosti dat. Tyto úlohy trvalosti by měl provádět vrstvy infrastruktury. Proto tato vrstva neměla by mít přímé závislosti na infrastruktuře, což znamená, že pravidlo důležité je, že by měl být vaší doménové třídy modelu entity [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)s.

Entity domény by neměla mít žádné přímé závislosti (například odvozené ze základní třídy) na jakékoli platformě dat přístup infrastruktury jako Entity Framework nebo NHibernate. V ideálním případě by neměl entity domény jsou odvozeny z nebo implementovat libovolný typ definovaný v rámci jakékoli infrastruktury.

Většina moderních ORM architektur, jako třeba Entity Framework Core umožňují tento přístup tak, aby třídách modelu domény nejsou spojeny s infrastrukturou. Nicméně s POCO entity není vždy možné při použití určitých databázemi NoSQL a architektur, jako jsou objekty actor a spolehlivé kolekce v Azure Service Fabric.

I v případě, že je potřeba postupovat podle principu neznalosti trvalosti pro doménový model, by neměla ignorovat trvalost obavy. Stále je velmi důležité uvědomit si fyzický datový model a jak mapuje na objekt modelu entity. V opačném případě můžete vytvořit nemožné návrhy.

Také neznamená to může trvat model určený pro relační databázi a přesuňte ho přímo k databázi NoSQL nebo dokumentově orientované. V některých modelů rychlou entity je možné umístit modelu, ale obvykle tomu tak není. Stále existují omezení, které musí dodržovat entity model založený na technologii úložiště a ORM technologie.

### <a name="the-application-layer"></a>Aplikační vrstvu

Pokračovat k aplikační vrstvě, můžeme znovu citovat Eric Evans v knize [domény Driven Design](https://domainlanguage.com/ddd/):

**Aplikační vrstvy:** Definuje úloh softwaru by měl provádět a přesměruje výrazové domény objekty, které chcete zjistit problémy. Úlohy, které tuto vrstvu je zodpovědná za jsou smysl v daném podniku nebo které jsou nezbytné pro interakci s jinými systémy vrstvy aplikace. Tato vrstva je udržováno dynamického zajišťování. Neobsahuje obchodních pravidel nebo znalosti, ale pouze souřadnice úkoly a delegáti pracovat na spolupráce objektů domény v další vrstvu dolů. Stav odráží obchodní situaci nemá, ale může mít stav, který zobrazuje průběh úloh pro uživatele nebo program.

Aplikační vrstvy mikroslužby v rozhraní .NET je běžně kódované jako projekt webového rozhraní API ASP.NET Core. Projekt implementuje interakce mikroslužbách, vzdálený přístup k síti a externích webových rozhraní API používá z uživatelského rozhraní nebo klientských aplikací. Pokud pomocí modelu CQRS přístup příkazy přijatý mikroslužbách a dokonce i založený na událostech komunikace mezi mikroslužbami (události integrace) obsahuje dotazy. ASP.NET Core webového rozhraní API, která představuje aplikační vrstvu nesmí obsahovat obchodní pravidla nebo znalosti domény (zejména domény pravidla pro transakce nebo aktualizace); Tyto by měl být vlastněn knihovny tříd modelu domény. Souřadnice pouze aplikace vrstvy musí úkoly a nesmí obsahovat nebo definovat libovolný stav domény (doménový model). Deleguje zpracování obchodních pravidel domény modelu třídám sami (agregační kořenových adresářů a entitami domény), které bude nakonec aktualizaci dat v rámci těchto entit domény.

Aplikace logiky je v podstatě, kde je implementovat všechny případy použití, které jsou závislé na dané front-endu. Například provádění související se službou webového rozhraní API.

Cílem je, že logiku domény ve vrstvě doménového modelu, jeho výstupních podmínek, datový model a související obchodní pravidla musí být zcela nezávislé na prezentaci a aplikační vrstvou. Co je nejdůležitější vrstvě doménového modelu nesmí být závislá přímo na libovolné architektury infrastruktury.

### <a name="the-infrastructure-layer"></a>Vrstvy infrastruktury

Vrstvy infrastruktury je, jak se ukládají data původně uložená v doméně entity (v paměti) v databázích nebo v jiném trvalého úložiště. Příklad používá Entity Framework Core kód pro implementaci vzoru třídy úložiště, které používají DBContext uchovávat data v relační databázi.

V souladu s výše uvedené [trvalost neznalosti](https://deviq.com/persistence-ignorance/) a [infrastruktury neznalosti](https://ayende.com/blog/3137/infrastructure-ignorance) zásady, vrstvy infrastruktury nesmí "způsobit kontaminaci" vrstvě doménového modelu. Nezávislé třídy entity model domény od infrastruktury, který používáte k uchování dat (EF nebo jiné rozhraní framework) je nutné zachovat díky není pevný závislosti na rozhraní. Knihovnu tříd modelu vrstvy domény by měl mít pouze váš kód domény právě [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object) entity třídy implementace srdce váš software a zcela oddělený od technologií infrastruktury.

Proto vrstvy nebo knihovny tříd a projekty by nakonec záviset na vrstvě doménového modelu (knihovna), ne naopak, jak je znázorněno v obrázek 7 – 7.

![Závislosti ve službě DDD, aplikační vrstvu, závisí na domény a infrastruktury a infrastruktury závisí na doméně, ale domény nezávisí na žádné vrstvy.](./media/image8.png)

**Obrázek 7 – 7**. Závislosti mezi vrstvami v DDD

Tento návrh vrstvy by měly být nezávislé u jednotlivých mikroslužeb. Jak bylo uvedeno dříve, můžete implementovat nejsložitější mikroslužeb následujících vzorů DDD při implementaci jednodušší řízené daty mikroslužby (jednoduché CRUD v jedné vrstvě) jednodušším způsobem.

#### <a name="additional-resources"></a>Další zdroje

- **DevIQ. Princip neznalosti trvalosti** \
  <https://deviq.com/persistence-ignorance/>

- **Oren Eini. Neznalosti infrastruktury** \
  <https://ayende.com/blog/3137/infrastructure-ignorance>

- **Angel Lopez. Vrstvené architektury v návrhu řízeného doménou** \
  <https://ajlopez.wordpress.com/2008/09/12/layered-architecture-in-domain-driven-design/>

>[!div class="step-by-step"]
>[Předchozí](cqrs-microservice-reads.md)
>[další](microservice-domain-model.md)
