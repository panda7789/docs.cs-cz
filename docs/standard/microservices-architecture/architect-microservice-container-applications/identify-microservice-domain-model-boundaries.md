---
title: Identifikace hranic mezi modelem a doménou u jednotlivých mikroslužeb
description: Prozkoumejte podstatu dělení rozsáhlé aplikace do mikroslužeb k dosažení Architektura zvuku.
ms.date: 09/20/2018
ms.openlocfilehash: aa903e13b20be1084fad60e6fb7bbb1c61403deb
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644395"
---
# <a name="identify-domain-model-boundaries-for-each-microservice"></a>Identifikace hranic mezi modelem a doménou u jednotlivých mikroslužeb

Cílem při identifikaci hranice modelu a velikosti u jednotlivých mikroslužeb není získat co nejpodrobnější oddělení je to možné, i když byste zpravidla směrem k malé mikroslužeb Pokud je to možné. Vaším cílem místo toho by mělo být získat smysluplných oddělení řídit své znalosti. Důraz není na velikosti, ale místo toho na obchodní možnosti. Kromě toho pokud není jasný soudržnosti potřebné pro určité oblasti signál aplikace založené na velký počet závislostí, určující potřebu mikroslužbě jeden příliš. Soudržnosti je způsob, jak identifikovat, jak rozdělit nebo skupiny společně mikroslužeb. Nakonec když získáte větší informace o doméně, přizpůsobte velikost mikroslužeb, zavádět postupně. Vyhledání správné velikosti není konečný procesu.

