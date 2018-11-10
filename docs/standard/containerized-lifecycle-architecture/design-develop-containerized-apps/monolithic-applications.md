---
title: Monolitické aplikace
description: Životní cyklus aplikace kontejnerizovaných Dockeru s platformou a nástroji Microsoft
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: a2fe2c325377ec49f89199ad2e36c950ebab6a24
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2018
ms.locfileid: "50757345"
---
# <a name="monolithic-applications"></a>Monolitické aplikace

V tomto scénáři jsou sestavení jednoho a monolitické webové aplikaci nebo službě a jeho nasazení jako kontejner. V rámci aplikace nemusí být struktura monolitické; To může se skládat z několika knihoven, komponenty nebo dokonce vrstvy (aplikační vrstva, vrstva domény, vrstva přístupu k datům atd.). Externě je jedním kontejnerem, jako je jeden proces, jednu webovou aplikaci nebo jedinou službou.

Správa tohoto modelu, nasadíte jedním kontejnerem pro reprezentaci aplikace. Pro její škálování, stačí přidáte několik více kopií s nástroji pro vyrovnávání zatížení v popředí. Jednoduchost pochází z Správa jedno nasazení z jednoho kontejneru nebo virtuální počítač (VM).

Následující objekt zabezpečení, že kontejner provádí pouze jednu věc a nemá v jednom procesu monolitické vzor je v konfliktu. Může zahrnovat více komponenty a knihovny nebo interní vrstvy v rámci každého kontejneru, jak je znázorněno na obrázku 4-1.

![](./media/image1.png)

Obrázek 4-1: Příklad architektura monolitické aplikace

Nevýhodou tento přístup se dodává spolu Pokud nebo když aplikace poroste, požadují škálování. Pokud v celé aplikaci škálovat, není ve skutečnosti k problému. Ve většině případů několik částí aplikace ale potlačení body, které vyžadují škálování, zatímco ostatní součásti jsou méně používaná.

Použijeme příklad typické elektronického obchodování, budete pravděpodobně potřebovat, je škálování informace součást produktu. Mnoho zákazníků další procházet produktů, než je koupit. Větší počet zákazníků pomocí nákupního košíku, než použití kanálu platby. Méně zákazníky přidat komentáře nebo zobrazení jejich historie nákupů. A pravděpodobně máte pouze několik zaměstnanců, v jedné oblasti, které potřebují spravovat obsah a marketingových kampaní. Díky škálování monolitický návrh, veškerý kód nasazuje více než jednou.

Kromě "škálovací – všechno, co" problém, změny jedinou komponentu vyžadovat úplné opakované celé aplikace, stejně jako úplné opětovné nasazení všech instancí.

Monolitického přístupu je běžné a mnoha organizacích jsou vývoj s využitím této architektury metody. Mnoho vám přinesou jistotu kvalitní dostatek výsledky, zatímco ostatní dojde k omezení. Mnoho navržené svých aplikací v tomto modelu, protože byly příliš obtížné sestavení SOAs nástroje a infrastruktura a jejich nezobrazila potřebu – dokud zvětšoval aplikace.

Každý server z hlediska infrastruktury, můžete spustit mnoho aplikací v rámci stejného hostitele a mají přijatelné poměr efektivitu ve využití prostředků, jak ukazuje obrázek 4-2.

![](./media/image2.png)

Obrázek 4 – 2: hostitele se více aplikací nebo kontejnerů

