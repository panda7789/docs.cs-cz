---
title: Identifikace hranic mezi modelem a doménou u jednotlivých mikroslužeb
description: Prozkoumejte podstatu rozdělení velké aplikace do mikroslužeb k dosažení zvukové architektury.
ms.date: 09/20/2018
ms.openlocfilehash: 9c433066dd8e93dbb09b15e58c9c85617775723d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "71834417"
---
# <a name="identify-domain-model-boundaries-for-each-microservice"></a>Identifikovat hranice modelu domény pro každou mikroslužbu

Cílem při identifikaci hranice modelu a velikost pro každou mikroslužbu není získat nejvíce podrobné oddělení možné, i když byste měli tendenci k malé mikroslužeb, pokud je to možné. Místo toho by vaším cílem mělo být dostat se k nejsmysluplnějšímu oddělení vedenému znalostmi domény. Důraz není kladen na velikost, ale na obchodní možnosti. Kromě toho pokud je jasná soudržnost potřebné pro určitou oblast aplikace na základě vysokého počtu závislostí, který označuje potřebu jedné mikroslužby, taky. Soudržnost je způsob, jak zjistit, jak rozdělit nebo seskupit mikroslužeb. Nakonec při získání dalších znalostí o doméně, měli byste přizpůsobit velikost mikroslužeb, iterativně. Nalezení správné velikosti není jednorázový proces.

