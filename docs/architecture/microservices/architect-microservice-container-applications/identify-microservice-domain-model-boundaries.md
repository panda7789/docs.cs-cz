---
title: Identifikace hranic doménových modelů pro jednotlivé mikroslužby
description: Prozkoumejte podstatu rozdělení velké aplikace na mikroslužby, aby se dosáhlo zvukové architektury.
ms.date: 09/20/2018
ms.openlocfilehash: 9c433066dd8e93dbb09b15e58c9c85617775723d
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834417"
---
# <a name="identify-domain-model-boundaries-for-each-microservice"></a>Identifikujte hranice doménového modelu pro jednotlivé mikroslužby.

Cíl, který identifikuje hranice modelu a velikost pro jednotlivé mikroslužby, se nedostane k nejpřesnější oddělitelné, i když je to možné, i když je to možné, měli byste se obrátit na malé mikroslužby. Místo toho by měl být vaším cílem získat nejsmysluplnější oddělení, které vás provedou znalostmi vaší domény. Důraz není na velikost, ale místo na obchodních funkcích. Pokud je navíc k dispozici jasná soudržnost pro určitou oblast aplikace na základě vysokého počtu závislostí, znamená to, že je to také potřeba pro jednu mikroslužbu. Soudržnost je způsob, jak určit, jak rozdělit nebo seskupit mikroslužby. I když získáte větší znalosti o doméně, měli byste ji v případě iterativní velikosti přizpůsobit. Vyhledání správné velikosti není proces jednoho snímku.

