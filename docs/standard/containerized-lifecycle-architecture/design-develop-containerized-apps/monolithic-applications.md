---
title: Monolitické aplikace
description: Základní koncepce pro kontejnerizování monolitických aplikací.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 76e1db8886fe75b79cea2e28ef05e62ca519ae58
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57676834"
---
# <a name="monolithic-applications"></a>Monolitické aplikace

V tomto scénáři provedete sestavování jednoho a monolitické webové aplikaci nebo službě a jeho nasazení jako kontejner. V rámci aplikace nemusí být struktura monolitické; To může se skládat z několika knihoven, komponenty nebo dokonce vrstvy (aplikační vrstva, vrstva domény, vrstva přístupu k datům atd.). Externě je jedním kontejnerem, jako je jeden proces, jednu webovou aplikaci nebo jedinou službou.

Správa tohoto modelu, nasadíte jedním kontejnerem pro reprezentaci aplikace. Pro její škálování, stačí přidáte několik více kopií s nástroji pro vyrovnávání zatížení v popředí. Jednoduchost pochází z Správa jedno nasazení z jednoho kontejneru nebo virtuální počítač (VM).

Následující objekt zabezpečení, že kontejner provádí pouze jednu věc a nemá v jednom procesu monolitické vzor je v konfliktu. Může zahrnovat více komponenty a knihovny nebo interní vrstvy v rámci každého kontejneru, jak je znázorněno na obrázku 4-1.

![Monolitické aplikace má všech nebo většiny ze svých funkcí v rámci jednoho procesu nebo kontejneru, a to je komponentní v interní vrstvy nebo knihovny.](./media/image1.png)

**Obrázek 4-1.** Příklad architektury monolitické aplikace

Nevýhodou tento přístup se dodává spolu Pokud nebo když aplikace poroste, požadují škálování. Pokud v celé aplikaci škálovat, není ve skutečnosti k problému. Ve většině případů několik částí aplikace ale potlačení body, které vyžadují škálování, zatímco ostatní součásti jsou méně používaná.

Použijeme příklad typické elektronického obchodování, budete pravděpodobně potřebovat, je škálování informace součást produktu. Mnoho zákazníků další procházet produktů, než je koupit. Větší počet zákazníků pomocí nákupního košíku, než použití kanálu platby. Méně zákazníky přidat komentáře nebo zobrazení jejich historie nákupů. A pravděpodobně máte pouze několik zaměstnanců, v jedné oblasti, které potřebují spravovat obsah a marketingových kampaní. Díky škálování monolitický návrh, veškerý kód nasazuje více než jednou.

Kromě "škálovací – všechno, co" problém, změny jedinou komponentu vyžadovat úplné opakované celé aplikace, stejně jako úplné opětovné nasazení všech instancí.

Monolitického přístupu je běžné a mnoha organizacích jsou vývoj s využitím této architektury metody. Mnoho vám přinesou jistotu kvalitní dostatek výsledky, zatímco ostatní dojde k omezení. Mnoho navržené svých aplikací v tomto modelu, protože byly příliš obtížné sestavení SOAs nástroje a infrastruktura a jejich nezobrazila potřebu – dokud zvětšoval aplikace.

Každý server z hlediska infrastruktury, můžete spustit mnoho aplikací v rámci stejného hostitele a mají přijatelné poměr efektivitu ve využití prostředků, jak ukazuje obrázek 4-2.

![Je jeden hostitel můžete spustit několik aplikací v samostatných kontejnery.](./media/image2.png)

**Obrázek 4-2.** Hostitele se více aplikací nebo kontejnerů

Nakonec se z hlediska dostupnosti, monolitické aplikace musí být nasazený jako celek; To znamená, že v případě, že je potřeba *zastavení a spuštění*, všechny funkce a všech uživatelů ovlivněných během časového intervalu pro nasazení. V některých případech použití Azure a kontejnery minimalizovat těchto situacích a snížit pravděpodobnost výpadku aplikace, jak je vidět v obrázek 4-3.

