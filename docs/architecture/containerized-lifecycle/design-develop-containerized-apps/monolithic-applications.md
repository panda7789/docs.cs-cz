---
title: Monolitické aplikace
description: Seznamte se s základními koncepty pro kontejnerizaci monolitických aplikací.
ms.date: 02/15/2019
ms.openlocfilehash: 8664153ee2e9d1d253164e43ac13105f6dbf476c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72771034"
---
# <a name="monolithic-applications"></a>Monolitické aplikace

V tomto scénáři vytváříte jednu a monolitickou webovou aplikaci nebo službu a nasazujete ji jako kontejner. V rámci aplikace struktura nemusí být monolitické; může obsahovat několik knihoven, komponent nebo dokonce vrstev (aplikační vrstva, doménová vrstva, vrstva přístupu k datům atd.). Externě je to jeden kontejner, jako je jeden proces, jedna webová aplikace nebo jedna služba.

Chcete-li spravovat tento model, nasadit jeden kontejner reprezentovat aplikaci. Chcete-li jej škálovat, stačí přidat několik dalších kopií s vyvažovačem zatížení vpředu. Jednoduchost pochází ze správy jednoho nasazení v jednom kontejneru nebo virtuálním počítači (VM).

Následující jistiny, že kontejner dělá pouze jednu věc a dělá to v jednom procesu, monolitický vzor je v konfliktu. Do každého kontejneru můžete zahrnout více součástí/knihoven nebo vnitřních vrstev, jak je znázorněno na obrázku 4-1.

![Diagram znázorňující monolitickou aplikaci, která se škáluje klonováním aplikace.](./media/monolithic-applications/monolithic-application-architecture-example.png)

**Obrázek 4-1.** Příklad architektury monolitických aplikací

Monolitická aplikace má všechny nebo většinu svých funkcí v rámci jednoho procesu nebo kontejneru a je komponentována ve vnitřních vrstvách nebo knihovnách. Nevýhodou tohoto přístupu přichází, pokud nebo když aplikace roste, vyžadující škálování. Pokud se celá aplikace škálovat, to není opravdu problém. Ve většině případů však několik částí aplikace jsou body sytiče, které vyžadují škálování, zatímco jiné součásti se používají méně.

Pomocí typického příkladu elektronického obchodování pravděpodobně budete potřebovat škálování komponenty informací o produktu. Mnohem více zákazníků procházet produkty, než je zakoupit. Více zákazníků používá svůj košík než kanál plateb. Méně zákazníků přidává komentáře nebo si prohlíží historii nákupů. A pravděpodobně máte jen hrstku zaměstnanců v jedné oblasti, kteří potřebují spravovat obsah a marketingové kampaně. Změnou měřítka monolitického návrhu je veškerý kód nasazen vícekrát.

Kromě problému "scale-everything" vyžadují změny jedné součásti úplné opětovné testování celé aplikace a také úplné opětovné nasazení všech instancí.

Monolitický přístup je běžný a mnoho organizací se vyvíjí s touto architektonickou metodou. Mnozí mají dost dobré výsledky, zatímco jiní se setkávají s limity. Mnozí navrhli své aplikace v tomto modelu, protože nástroje a infrastruktura byly příliš obtížné vytvořit SOA a neviděli potřebu – dokud aplikace nerostla.

Z hlediska infrastruktury může každý server spouštět mnoho aplikací v rámci stejného hostitele a mít přijatelný poměr efektivity využití prostředků, jak je znázorněno na obrázku 4-2.

![Diagram znázorňující jednoho hostitele s více aplikacemi v samostatných kontejnerech.](./media/monolithic-applications/host-with-multiple-apps-containers.png)

**Obrázek 4-2.** Hostitel s více aplikacemi a kontejnery

Nakonec z hlediska dostupnosti monolitické aplikace musí být nasazeny jako celek; to znamená, že v případě, že musíte *zastavit a spustit*, všechny funkce a všichni uživatelé budou ovlivněny během okna nasazení. V určitých situacích použití Azure a kontejnerů můžete minimalizovat tyto situace a snížit pravděpodobnost prostojů vaší aplikace, jak můžete vidět na obrázku 4-3.