[Sam Newman](https://samnewman.io/), uznávaná propagace mikroslužeb a autorů knih [sestavování mikroslužeb](https://samnewman.io/books/building_microservices/), zdůrazňuje, že byste měli navrhovat mikroslužby založené na vzoru ohraničeného kontextu (Bc) (součást návrhu založeného na doméně), jak je představena nejdříve. V některých případech může být BC tvořen několika fyzickými službami, ale nikoli naopak.

Doménový model s konkrétními doménovými entitami platí v rámci konkrétního BC nebo mikroslužby. Množina BC odděluje použitelnost doménového modelu a členům týmu vývojářů poskytuje jasné a sdílené vysvětlení toho, co musí být soudržné a co se dá vyvíjet nezávisle. Jedná se o stejné cíle jako u mikroslužeb.

Dalším nástrojem, který je v souladu s návrhem, je [právo na Conwayův kodex](https://en.wikipedia.org/wiki/Conway%27s_law), které uvádí, že aplikace bude odrážet hranice sociálních organizací, které ji vytvořily. Ale v některých případech má opak hodnotu true – organizace je vytvořená softwarem. Je možné, že budete muset obrátit zákon na Conwayův kodex a vytvořit hranice tak, jak chcete, aby společnost byla uspořádána do konzultačních procesů obchodních procesů.

Chcete-li identifikovat ohraničené kontexty, můžete použít vzor DDD pojmenovaný [vzor mapování kontextu](https://www.infoq.com/articles/ddd-contextmapping). Pomocí mapování kontextu identifikujete různé kontexty v aplikaci a jejich hranice. Je běžné mít jiný kontext a hranici pro každý malý podsystém, například. Mapování kontextu je způsob, jak definovat a zadat explicitní hranice mezi doménami. BC je autonomní a obsahuje podrobnosti o jednotlivých doménových detailech, jako jsou například entity domény – a definuje kontrakty integrace s jinou službou BCs. To je podobné jako definice mikroslužeb: je to autonomní, implementuje určitou doménovou schopnost a musí poskytovat rozhraní. To je důvod, proč mapování kontextu a vzor vázaného kontextu jsou dobré přístupy k identifikaci hranic doménových modelů vašich mikroslužeb.

Když navrhujete velkou aplikaci, zjistíte, jak se dá rozdělit jeho doménový model – odborník na doménu z domény katalogu bude v katalogu a v doménách katalogu pojmenovat entity jinak, než je odborník na doménu pro expedici. Nebo entita domény uživatele se může lišit v velikosti a počtu atributů při práci s odborníkem na CRM, který chce uložit všechny podrobnosti o zákazníkovi, než pro odborníka na doménu, který právě potřebuje částečná data o zákazníkovi. Je velmi obtížné rozlišit všechny doménové oblasti napříč všemi doménami, které se vztahují k velké aplikaci. Nejdůležitějším aspektem je, že byste se neměli pokoušet sjednotit tyto výrazy. Místo toho přijměte rozdíly a bohatosti poskytované jednotlivými doménami. Pokud se pokusíte mít sjednocenou databázi pro celou aplikaci, pokusy na sjednoceném slovníku budou nevhodné a nebudou se jednat o zvukové právo na žádného odborníka na více domén. Proto služba BCs (implementovaná jako mikroslužby) vám pomůže objasnit, kde můžete použít určité doménové smlouvy, a kde budete muset rozdělit systém a vytvořit další službu BCs s různými doménami.

Dozvíte se, že máte správné hranice a velikosti jednotlivých modelů BC a domén, pokud máte několik silných vztahů mezi doménovými modely a nepotřebujete při provádění typických operací s aplikacemi obvykle sloučit informace z více doménových modelů. .

Možná nejlepší odpověď na otázku, jak velký doménový model pro jednotlivé mikroslužby by měl být následující: by měl mít autonomní nadmnožinu BC, jak je izolovaný, což vám umožní pracovat bez nutnosti nepřetržitě přepínat na jiné kontexty (jiné modely mikroslužeb). Na obrázku 4-10 vidíte, jak různé mikroslužby (více BCs) mají svůj vlastní model a jak se jejich entity dají definovat, v závislosti na konkrétních požadavcích pro jednotlivé identifikované domény ve vaší aplikaci.

![Diagram znázorňující entity v několika hranicích modelu](./media/identify-microservice-domain-model-boundaries/identify-entities-microservice-model-boundries.png)

**Obrázek 4-10**. Identifikace entit a hranic modelu mikroslužeb

Obrázek 4-10 znázorňuje vzorový scénář týkající se systému správy online konferencí. Stejná entita se zobrazí jako "uživatelé", "nákupčí", "Payers" a "zákazníci" v závislosti na ohraničeném kontextu. Identifikovali jste několik BCs, které by se daly implementovat jako mikroslužby, a to na základě domén, které vám odborníci na doménu definovali. Jak vidíte, existují entity, které jsou přítomny pouze v jednom modelu mikroslužby, jako jsou platby v mikroslužbě plateb. Ty budou snadno implementovány.

Můžete ale také mít entity, které mají jiný tvar, ale sdílet stejnou identitu napříč různými doménovými modely z více mikroslužeb. Například entita uživatele je identifikována v mikroslužbě správy konferencí. Stejný uživatel se stejnou identitou je ten, který se jmenuje Customers v rámci objednávání mikroslužby, nebo druhý s názvem plátce v rámci platební služby a dokonce i ten, kdo je v mikroslužbě Customer Service pro zákazníky. Důvodem je to, že v závislosti na [jazyku všudypřítomný](https://martinfowler.com/bliki/UbiquitousLanguage.html) , který používá každý odborník domény, může mít uživatel jinou perspektivu i s různými atributy. Entita uživatele v modelu mikroslužeb s názvem konference může mít většinu svých atributů osobních dat. Stejný uživatel ale v rámci platby plátce v platební službě nebo ve tvaru zákazníka ve službě pro zákazníky mikroslužeb ale nemusí potřebovat stejný seznam atributů.

Podobný přístup je znázorněný na obrázku 4-11.

![Diagram znázorňující, jak rozložit datový model do více doménových modelů](./media/identify-microservice-domain-model-boundaries/decompose-traditional-data-models.png)

**Obrázek 4-11**. Deskládání tradičních datových modelů do několika doménových modelů

Při deskládání tradičního datového modelu mezi ohraničenými kontexty můžete mít různé entity, které sdílejí stejnou identitu (kupující je také uživatel) s různými atributy v každém ohraničeném kontextu. Můžete zjistit, jak se uživatel nachází v modelu mikroslužeb správy konferencí, jako uživatelskou entitu a také ve formě entity nákupčího v rámci cenové služby cen, s alternativními atributy nebo podrobnostmi o uživateli, když je ve skutečnosti kupující. Každá mikroslužba nebo BC nemusí potřebovat všechna data související s entitou uživatele, a to jenom v závislosti na problému, který chcete vyřešit, nebo v kontextu. Například v modelu cenové služby Price nepotřebujete adresu ani jméno uživatele, jenom ID (jako identitu) a stav, což bude mít dopad na slevy při cenách za počet míst na odběratele.

Entita sedadla má stejný název, ale různé atributy v každém doménovém modelu. Sdílí ale identitu na základě stejného ID, co se stane se jménem uživatele a nákupčího.

V podstatě existuje sdílený koncept uživatele, který existuje ve více službách (doménách), které všechny sdílí identitu daného uživatele. V každém modelu domény ale můžou být informace o entitě uživatele další nebo jiné. Proto musí být k dispozici způsob, jak namapovat entitu uživatele z jedné domény (mikroslužba) na jinou.

Existuje několik výhod, které nesdílí stejnou entitu uživatele se stejným počtem atributů napříč doménami. Jednou z výhod je omezit duplicity, aby modely mikroslužeb nemusely mít žádná data, která nepotřebují. Další výhodou je mít hlavní mikroslužbu, která vlastní určitý typ dat na entitu, aby aktualizace a dotazy pro tento typ dat byly řízené pouze touto mikroslužbou.

>[!div class="step-by-step"]
>[Předchozí](distributed-data-management.md)@no__t – 1 –[Další](direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md)
