---
title: Kontejnerizování monolitických aplikací
description: Kontejnerizace monolitických aplikací, i když nezíská všechny výhody z architektury mikroslužeb, má důležité výhody nasazení, které mohou být dodány hned.
ms.date: 01/30/2020
ms.openlocfilehash: 0e6f7504a91d2b1a89193471746168fc34f50956
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503289"
---
# <a name="containerizing-monolithic-applications"></a>Kontejnerizování monolitických aplikací

Můžete chtít vytvořit jednu, monoliticky nasazenou webovou aplikaci nebo službu a nasadit ji jako kontejner. Samotná aplikace nemusí být interně monolitická, ale strukturovaná jako několik knihoven, komponent nebo dokonce vrstev (aplikační vrstva, doménová vrstva, vrstva přístupu k datům atd.). Externě se však jedná o jeden kontejner – jeden proces, jednu webovou aplikaci nebo jednu službu.

Chcete-li spravovat tento model, nasadit jeden kontejner reprezentovat aplikaci. Chcete-li zvýšit kapacitu, můžete horizontální navýšení kapacity, to znamená, že stačí přidat další kopie s vyrovnáváním zatížení vpředu. Jednoduchost pochází ze správy jednoho nasazení v jednom kontejneru nebo virtuálním počítače.

![Diagram znázorňující součásti monolitické kontejnerové aplikace.](./media/containerize-monolithic-applications/monolithic-containerized-application.png)

**Obrázek 4-1**. Příklad architektury kontejnerizované monolitické aplikace

Do každého kontejneru můžete zahrnout více součástí, knihoven nebo vnitřních vrstev, jak je znázorněno na obrázku 4-1. Monolitické kontejnerizované aplikace má většinu svých funkcí v rámci jednoho kontejneru, s vnitřní vrstvy nebo knihovny a škáluje se klonování kontejneru na více serverů nebo virtuálních počítačích. Tento monolitický vzor však může být v konfliktu s principem kontejneru "kontejner dělá jednu věc a dělá to v jednom procesu", ale může být v pořádku v některých případech.

Nevýhodou tohoto přístupu se projeví, pokud aplikace roste, vyžadující škálování. Pokud celá aplikace může škálovat, není to opravdu problém. Ve většině případů však pouze několik částí aplikace jsou body sytiče, které vyžadují změnu měřítka, zatímco jiné součásti se používají méně.

Například v typické aplikaci elektronického obchodování budete pravděpodobně muset škálovat subsystém informací o produktu, protože mnohem více zákazníků prochází produkty, než je zakoupí. Více zákazníků používá svůj košík než kanál plateb. Méně zákazníků přidává komentáře nebo si prohlíží historii nákupů. A můžete mít jen hrstka zaměstnanců, kteří potřebují spravovat obsah a marketingové kampaně. Pokud změníte velikost monolitické návrhu, veškerý kód pro tyto různé úkoly se nasadí vícekrát a škálovat na stejném stupni.

Existuje několik způsobů škálování duplikace aplikace horizontální, rozdělení různých oblastí aplikace a dělení podobné obchodní koncepty nebo data. Kromě problému škálování všech součástí však změny jedné součásti vyžadují úplné opětovné testování celé aplikace a úplné opětovné nasazení všech instancí.

Monolitický přístup je však běžné, protože vývoj aplikace je zpočátku jednodušší než pro přístupy mikroslužeb. Tak, mnoho organizací rozvíjet pomocí tohoto architektonického přístupu. Zatímco některé organizace mají dost dobré výsledky, jiné jsou bít limity. Mnoho organizací navrhlo své aplikace pomocí tohoto modelu, protože nástroje a infrastruktura ztěžovaly vytváření architektur orientovaných na služby (SOA) před lety a neviděly potřebu - dokud aplikace nerostla.

Z hlediska infrastruktury může každý server spouštět mnoho aplikací v rámci stejného hostitele a mít přijatelný poměr efektivity využití prostředků, jak je znázorněno na obrázku 4-2.

![Diagram znázorňující jednoho hostitele, který používá mnoho aplikací v kontejnerech.](./media/containerize-monolithic-applications/host-multiple-apps-containers.png)

**Obrázek 4-2**. Monolitický přístup: Host se spuštěným více aplikacemi, z nichž každá běží jako kontejner

