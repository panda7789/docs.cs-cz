---
title: Navrhování orientované DDD mikroslužbu
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Navrhování orientované DDD mikroslužbu
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/06/2017
ms.openlocfilehash: 7793a3ffded788698fcbc4ba28edefde44268989
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105768"
---
# <a name="designing-a-ddd-oriented-microservice"></a>Navrhování orientované DDD mikroslužbu

Řízené domény návrhu (DDD) obhajuje modelování podle když ve skutečnosti firmy jako relevantní pro vaše případy použití. V rámci sestavení aplikací DDD zmíněn problémy jako domény. Popisuje nezávislé problémových oblastí jako ohraničenou kontexty (každý kontext ohraničenou koreluje s mikroslužbu) a klade důraz běžné jazyka, který má v souvislosti se tyto problémy. Rovněž nabízí mnoho technické koncepty a vzory, třeba domény entity s bohatou modely (žádné [modelu anemic domény](https://martinfowler.com/bliki/AnemicDomainModel.html)), hodnota objekty, agregace a agregační kořenové (nebo kořenové entity) pravidla pro podporu interní implementace. Tato část představuje návrh a implementaci tyto interní vzorce.

Tyto technické pravidla DDD a vzory jsou někdy považován za překážky, které mají zvládnutí křivku pro implementaci DDD přístupy. Ale je důležitou součástí není vzorky sami, ale uspořádání kód, takže je umístěno na obchodní problémy a pomocí stejných podmínek firmy (všudypřítomný language). Kromě toho DDD přístupy bude použito pouze v případě, že implementujete komplexní mikroslužeb s významné obchodní pravidla. Jednodušší odpovědnosti, jako je služba CRUD, lze spravovat pomocí jednodušší přístupy.

Kde kreslení hranice je klíče úloha při návrhu a definování mikroslužby. DDD vzory vám pomohou porozumět složitost v doméně. Pro model domény pro každý kontext ohraničenou identifikovat a definovat entity, hodnota objekty a agregace, které modelu domény. Sestavení a upřesněte modelu domény, který je obsažen v rámci hranice, která definuje váš kontext. A který bude velmi explicitní ve formě mikroslužby. Součásti v rámci těchto hranicích skončili se mikroslužeb, i když v některých případech a BC nebo obchodní mikroslužeb se může skládat z několika fyzických služeb. DDD je o hranice a proto nejsou mikroslužeb.

## <a name="keep-the-microservice-context-boundaries-relatively-small"></a>Zachovat mikroslužbu kontextu hranice poměrně malý

Určení, kam umístit hranice mezi ohraničenou kontexty vyrovnává dvě konkurenční cíle. Nejprve chcete nejprve vytvořit nejmenší možné mikroslužeb, i když, který by neměl být hlavní ovladač; měli byste vytvořit hranici kolem věcí, které je třeba soudržnost. Druhý budete chtít vyhnout chatty komunikace mezi mikroslužeb. Těchto cílů může být v rozporu jednu na druhou. Je měli vyvážit podle decomposing systému do tolik malé mikroslužeb, jako je možné, dokud neuvidíte komunikace hranice narůstají rychle s každou další pokus o oddělení nový kontext vázaný. Soudržnost se klíč v rámci jedné ohraničené kontextu.

Je podobná [pach kód nepotřebnými Intimacy](https://sourcemaking.com/refactoring/smells/inappropriate-intimacy) při implementaci třídy. Pokud dva mikroslužeb potřebovat mnoho vzájemnou spolupráci, měly by být pravděpodobně stejné mikroslužby.

Dalším způsobem podívejte se na to je nezávislé. Pokud mikroslužbu musíte spoléhat na jiné služby pro přímo obsloužit požadavek, není skutečně autonomní.

## <a name="layers-in-ddd-microservices"></a>Vrstvy v DDD mikroslužeb

Většina aplikací enterprise významné obchodních a technických složitosti jsou definovány více vrstev. Vrstvy, které jsou logické artefaktů a nesouvisí se nasazení služby. Existují, což vývojářům zvládnout složité v kódu. Různé vrstvy (jako vrstva modelu domény oproti prezentační vrstvy, atd.) může mít různé typy, které vyžaduje převody mezi tyto typy.

Například může entity načíst z databáze. Součástí těchto informací nebo agregaci informace, včetně další data z jinými entitami, potom můžete odeslat klientovi uživatelského rozhraní pomocí webového rozhraní API REST. Bodem tady je, že entita domény je obsažena v vrstva modelu domény a neměli rozšíří do jiných oblastí, které nepatří, jako je třeba do prezentační vrstvy.

Kromě toho je potřeba mít vždy platné entity (najdete v článku [navrhování ověření ve vrstvě modelu domény](#designing-validations-in-the-domain-model-layer) část) řízené agregační kořenových certifikačních autorit (kořenové entity). Proto entity by neměl být vázána na zobrazení klientů, protože úrovni uživatelského rozhraní nemusí stále ověřit některá data. Toto je, co ViewModel je. ViewModel je datový model výhradně pro potřeby prezentační vrstvy. Domény entity, které nejsou členy přímo ViewModel. Místo toho musíte k převodu mezi ViewModels a domény entity a naopak.

Při boji se složitost, je důležité mít modelu domény řídí agregační kořeny, které se ujistěte, že všechny výstupních podmínek a pravidel, vztahuje k této skupině entit (agregační) prováděno prostřednictvím jeden vstupní bod nebo brány, kořenu agregační.

Obrázek 9-5 ukazuje, jak je implementována vrstvený návrh v aplikaci eShopOnContainers.

![](./media/image6.png)

**Obrázek 9-5**. DDD vrstvy v řazení mikroslužbu v eShopOnContainers

Chcete navrhnout systému tak, aby každé vrstvě komunikuje jenom s některých jiných vrstev. Které mohou být snazší vynutit v případě, že vrstvy jsou implementované jako jinou třídu knihovny, protože jasně zjistíte, jaké závislosti jsou nastaveny mezi knihovny. Například vrstva modelu domény by neměly být závislý na další vrstvou (třídy modelu domény by měl být prostý staré objekty CLR nebo [objektů POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object), třídy). Jak je znázorněno na obrázku 9-6 **Ordering.Domain** vrstvy knihovny má závislosti, jenom na knihovny .NET Core nebo balíčky NuGet, ale ne na jiných vlastní knihovny, například data knihovnu nebo trvalost.

![](./media/image7.PNG)

**Obrázek 9-6**. Vrstvy, které jsou implementované jako knihovny umožňují lepší kontrolu nad závislosti mezi vrstvami

### <a name="the-domain-model-layer"></a>Vrstva modelu domény

Zařízení Erica Evans vynikající kniha [řízené návrhu domény](https://domainlanguage.com/ddd/) s následujícím textem o vrstva modelu domény a aplikační vrstvu.

**Vrstva modelu domény**: zodpovědná za představující koncepty firmy, informace o obchodní situaci a obchodní pravidla. Stav, který se vztahuje k obchodní situaci je řízena a použít se zde, i když jsou delegovanými technické informace o ukládání do infrastruktury. Tato vrstva jsou srdcem obchodní softwaru.

Vrstva modelu domény je, kde je vyjádřen firmy. Pokud implementujete vrstva mikroslužbu domény modelu v rozhraní .NET, této vrstvy je zakódovaný jako knihovny tříd s entitami domény, které zaznamenání dat a chování (metody s logiku).

Následující [trvalost které](http://deviq.com/persistence-ignorance/) a [infrastruktury, které](https://ayende.com/blog/3137/infrastructure-ignorance) zásady, tato vrstva musí být zcela ignorovat podrobnosti trvalosti dat. Vrstvě infrastruktury by měli provádět tyto úlohy trvalost. Proto tuto vrstvu by neměl trvat přímé závislosti na infrastruktuře, což znamená, že pravidlo důležité je, že by měl být tříd domény modelu entity [objektů POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)s.

Entity domény by neměl mít žádné přímé závislosti (např. odvozování od třídy base) na libovolnou architekturu data přístup infrastruktury jako Entity Framework nebo NHibernate. V ideálním případě by neměl odvozena z vaší domény entity nebo jsou implementovány libovolného typu definované v libovolnou architekturu infrastruktury.

Většina moderních ORM architektury, jako je Entity Framework Core povolit tuto metodu tak, aby tříd modelu domény nejsou doplněná infrastruktury. Nicméně s entity objektů POCO není vždy možné při použití určitých databáze NoSQL a rozhraní, jako je aktéři a spolehlivé kolekcí v Azure Service Fabric.

I v případě, že je důležité dodržet zásadu které trvalosti pro domény model, by neměl ignorovat trvalost otázky. Stále je velmi důležité, abyste pochopili, fyzický datový model a jak se mapuje na objekt modelu entity. V opačném případě můžete vytvořit možné návrhů.

Navíc neznamená to můžete provést model určený pro relační databázi a přímo ho přesunout do NoSQL nebo orientované dokumentu databáze. V některých modelů entity může přizpůsobit modelu, ale obvykle je nepoužívá. Stále existují omezení, která musí splňovat modelu entity na základě technologie úložiště a ORM technologie.

### <a name="the-application-layer"></a>Aplikační vrstvu

Přejdete na aplikační vrstvu, jsme můžete znovu cite zařízení Erica Evans kniha [řízené návrhu domény](https://domainlanguage.com/ddd/):

**Aplikační vrstvu:** definuje úloh softwaru by měla provést a přesměruje objekty výrazovou domény k vyřešení problémů. Úlohy, které tuto vrstvu zodpovídá za jsou důležité pro jejich podnikání nebo potřebné pro interakci s aplikačními vrstvami jiných systémů. Tuto vrstvu je udržováno dynamické. Neobsahuje obchodní pravidla nebo znalostní báze, ale pouze souřadnice úlohy a delegáti spolupracovat na spolupráce objektů domény v další vrstva dolů. Nemá stav odrážející stav firmy, ale může mít stav, který zobrazuje průběh úlohy pro uživatele nebo program.

Mikroslužbu na aplikační vrstvu v rozhraní .NET je běžně programového jako projekt webového rozhraní API ASP.NET Core. Projekt implementuje interakce mikroslužbu, vzdálený přístup k síti a externí webovým rozhraním API používá z aplikací uživatelského rozhraní nebo klienta. Pokud pomocí CQRS přístupu příkazy přijatý mikroslužbu a i událostmi řízené komunikace mezi mikroslužeb (integrace událostí) obsahuje dotazy. Rozhraní ASP.NET Web API Core, který představuje aplikační vrstvu nesmí obsahovat obchodní pravidla a znalosti domény (zejména domény pravidla pro transakce nebo aktualizace); Tyto vlastníkem by měl být knihovny tříd modelu domény. Souřadnice pouze aplikace vrstvy musí úloh a nesmí obsahovat nebo definovat stav všechny domény (modelu domény). Deleguje provádění obchodní pravidla domény modelu třídy sami (agregační kořeny a entity domény), které bude nakonec aktualizovat data v rámci těchto domény entity.

Logiku aplikace je v podstatě, kde budete implementovat všechny případy použití, které jsou závislé na danou front-end. Například implementace související s webového rozhraní API služby.

Cílem je, že logiku domény v vrstva modelu domény, jeho výstupních podmínek, datový model a související obchodní pravidla musí být zcela nezávislé na vrstvy prezentace a aplikace. Vrstva modelu domény nesmí nejvíce všech, závisí přímo na libovolnou architekturu infrastruktury.

### <a name="the-infrastructure-layer"></a>Vrstvě infrastruktury

Vrstvě infrastruktury je, jak je databáze nebo jiného trvalé úložiště trvalá data, která je původně uchovávat v doméně entity (v paměti). Příklad používá Entity Framework Core kód pro implementaci třídy vzor úložiště, které pomocí konstruktoru DBContext lze zachovat data z relační databáze.

V souladu s výše uvedených [trvalost které](http://deviq.com/persistence-ignorance/) a [infrastruktury které](https://ayende.com/blog/3137/infrastructure-ignorance) zásady, vrstvě infrastruktury nesmí "kontaminovat" vrstva modelu domény. Je nutné zachovat třídy vznikl domény modelu entity z infrastruktury, který používáte k zachování dat (EF nebo jiných framework) není provedením pevný závislosti na rozhraní. Knihovny tříd vrstvy modelu domény by měl mít jenom kódu domény, právě [objektů POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object) entity třídy implementace srdcem váš software a úplně odpojená od technologií infrastruktury.

Proto vrstvy nebo knihovny tříd a projekty by měl nakonec záviset na vrstvě modelu domény (knihovna), ne naopak, jak je znázorněno na obrázku 9-7.

![](./media/image8.png)

**Obrázek 9-7**. Závislosti mezi vrstvy v DDD

Tento návrh vrstvy musí být pro každý mikroslužbu nezávislé. Jak již bylo uvedeno dříve, můžete implementovat těch nejsložitějších mikroslužeb následující vzory DDD, při implementaci jednodušší řízené daty mikroslužeb (jednoduché CRUD v jedné vrstvě) v jednodušší způsob.

#### <a name="additional-resources"></a>Další zdroje

-   **DevIQ. Princip které trvalost**
    [*http://deviq.com/persistence-ignorance/*](http://deviq.com/persistence-ignorance/)

-   **Oren Eini. Které infrastruktury**
    [*https://ayende.com/blog/3137/infrastructure-ignorance*](https://ayende.com/blog/3137/infrastructure-ignorance)

-   **Anděl Lopez. Vrstvená architektura v řízené domény návrhu**
    [*https://ajlopez.wordpress.com/2008/09/12/layered-architecture-in-domain-driven-design/*](https://ajlopez.wordpress.com/2008/09/12/layered-architecture-in-domain-driven-design/)


>[!div class="step-by-step"]
[Předchozí](cqrs-microservice-reads.md)
[další](microservice-domain-model.md)
