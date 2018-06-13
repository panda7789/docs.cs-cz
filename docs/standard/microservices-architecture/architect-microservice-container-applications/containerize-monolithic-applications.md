---
title: Containerizing monolitický aplikace
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Containerizing monolitický aplikace
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: f5d00c6ce4c965d66937dae3f8e5453883afb4b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33577248"
---
# <a name="containerizing-monolithic-applications"></a>Containerizing monolitický aplikace

Můžete chtít vytvořit jeden, monolithically nasazené webové aplikace nebo služby a nasaďte ho jako kontejner. Vlastní aplikace nemusí být interně monolitický, ale strukturovaná jako několik knihovny, komponenty nebo dokonce i vrstvy (aplikační vrstvu, domény vrstvy, přístup k datům vrstvy atd.). Externě, ale je jediný kontejner – jeden proces, jednu webovou aplikaci nebo jedné služby.

Ke správě tohoto modelu, můžete nasadit jediný kontejner k reprezentaci aplikace. Škálování, stačí přidat více kopií pro vyrovnávání zatížení vpředu. Jednoduchost pochází z Správa jedno nasazení v jedné kontejneru nebo virtuálních počítačů.

![](./media/image1.png)

**Obrázek 4-1**. Příklad architektury kontejnerizované monolitický aplikace

V každém kontejneru, můžete zahrnout více součástí, knihovny nebo interní vrstvy, jak ukazuje obrázek 4-1. Však může tento vzor monolitický konfliktu se zásadou kontejneru "kontejner nemá jednou z věcí a nemá v jednom procesu", ale může být v některých případech ok.

Nevýhodou tohoto přístupu bude zřejmé, pokud aplikace roste, vyžadování ji škálovat. Pokud bude celá aplikace můžete použít škálování, není skutečně problém. Ve většině případů jsou několika částí aplikace potlačení body, že vyžadování škálování, zatímco ostatní součásti jsou používá menší.

Například v aplikaci typické elektronické obchodování, je pravděpodobně potřeba škálování subsystému informace o produktu, protože mnoho zákazníků další Procházet produkty než jejich zakoupení. Další zákazníci využívat nákupního košíku než použití kanálu platba. Méně zákazníky přidání komentářů nebo zobrazit historii jejich nákupu. A může mít jen někteří z nich zaměstnancům, kteří potřebují spravovat obsah a marketingové kampaně. Pokud je škálovat monolitický návrhu, všechny kód pro tyto různé úlohy je nasadit více než jednou a škálovat na stejné úrovni.

Existuje více způsobů škálování aplikace – duplikaci vodorovné rozdělení různé oblasti aplikace a rozdělení podobné koncepty firmy nebo data. Ale kromě problém škálování všechny součásti, změny jedinou komponentu vyžadují opětovném dokončení testování v celé aplikaci a dokončení opětovného nasazení všech instancí.

Monolitický přístup je však běžné, protože je původně jednodušší než mikroslužeb přístupy vývoje aplikace. Mnoho organizací vyvíjet proto tento architektury přístup. Když některé organizace mají vhodné měl dostatek výsledky, ostatní nedosáhli limitů. Mnoho organizací určené svých aplikací pomocí tohoto modelu, protože nástroje a infrastruktura provedené příliš složité, vytvoření služby zaměřené na konkrétní architektury (SOA) lety a nenalezli potřeba – dokud vzrostla aplikace.

Z hlediska služby infrastruktury každý server můžete spustit mnoho aplikací v rámci stejného hostitele a mají přijatelné poměr efektivitu využití prostředků, jak je znázorněno na obrázku 4-2.

![](./media/image2.png)

**Obrázek 4-2**. Monolitický přístup: hostitele spuštěných víc aplikací, každou aplikaci spuštěnou jako kontejner