Monolitické aplikace v Microsoft Azure lze nasadit pomocí vyhrazených virtuálních počítačů pro každou instanci. Kromě toho pomocí [škálovacísady virtuálních strojů Azure](https://azure.microsoft.com/documentation/services/virtual-machine-scale-sets/)můžete snadno škálovat virtuální počítače. [Azure App Service](https://azure.microsoft.com/services/app-service/) můžete také spouštět monolitické aplikace a snadno škálovat instance bez nutnosti spravovat virtuální počítače. Od roku 2016 můžou Azure App Services spouštět i jednotlivé instance kontejnerů Dockeru, což zjednodušuje nasazení.

Jako prostředí qa nebo omezené produkční prostředí můžete nasadit více hostitelských virtuálních počítačů Dockeru a vyvážit je pomocí vyvažovače Azure, jak je znázorněno na obrázku 4-3. To umožňuje spravovat škálování s hrubým koeficientem přístup, protože celá aplikace žije v rámci jednoho kontejneru.

![Diagram znázorňující několik hostitelů, kteří spouštějí kontejnery monolitických aplikací.](./media/containerize-monolithic-applications/docker-infrastructure-monolithic-application.png)

**Obrázek 4-3**. Příklad více hostitelů, kteří zvětšují jednu aplikaci kontejneru

Nasazení do různých hostitelů lze spravovat pomocí tradičních technik nasazení. Hostitelé Dockeru lze spravovat `docker run` `docker-compose` pomocí příkazů, jako je třeba provést ručně nebo provádět je ručně, nebo prostřednictvím automatizace, jako jsou kanály pro průběžné doručování (CD).

## <a name="deploying-a-monolithic-application-as-a-container"></a>Nasazení monolitické aplikace jako kontejneru

Použití kontejnerů ke správě nasazení monolitických aplikací přináší výhody. Škálování instance kontejneru je mnohem rychlejší a jednodušší než nasazení dalších virtuálních mandů. I v případě, že používáte škálovací sady virtuálních strojů, virtuální počítače nějakou dobu trvat, než začít. Při nasazení jako tradiční instance aplikace namísto kontejnerů, konfigurace aplikace se spravuje jako součást virtuálního počítače, což není ideální.

Nasazení aktualizací jako inamů Dockeru je mnohem rychlejší a efektivní v síti. Image Dockeru se obvykle spouštějí během několika sekund, což urychluje zavádění. Stržení instance image Dockeru je stejně snadné jako vydání příkazu `docker stop` a obvykle se dokončí za méně než sekundu.

Vzhledem k tomu, že kontejnery jsou neměnné podle návrhu, nikdy se nemusíte starat o poškozené virtuální chody. Naproti tomu aktualizace skriptů pro virtuální počítač může zapomenout na účet pro některé konkrétní konfigurace nebo soubor vlevo na disku.

Zatímco monolitické aplikace mohou těžit z Dockeru, dotýkáme se pouze výhod. Další výhody správy kontejnerů pocházejí z nasazení s orchestrátory kontejnerů, které spravují různé instance a životní cyklus každé instance kontejneru. Rozdělení monolitické aplikace do subsystémů, které lze škálovat, vyvíjet a nasazovat jednotlivě, je vstupním bodem do sféry mikroslužeb.

## <a name="publishing-a-single-container-based-application-to-azure-app-service"></a>Publikování aplikace založené na jednom kontejneru do služby Azure App Service

Ať už chcete získat ověření kontejneru nasazeného do Azure nebo když je aplikace jednoduše aplikace s jedním kontejnerem, Azure App Service poskytuje skvělý způsob, jak poskytovat škálovatelné služby založené na jednom kontejneru. Používání služby Azure App Service je jednoduché. Poskytuje skvělou integraci s Gitem, která usnadňuje převzít váš kód, sestavit ho ve Visual Studiu a nasadit ho přímo do Azure.

![Snímek obrazovky s dialogem Vytvořit službu aplikace zobrazujícího registr kontejnerů](./media/containerize-monolithic-applications/publish-azure-app-service-container.png)

**Obrázek 4-4**. Publikování aplikace s jedním kontejnerem do služby Azure App Service z Visual Studia 2019

Bez Dockeru, pokud potřebujete další možnosti, architektury nebo závislosti, které nejsou podporované ve službě Azure App Service, museli jste počkat, dokud tým Azure tyto závislosti aktualizuje ve službě App Service. Nebo jste museli přejít na jiné služby, jako jsou Azure Cloud Services nebo virtuální počítače, kde jste měli další kontrolu a můžete nainstalovat požadovanou komponentu nebo architekturu pro vaši aplikaci.

Podpora kontejnerů ve Visual Studiu 2017 a novějších vám dává možnost zahrnout do aplikačního prostředí vše, co chcete, jak je znázorněno na obrázku 4-4. Vzhledem k tomu, že jej spouštěte v kontejneru, pokud přidáte závislost do vaší aplikace, můžete zahrnout závislost do image Dockerfile nebo Docker.

Jak je znázorněno také na obrázku 4-4, tok publikování tlačí bitovou kopii prostřednictvím registru kontejneru. Může se jednalo o registr kontejnerů Azure (registr blízký vašim nasazením v Azure a zabezpečený skupinami a účty služby Azure Active Directory) nebo jakýkoli jiný registr Dockeru, jako je Docker Hub nebo místní registr.

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[další](docker-application-state-data.md)
