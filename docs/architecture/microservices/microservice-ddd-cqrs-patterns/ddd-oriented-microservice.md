---
title: Návrh mikroslužby orientované na DDD
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Seznamte se s návrhem mikroslužeb pro objednávání orientovaných na DDD a jeho aplikačních vrstev.
ms.date: 10/08/2018
ms.openlocfilehash: 583e103c8bd9d828731a658ea2fd2aa0758e7a12
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988736"
---
# <a name="design-a-ddd-oriented-microservice"></a>Návrh mikroslužby orientované na DDD

Návrh řízený doménou (DDD) obhajuje modelování založené na realitě podnikání, která je relevantní pro vaše případy použití. V souvislosti se vytvářením aplikací, DDD hovoří o problémech jako domény. Popisuje nezávislé problémové oblasti jako ohraničené kontexty (každý ohraničený kontext koreluje s mikroslužbou) a zdůrazňuje společný jazyk mluvit o těchto problémech. Navrhuje také mnoho technických konceptů a vzorů, jako jsou entity domény s bohatými modely (žádný [model anemické domény),](https://martinfowler.com/bliki/AnemicDomainModel.html)hodnotové objekty, agregáty a agregační kořenová (nebo kořenová entita) pro podporu interní implementace. Tato část představuje návrh a implementaci těchto vnitřních vzorů.

Někdy jsou tato technická pravidla a vzory DDD vnímány jako překážky, které mají strmou křivku učení pro implementaci přístupů DDD. Ale důležitou součástí není vzory samy o sobě, ale organizování kódu tak, aby byl v souladu s obchodními problémy, a pomocí stejné obchodní podmínky (všudypřítomný jazyk). Kromě toho ddd přístupy by měly být použity pouze v případě, že implementujete složité mikroslužeb s významnými obchodními pravidly. Jednodušší odpovědnosti, jako je služba CRUD, lze spravovat pomocí jednodušších přístupů.

Kde nakreslit hranice je klíčovým úkolem při navrhování a definování mikroslužeb. Vzory DDD vám pomohou pochopit složitost domény. Pro model domény pro každý ohraničený kontext identifikujete a definujete entity, hodnotové objekty a agregace, které modelují vaši doménu. Sestavení a upřesnění modelu domény, který je obsažen v rámci hranice, která definuje váš kontext. A to je velmi explicitní ve formě mikroslužby. Součásti v rámci těchto hranic nakonec vaše mikroslužby, i když v některých případech BC nebo obchodní mikroslužeb se může skládat z několika fyzických služeb. DDD je o hranicích a tak jsou mikroslužby.

## <a name="keep-the-microservice-context-boundaries-relatively-small"></a>Udržujte hranice kontextu mikroslužeb relativně malé

Určení, kam umístit hranice mezi ohraničené kontexty, vyvažuje dva konkurenční cíle. Nejprve chcete vytvořit nejmenší možné mikroslužeb, i když to by nemělo být hlavní ovladač; měli byste vytvořit hranici kolem věcí, které potřebují soudržnost. Za druhé chcete, aby se zabránilo chatty komunikace mezi mikroslužeb. Tyto cíle si mohou vzájemně odporovat. Měli byste je vyvážit rozkladem systému na co nejvíce malých mikroslužeb, dokud neuvidíte, že hranice komunikace rychle rostou s každým dalším pokusem o oddělení nového ohraničeného kontextu. Soudržnost je klíčová v rámci jediného ohraničeného kontextu.

Je podobný [zápachu kódu nevhodnosti](https://sourcemaking.com/refactoring/smells/inappropriate-intimacy) při implementaci tříd. Pokud dvě mikroslužby potřebují hodně spolupracovat mezi sebou, by pravděpodobně měly být stejné mikroslužby.

Dalším způsobem, jak se na to dívat, je autonomie. Pokud mikroslužby musí spoléhat na jinou službu přímo služby požadavku, není skutečně autonomní.

## <a name="layers-in-ddd-microservices"></a>Vrstvy v mikroslužbách DDD

Většina podnikových aplikací s významnou obchodní a technickou složitostí je definována více vrstvami. Vrstvy jsou logický artefakt a nesouvisí s nasazením služby. Existují, aby vývojářům pomohly spravovat složitost kódu. Různé vrstvy (například vrstva modelu domény versus prezentační vrstva atd.) mohou mít různé typy, které vyžadují překlady mezi těmito typy.

Entita může být například načtena z databáze. Potom část těchto informací nebo agregaci informací včetně dalších dat z jiných entit, lze odeslat do uživatelského rozhraní klienta prostřednictvím rozhraní REST Web API. Jde o to, že entita domény je obsažena ve vrstvě modelu domény a neměla by být rozšířena do jiných oblastí, do kterých nepatří, jako je prezentační vrstva.

Kromě toho musíte mít vždy platné entity (viz Návrh ověření v části [vrstvy modelu domény)](domain-model-layer-validations.md) řízené agregačními kořeny (kořenové entity). Entity by proto neměly být vázány na zobrazení klienta, protože na úrovni ui některá data stále nemusí být ověřena. To je to, co ViewModel je pro. ViewModel je datový model výhradně pro potřeby prezentační vrstvy. Entity domény nepatří přímo do ViewModel. Místo toho je třeba přeložit mezi ViewModels a entity domény a naopak.

Při řešení složitosti je důležité mít model domény řízený agregačníkořeny, které zajistí, že všechny invariants a pravidla vztahující se k této skupině entit (agregace) jsou prováděny prostřednictvím jednoho vstupního bodu nebo brány, agregační kořen.

Obrázek 7-5 ukazuje, jak je vrstvený návrh implementován v aplikaci eShopOnContainers.

![Diagram znázorňující vrstvy v mikroslužbě návrhu řízeného doménou.](./media/ddd-oriented-microservice/domain-driven-design-microservice.png)

**Obrázek 7-5**. Vrstvy DDD v objednávající mikroslužbě v eShopOnContainers

Tři vrstvy v mikroslužbě DDD, jako je řazení. Každá vrstva je projekt VS: Aplikační vrstva je Ordering.API, vrstva domény je Ordering.Domain a vrstva infrastruktury je Ordering.Infrastructure. Chcete navrhnout systém tak, aby každá vrstva komunikovala pouze s určitými jinými vrstvami. To může být jednodušší vynutit, pokud vrstvy jsou implementovány jako knihovny různých tříd, protože můžete jasně určit, jaké závislosti jsou nastaveny mezi knihovnami. Například vrstva modelu domény by neměla mít závislost na žádné jiné vrstvě (třídy modelu domény by měly být plain old CLR Objects nebo [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object), classes). Jak je znázorněno na obrázku 7-6, knihovna vrstev **Ordering.Domain** obsahuje závislosti pouze na knihovnách .NET Core nebo balíčcích NuGet, ale ne na žádné jiné vlastní knihovně, jako je například knihovna dat nebo knihovna trvalosti.

![Snímek obrazovky se závislostmi Ordering.Domain](./media/ddd-oriented-microservice/ordering-domain-dependencies.png)

**Obrázek 7-6**. Vrstvy implementované jako knihovny umožňují lepší kontrolu závislostí mezi vrstvami

### <a name="the-domain-model-layer"></a>Vrstva modelu domény

Eric Evans je vynikající kniha [Domain Driven Design](https://domainlanguage.com/ddd/) říká následující o vrstvě modelu domény a aplikační vrstvy.

**Vrstva modelu domény**: Odpovídá za reprezentaci konceptů podniku, informací o obchodní situaci a obchodních pravidel. Stát, který odráží obchodní situaci, je zde kontrolován a používán, i když technické podrobnosti o jeho uložení jsou přeneseny na infrastrukturu. Tato vrstva je srdcem obchodního softwaru.

Vrstva modelu domény je místo, kde je vyjádřena obchodní. Když implementujete vrstvu modelu domény mikroslužeb v rozhraní .NET, je tato vrstva kódována jako knihovna tříd s entitami domény, které zachycují data plus chování (metody s logikou).

V návaznosti [na zásady nevědomosti trvalosti](https://deviq.com/persistence-ignorance/) a [neznalosti infrastruktury](https://ayende.com/blog/3137/infrastructure-ignorance) musí tato vrstva zcela ignorovat podrobnosti o trvalosti dat. Tyto úlohy trvalosti by měly být prováděny vrstvou infrastruktury. Proto by tato vrstva neměla převzít přímé závislosti na infrastruktuře, což znamená, že důležitým pravidlem je, že vaše třídy entit modelu domény by měly být [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)s.

Entity domény by neměly mít žádnou přímou závislost (například odvození ze základní třídy) na jakékoli infrastruktuře pro přístup k datům, jako je entity Framework nebo NHibernate. V ideálním případě by entity domény neměly odvozovat ani implementovat žádný typ definovaný v jakékoli infrastruktuře.

Většina moderních orm architektury, jako je entity Framework Core umožňují tento přístup, tak, aby vaše třídy modelu domény nejsou spojeny s infrastrukturou. Však s POCO entity není vždy možné při použití určitých NoSQL databází a architektury, jako jsou objekty actor a spolehlivé kolekce v Azure Service Fabric.

I v případě, že je důležité dodržovat zásadu trvalosti nevědomosti pro model domény, neměli byste ignorovat obavy o trvalost. Je stále velmi důležité pochopit fyzický datový model a jak se mapuje na objektový model entity. V opačném případě můžete vytvořit nemožné návrhy.

Také to neznamená, že můžete vzít model určený pro relační databázi a přímo jej přesunout do nosql nebo dokument-orientované databáze. V některých modelech entit se model může vejít, ale obvykle se mu to nevejde. Stále existují omezení, která musí model entity dodržovat, a to na základě technologie úložiště a technologie ORM.

### <a name="the-application-layer"></a>Aplikační vrstva

Pohybující se na aplikační vrstvy, můžeme opět citovat Eric Evans kniha [Domény Driven Design:](https://domainlanguage.com/ddd/)

**Aplikační vrstva:** Definuje úlohy, které má software provádět, a nasměruje objekty expresivní domény k řešení problémů. Úkoly, za které je tato vrstva zodpovědná, jsou smysluplné pro podnik nebo jsou nezbytné pro interakci s aplikačními vrstvami jiných systémů. Tato vrstva je udržována tenká. Neobsahuje obchodní pravidla ani znalosti, ale pouze koordinuje úkoly a delegáti pracují na spolupráci objektů domény v další vrstvě dolů. Nemá stav odrážející obchodní situaci, ale může mít stav, který odráží průběh úkolu pro uživatele nebo program.

Aplikační vrstva mikroslužby v rozhraní .NET je běžně kódována jako ASP.NET projektu základního webového rozhraní API. Projekt implementuje interakci mikroslužby, vzdálený přístup k síti a externí webová api používaná z uživatelského prostředí nebo klientských aplikací. Zahrnuje dotazy, pokud používáte přístup CQRS, příkazy přijaté mikroslužbou a dokonce i komunikaci řízenou událostmi mezi mikroslužbami (události integrace). Základní webové rozhraní ASP.NET, které představuje aplikační vrstvu, nesmí obsahovat obchodní pravidla nebo znalosti domény (zejména pravidla domény pro transakce nebo aktualizace); ty by měly být vlastněny knihovnou třídmodelu domény. Aplikační vrstva musí pouze koordinovat úkoly a nesmí obsahovat ani definovat žádný stav domény (model domény). Deleguje provádění obchodních pravidel na samotné třídy modelu domény (agregační kořeny a entity domény), které nakonec aktualizují data v rámci těchto entit domény.

V podstatě aplikační logiky je místo, kde implementovat všechny případy použití, které závisí na daném front-endu. Například implementace související se službou webového rozhraní API.

Cílem je, že logika domény ve vrstvě modelu domény, její invarianty, datový model a související obchodní pravidla musí být zcela nezávislé na vrstvách prezentace a aplikace. Vrstva modelu domény především nesmí přímo záviset na žádné infrastruktuře.

### <a name="the-infrastructure-layer"></a>Vrstva infrastruktury

Vrstva infrastruktury je způsob, jakým jsou data, která jsou zpočátku uložena v entitách domény (v paměti), uchována v databázích nebo jiném trvalém úložišti. Příkladem je použití entity Framework Základní kód k implementaci třídy vzoru úložiště, které používají DBContext k uchování dat v relační databázi.

V souladu s výše uvedenými zásadami [nevědomosti persistence](https://deviq.com/persistence-ignorance/) a [neznalosti infrastruktury](https://ayende.com/blog/3137/infrastructure-ignorance) nesmí vrstva infrastruktury "kontaminovat" vrstvu modelu domény. Je nutné zachovat třídy entity modelu domény agnostik z infrastruktury, které používáte k uchování dat (EF nebo jiné rozhraní) tím, že nebude mít pevné závislosti na rozhraní. Knihovna tříd vrstvy vrstvy modelu domény by měla mít pouze kód domény, pouze třídy entit [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object) implementující srdce softwaru a zcela oddělené od technologií infrastruktury.

Proto vrstvy nebo knihovny tříd a projekty by měly v konečném důsledku záviset na vrstvě modelu domény (knihovna), nikoli naopak, jak je znázorněno na obrázku 7-7.

![Diagram zobrazující závislosti, které existují mezi vrstvami služby DDD.](./media/ddd-oriented-microservice/ddd-service-layer-dependencies.png)

**Obrázek 7-7**. Závislosti mezi vrstvami v DDD

Závislosti ve službě DDD, aplikační vrstva závisí na doméně a infrastruktuře a infrastruktura závisí na doméně, ale doména nezávisí na žádné vrstvě. Tento návrh vrstvy by měl být nezávislý pro každou mikroslužbu. Jak již bylo uvedeno dříve, můžete implementovat nejsložitější mikroslužeb podle vzorů DDD, při implementaci jednodušší mikroslužeb řízených daty (jednoduché CRUD v jedné vrstvě) jednodušším způsobem.

#### <a name="additional-resources"></a>Další zdroje

- **DevIQ. Princip nevědomosti perzistence** \
  <https://deviq.com/persistence-ignorance/>

- **Oren Eini. Infrastruktura Nevědomost** \
  <https://ayende.com/blog/3137/infrastructure-ignorance>

- **Anděllopez. Vrstvená architektura v návrhu řízeném doménou** \
  <https://ajlopez.wordpress.com/2008/09/12/layered-architecture-in-domain-driven-design/>

>[!div class="step-by-step"]
>[Předchozí](cqrs-microservice-reads.md)
>[další](microservice-domain-model.md)