Monolitické aplikace v Azure můžete nasadit pomocí vyhrazených virtuálních počítačů pro každou instanci. Pomocí [škálovacích sad virtuálních počítačích Azure](https://docs.microsoft.com/azure/virtual-machine-scale-sets/)můžete snadno škálovat virtuální počítače.

Pomocí azure [app services](https://azure.microsoft.com/services/app-service/) můžete taky spouštět monolitické aplikace a snadno škálovat instance, aniž byste museli spravovat virtuální počítače. Azure App Services můžete spustit jednotlivé instance kontejnerů Dockeru, také zjednodušení nasazení.

Můžete nasadit více virtuálních počítačů jako hostitele Dockeru a spustit libovolný počet kontejnerů na virtuální počítač. Potom pomocí Azure Balancer, jak je znázorněno na obrázku 4-3, můžete spravovat škálování.

![Diagram znázorňující monolitickou aplikaci, která se škáluje na různé hostitele.](./media/monolithic-applications/multiple-hosts-from-single-docker-container.png)

**Obrázek 4-3**. Více hostitelů škálování z jedné aplikace Dockeru

Nasazení samotných hostitelů můžete spravovat pomocí tradičních technik nasazení.

Kontejnery Dockeru můžete spravovat z příkazového `docker run` `docker-compose up`řádku pomocí příkazů jako a , a můžete je také automatizovat v kanálech průběžného doručování (CD) a nasadit je na hostitele Dockeru ze služby Azure DevOps Services, například.

## <a name="monolithic-application-deployed-as-a-container"></a>Monolitická aplikace nasazená jako kontejner

Použití kontejnerů ke správě monolitických nasazení přináší výhody. Škálování instance kontejnerů je mnohem rychlejší a jednodušší než nasazení dalších virtuálních mandů.

Nasazení aktualizací jako inamů Dockeru je mnohem rychlejší a efektivní v síti. Kontejnery Dockeru se obvykle spouštějí během několika sekund, což urychluje zavádění. Stržení kontejneru Dockeru je stejně `docker stop` snadné jako vyvolání příkazu, obvykle dokončení za méně než sekundu.

Vzhledem k tomu, že kontejnery jsou ze své podstaty neměnné, podle návrhu se nikdy nemusíte starat o poškozené virtuální počítače, protože skript aktualizace zapomněl účet pro některé konkrétní konfigurace nebo soubor vlevo na disku.

I když monolitické aplikace mohou těžit z Dockeru, dotýkáme se pouze tipů výhod. Větší výhody správy kontejnerů pocházejí z nasazení s orchestrátory kontejnerů, které spravují různé instance a životní cyklus každé instance kontejneru. Rozdělení monolitické aplikace do subsystémů, které lze škálovat, vyvíjet a nasazovat jednotlivě, je vstupním bodem do sféry mikroslužeb.

Chcete-li se dozvědět o tom, jak "zvednout a posunout" monolitické aplikace s kontejnery a jak můžete modernizovat aplikace, přečtěte si tento další průvodce Microsoft, [Modernizovat stávající aplikace .NET s Azure cloud a Windows Containers](../../modernize-with-azure-containers/index.md), které si můžete stáhnout také ve formátu PDF z <https://aka.ms/LiftAndShiftWithContainersEbook>.

## <a name="publish-a-single-docker-container-app-to-azure-app-service"></a>Publikování jedné aplikace kontejneru Dockeru do služby Azure App Service

Buď proto, že chcete získat rychlé ověření kontejneru nasazeného do Azure, nebo proto, že aplikace je jednoduše aplikace s jedním kontejnerem, Azure App Services poskytuje skvělý způsob, jak poskytovat škálovatelné služby s jedním kontejnerem.

Používání služby Azure App Service je intuitivní a můžete rychle začít pracovat, protože poskytuje skvělou integraci Gitu, která umožňuje vzít váš kód, sestavit ho v Microsoft Visual Studiu a přímo ho nasadit do Azure. Ale tradičně (bez Dockeru), pokud jste potřebovali další funkce, architektury nebo závislosti, které nejsou podporované ve Službách aplikací, musíte na to počkat, dokud tým Azure neaktualizuje tyto závislosti ve službě App Service nebo přejde na jiné služby, jako je Service Fabric, cloudové služby nebo dokonce prosté virtuální počítače, pro které máte další kontrolu a můžete nainstalovat požadovanou komponentu nebo architekturu pro vaši aplikaci.

Teď, jak je znázorněno na obrázku 4-4, při použití Visual Studia 2017, podpora kontejnerů ve službě Azure App Service vám dává možnost zahrnout vše, co chcete v prostředí aplikace. Pokud jste do aplikace přidali závislost, protože ji spouštěte v kontejneru, získáte možnost zahrnutí těchto závislostí do image Dockerfile nebo Dockeru.

![Snímek obrazovky s dialogem Vytvořit službu aplikace zobrazujícího registr kontejnerů](./media/monolithic-applications/publish-azure-app-service-container.png)

**Obrázek 4-4**. Publikování kontejneru do služby Azure App Service z aplikací a kontejnerů Visual Studia

Obrázek 4-4 také ukazuje, že tok publikování tlačí image prostřednictvím registru kontejnerů, což může být Registr kontejnerů Azure (registr v blízkosti vašich nasazení v Azure a zabezpečené skupinami a účty Služby Azure Active Directory) nebo jakýkoli jiný registr Dockeru jako je Docker Hub nebo místní registry.

>[!div class="step-by-step"]
>[Předchozí](common-container-design-principles.md)
>[další](state-and-data-in-docker-applications.md)
