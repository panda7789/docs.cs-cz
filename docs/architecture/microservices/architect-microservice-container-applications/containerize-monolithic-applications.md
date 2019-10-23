---
title: Kontejnerizování monolitických aplikací
description: Uzavření monolitické aplikace, i když nezískají všechny výhody architektury mikroslužeb, přináší důležité výhody nasazení, které se dají hned doručovat.
ms.date: 09/20/2018
ms.openlocfilehash: 5b38ba1c2954f4fd4064723b1316afbf09d25bf2
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771482"
---
# <a name="containerizing-monolithic-applications"></a>Kontejnerizování monolitických aplikací

Možná budete chtít sestavit jednu, monolithically nasazenou webovou aplikaci nebo službu a nasadit ji jako kontejner. Samotná aplikace nemusí být interně monolitické, ale bude strukturovaná jako několik knihoven, komponent nebo dokonce vrstev (vrstva aplikace, vrstva domény, vrstva přístupu k datům atd.). Externě ale je to jediný kontejner – jeden proces, jedna webová aplikace nebo jedna služba.

Chcete-li spravovat tento model, nasadíte jeden kontejner, který bude představovat aplikaci. Abyste zvýšili kapacitu, můžete škálovat, to znamená, že stačí přidat další kopie pomocí nástroje pro vyrovnávání zatížení předem. Jednoduchost pochází ze správy jednoho nasazení v jednom kontejneru nebo virtuálním počítači.

![Monolitické kontejnerová aplikace má většinu funkcí v rámci jednoho kontejneru, interní vrstvy nebo knihovny, ANS se škáluje klonování kontejneru na více serverech nebo virtuálních počítačů.](./media/image1.png)

**Obrázek 4-1**. Příklad architektury kontejnerové aplikace monolitické

Do každého kontejneru můžete zahrnout více komponent, knihoven nebo vnitřních vrstev, jak je znázorněno na obrázku 4-1. Tento vzor monolitické ale může být v konfliktu s principem kontejneru "kontejner provede jednu věc a provede ho v jednom procesu", ale může být v některých případech v pořádku.

Nevýhodou tohoto přístupu se projeví i v případě, že aplikace roste a vyžaduje, aby se změnila. Pokud se celá aplikace může škálovat, není ve skutečnosti problém. Ve většině případů je však pouze několik částí aplikace sytiče body, které vyžadují škálování, zatímco jiné součásti jsou používány méně.

Například v typické aplikaci elektronického obchodování pravděpodobně budete potřebovat škálovat podsystém informací o produktu, protože mnoho dalších zákazníků prochází produkty, než je koupí. Další zákazníci používají svůj koš, než používá platební kanál. Méně zákazníkům přidávají komentáře nebo zobrazují historii jejich nákupu. A můžete mít jenom několik zaměstnance, kteří potřebují spravovat obsah a marketingové kampaně. Pokud budete škálovat návrh monolitické, veškerý kód těchto různých úloh se nasadí několikrát a škáluje se ve stejné třídě.

Existuje několik způsobů, jak škálovat horizontální duplikaci aplikace, dělení různých oblastí aplikace a dělení podobných obchodních konceptů nebo dat. Kromě problému s škálováním všech komponent ale změny jedné součásti vyžadují dokončení opětovného testování celé aplikace a úplné opětovné nasazení všech instancí.

Přístup k monolitické je ale běžný, protože vývoj aplikace je zpočátku jednodušší než u přístupů k mikroslužbám. Mnohé organizace proto vyvíjejí používání tohoto přístupu do architektury. I když některé organizace mají dostatečný výsledek, ostatní jsou limity pro povýšení. Řada organizací navrhla své aplikace pomocí tohoto modelu, protože nástroje a infrastruktura je moc obtížné sestavovat před roky orientované na služby (SOA), a nemuseli nevidět potřebu, dokud se aplikace nezvětšila.

Z hlediska infrastruktury může každý server spouštět mnoho aplikací v rámci stejného hostitele a mít přijatelný poměr efektivity při využití prostředků, jak je znázorněno na obrázku 4-2.

![Hostitel může spustit několik aplikací monolitické, každý z nich na samostatném kontejneru.](./media/image2.png)

**Obrázek 4-2**. Přístup k monolitické: hostitel spouštějící víc aplikací, každou aplikaci spuštěnou jako kontejner.