[SAM Newman](https://samnewman.io/), známá promoter mikroslužeb a autor knihy [vytváření Mikroslužeb](https://samnewman.io/books/building_microservices/), zvýrazní, měli byste navrhnout mikroslužby založena na vzoru ohraničená kontextu (BC) (součást návrhy řízené doménou), jak to je zavedeno dříve. V některých případech může BC skládá z několika fyzických služeb, ale ne naopak.

Doménový model s konkrétní doménu entity lze použít v rámci konkrétní BC nebo mikroslužeb. BC vymezuje použitelnosti doménový model a vývojáře poskytuje členům týmu, jasné a sdílené pochopení, co musíte mít získá na ucelenosti a co mohou být vytvořeny nezávisle na sobě. Jedná se o stejné cíle pro mikroslužby.

Dalším nástrojem, který informuje zvoleného návrhu je [Conwayův kodex](https://en.wikipedia.org/wiki/Conway%27s_law), která uvádí, že aplikace bude odrážet sociální hranice organizace, který jej vytvořil. Ale někdy je opakem true – organizace společnosti je tvořen přidáním tohoto softwaru. Můžete potřebovat reverse Conwayův kodex a vytvářet tak, jak chcete, aby společnosti uspořádání, hranice leaning směrem k consulting obchodní proces.

K identifikaci ohraničené kontexty, můžete použít vzor DDD volá [mapování kontextu vzoru](https://www.infoq.com/articles/ddd-contextmapping). S mapováním kontextu identifikaci různých kontextech v aplikaci a jejich ohraničení. Je běžné mít jiný kontext a hranic pro každý subsystém malý pro instanci. Mapa kontext je způsob, jak definovat a vytvořit explicitní tyto hranice mezi doménami. BC je autonomní obsahuje podrobnosti o jednu doménu – podrobnosti o stejně jako entity domény – a definuje smlouvy integrace s další BCs. Toto je podobná definici mikroslužby: je autonomní implementuje určité funkce domény a musí poskytovat rozhraní. To je důvod, proč mapování kontextu a ohraničená kontextu vzoru jsou dobré přístupy k určení hranic domény modelu mikroslužby.

Při navrhování rozsáhlé aplikace, uvidíte, jak můžete svůj model domény fragmentaci – entity odlišně v katalogu a inventáře domény než přesouvání domény odborné, bude název pro instanci odborné domény z domény katalogu. Nebo může být při zpracování komplexnějších odborné CRM, který chce uložit všechny podrobnosti o zákazníkovi než odborník pořadí domény, který potřebuje pouze částečná data o zákazníkovi jinou velikost a počet atributů entity uživatele domény. Je velmi obtížné rozpoznat všechny podmínky domény napříč všemi doménami související s velké aplikace. Ale nejdůležitější je, že by se neměl pokoušet sjednocení podmínky. Místo toho přijměte rozdíly a bohatost poskytované v každé doméně. Pokud se pokusíte k dispozici jednotný databáze pro celou aplikaci, pokusy o jednotné slovník bude nevhodnou a nebude zvukové právo na některý z více odborníky na domény. Proto BCs (implementované jako mikroslužeb) vám pomůže objasnit, kde můžete použít některé podmínky domény a kde je potřeba rozdělit systém a vytvořit další BCs pomocí různých doménách.

Budete vědět, že máte správný hranice a velikosti jednotlivých BC a doménový model Pokud máte několik silné vztahy mezi doménových modelů a provedete není obvykle nutné ke sloučení informací z několika doménových modelů při provádění operací Typická aplikace .

Možná nejlepší odpověď na otázku, jak velký má být model domény u jednotlivých mikroslužeb je následující: měl by mít autonomní BC, izolaci nejvíce, která umožňuje pracovat, aniž by museli neustále přepnout na jiné kontexty (ostatní modely na mikroslužbách). Obrázek 4 – 10 uvidíte jak různými mikroslužbami (více BCs) každý má své vlastní model a jak lze definovat jejich entity, v závislosti na konkrétních požadavcích pro jednotlivé identifikované domén ve vaší aplikaci.

![Entity v několika model hranice (ohraničených kontextech), kde stejné entity se zobrazí jako "Users", "Kupci", "Poplatníkům" a "Zákazníci" v závislosti na ohraničený kontext](./media/image10.png)

**Obrázek 4 – 10**. Identifikace entit a model hranic mikroslužby

Obrázek 4 – 10 znázorňuje vzorový scénář související se systému správy konferencí online. Když jste identifikovali několik BCs, které může být implementovány jako mikroslužeb, podle domén, které pro vás definováno odborníky na domény. Jak vidíte, jsou entity, které jsou k dispozici pouze v modelu jeden mikroslužby, stejně jako platby v mikroslužbách platby. Ty budou snadno se implementuje.

Můžete však také může mít entity, které mají jiný tvar ale sdílejí stejnou identitu napříč několika doménových modelů z několika mikroslužeb. Například je uživatel identifikován v mikroslužbě správy konferencí. Tomuto uživateli, se stejnou identitou, je ten pojmenují kupci mikroslužeb řazení nebo ten plátce pojmenují platby mikroslužeb a ještě jeden s názvem zákazníka v mikroslužeb zákaznických služeb. Důvodem je, že v závislosti na tom [všudypřítomná jazyka](https://martinfowler.com/bliki/UbiquitousLanguage.html) , že používá každé domény expert, uživatel může mít jiný pohled i s rozdílnými atributy. Uživatel entity v modelu mikroslužby s názvem správy konferencí mít asi většinu jeho atributy osobní údaje. Však nemusí tomuto uživateli ve tvaru plátce v mikroslužbách platbu nebo ve tvaru zákazníka v mikroslužbách služby zákazníkům stejným seznamem atributů.

Podobný přístup je znázorněn v obrázek 4 – 11.

![Když rozložení tradiční datový model mezi ohraničené kontexty, můžete mít různé entity, které sdílejí stejnou identitu (kupující je také uživatele) s rozdílnými atributy v jednotlivých ohraničených kontextech.](./media/image11.png)

**Obrázek 4 – 11**. Rozložení tradičních datových modelů do více doménových modelů

Uvidíte jak uživatel nachází v modelu mikroslužby správy konferencí jako entitu uživatele a je také k dispozici ve formě kupujících entity v mikroslužbě ceny s alternativní atributy nebo podrobnosti o uživateli, když je ve skutečnosti odběratele. Každá mikroslužba nebo BC nemusí všechna data související s entitou Uživatel, jenom část, v závislosti na problém, který chcete vyřešit nebo kontext. Například v modelu mikroslužby ceny, nepotřebujete adresu nebo jméno uživatele, stačí ID (identity) a stav, který bude mít vliv na slevy při ceny licencí na odběratele.

Licence entita má stejný název ale různé atributy v každé doménovém modelu. Ale licence sdílí identity na základě stejné ID, protože se stane s uživateli a odběratele.

V podstatě je sdílený koncept jako uživatel, který existuje ve více služeb (domény), které sdílejí identitě daného uživatele. Ale v každém modelu domény může být dalšími nebo jinými podrobnosti o entitu uživatele. Proto musí existovat způsob, jak mapovat entity uživatele z jedné domény (mikroslužeb) do jiného.

Existuje několik výhod nesdílí stejnou entitu uživatele se stejným číslem atributy napříč doménami. Jedním z důvodů je zmenšit jejich duplikování, tak, aby vyladěných modelů všechna data, která nejsou potřeba. Další výhodou dochází k danému hlavní mikroslužeb, která vlastní typ data pro jednotlivé entity tak, aby aktualizace a dotazy pro daný typ dat se řídí pouze tento mikroslužeb.

>[!div class="step-by-step"]
>[Předchozí](distributed-data-management.md)
>[další](direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md)
