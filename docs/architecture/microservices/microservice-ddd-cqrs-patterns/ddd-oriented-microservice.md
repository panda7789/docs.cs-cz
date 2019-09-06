---
title: Návrh mikroslužby orientované na DDD
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Seznamte se s návrhem mikroslužeb a vrstev jejich aplikací orientovaných na DDD.
ms.date: 10/08/2018
ms.openlocfilehash: 303f8909d12dddef93b20604a00b9ea8e8493ee5
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295992"
---
# <a name="design-a-ddd-oriented-microservice"></a>Návrh mikroslužby orientované na DDD

Návrh založený na doméně (DDD) pomáhá modelování na základě reality firmy, které jsou relevantní pro vaše případy použití. V kontextu sestavování aplikací se DDD na problémy jako domény. Popisuje nezávisle problematické oblasti jako ohraničené kontexty (každý ohraničený kontext odpovídá mikroslužbám) a zvýrazňuje společný jazyk, ve kterém se tyto problémy potýkají. Navrhuje taky mnoho technických konceptů a vzorů, jako jsou entity domény s bohatými modely (žádný [anemic model](https://martinfowler.com/bliki/AnemicDomainModel.html)), objekty hodnot, agregace a agregovaná kořenová pravidla (nebo kořenová entita) pro podporu interní implementace. V této části se seznámíte s návrhem a implementací těchto interních vzorů.

Někdy jsou tato DDD technická pravidla a vzory vnímané jako překážky, které mají pro implementaci DDDých přístupů křivku výukového strmé. Ale důležitá součást není vzorci, ale organizuje kód tak, aby byl zarovnán k obchodním problémům a používal stejné obchodní výrazy (všudypřítomný jazyk). Kromě toho by se měly použít jenom DDD, Pokud implementujete komplexní mikroslužby s významnými obchodními pravidly. Jednodušší zodpovědnosti, jako je třeba služba CRUD, je možné spravovat pomocí jednodušších přístupů.

Místo vykreslování hranic je klíčovou úlohou při navrhování a definování mikroslužby. Vzory DDD vám pomůžou pochopit složitost v doméně. Pro model domény pro každý ohraničený kontext identifikujete a definujete entity, objekty hodnot a agregované modely, které modelují vaši doménu. Vytvoříte a upřesníte model domény, který je obsažen v hranici definující váš kontext. A to je velmi jasné v podobě mikroslužby. Komponenty v těchto hranicích mají za následek vaše mikroslužby, i když v některých případech mohou být BC nebo obchodní mikroslužby tvořené několika fyzickými službami. DDD je o hranicích, takže se jedná o mikroslužby.

## <a name="keep-the-microservice-context-boundaries-relatively-small"></a>Ponechejte hranice kontextu mikroslužeb relativně malé.

Určení místa, kde umístit hranice mezi ohraničené kontexty, vyvažuje ze dvou konkurenčních cílů. Nejdřív budete chtít zpočátku vytvořit nejmenší možné mikroslužby, i když by neměl být hlavním ovladačem. měli byste vytvořit hranici kolem akcí, které vyžadují soudržnost. Za druhé se chcete vyhnout komunikaci mezi těmito mikroslužbami v konverzaci. Tyto cíle mohou být vzájemně v konfliktu. Měli byste je vyrovnávat tím, že systém vyřadíte do tolika malých mikroslužeb, dokud se každý další pokus o oddělíte novým ohraničeným kontextem, dokud neuvidíte hranice komunikace. Soudržnost je klíč v rámci jednoho ohraničeného kontextu.

Je podobná [nevhodnému pachu kódu Intimacy](https://sourcemaking.com/refactoring/smells/inappropriate-intimacy) při implementaci tříd. Pokud je potřeba, aby dvě mikroslužby vzájemně spolupracovaly, měly by být stejné mikroslužby.

Dalším způsobem, jak se podívat, je autonomie. Pokud mikroslužba musí spoléhat na jinou službu, aby mohla přímo obsluhovat požadavek, není to skutečně autonomní.

## <a name="layers-in-ddd-microservices"></a>Vrstvy v DDD mikroslužby

Většina podnikových aplikací s významnou firmou a technickou složitostí je definována více vrstvami. Vrstvy jsou logický artefakt a nesouvisejí s nasazením služby. Existují, aby usnadnily vývojářům spravovat složitost v kódu. Různé vrstvy (podobně jako vrstva doménového modelu oproti prezentační vrstvě atd.) mohou mít různé typy, které přijímají překlady mezi těmito typy.

Například entita může být načtena z databáze. Tato informace je pak součástí těchto informací, nebo agregace informací, včetně dalších dat z jiných entit, je možné odeslat do uživatelského rozhraní klienta prostřednictvím webového rozhraní REST API. Zde je uvedeno, že entita domény je obsažena v rámci vrstvy doménového modelu a neměla by být šířena do jiných oblastí, do kterých nepatří, například do prezentační vrstvy.

Kromě toho je potřeba mít vždycky platné entity (viz téma [návrh ověření v oddílu vrstva doménového modelu](domain-model-layer-validations.md) ) řízené agregovanými kořeny (kořenové entity). Entity by proto neměly být vázány na zobrazení klientů, protože na úrovni uživatelského rozhraní mohou být některá data stále neověřena. To je to, pro který je ViewModel pro. ViewModel je datový model výhradně pro potřeby prezentační vrstvy. Entity domény nepatří přímo do rozhraní ViewModel. Místo toho je třeba překládat mezi ViewModels a doménovými entitami a naopak.

Při řešení složitosti je důležité mít doménový model řízený agregovanými kořeny, které zajistí, že všechny invariantní a pravidla související s touto skupinou entit (agregace) jsou prováděna prostřednictvím jediného vstupního bodu nebo brány, agregovaného kořene.

Obrázek 7-5 ukazuje, jak se v aplikaci eShopOnContainers implementuje vrstvený návrh.

![Tři vrstvy ve mikroslužbě DDD, jako je objednávání. Každá vrstva je projekt VS: Aplikační vrstva seřazení. API, vrstva domény se seřazením. doména a vrstva infrastruktury se seřazením. infrastruktura.](./media/image6.png)

**Obrázek 7-5**. DDD vrstev v eShopOnContainersu pro řazení mikroslužeb

Chcete navrhnout systém tak, aby každá vrstva komunikovala pouze s některými jinými vrstvami. To může být snazší vyhovět, pokud jsou vrstvy implementovány jako jiné knihovny tříd, protože můžete jasně určit, jaké závislosti jsou nastaveny mezi knihovnami. Například vrstva doménového modelu by neměla mít závislost na žádné jiné vrstvě (třídy doménového modelu by měly být prosté staré objekty CLR nebo [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object), třídy). Jak je znázorněno na obrázku 7-6, **seřazení** knihovny vrstev domény má závislosti pouze na knihovnách .NET Core nebo balíčcích NuGet, ale ne na žádné jiné vlastní knihovně, jako je například knihovna dat nebo knihovna trvalosti.

![Průzkumník řešení zobrazení řazení. závislosti domén, které ukazují, závisí pouze na knihovnách .NET Core.](./media/image7.png)

**Obrázek 7-6**. Vrstvy implementované jako knihovny umožňují lepší kontrolu závislostí mezi vrstvami.

### <a name="the-domain-model-layer"></a>Vrstva doménového modelu

Vynikající [návrh založený na doméně](https://domainlanguage.com/ddd/) Eric Evans uvádí následující informace o vrstvě doménového modelu a vrstvě aplikace.

**Vrstva doménového modelu**: Zodpovídá za reprezentaci konceptů podnikání, informací o obchodní situaci a obchodních pravidel. Stav, který odráží provozní situaci, se řídí a používá, i když jsou technické podrobnosti o jejich uložení delegovány na infrastrukturu. Tato vrstva je srdcem podnikového softwaru.

Vrstva doménového modelu je místo, kde se vyjadřuje podnikání. Při implementaci vrstvy modelu domény mikroslužeb v rozhraní .NET je tato vrstva kódována jako knihovna tříd s entitami domény, které zachycují chování dat a chování (metody s logikou).

Po [ignorování perzistence](https://deviq.com/persistence-ignorance/) a principu [ignorování infrastruktury](https://ayende.com/blog/3137/infrastructure-ignorance) musí tato vrstva zcela ignorovat podrobnosti o trvalosti dat. Tyto úlohy trvalosti by měly být provedeny vrstvou infrastruktury. Proto by tato vrstva neměla mít přímé závislosti na infrastruktuře, což znamená, že důležité pravidlo je, že třídy entit doménového modelu by měly být [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)s.

Entity domény by neměly mít žádné přímé závislosti (například odvozené od základní třídy) na jakémkoli rozhraní infrastruktury pro přístup k datům, jako je Entity Framework nebo NHibernate. V ideálním případě by vaše entity domény neměly odvozovat ani implementovat jakýkoli typ definovaný v žádném rozhraní infrastruktury.

Většina moderních rozhraní ORM, jako je Entity Framework Core, umožňují tento přístup, takže vaše třídy doménového modelu nejsou spojeny s infrastrukturou. Nicméně při použití určitých databází NoSQL a architektur, jako jsou aktéri a spolehlivé kolekce v Azure Service Fabric, ale POCO entity nejsou vždy možné.

I v případě, že je důležité dodržovat princip ignorování trvalosti pro doménový model, neměli byste ignorovat obavy o trvalosti. Pořád je důležité pochopit fyzický datový model a jak se mapuje na model objektu entity. V opačném případě můžete vytvořit neproveditelné návrhy.

To neznamená, že můžete vytvořit model navržený pro relační databázi a přímo ho přesunout do NoSQL nebo databáze orientované na dokument. V některých modelech entit se model může přizpůsobit, ale obvykle to není. K dispozici jsou i omezení, která musí splňovat váš model entity, a to na základě technologie úložiště i technologie ORM.

### <a name="the-application-layer"></a>Aplikační vrstva

Když se přesunete na aplikační vrstvu, můžeme znovu citovat [Návrh řízený](https://domainlanguage.com/ddd/)z Eric Evans v knize založené na doméně:

**Aplikační vrstva:** Definuje úlohy, které má software dělat, a směruje objekty pro vyjádření na zpracování problémů. Úkoly, za které je tato vrstva odpovědná, jsou smysluplné pro firmu nebo nutné pro interakci s aplikačními vrstvami jiných systémů. Tato vrstva je udržována tenká. Neobsahuje obchodní pravidla ani znalosti, ale koordinuje úlohy a delegáty fungují na spolupráci doménových objektů v další vrstvě. Neodráží stav, který odráží provozní situaci, ale může mít stav, který odráží průběh úkolu pro uživatele nebo program.

Aplikační vrstva mikroslužeb v rozhraní .NET je běžně kódována jako ASP.NET Core projekt webového rozhraní API. Projekt implementuje interakci mikroslužby, vzdálený přístup k síti a externí webová rozhraní API, která se používají z uživatelského rozhraní nebo klientských aplikací. Zahrnuje dotazy, pokud používáte přístup CQRS, příkazy akceptované mikroslužbou a dokonce i komunikaci řízenou událostmi mezi mikroslužbami (integračními událostmi). ASP.NET Core webové rozhraní API, které představuje aplikační vrstvu, nesmí obsahovat obchodní pravidla ani znalostní bázi domény (zejména pravidla domény pro transakce a aktualizace). Ty by měly být vlastněny knihovnou tříd doménového modelu. Aplikační vrstva musí koordinovat pouze úlohy a nesmí obsahovat ani definovat žádný stav domény (doménový model). Deleguje provádění obchodních pravidel pro samotné třídy doménového modelu (agregované kořeny a doménové entity), které budou nakonec aktualizovat data v těchto doménových entitách.

V podstatě aplikační logika je místo, kde implementujete všechny případy použití, které závisejí na daném front-endu. Například implementace týkající se služby webového rozhraní API.

Cílem je, aby doménová logika v úrovni doménového modelu, její invariantní, datového modelu a souvisejících obchodních pravidel musela být zcela nezávislá na prezentačních a aplikačních vrstvách. Ve většině případů nesmí vrstva doménového modelu přímo záviset na žádném rozhraní infrastruktury.

### <a name="the-infrastructure-layer"></a>Vrstva infrastruktury

Vrstva infrastruktury je způsob, jakým se data, která se zpočátku ukládají v doménových entitách (v paměti), ukládají v databázích nebo jiném trvalém úložišti. Příklad používá Entity Framework Core kód k implementaci tříd vzoru úložiště, které používají DBContext k uchování dat v relační databázi.

V souladu se zásadami pro [ignorování trvalého přetrvávání](https://deviq.com/persistence-ignorance/) a [ignorování infrastruktury](https://ayende.com/blog/3137/infrastructure-ignorance) nesmí vrstva infrastruktury "kontaminovat" vrstvu doménového modelu. Aby se třídy entit doménového modelu nezávislá z infrastruktury, která se používá k zachování dat (EF nebo jiných rozhraní), je nutné, aby nedošlo k nevynuceným závislostem na architekturách. Knihovna tříd vrstvy doménového modelu by měla mít jenom svůj doménový kód, stačí [POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object) třídy entit, které implementují srdcový software a kompletně se odpojí od technologií infrastruktury.

Proto by vaše vrstvy nebo knihovny tříd a projekty měly nakonec záviset na vaší vrstvě doménového modelu (knihovny), nikoli naopak, jak je znázorněno na obrázku 7-7.

![Závislosti v rámci služby na DDD závisí na doméně a infrastruktuře a infrastruktura závisí na doméně, ale doména není závislá na žádné vrstvě.](./media/image8.png)

**Obrázek 7-7**. Závislosti mezi vrstvami v DDD

Tento návrh vrstvy by měl být nezávislý na každé mikroslužbě. Jak bylo uvedeno dříve, můžete implementovat nejvíc komplexní mikroslužby za vzory DDD, zatímco při jednodušším způsobu implementace jednodušších mikroslužeb založených na datech (jednoduchá CRUD v jedné vrstvě).

#### <a name="additional-resources"></a>Další zdroje

- **DevIQ. Princip ignorování trvalosti** \
  <https://deviq.com/persistence-ignorance/>

- **Oren Eini. Ignorování infrastruktury** \
  <https://ayende.com/blog/3137/infrastructure-ignorance>

- **Angel Lopez. Vrstvená architektura v návrhu založeném na doméně** \
  <https://ajlopez.wordpress.com/2008/09/12/layered-architecture-in-domain-driven-design/>

>[!div class="step-by-step"]
>[Předchozí](cqrs-microservice-reads.md)Další
>[](microservice-domain-model.md)
