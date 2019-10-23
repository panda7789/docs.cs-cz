---
title: Monolitické aplikace
description: Seznamte se se základními koncepty pro aplikace uzavření monolitické.
ms.date: 02/15/2019
ms.openlocfilehash: 8664153ee2e9d1d253164e43ac13105f6dbf476c
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771034"
---
# <a name="monolithic-applications"></a>Monolitické aplikace

V tomto scénáři vytváříte jednu a monolitické webovou aplikaci nebo službu a nasazujete ji jako kontejner. V rámci aplikace struktura nemusí být monolitické; může zahrnovat několik knihoven, komponent nebo dokonce vrstev (aplikační vrstva, vrstva domény, vrstva přístupu k datům atd.). Externě je to jeden kontejner, například jeden proces, jedna webová aplikace nebo jedna služba.

Chcete-li spravovat tento model, nasadíte jeden kontejner, který bude představovat aplikaci. Pokud ho chcete škálovat, stačí přidat několik dalších kopií s nástrojem pro vyrovnávání zatížení předem. Jednoduchost pochází ze správy jediného nasazení v jednom kontejneru nebo virtuálním počítači (VM).

Po objektu zabezpečení, který má kontejner pouze jedna věc, a provede ho v jednom procesu, je vzor monolitické v konfliktu. V rámci každého kontejneru můžete zahrnout více komponent, knihoven nebo vnitřních vrstev, jak je znázorněno na obrázku 4-1.

![Diagram znázorňující aplikaci monolitické, která se škáluje klonováním aplikace](./media/monolithic-applications/monolithic-application-architecture-example.png)

**Obrázek 4-1.** Příklad architektury aplikace monolitické

Aplikace monolitické má celou nebo většinu funkcí v rámci jednoho procesu nebo kontejneru a je součástí vnitřních vrstev nebo knihoven. Nevýhodou na tento přístup přichází, pokud nebo když aplikace roste a vyžaduje škálování. Pokud se celá aplikace škáluje, není ve skutečnosti problém. Ve většině případů je však několik částí aplikace sytičmi body, které vyžadují škálování, zatímco jiné součásti jsou používány méně.

Pomocí typického příkladu elektronického obchodování budete pravděpodobně potřebovat škálovat součást informací o produktu. Mnoho dalších zákazníků prochází produkty, než je koupí. Další zákazníci používají svůj koš, než používá platební kanál. Méně zákazníkům přidávají komentáře nebo zobrazují historii jejich nákupu. A máte pravděpodobně pouze několik zaměstnance v jedné oblasti, které potřebují spravovat obsah a marketingové kampaně. Změnou měřítka návrhu monolitické je celý kód nasazen několikrát.

Kromě problému "škálování na vše" se změny jedné součásti vyžadují kompletní opětovné testování celé aplikace a také úplné opětovné nasazení všech instancí.

Přístup k monolitické je společný a mnoho organizací vyvíjí s touto architekturou. Spousta lidí má dobré výsledky, zatímco ostatní mají omezení. Mnoho z nich navrhlo své aplikace v tomto modelu, protože nástroje a infrastruktura byly příliš obtížné sestavovat SOAs a neviděli nutnost, dokud se aplikace vypnula.

Z hlediska infrastruktury může každý server spouštět mnoho aplikací v rámci stejného hostitele a mít přijatelný poměr efektivity v používání prostředků, jak je znázorněno na obrázku 4-2.

![Diagram znázorňující jednoho hostitele s více aplikacemi v samostatných kontejnerech.](./media/monolithic-applications/host-with-multiple-apps-containers.png)

**Obrázek 4-2.** Hostitel, na kterém běží víc aplikací nebo kontejnerů

Z perspektivy dostupnosti musí být aplikace monolitické nasazené jako celek; To znamená, že v případě, že je třeba *zastavit a spustit*, budou všechny funkce a všichni uživatelé ovlivněni během okna nasazení. V některých situacích může použití Azure a kontejnerů minimalizovat tyto situace a snížit pravděpodobnost výpadku aplikace, jak vidíte na obrázku 4-3.

