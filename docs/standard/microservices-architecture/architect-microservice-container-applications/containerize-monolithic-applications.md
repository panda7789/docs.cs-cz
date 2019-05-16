---
title: Kontejnerizování monolitických aplikací
description: Kontejnerizování monolitických aplikací, i když není získáte všechny výhody z architektury mikroslužeb, je důležité nasazení výhod, které může doručit okamžitě.
ms.date: 09/20/2018
ms.openlocfilehash: 061afe86e0d38f058becde2b3afdb45b4428517a
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65640819"
---
# <a name="containerizing-monolithic-applications"></a>Kontejnerizování monolitických aplikací

Můžete chtít sestavit jeden, monolithically nasazené webové aplikaci nebo službě a nasadit ho jako kontejner. Samotná aplikace nemusí být interně monolitické, ale strukturované jako několik knihoven, komponenty nebo dokonce vrstvy (aplikační vrstva, vrstva domény, vrstvy přístupu k datům atd.). Externě, je ale jedním kontejnerem – jeden proces, jednu webovou aplikaci nebo jedinou službou.

Správa tohoto modelu, nasadíte jedním kontejnerem pro reprezentaci aplikace. Pokud chcete zvýšit kapacitu, horizontální navýšení kapacity, to znamená, stačí přidat více kopií s nástroji pro vyrovnávání zatížení v popředí. Jednoduchost pochází z jednoho nasazení ve virtuální počítač s jedním kontejnerem nebo Správa.

![Monolitické kontejnerizovanou aplikaci s nejvíce ze svých funkcí v rámci jednoho kontejneru s interní vrstvy nebo knihovny, a škáluje naklonováním kontejneru na víc serverech nebo virtuálních počítačích](./media/image1.png)

**Obrázek 4-1**. Příklad architektury kontejnerizované monolitické aplikace

V jednotlivých kontejnerech může obsahovat více komponent, knihovny nebo interní vrstvy, jak je znázorněno na obrázku 4-1. Však může tento model monolitické porušovat principu kontejneru "kontejner nemá jednou z věcí a dělá v jednom procesu", ale může být pro některé případy ok.

Nevýhodou tento přístup bude zřejmé, pokud aplikace poroste, požadují škálování. Pokud celou aplikaci je možné škálovat, není ve skutečnosti k problému. Ve většině případů jsou několika částí aplikace body potlačení, že nutnosti škálování, zatímco ostatní součásti jsou použít menší.

Například v aplikaci elektronického obchodování typické je pravděpodobně muset škálovat subsystému informace o produktu, protože mnoho více zákazníkům procházet produktů, než je koupit. Větší počet zákazníků pomocí nákupního košíku, než použití kanálu platby. Méně zákazníky přidat komentáře nebo zobrazení jejich historie nákupů. A může mít pouze několik zaměstnanců, kteří potřebují spravovat obsah a marketingových kampaní. Pokud převedete monolitický návrh, je celý kód pro tyto různé úlohy nasadit více než jednou a škálovat na stejné úrovni.

Existuje několik způsobů, jak škálovat duplikaci aplikace vodorovné rozdělení různých oblastí aplikace a dělení podobné obchodních konceptů nebo data. Ale kromě problém škálování všechny součásti, vyžadují změny jedné komponenty kompletní opakované celé aplikace a dokončení opětovné nasazení všech instancí.

Ale monolitického přístupu dochází, protože vývoje aplikace je zpočátku snazší než u metod mikroslužeb. Mnoho organizací proto vývoj pomocí tento architektonický přístup umožňuje vytvářet. Přestože některé organizace mají kvalitní měli dostatek výsledky, ostatní omezení výskytu. Mnoho organizací určená svým aplikacím pomocí tohoto modelu, protože nástroje a infrastruktura pro změnit příliš obtížné umožňuje vytvářet architektury orientované na služby (SOA) před lety a nenalezli potřebu – dokud zvětšoval aplikace.

Každý server z hlediska infrastruktury, můžete spustit mnoho aplikací v rámci stejného hostitele a mají přijatelné poměr efektivitu využití prostředků, jak ukazuje obrázek 4-2.

![Hostitele můžete spustit několik monolitické aplikace, každý z nich na samostatný kontejner.](./media/image2.png)

**Obrázek 4-2**. Monolitického přístupu: Hostiteli s více aplikacemi, každou aplikaci spuštěnou jako kontejner

