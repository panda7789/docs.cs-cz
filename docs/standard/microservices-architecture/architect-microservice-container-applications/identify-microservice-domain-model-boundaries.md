---
title: "Identifikace modelu domény hranice pro každou mikroslužbu"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Identifikace modelu domény hranice pro každou mikroslužbu"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 6fef11e5718706701abb29149c4c4a23ba39bde0
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="identify-domain-model-boundaries-for-each-microservice"></a>Určení modelu domény hranice pro každou mikroslužbu

Cílem při identifikaci hranice modelu a velikost každé mikroslužbu je nechcete dostávat nejvíce granulární oddělení možné, i když má mívají směrem k malé mikroslužeb Pokud je to možné. Místo toho vaším cílem mělo být pro zajištění smysluplných oddělení provést podle vašich znalostí domény. Důraz na velikost, ale místo toho na není obchodní možnosti. Kromě toho pokud je zrušte soudržnost potřebné pro určité oblasti aplikace založené na velký počet závislostí, určující potřebu jeden mikroslužbu, příliš. Soudržnost je způsob, jak identifikovat tom, jak rozdělit nebo skupiny společně mikroslužeb. Nakonec zatímco, získáte další informace o doméně, přizpůsobte velikost vašeho mikroslužbu interaktivně. Hledání správnou velikost není jednorázové procesu.