Monolitický aplikací v Microsoft Azure se dá nasadit pomocí vyhrazených virtuálních počítačích pro každou instanci. Kromě toho používání [škálovatelné sady virtuálních počítačů Azure](https://docs.microsoft.com/azure/virtual-machine-scale-sets/), je možné snadno škálovat virtuálních počítačů. [Aplikační služba Azure](https://azure.microsoft.com/services/app-service/) můžete také spouštět monolitický aplikace a snadno škálovat instance, aniž by bylo nutné ke správě virtuálních počítačů. Od 2016 můžete Azure App Services spustit jedné instance Docker kontejnery také, což výrazně zjednodušuje nasazování.

Jako prostředí QA nebo omezeném produkčním prostředí můžete nasadit více Docker hostitele virtuálních počítačů a vyvážení pomocí Azure vyrovnávání, jak je uvedené v obrázek 4-3. To vám umožní spravovat škálování s hrubým intervalem přístup, protože celou aplikaci obsažen v jednom kontejneru.

![](./media/image3.png)

**Obrázek 4-3**. Příklad více hostitelů vertikálním navýšení kapacity aplikace jediný kontejner

Nasazení na různých hostitelích lze spravovat pomocí techniky tradiční nasazení. Hostitelů docker lze spravovat pomocí příkazů jako `docker run` nebo `docker-compose` provést ručně, nebo prostřednictvím automatizace například kanály nastavené průběžné doručování (CD).

## <a name="deploying-a-monolithic-application-as-a-container"></a>Nasazení monolitický aplikace jako kontejner

Existují výhody použití kontejnerů ke správě nasazení monolitický aplikací. Změna velikosti kontejner instancí je mnohem rychlejší a snadnější než nasazení dalších virtuálních počítačů. I když používáte škálovatelné sady virtuálních počítačů, virtuálních počítačů trvat dobu spuštění. Při nasazení jako instancemi tradiční aplikace místo kontejnery, konfigurace aplikace je spravovaná v rámci virtuálního počítače, což není ideální.

Nasazení aktualizací, jako je mnohem rychlejší imagí Dockeru a efektivní sítě. Imagí dockeru obvykle spustit v sekundách, tím se urychlí zavedení uživatelům. Zrušení do instance Docker bitové kopie je stejně snadná jako vystavování `docker stop` příkazů a obvykle se dokončí za méně než jedna sekunda.

Protože kontejnery jsou neměnné záměrné, budete muset nikdy starat o poškozená virtuálních počítačů. Naproti tomu skriptů pro aktualizaci pro virtuální počítač může nezapomněli účet pro některé specifické konfigurace nebo soubor místu na disku.

Při monolitický aplikace, můžete využít Docker, jsou dotykové ovládání pouze na výhody. Další výhody správy kontejnerů pocházet z nasazení s orchestrators kontejneru, které spravovat různé instance a životního cyklu jednotlivých instancí kontejneru. Rozdělení monolitický aplikaci do subsystémy, které můžete škálovat, vyvinuté a nasadit jednotlivě je vašim vstupním bodem do sféru mikroslužeb.

## <a name="publishing-a-single-container-based-application-to-azure-app-service"></a>Publikování aplikace na základě jednoho kontejneru do služby Azure App Service

Jestli chcete získat ověření kontejner nasadí do Azure nebo pokud aplikace je jednoduše jedním kontejnerem aplikace, služby Azure App Service nabízí skvělý způsob, jak poskytnout škálovatelných služeb na základě jednoho kontejneru. Pomocí služby Azure App Service je jednoduché. Nabízí skvělý integrace s Gitem snadno využít kódu, sestavení v sadě Visual Studio a nasadit přímo do Azure.

![](./media/image4.png)

**Obrázek 4 – 4**. Publikování jedním kontejneru aplikace do služby Azure App Service ze sady Visual Studio

Bez Docker v případě potřeby další možnosti, architektury nebo závislosti, které nejsou podporovány v Azure App Service, museli jste Počkejte, dokud tým Azure aktualizovat tyto závislosti ve službě App Service. Nebo jste museli přepnout na další služby, jako je Azure Service Fabric, Azure Cloud Services nebo i virtuální počítače, kde jste měli další ovládací prvek a můžete nainstalovat požadovanou součást nebo framework pro vaši aplikaci.

Podpora kontejnerů v Visual Studio 2017 vám dává možnost zahrnout všechno ve vašem prostředí aplikace, jak je znázorněno na obrázku 4-4. Vzhledem k tomu, že spustíte ji v kontejneru, je-li přidat závislost do vaší aplikace, můžete zahrnout závislost soubor Docker nebo Docker image.

Jak je také uvedené na obrázku 4-4 doručí toku publikovat bitovou kopii prostřednictvím registru kontejneru. To může být Azure registru kontejneru (registru zavřete pro vaše nasazení v Azure a zabezpečené účty a skupiny Azure Active Directory), nebo jakékoli jiné Docker registru jako úložiště Docker Hub nebo místní registru.


>[!div class="step-by-step"]
[Předchozí] (index.md) [Další] (docker-application-state-data.md)