V Azure můžete nasazovat aplikace monolitické pomocí vyhrazených virtuálních počítačů pro každou instanci. Pomocí [Azure VM Scale Sets](https://docs.microsoft.com/azure/virtual-machine-scale-sets/)můžete virtuální počítače snadno škálovat.

[Azure App Services](https://azure.microsoft.com/services/app-service/) můžete použít také ke spouštění aplikací monolitické a ke snadnému škálování instancí bez nutnosti správy virtuálních počítačů. Azure App Services může spouštět jednotlivé instance kontejnerů Docker a zjednodušit tak nasazení.

Můžete nasadit více virtuálních počítačů jako hostitele Docker a spustit libovolný počet kontejnerů na virtuální počítač. Pak pomocí Azure Load Balancer, jak je znázorněno na obrázku 4-3, můžete spravovat škálování.

![Diagram znázorňující monolitické aplikaci škálované na různé hostitele.](./media/monolithic-applications/multiple-hosts-from-single-docker-container.png)

**Obrázek 4-3**. Víc hostitelů škáluje jednu aplikaci Docker

Nasazení hostitelů můžete spravovat pomocí tradičních technik nasazení.

Kontejnery Docker můžete spravovat z příkazového řádku pomocí příkazů jako `docker run` a `docker-compose up` a můžete je také automatizovat v kanálech pro průběžné doručování (CD) a nasazovat je do hostitelů Docker z Azure DevOps Services.

## <a name="monolithic-application-deployed-as-a-container"></a>Aplikace monolitické nasazená jako kontejner

Existují výhody použití kontejnerů ke správě nasazení monolitické. Škálování instancí kontejnerů je mnohem rychlejší a jednodušší než nasazení dalších virtuálních počítačů.

Nasazování aktualizací jako imagí Docker je mnohem rychlejší a efektivně v síti. Kontejnery Docker obvykle začínají během sekund a urychlují uvádění. Vysunutí kontejneru Docker je stejně snadné jako vyvolání příkazu `docker stop`, obvykle se dokončuje za méně než sekundu.

Vzhledem k tomu, že kontejnery jsou z vlastního podstaty neměnné, nemusíte se o poškozených virtuálních počítačích starat, protože se pro určitou konkrétní konfiguraci nebo soubory, které jsou ponechány na disku, zazapomněl skript pro aktualizaci

I když aplikace monolitické můžou využívat Docker, zajímáme jenom tipy k výhodám. Větší výhody správy kontejnerů přináší nasazení s orchestrací kontejnerů, které spravují různé instance a životní cyklus každé instance kontejneru. Rozdělení aplikace monolitické do subsystémů, které je možné škálovat, vyvíjet a nasadit samostatně, je vstupním bodem ve sféře mikroslužeb.

Další informace o tom, jak namonolitické aplikace pomocí kontejnerů a jak modernizovat vaše aplikace, si můžete přečíst v této další příručce k Microsoftu, [modernizovat stávající aplikace .NET pomocí cloudu Azure a kontejnerů Windows](../../modernize-with-azure-containers/index.md). které můžete také stáhnout jako PDF z <https://aka.ms/LiftAndShiftWithContainersEbook>.

## <a name="publish-a-single-docker-container-app-to-azure-app-service"></a>Publikování jedné aplikace kontejneru Docker pro Azure App Service

Vzhledem k tomu, že chcete získat rychlé ověření kontejneru nasazeného do Azure nebo protože aplikace je jednoduše aplikace s jedním kontejnerem, Azure App Services poskytuje skvělý způsob, jak zajistit škálovatelné služby s jedním kontejnerem.

Použití Azure App Service je intuitivní a můžete rychle začít pracovat, protože poskytuje skvělou integraci Git, jak si svůj kód sestavit, vytvořit ho v Microsoft Visual Studio a přímo ho nasadit do Azure. Ale tradičně (bez Docker), pokud jste potřebovali jiné funkce, architektury nebo závislosti, které nejsou podporované v App Services, je potřeba počkat, dokud tým Azure tyto závislosti v App Service neaktualizuje nebo přepnete na jiné služby, jako je například Service Fabric, Cloud Services nebo dokonce jednoduché virtuální počítače, pro které máte další kontrolu a můžete nainstalovat požadovanou součást nebo architekturu pro vaši aplikaci.

Jak je znázorněno na obrázku 4-4, při použití sady Visual Studio 2017 vám podpora kontejnerů v Azure App Service dává možnost zahrnout cokoli, co chcete v prostředí aplikace. Pokud jste do své aplikace přidali závislost, protože ji spouštíte v kontejneru, získáte možnost zahrnout tyto závislosti do souboru Dockerfile nebo Docker image.

![Snímek obrazovky dialogového okna pro vytvoření App Service zobrazující Container Registry](./media/monolithic-applications/publish-azure-app-service-container.png)

**Obrázek 4-4**. Publikování kontejneru do Azure App Service z aplikací nebo kontejnerů sady Visual Studio

Obrázek 4-4 také ukazuje, že tok publikování nabízí obrázek prostřednictvím Container Registry, což může být Azure Container Registry (registr poblíž nasazení v Azure a zabezpečeného Azure Active Directorymi skupinami a účty) nebo jakýmkoli jiným registrem Docker. například Docker Hub nebo místní registry.

>[!div class="step-by-step"]
>[Předchozí](common-container-design-principles.md)
>[Další](state-and-data-in-docker-applications.md)
