---
title: Úvod k aplikacím nativním pro cloud
description: Další informace o computingu nativního cloudu
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 6ec02a1388d6e0f26cdaa1f728f23a22ba52d735
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613938"
---
# <a name="introduction-to-cloud-native-applications"></a>Úvod k aplikacím nativním pro cloud

Druhý den, v kanceláři, pracuje na "dalších velkých věcí".

Vaše cellphoneové prstence. Je to uživatelsky přívětivý náborový pracovník – ten, který se na nové úlohy zavolá dvakrát denně.

V tuto chvíli se ale liší: spuštění, jmění a dostatek finančních prostředků.

Zmínka o cloudových a špičkových technologiích vás na hraničních zařízeních nabízí.

Rychle předejte pár týdnů a teď jste nový zaměstnanec v relaci návrhu, která je navržena jako hlavní elektronického obchodování aplikace. Chystáte se soutěžit s předními elektronického obchodování servery.

Jak ho budete sestavovat?

Pokud budete postupovat podle pokynů v posledních 15 letech, pravděpodobně sestavíte systém uvedený na obrázku 1,1.

![Tradiční design monolitické](./media/monolithic-design.png)

**Obrázek 1-1**. Tradiční design monolitické

Vytvoříte velkou základní aplikaci obsahující všechny vaše doménové logiky. Obsahuje i moduly, jako je identita, katalog, řazení a další. Základní aplikace komunikuje s velkou relační databází. Jádro zpřístupňuje funkce přes rozhraní HTML.

Gratulujeme!  Právě jste vytvořili aplikaci monolitické.

Ne vše je chybné. Monolitů nabízí několik různých výhod. Například jsou jednoduché...

- sestavení
- test
- nasazení
- troubleshoot
- scale

Mnoho úspěšných aplikací, které dnes existovaly, bylo vytvořeno jako monolitů. Aplikace je vybrána a nadále se vyvíjí, iterace po iteraci přidá další a další funkce.

V určitém okamžiku ale začnete Uncomfortable. Narazíte na ztrátu řízení aplikace. V době, kdy je to možné, se nepůjde rozroste a nakonec zadáte stav známý jako `Fear Cycle` .

- Aplikace se stala, takže ji nikdo nerozumí.
- Nejste se obávat provádění změn – každá změna má nezamýšlené a nákladné vedlejší účinky.
- Nové funkce nebo opravy se stávají podniknout, časově náročné a náročné na implementaci.
- Každé vydání je co nejmenší a vyžaduje úplné nasazení celé aplikace.
- Jedna nestabilní součást může způsobit selhání celého systému.
- Nové technologie a architektury nejsou možností.
- Je obtížné implementovat metodologie agilního doručování.
- Nastavení eroze architektury v nástroji jako základ kódu se zhoršila s nikdy nekonečnými "speciálními případy".
- Konzultanti vás upozorní, že ji přepsat.

Řada organizací vyřešila cyklus monolitické strach tím, že přijímá cloudový nativní přístup k vytváření systémů. Obrázek 1-2 ukazuje stejný systém sestavený s použitím techniků a postupů nativních pro Cloud.

![Návrh nativního cloudu](./media/cloud-native-design.png)

**Obrázek 1-2**. Návrh nativního cloudu

Všimněte si, jak se aplikace rozloží v rámci sady malých izolovaných mikroslužeb. Každá služba je samostatně obsažená a zapouzdřuje svůj vlastní kód, data a závislosti. Každá je nasazena v kontejneru softwaru a spravovaná nástrojem kontejner Orchestrator. Místo velké relační databáze je každá služba vlastníkem vlastního úložiště dat, což závisí na závislosti na potřebách dat. Všimněte si, že některé služby závisí na relační databázi, ale v databázích NoSQL. Jedna služba ukládá svůj stav do distribuované mezipaměti. Všimněte si, jak všechny trasy přenosů prostřednictvím služby brány rozhraní API zodpovídá za směrování provozu do základních back-endové služby a vynucování mnoha otázek pro průřezy. Nejdůležitější je, že aplikace plně využívá možnosti škálovatelnosti, dostupnosti a odolnosti, které najdete v moderních cloudových platformách.

### <a name="cloud-native-computing"></a>Nativní výpočetní prostředí pro Cloud

Hmm... Právě jsme používali termín _Cloud Native_. Vaše první myšlenka může být "co přesně to znamená?" Jiný obor Buzzword concocted dodavatelé softwaru o uvedení na trh? "

Naštěstí je mnohem odlišná a snad tato kniha vám pomůže vás posvědčit.

Cloudový nativní se v krátké době stal vývojovým trendem v softwarovém odvětví. Je to nový způsob, jak si představit informace o vytváření rozsáhlých, složitých systémů, přístupu, který plně využívá moderní postupy pro vývoj softwaru, technologie a cloudovou infrastrukturu. Přístup mění způsob návrhu, implementace, nasazení a zprovoznění systémů.

Na rozdíl od souvislého Hype, který je v našem odvětví, je cloudový nativní _pro_Cloud. Vezměte v úvahu [Cloud Native Computing Foundation](https://www.cncf.io/) (CNCF), konsorcium více než 300 hlavních společností s Chartou pro vytváření cloudových všudypřítomných computingu napříč technologiemi a cloudových zásobníků. Jako jedna z nejvíc neužitečných Open Source skupin je hostitelem mnoha nejrychlejších open source projektů v GitHubu. Zahrnují projekty, jako jsou [Kubernetes](https://kubernetes.io/), [Prometheus](https://prometheus.io/), [Helm](https://helm.sh/), [zástupné](https://www.envoyproxy.io/)a [gRPC](https://grpc.io/).

CNCF podporuje ekosystém open source a neutrálního dodavatele. Od tohoto zájemce představují tato kniha zásady, vzory a osvědčené postupy pro Cloud, které jsou nezávislá technologií. Ve stejnou chvíli probereme služby a infrastrukturu, které jsou k dispozici v cloudu Microsoft Azure pro vytváření nativních systémů cloudu.

Takže co přesně je cloudová nativní? Nasaďte se zpátky, uvolněte a sdělte nám, jak vám pomůžeme prozkoumat tento nový svět.

>[!div class="step-by-step"]
>[Předchozí](index.md) 
> [Další](definition.md)