[SAM Newman](http://samnewman.io/), rozpoznaný vykonavatel mikroslužeb a autor knihy [vytváření Mikroslužeb](http://samnewman.io/books/building_microservices/), označuje, měli byste navrhnout vaše mikroslužeb na základě vzoru ohraničenou kontextu (BC) (součást řízené domény návrhu), zavedeném dříve. V některých případech může BC skládá z několika fyzických služeb, ale ne naopak.

Model domény s konkrétní doménu entity lze použít v rámci konkrétní BC nebo mikroslužby. BC vymezuje použitelnost modelu domény a vývojáře poskytuje členové týmu, zrušte a sdílené vysvětlení, co musí být získá na ucelenosti a co mohou být vytvořeny nezávisle. Jedná se o stejné cíle pro mikroslužeb.

Jiný nástroj, který informuje zvoleného návrhu se [na Conwayovu zákonem](https://en.wikipedia.org/wiki/Conway%27s_law), který uvádí, že aplikace bude odrážet sociálních hranice organizace, která je vytvořena. Ale v některých případech je true jako opak – společnosti organizace je vytvořen softwarem. Může musíte obrátit na Conwayovu zákony a vytvoření hranice způsob, jakým chcete společnosti k uspořádání, leaning směrem k poradě obchodní proces.

Aby bylo možné identifikovat ohraničené kontexty, DDD vzor, který lze použít pro toto je [kontextu mapování vzor](https://www.infoq.com/articles/ddd-contextmapping). Pomocí kontextu mapování identifikujete různé kontexty v aplikaci a jejich hranice. Je běžně používají různé kontextu a hranice pro každou malé subsystém pro instanci. Mapa kontextu je způsob, jak definovat a proveďte explicitní tyto hranice mezi doménami. Autonomní a zahrnuje podrobnosti o na jednu doménu BC – podrobnosti, jako entity domény – a definuje kontrakty integrace s další BCs. Toto je podobná definici mikroslužbu: je autonomního, implementuje určité funkce domény a je nutné zadat rozhraní. Z tohoto důvodu mapování kontextu a vzoru ohraničenou kontextu jsou dobrou přístupy k identifikaci hranice vaší mikroslužeb modelu domény.

Při navrhování rozsáhlé aplikace, se zobrazí, jak může být jeho modelu domény fragmentované – expert domény z domény katalog bude název entity jinak v doménách katalogu a inventáře než odborné, přesouvání domény pro instanci. Nebo může být při plánování práce s odborné CRM, který chce uložit všechny podrobnosti o zákazníkovi, než pro řazení expert domény, který právě potřebuje částečná data o zákazníkovi liší velikost a počet atributů entita domény uživatele. Je velmi obtížné rozlišení podmínky pro všechny domény napříč všemi doménami související s rozsáhlé aplikace. Ale většina důležité je, že by se neměl pokoušet sjednocení podmínky; Místo toho přijměte rozdíly a bohatost poskytované každou doménu. Pokud se pokusíte mít jednotná databázi pro celou aplikaci, pokusů na jednotné termínů bude nevhodných a nebude zvukových správné k některému z více odborníky domény. Proto BCs (implementovaný jako mikroslužeb) vám pomůže o vysvětlení, kde můžete použít určité podmínky domény a kde budete muset rozdělení systému a vytvořte další BCs v různých doménách.

Budete vědět, že jste získali správné hranic a velikosti jednotlivých BC a modelu domény Pokud máte několik silné vztahy mezi modely domény, a proveďte není obvykle nutné sloučit informace z více modelů domény při provádění Typická aplikace operace.

Možná nejlepší odpověď na otázku, jak velký má být model domény pro každou mikroslužbu je následující: autonomní BC, musí mít jako izolované nejdříve, který umožňuje pracovat bez nutnosti neustále přepnout do jiných kontextech (jiné mikroslužbu na modelů). Obrázek 4 – 10 uvidíte jak více mikroslužeb (více BCs) každou mají své vlastní modelu a jak lze definovat jejich entity, v závislosti na konkrétních požadavcích pro každý zjištěný domén ve vaší aplikaci.

![](./media/image10.png)

**Obrázek 4 – 10**. Identifikace entity a mikroslužbu modelu hranice

Obrázek 4 – 10 znázorňuje vzorový scénář související do systému správy online konference. Určili jste několik BCs, které by mohly být implementovány jako mikroslužeb, podle domén, které domény odborníky definované za vás. Jak je vidět, existují entit, které jsou k dispozici jenom v jedné mikroslužbu modelu, jako plateb v mikroslužbu platebních. Budou snadno implementovat.

Můžete však také může mít entit, které mají různé obrazce ale sdílejí stejnou identitu napříč více modelů domény z více mikroslužeb. Například entitu uživatele je definovaný v mikroslužbu konferencí správy. Tomuto uživateli, se stejnou identitou, je ten s názvem kupující v mikroslužbu řazení, nebo jednu s názvem plátce v mikroslužbu platby a i jednu s názvem zákazníka v oddělení služeb zákazníkům mikroslužby. Důvodem je, že v závislosti na [všudypřítomný jazyk](https://martinfowler.com/bliki/UbiquitousLanguage.html) , používá expert každé domény, uživatel může mít různé perspektivy i přes různé atributy. Entitu uživatele v modelu mikroslužbu s názvem konferencí správu mít asi většinu jeho atributy osobní data. Tomuto uživateli ve tvaru plátce v mikroslužbu platebních nebo ve tvaru zákazníka v mikroslužbu oddělení služeb zákazníkům však nemusí stejný seznam atributů.

Podobný postup je zobrazená v obrázek 4-11.

![](./media/image11.png)

**Obrázek 4-11**. Decomposing tradiční datové modely do více domény modelů

Uvidíte, jak uživatel nachází v modelu správy konferencí mikroslužbu jako entitu uživatele a také se nachází ve formě kupujících entity v cenová mikroslužbu, s alternativní atributy nebo podrobnosti o uživateli, pokud je ve skutečnosti kupujících. Každé mikroslužbu nebo BC nemusí všechna data související s entitu uživatele, právě součástí, podle toho, problém lze vyřešit nebo kontextu. Například v modelu mikroslužbu cenová, není nutné adresu nebo ID uživatele, stačí ID (identity) a stav, který bude mít dopad na slevy při ceny licencí za kupujících.

Stanici entita, která má stejný název ale různé atributy v každém modelu domény. Ale stanici sdílí identity na základě stejné ID, jak se stane s uživatelů a kupujících.

V podstatě je sdílený koncept uživatele, který v několika služeb (domény), které sdílet identitu tohoto uživatele existuje. Ale v každé doméně modelu může být další nebo jiné podrobnosti o entitu uživatele. Proto je potřeba mapováním entitu uživatele z jedné domény (mikroslužbu) do jiné.

Existuje několik výhod není sdílení stejnou entitu uživatele se stejným číslem atributů napříč doménami. Jedním z důvodů je snížit duplikaci tak, aby modely mikroslužbu neobsahuje žádná data, která není nutné. Mezi další výhody má hlavní mikroslužbu, vlastnící určitý typ dat na entity tak, aby aktualizace a dotazů pro tento typ dat se řídí pouze tento mikroslužby.


>[!div class="step-by-step"]
[Předchozí] (distribuované data-management.md) [Další] (direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md)