Monolitické aplikace v Azure můžete nasadit pomocí vyhrazených virtuálních počítačů pro každou instanci. Pomocí [Azure VM Scale Sets](https://docs.microsoft.com/azure/virtual-machine-scale-sets/), je možné snadno škálovat virtuální počítače. [Služba Azure App Services](https://azure.microsoft.com/services/app-service/) můžete spustit monolitické aplikace a snadno škálovat instance, aniž byste museli spravovat virtuální počítače. Od verze 2016 Azure App Services spuštění jedné instance kontejnerů Dockeru, také zjednodušení nasazení. A pomocí Dockeru, můžete nasadit jeden virtuální počítač jako hostitele Dockeru a spouštět více instancí. Pomocí nástroje Azure pro vyrovnávání, jak je znázorněno v obrázek 4-3, můžete spravovat škálování.

![](./media/image3.png)

Obrázek 4-3: více hostitelů škálování na více instancí jednu aplikaci aplikace/kontejnery Dockeru

Můžete spravovat na různých hostitelích prostřednictvím nasazení tradiční techniky nasazení. Hostitele Docker můžete spravovat pomocí příkazů, jako jsou `docker run` ručně, pomocí automatizace, jako jsou průběžné doručování (CD) kanálů, které vám vysvětlíme, dále v této e knihy.

## <a name="monolithic-application-deployed-as-a-container"></a>Monolitické aplikace nasazená jako kontejner

Existují výhody použití kontejnerů pro správu monolitické nasazení. Škálování instance kontejnerů je mnohem jednodušší a rychlejší než nasazení dalších virtuálních počítačů. I když Škálovací sady virtuálních počítačů jsou skvělé funkce, která škálování virtuálních počítačů, které se vyžadují pro hostování kontejnerů Docker, přebírají čas nastavit. Po nasazení jako instance aplikace, je konfigurace aplikace spravovaná v rámci virtuálního počítače.

Nasazení aktualizací, je mnohem rychlejší imagí Dockeru a efektivní sítě. Instance Vn můžete nastavit na stejného hostitele jako vaše instance Vn-1, což eliminuje náklady plynoucí z dalších virtuálních počítačů. Image dockeru se obvykle začít během několika sekund, a tím i urychlení uvedení. Opětné do instance Docker je stejně jednoduché jako volání obsluhy `docker stop` příkaz obvykle dokončení v menší než druhý.

Vzhledem k tomu, že kontejnery jsou ze své podstaty neměnné záměrné, potřebujete nikdy starat o poškozená virtuálních počítačů, protože aktualizační skript si vzpomenout na některé konkrétní konfiguraci nebo soubor na disku.

Přestože monolitických aplikací můžete využívat Docker, jsme se dotýká na pouze tipy výhody. Větší výhody správy kontejnerů pochází z nasazení pomocí orchestrátorů kontejnerů, které spravují různé instance a životního cyklu každou instanci kontejneru. Rozdělení monolitické aplikace do subsystémů, které můžete škálovat, vyvinuli a nasazují samostatně je vstupním bodem do sféry mikroslužeb.

## <a name="publishing-a-single-docker-container-app-to-azure-app-service"></a>Publikování do služby Azure App Service jedné aplikace kontejneru Docker

Buď vzhledem k tomu, že chcete získat rychlé ověření kontejneru nasadit do Azure, nebo protože aplikace je jednoduše jedním – aplikace typu kontejner, Azure App Service nabízí skvělý způsob, jak poskytnout škálovatelných služeb určených jeden kontejner.

Pomocí služby Azure App Service je intuitivní a můžete a rychlý, protože poskytuje skvělé Git integrace kódu, sestavení v sadě Microsoft Visual Studio a nasaďte ji přímo do Azure. Ale tradičně (žádné Dockeru), v případě potřeby další možnosti, rozhraní nebo závislosti, které nejsou podporovány v App Services, jste museli čekat, dokud nebude tým Azure aktualizace těchto závislostí ve službě App Service nebo přepnout do jiných služeb, třeba Service Fabric, Cloud Services nebo dokonce prostý virtuálních počítačů, pro které mají další kontrolu a můžete nainstalovat na požadovanou součást nebo architekturu pro vaši aplikaci.

Teď, ale (bylo ohlášená na Microsoft Connect 2016 v listopadu 2016) a jak je znázorněno v 4‑4 obrázek, když pomocí sady Visual Studio 2017, podpora kontejnerů ve službě Azure App Service vám dává možnost zahrnout cokoliv, co chcete v prostředí aplikace. Přidá závislost do vaší aplikace, protože běží v kontejneru, získáte možnost do své image soubor Dockerfile nebo Docker, včetně těchto závislostí.

![](./media/image4.png)

Obrázek 4-4: publikování kontejneru do služby Azure App Service ze sady Visual Studio. aplikace/kontejnery

Obrázek 4-4 také ukazuje, že tok publikovat nabízených oznámení image do registru kontejneru, který může být Azure Container Registry (registr téměř svá nasazení v Azure a zabezpečené pomocí skupin Azure Active Directory a účty) nebo jiné registru Dockeru například Docker Hub nebo v místním Registry.


>[!div class="step-by-step"]
[Předchozí](common-container-design-principles.md)
[další](state-and-data-in-docker-applications.md)