Monolitické aplikace v Azure můžete nasadit pomocí vyhrazených virtuálních počítačů pro každou instanci. Pomocí [Azure VM Scale Sets](https://docs.microsoft.com/azure/virtual-machine-scale-sets/), je možné snadno škálovat virtuální počítače.

Můžete také použít [Azure App Services](https://azure.microsoft.com/services/app-service/) spouštět monolitické aplikace a snadno škálovat instance, aniž byste museli spravovat virtuální počítače. Služba Azure App Services můžete spustit jedné instance kontejnerů Dockeru, také zjednodušit nasazení.

Můžete nasadit několik virtuálních počítačů jako hostitelů Docker a spustit libovolný počet kontejnerů na virtuální počítač. Potom pomocí služby Azure Load Balancer, jak je znázorněno v 3 – obrázek 4, můžete spravovat škálování.

![Monolitické aplikace může být horizontálním navýšením kapacity na různých hostitelích, kde každý z nich je spuštění aplikace v kontejnerech.](./media/image3.png)

**Obrázek 4-3**. Více hostitelů škálování na více instancí jednu aplikaci aplikace/kontejnery Dockeru

Můžete spravovat nasazení hostitele sami prostřednictvím nasazení tradiční techniky.

Kontejnery Dockeru můžete spravovat z příkazového řádku pomocí příkazů, jako jsou `docker run` a `docker-compose up`, a můžete také automatizovat v průběžné doručování (CD) kanálů a nasazovat do hostitelů Docker ze služeb Azure DevOps, pro instanci.

## <a name="monolithic-application-deployed-as-a-container"></a>Monolitické aplikace nasazená jako kontejner

Existují výhody použití kontejnerů pro správu monolitické nasazení. Škálování instance kontejnerů je mnohem jednodušší a rychlejší než nasazení dalších virtuálních počítačů.

Nasazení aktualizací, je mnohem rychlejší imagí Dockeru a efektivní sítě. Kontejnery dockeru jsou obvykle spustí během několika sekund, tím i urychlení uvedení. Opětné kontejneru Dockeru je stejně jednoduché jako volání obsluhy `docker stop` příkaz obvykle dokončení v menší než druhý.

Vzhledem k tomu, že kontejnery jsou ze své podstaty neměnné záměrné, potřebujete nikdy starat o poškozená virtuálních počítačů, protože aktualizační skript si vzpomenout na některé konkrétní konfiguraci nebo soubor na disku.

Přestože monolitických aplikací můžete využívat Docker, jsme se dotýká na pouze tipy výhody. Větší výhody správy kontejnerů, pocházejí z nasazení pomocí orchestrátorů kontejnerů, které spravují různé instance a životního cyklu každou instanci kontejneru. Rozdělení monolitické aplikace do subsystémů, které můžete škálovat, vyvinuli a nasazují samostatně je vstupním bodem do sféry mikroslužeb.

Další informace o tom, jak "metodou lift and shift" monolitické aplikace s kontejnery a jak můžete modernizovat aplikace, najdete další příručky Microsoftu [modernizace stávajících aplikací .NET pomocí cloudu Azure a kontejnery Windows ](https://docs.microsoft.com/dotnet/standard/modernize-with-azure-and-containers/), kterou můžete také stáhnout ve formátu PDF z <https://aka.ms/LiftAndShiftWithContainersEbook>.

## <a name="publish-a-single-docker-container-app-to-azure-app-service"></a>Publikovat jedinou aplikaci kontejneru Dockeru do služby Azure App Service

Buď vzhledem k tomu, že chcete získat rychlé ověření kontejneru nasadit do Azure, nebo protože aplikace je jednoduše jedním – aplikace typu kontejner, Azure App Service nabízí skvělý způsob, jak poskytnout škálovatelných služeb určených jeden kontejner.

Pomocí služby Azure App Service je intuitivní a můžete a rychlý, protože poskytuje skvělé Git integrace kódu, sestavení v sadě Microsoft Visual Studio a nasaďte ji přímo do Azure. Ale tradičně (žádné Dockeru), v případě potřeby další možnosti, rozhraní nebo závislosti, které nejsou podporovány v App Services, jste museli čekat, dokud nebude tým Azure aktualizace těchto závislostí ve službě App Service nebo přepnout do jiných služeb, třeba Service Fabric, Cloud Services nebo dokonce prostý virtuálních počítačů, pro které mají další kontrolu a můžete nainstalovat na požadovanou součást nebo architekturu pro vaši aplikaci.

Nyní, jak ukazuje obrázek 4-4 při používání sady Visual Studio 2017, podpora kontejnerů ve službě Azure App Service poskytuje možnost zahrnout cokoliv, co chcete v prostředí aplikace. Přidat závislost do vaší aplikace, protože ji používáte v kontejneru, získáte možnost do své image soubor Dockerfile nebo Docker, včetně těchto závislostí.

![Zobrazit průvodce Visual Studio k publikování do služby Azure app service, zvýraznění selektor pro registr kontejneru.](./media/image4.png)

**Obrázek 4-4**. Publikování z aplikace Visual Studio/kontejnery kontejneru do služby Azure App Service

Obrázek 4-4 také ukazuje, že tok publikovat nabízených oznámení image do registru kontejneru, který může být Azure Container Registry (registr téměř svá nasazení v Azure a zabezpečené pomocí skupin Azure Active Directory a účty) nebo jiné registru Dockeru například Docker Hub nebo v místním Registry.

>[!div class="step-by-step"]
>[Předchozí](common-container-design-principles.md)
>[další](state-and-data-in-docker-applications.md)