[Sam Newman](https://samnewman.io/), uznávaný propagátor mikroslužeb a autor knihy [Building Microservices](https://samnewman.io/books/building_microservices/), zdůrazňuje, že byste měli navrhnout mikroslužeb na základě vzoru ohraničeného kontextu (BC) (součást návrhu řízeného doménou), jak byl zaveden dříve. Někdy může být BC složena z několika fyzických služeb, ale ne naopak.

Model domény s konkrétními entitami domény platí v rámci konkrétní BC nebo mikroslužeb. Bc vymezuje použitelnost modelu domény a poskytuje členům vývojářského týmu jasné a sdílené pochopení toho, co musí být soudržné a co lze vyvíjet nezávisle. Jedná se o stejné cíle pro mikroslužby.

Dalším nástrojem, který informuje o vaší volbě návrhu, je [Conwayův zákon](https://en.wikipedia.org/wiki/Conway%27s_law), který uvádí, že aplikace bude odrážet sociální hranice organizace, která ji vyrobila. Ale někdy je opak pravdou -organizace společnosti je tvořena softwarem. Možná budete muset zvrátit Conwayův zákon a vybudovat hranice tak, jak chcete, aby společnost byla organizována, a přiklánět se k poradenství v oblasti obchodních procesů.

Chcete-li identifikovat ohraničené kontexty, můžete použít vzorek DDD nazvaný [vzor kontextové mapování](https://www.infoq.com/articles/ddd-contextmapping). Pomocí mapování kontextu můžete identifikovat různé kontexty v aplikaci a jejich hranice. Je běžné mít jiný kontext a hranice pro každý malý subsystém, například. Mapa kontextu je způsob, jak definovat a explicitní tyto hranice mezi doménami. Bc je autonomní a obsahuje podrobnosti o jedné doméně - podrobnosti, jako jsou entity domény - a definuje integrační smlouvy s jinými řadiči domény. To je podobné definici mikroslužby: je autonomní, implementuje určité funkce domény a musí poskytovat rozhraní. To je důvod, proč context mapping a ohraničený kontext vzor jsou dobré přístupy pro identifikaci hranice modelu domény mikroslužeb.

Při navrhování velké aplikace uvidíte, jak může být její model domény fragmentován – odborník na doménu z domény katalogu bude v doménách katalogu a inventáře například pojmenovávat entity jinak než odborník na doručovací doménu. Nebo entita domény uživatele se může lišit velikostí a počtem atributů při práci s odborníkem na CRM, který chce uložit každý detail o zákazníkovi než pro odborníka na objednávající doménu, který potřebuje pouze částečná data o zákazníkovi. Je velmi těžké rozptýlit všechny termíny domény ve všech doménách souvisejících s velkou aplikací. Ale nejdůležitější je, že byste se neměli snažit sjednotit podmínky. Místo toho přijměte rozdíly a bohatost poskytoanou jednotlivými doménami. Pokud se pokusíte mít jednotnou databázi pro celou aplikaci, pokusy o jednotný slovník bude nepříjemné a nebude znít právo na některý z více doménových odborníků. Proto bccs (implementované jako mikroslužeb) vám pomůže objasnit, kde můžete použít určité podmínky domény a kde budete muset rozdělit systém a vytvořit další řadiče domény s různými doménami.

Budete vědět, že máte správné hranice a velikosti každého modelu BC a domény, pokud máte několik silných vztahů mezi modely domény a obvykle nemusíte slučovat informace z více modelů domény při provádění typických operací aplikace .

Snad nejlepší odpověď na otázku, jak velký model domény pro každou mikroslužbu by měl být, je následující: měl by mít autonomní BC, co by bylo možné tak izolované, které vám umožní pracovat, aniž byste museli neustále přepínat do jiných kontextů (jiné mikroslužeb). Na obrázku 4-10 uvidíte, jak více mikroslužeb (více řadičů domény) každý má svůj vlastní model a jak jejich entity lze definovat, v závislosti na konkrétní požadavky pro každou z identifikovaných domén ve vaší aplikaci.

![Diagram znázorňující entity v několika hranicích modelu.](./media/identify-microservice-domain-model-boundaries/identify-entities-microservice-model-boundries.png)

**Obrázek 4-10**. Identifikace entit a hranic modelu mikroslužeb

Obrázek 4-10 znázorňuje ukázkový scénář související se systémem správy online konferencí. Stejná entita se zobrazí jako "Uživatelé", "Kupující", "Plátci" a "Zákazníci" v závislosti na ohraničeném kontextu. Identifikovali jste několik řadičů domény, které by mohly být implementovány jako mikroslužby, na základě domén, které pro vás definovali odborníci na doménu. Jak můžete vidět, existují entity, které jsou k dispozici pouze v jednom modelu mikroslužeb, jako jsou platby v mikroslužbě platby. Ty budou snadno realizovatelné.

Můžete však mít také entity, které mají jiný tvar, ale sdílejí stejnou identitu napříč více modely domén z více mikroslužeb. Například user entity je identifikován v mikroslužbě Správy konferencí. Stejný uživatel se stejnou identitou je ten, který je pojmenován kupující v objednávání mikroslužby, nebo ten s názvem Plátce v platební mikroslužby a dokonce i ten s názvem Zákazník v mikroslužbě služby zákazníkům. Důvodem je, že v závislosti na [všudypřítomném jazyce,](https://martinfowler.com/bliki/UbiquitousLanguage.html) který používá každý odborník domény, může mít uživatel jinou perspektivu i s různými atributy. Entita uživatele v modelu mikroslužeb s názvem Správa konferencí může mít většinu atributů svých osobních dat. Však stejný uživatel ve tvaru plátce v mikroslužeb platby nebo ve tvaru zákazníka v mikroslužeb zákaznický servis nemusí potřebovat stejný seznam atributů.

Podobný přístup je znázorněn na obrázku 4-11.

![Diagram znázorňující, jak rozložit datový model do více modelů domény.](./media/identify-microservice-domain-model-boundaries/decompose-traditional-data-models.png)

**Obrázek 4-11**. Rozklad tradičních datových modelů na více modelů domény

Při rozkladu tradiční datový model mezi ohraničené kontexty, můžete mít různé entity, které sdílejí stejnou identitu (kupující je také uživatel) s různými atributy v každém ohraničeném kontextu. Můžete vidět, jak je uživatel přítomen v modelu mikroslužeb správy konferencí jako entita User a je také k dispozici ve formě entity Kupující v cenové mikroslužbě, s alternativními atributy nebo podrobnosti o uživateli, když je ve skutečnosti kupující. Každá mikroslužba nebo BC nemusí potřebovat všechna data související s entitou Uživatele, jen její část, v závislosti na problému k vyřešení nebo kontextu. Například v modelu cenové mikroslužby nepotřebujete adresu nebo jméno uživatele, pouze ID (jako identitu) a stav, což bude mít vliv na slevy při stanovení cen licencí na kupujícího.

Entita Seat má stejný název, ale různé atributy v každém modelu domény. Seat však sdílí identitu na základě stejného ID, jak se děje s uživatelem a kupujícím.

V podstatě existuje sdílený koncept uživatele, který existuje ve více službách (doménách), které všechny sdílejí identitu tohoto uživatele. Ale v každém modelu domény může být další nebo různé podrobnosti o entitě uživatele. Proto musí existovat způsob, jak mapovat entitu uživatele z jedné domény (mikroslužby) do jiné.

Existuje několik výhod, které nesdílejí stejnou entitu uživatele se stejným počtem atributů napříč doménami. Jednou z výhod je snížit duplicitu, takže modely mikroslužeb nemají žádná data, která nepotřebují. Další výhodou je mít hlavní mikroslužbu, která vlastní určitý typ dat na entitu tak, aby aktualizace a dotazy pro tento typ dat jsou řízeny pouze této mikroslužby.

>[!div class="step-by-step"]
>[Předchozí](distributed-data-management.md)
>[další](direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md)
