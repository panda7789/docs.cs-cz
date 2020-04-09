---
title: Úvod k aplikacím nativním pro cloud
description: Další informace o cloudově nativním výpočetním techniku
author: robvet
ms.date: 08/26/2019
ms.openlocfilehash: c9ffd34ec3deb04abddbbf85a9e5a6ed2b57c8f9
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989048"
---
# <a name="introduction-to-cloud-native-applications"></a>Úvod k aplikacím nativním pro cloud

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Další den, v kanceláři, pracuje na "další velké věci."

Zazvoní ti mobil. Je to tvůj přátelský náborář, ten, co ti dvakrát denně volá kvůli nové práci.

Ale tentokrát je to jiné: Start-up, spravedlnost a spousta finančních prostředků.

Zmínka o cloudu a špičkové technologii vás posouvá přes okraj.

Rychlý posun vpřed několik týdnů a vy jste nyní nový zaměstnanec v návrhu zasedání architekta hlavní eCommerce aplikace. Budete kompletní s dalšími předními eCommerce stránky.

Jak to postavíš?

Pokud se budete řídit pokyny z posledních 15 let, budete s největší pravděpodobností stavět systém uvedený na obrázku 1.1.

![Tradiční monolitický design](./media/monolithic-design.png)

**Obrázek 1-1**. Tradiční monolitický design

Vytvořit velké základní aplikace obsahující všechny logiky domény. Obsahuje moduly, jako je identita, katalog, řazení a další. Základní aplikace komunikuje s velkou relační databází. Jádro poskytuje funkce prostřednictvím rozhraní HTML.

Blahopřejeme!  Právě jste vytvořili monolitickou aplikaci.

Ne všechno je špatné. Monolity nabízejí některé zřetelné výhody. Například, oni jsou přímočaré ...

- sestavení
- test
- Nasazení
- troubleshoot
- scale

Mnoho úspěšných aplikací, které existují dnes byly vytvořeny jako monolity. Aplikace je hit a nadále se vyvíjí, iterace po iteraci, přidání další a další funkce.

V určitém okamžiku se však začnete cítit nepříjemně. Zjistíte, že ztrácíte kontrolu nad aplikací. Jak plyne čas, pocit se stává intenzivnější a nakonec vstoupíte do stavu známého jako **cyklus strachu**.

- Aplikace se stala tak nesmírně komplikovanou, že jí nikdo nerozumí.
- Bojíte se změn - každá změna má nezamýšlené a nákladné vedlejší účinky.
- Nové funkce / opravy se stávají složitými, časově náročnými a nákladnými implementací.
- Každá verze tak malá, jak to může být vyžaduje úplné nasazení celé aplikace.
- Jedna nestabilní součást může srazit celý systém.
- Nové technologie a rámce nepřichází v úvahu.
- Je obtížné implementovat agilní metodiky doručování.
- Architektonická eroze nastává jako základ kódu, který se zhoršuje s nekonečnými "zvláštními případy".
- Konzultanti vám řeknou, abyste to přepsali.

Mnoho organizací se zabývalo monolitickým cyklem strachu přijetím cloudově nativního přístupu k budování systémů. Obrázek 1-2 ukazuje stejný systém vytvořený s použitím technik a postupů nativních pro cloud.

![Návrh nativní pro cloud](./media/cloud-native-design.png)

**Obrázek 1-2**. Návrh nativní pro cloud

Všimněte si, jak se aplikace rozloží napříč sadou malých izolovaných mikroslužeb. Každá služba je samostatná a zapouzdřuje svůj vlastní kód, data a závislosti. Každý je nasazen v kontejneru softwaru a spravuje orchestrátor kontejneru. Namísto velké relační databáze, každá služba vlastní úložiště dat, typ, který se liší v závislosti na potřebách dat. Všimněte si, jak některé služby závisí na relační databáze, ale jiné na NoSQL databází. Jedna služba ukládá svůj stav v distribuované mezipaměti. Všimněte si, jak všechny dopravní trasy prostřednictvím služby brány rozhraní API, která je zodpovědná za směrování provozu do základní back-endové služby a vynucování mnoho průřezové obavy. A co je nejdůležitější, aplikace plně využívá funkce škálovatelnosti a odolnosti, které se nacházejí v moderních cloudových platformách.

### <a name="cloud-native-computing"></a>Cloud-nativní výpočetní technika

Hmm... Právě jsme použili termín "*Cloud Native*". Nejprve jste si mysleli, že by mohlo být: "Co přesně to znamená?" Další průmyslové módní slovo vymyšlené dodavateli softwaru na trh více věcí?"

Naštěstí je to daleko jiné a doufejme, že tato kniha vám pomůže přesvědčit.

Během krátké doby se rodák z cloudu stal hnacím trendem v softwarovém průmyslu. Je to nový způsob, jak přemýšlet o budování velkých a složitých systémů, což je přístup, který plně využívá moderní postupy vývoje softwaru, technologie a cloudovou infrastrukturu. Přístup mění způsob, jakým navrhujete, implementujete, nasazujete a zprovozňujete systémy.

Na rozdíl od neustálého humbuku, který pohání náš průmysl, cloud nativní je "*pro-real*". Vezměme si [Cloud Native Computing Foundation](https://www.cncf.io/) (CNCF), konsorcium více než 300 velkých korporací s chartou, která činí cloudově nativní výpočetní techniku všudypřítomnou napříč technologiemi a cloudovými zásobníky. Jako jedna z nejvlivnějších open source skupin hostí mnoho nejrychleji rostoucích open source projektů v GitHubu. Patří mezi ně projekty jako [Kubernetes](https://kubernetes.io/), [Prometheus](https://prometheus.io/), [Helm](https://helm.sh/), [Envoy](https://www.envoyproxy.io/)a [gRPC](https://grpc.io/).

CNCF podporuje ekosystém open-source a vendor-neutrality. V návaznosti na toto vodítko uvádíme zásady, vzory a osvědčené postupy, které jsou agnostik emitované do cloudu. Současně diskutujeme o službách a infrastruktuře, které jsou dostupné v cloudu Microsoft Azure pro vytváření cloudových nativních systémů.

Takže, co přesně je Cloud Native? Sednout si, relaxovat a dovolte nám, abychom vám pomohli prozkoumat tento nový svět.

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[další](definition.md)