Monolitické aplikace v Microsoft Azure se dá nasadit pomocí vyhrazených virtuálních počítačů pro každou instanci. Kromě toho používání [škálovací sady virtuálních počítačů Azure](https://azure.microsoft.com/documentation/services/virtual-machine-scale-sets/), je možné snadno škálovat virtuální počítače. [Azure App Service](https://azure.microsoft.com/services/app-service/) můžete také spustit monolitické aplikace a snadno škálovat instance, aniž by bylo potřeba spravovat virtuální počítače. Od verze 2016 Azure App Services spuštění jedné instance kontejnerů Dockeru, zjednodušit nasazování.

Jako prostředí QA nebo omezeném produkčním prostředí můžete nasadit hostitele Docker více virtuálních počítačů a vyvážit je pomocí Azure balancer, jak ukazuje obrázek 4-3. To vám umožní spravovat škálování s hrubým intervalem přístup, protože se nachází v rámci jednoho kontejneru celou aplikaci.

![Několik hostitelů, každý z nich spouštění kontejneru s monolitickými aplikacemi.](./media/image3.png)

**Obrázek 4-3**. Příklad více hostitelů vertikálním navýšení kapacity aplikace jednoho kontejneru

Nasazení do různých hostitelů lze spravovat pomocí nasazení tradiční techniky. Hostitele docker můžete spravovat pomocí příkazů, jako jsou `docker run` nebo `docker-compose` provést ručně nebo pomocí automatizace, jako jsou průběžné doručování (CD) kanálů.

## <a name="deploying-a-monolithic-application-as-a-container"></a>Nasazení monolitické aplikace jako kontejner

Existují výhody použití kontejnerů ke správě nasazení monolitických aplikací. Škálování instance kontejneru je mnohem jednodušší a rychlejší než nasazení dalších virtuálních počítačů. I když používáte škálovací sady virtuálních počítačů, virtuálních počítačů trvat dobu spuštění. Po nasazení jako instance tradiční aplikace, aby místo kontejnery, nastavení aplikace se spravuje v rámci virtuálního počítače, což není ideální.

Nasazení aktualizací, je mnohem rychlejší imagí Dockeru a efektivní sítě. Image dockeru obvykle spustí během několika sekund, což urychluje uvedení. Opětné instance image Dockeru je stejně jednoduché jako vydání `docker stop` příkazů a obvykle dokončí za kratší dobu než druhý.

Vzhledem k tomu, že kontejnery jsou neměnné záměrné, potřebujete nikdy starat o poškozená virtuálních počítačů. Naproti tomu skripty pro aktualizaci pro virtuální počítač může být zapomenout pro některé konkrétní konfiguraci nebo soubor na disku.

Zatímco monolitických aplikací můžete využívat Docker, jsme už zasahuje pouze na výhody. Další výhody správy kontejnerů, pocházejí z nasazení s orchestrátory kontejnerů, které spravují různé instance a životního cyklu každou instanci kontejneru. Rozdělení monolitické aplikace do subsystémů, které můžete škálovat, vyvinuli a nasazují samostatně je vstupním bodem do sféry mikroslužeb.

## <a name="publishing-a-single-container-based-application-to-azure-app-service"></a>Publikování aplikace na základě jednoho kontejneru do služby Azure App Service

Jestli se má získat ověření kontejneru nasadit do Azure nebo když se aplikace nachází pouze jeden kontejner aplikace, služby Azure App Service nabízí skvělý způsob, jak poskytnout škálovatelných služeb na základě jednoho kontejneru. Pomocí služby Azure App Service je jednoduché. Poskytuje skvělé integrace s úložištěm Git, abyste usnadnili snadnou využít váš kód, sestavte ho v sadě Visual Studio a nasaďte ji přímo do Azure.

![Průvodce pro publikování aplikace jednoho kontejneru do služby Azure App Service ze sady Visual Studio](./media/image4.png)

**Obrázek 4-4**. Publikování aplikace jeden kontejner do služby Azure App Service ze sady Visual Studio

Bez Dockeru v případě potřeby další možnosti, rozhraní nebo závislosti, které nejsou podporované ve službě Azure App Service, jste měli počkat, až tým Azure aktualizovat tyto závislosti ve službě App Service. Nebo jste museli přepínat do jiných služeb, jako je Azure Service Fabric, Azure Cloud Services nebo dokonce i virtuální počítače, kde jste měli další ovládací prvek a můžete nainstalovat na požadovanou součást nebo architekturu pro vaši aplikaci.

Podpora kontejnerů v sadě Visual Studio 2017 dává možnost zahrnout cokoliv, co chcete v prostředí pro vaše aplikace, jak ukazuje obrázek 4-4. Vzhledem k tomu, že ji používáte v kontejneru, pokud chcete přidat závislost pro vaši aplikaci, můžete zahrnout závislost image soubor Dockerfile nebo Dockeru.

Jak jsou také uvedeny v obrázek 4-4 tok publikovat posune bitovou kopii prostřednictvím registru kontejneru. To může být služba Azure Container Registry (registr zavřít svá nasazení v Azure a zabezpečené pomocí skupin Azure Active Directory a účty) nebo jakékoli jiné registru Dockeru, jako je Docker Hubu nebo v místním registru.

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[další](docker-application-state-data.md)