Monolitické aplikace v Microsoft Azure lze nasadit pomocí vyhrazených virtuálních počítačů pro každou instanci. Kromě toho můžete pomocí [Azure Virtual Machine Scale Sets](https://azure.microsoft.com/documentation/services/virtual-machine-scale-sets/)snadno škálovat virtuální počítače. [Azure App Service](https://azure.microsoft.com/services/app-service/) můžou také spouštět aplikace monolitické a snadno škálovat instance, aniž byste museli spravovat virtuální počítače. Od 2016 může Azure App Services spustit i jednu instanci kontejnerů Docker a zjednodušit tak nasazení.

Jako prostředí QA nebo omezené provozní prostředí můžete nasadit víc virtuálních počítačů hostitele Docker a vyvážit je pomocí nástroje Azure Balancer, jak je znázorněno na obrázku 4-3. To vám umožní spravovat škálování pomocí hrubého přístupu, protože celá aplikace žije v rámci jednoho kontejneru.

![Několik hostitelů, každý z nich, který spouští kontejner s aplikací monolitické.](./media/image3.png)

**Obrázek 4-3**. Příklad více hostitelů s vertikálním škálováním jedné aplikace kontejneru

Nasazení na různé hostitele je možné spravovat pomocí tradičních technik nasazení. Hostitelé Docker je možné spravovat pomocí příkazů, jako je `docker run` nebo `docker-compose` provést ručně nebo prostřednictvím automatizace, jako jsou kanály pro průběžné doručování (CD).

## <a name="deploying-a-monolithic-application-as-a-container"></a>Nasazení aplikace monolitické jako kontejneru

Existují výhody použití kontejnerů ke správě nasazení aplikací monolitické. Škálování instancí kontejnerů je mnohem rychlejší a jednodušší než nasazení dalších virtuálních počítačů. I když používáte Virtual Machine Scale Sets, virtuální počítače se budou spouštět až po dobu. Při nasazení jako tradičních instancí aplikace namísto kontejnerů se konfigurace aplikace spravuje jako součást virtuálního počítače, což není ideální.

Nasazování aktualizací jako imagí Docker je mnohem rychlejší a efektivně v síti. Image Docker obvykle začínají během pár sekund, což zrychluje uvádění. Zrušení instance image Docker je stejně snadné jako vystavení příkazu `docker stop` a obvykle se dokončí za méně než sekundu.

Vzhledem k tomu, že kontejnery nejsou proměnlivé návrhem, nikdy nemusíte mít starosti s poškozenými virtuálními počítači. Naproti tomu se skriptům aktualizace pro virtuální počítač může zapomenout na určitou konkrétní konfiguraci nebo soubor, které zůstaly na disku.

I když můžou aplikace monolitické těžit z Docker, dohlížíme jenom na výhody. Další výhody správy kontejnerů pocházejí od nasazení s orchestrací kontejnerů, které spravují různé instance a životní cyklus každé instance kontejneru. Rozdělení aplikace monolitické do subsystémů, které je možné škálovat, vyvíjet a nasadit samostatně, je vstupním bodem ve sféře mikroslužeb.

## <a name="publishing-a-single-container-based-application-to-azure-app-service"></a>Publikování aplikace založené na jednom kontejneru pro Azure App Service

Bez ohledu na to, jestli chcete získat ověření kontejneru nasazeného do Azure nebo když je aplikace jednoduše aplikace s jedním kontejnerem, Azure App Service poskytuje skvělý způsob, jak zajistit škálovatelné služby založené na jednom kontejneru. Použití Azure App Service je jednoduché. Poskytuje skvělou integraci s Git, která usnadňuje pořizovat kód, sestavit ho v aplikaci Visual Studio a nasadit ho přímo do Azure.

![Průvodce pro publikování jedné aplikace typu kontejner do Azure App Service ze sady Visual Studio](./media/image4.png)

**Obrázek 4-4**. Publikování aplikace s jedním kontejnerem pro Azure App Service ze sady Visual Studio

Bez Docker, pokud jste potřebovali jiné funkce, architektury nebo závislosti, které nejsou podporované v Azure App Service, museli byste počkat, dokud tým Azure tyto závislosti v App Service neaktualizoval. Nebo jste museli přepnout na jiné služby, jako je Azure Cloud Services nebo virtuální počítače, kde jste měli další kontrolu a mohli jste pro svou aplikaci nainstalovat požadovanou komponentu nebo architekturu.

Podpora kontejnerů v aplikaci Visual Studio 2017 a novější vám dává možnost zahrnout cokoli, co potřebujete, do prostředí aplikace, jak je znázorněno na obrázku 4-4. Vzhledem k tomu, že ho spouštíte v kontejneru, můžete v případě, že přidáte závislost do aplikace, použít závislost do souboru Dockerfile nebo Docker image.

Jak ukazuje obrázek 4-4, tok publikování nahraje obrázek prostřednictvím registru kontejneru. Může to být Azure Container Registry (registr blízko nasazení v Azure a zabezpečený Azure Active Directorymi skupinami a účty), nebo jakýmkoli jiným registrem Docker, jako je Docker Hub nebo místní registr.

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[Další](docker-application-state-data.md)
