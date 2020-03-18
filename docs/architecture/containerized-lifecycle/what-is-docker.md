---
title: Co je Docker?
description: Získejte trochu hlouběji ve svém chápání Docker, jednoduchá analogie zde vám může pomoci.
ms.date: 02/15/2019
ms.openlocfilehash: e3b3685f2fc6d5a9d33bb176d04ca910f0289344
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76919879"
---
# <a name="what-is-docker"></a>Co je Docker?

[Docker](https://www.docker.com/) je [open source projekt](https://github.com/docker/docker) pro automatizaci nasazení aplikací jako přenosných, soběstačných kontejnerů, které lze spustit v cloudu nebo v místním prostředí. Docker je také [společnost,](https://www.docker.com/) která tuto technologii propaguje a vyvíjí a spolupracuje s dodavateli cloudu, Linuxu a Windows, včetně Microsoftu.

![Diagram znázorňující místa, kde mohou být spuštěny kontejnery Dockeru.](./media/what-is-docker/docker-containers-run-anywhere.png)

**Obrázek 1-2**. Docker nasazuje kontejnery ve všech vrstvách hybridního cloudu

Jak je znázorněno na výše uvedeném diagramu, kontejnery Dockeru můžou běžet kdekoli, místně v zákaznickém datovém centru, u externího poskytovatele služeb nebo v cloudu v Azure. Kontejnery image Dockeru můžou taky běžet nativně v Linuxu a Windows. Bitové kopie systému Windows však mohou běžet pouze na hostitelích systému Windows a bitové kopie Linuxu mohou běžet na hostitelích Linuxu a hostitelích systému Windows (pomocí virtuálního počítače Hyper-V Linux), kde hostitel znamená server nebo virtuální počítač.

Vývojáři můžou používat vývojová prostředí ve Windows, Linuxu nebo macOS. Ve vývojovém počítači vývojář spustí hostitele Dockeru, kde se nasazují ifotky Dockeru, včetně aplikace a jejích závislostí. Vývojáři, kteří pracují na Linuxu nebo na Macu, používají hostitele Dockeru, který je založený na Linuxu, a mohou vytvářet pouze obrázky pro kontejnery Linuxu. (Vývojáři pracující na Macu můžou upravovat kód nebo spouštět rozhraní příkazového příkazu Dockeru z macOS, ale od tohoto psaní kontejnery neběží přímo v systému macOS.) Vývojáři, kteří pracují v systému Windows, mohou vytvářet obrázky pro linuxové nebo kontejnery windows.

Aby bylo účelem hostování kontejnerů ve vývojových prostředích a poskytování dalších vývojářských nástrojů, docker dodává [Docker Community Edition (CE)](https://www.docker.com/community-edition) pro Windows nebo macOS. Tyto produkty nainstalují potřebný virtuální hod (hostitele Dockeru) k hostování kontejnerů. Docker také zpřístupňuje [Docker Enterprise Edition (EE),](https://www.docker.com/enterprise-edition)který je určen pro vývoj podniku a používá it týmy, které vytvářejí, doručují a provozují velké důležité podnikové aplikace v produkčním prostředí.

Chcete-li spustit [kontejnery systému Windows](/virtualization/windowscontainers/about/), existují dva typy runtimes:

- **Kontejnery windows serveru** poskytují izolaci aplikací prostřednictvím technologie izolace procesu a oboru názvů. Kontejner systému Windows Server sdílí jádro s hostitelem kontejneru a se všemi kontejnery spuštěnými na hostiteli.

- **Kontejnery Hyper-V** se rozšiřují na izolaci poskytovanou kontejnery Windows Server spuštěním každého kontejneru ve vysoce optimalizovaném virtuálním počítači. V této konfiguraci jádro hostitele kontejneru není sdíleno s hyper-v kontejnery, poskytuje lepší izolaci.

Obrázky pro tyto kontejnery jsou vytvořeny a fungují stejným způsobem. Rozdíl je v tom, jak je kontejner vytvořen z bitové kopie – spuštění kontejneru Hyper-V vyžaduje další parametr. Podrobnosti naleznete v [tématu Hyper-V Containers](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/hyperv-container).

## <a name="comparing-docker-containers-with-virtual-machines"></a>Porovnání kontejnerů Dockeru s virtuálními počítači

Obrázek 1-3 ukazuje porovnání mezi virtuálními a dockerovými kontejnery.

![Diagram znázorňující porovnání virtuálních virtuálních připojení a prostředí kontejnerů.](./media/what-is-docker/comparison-vms-docker-conatiners.png)

**Obrázek 1-3**. Porovnání tradičních virtuálních počítačů s kontejnery Dockeru

Jak je znázorněno na výše uvedeném diagramu, pro virtuální servery existují tři základní vrstvy na hostitelském serveru. Zdola nahoru: Infrastruktura, Hostitelský operační systém a Hypervisor. Kromě toho má každý virtuální počítač svůj vlastní operační systém a všechny potřebné knihovny. Na druhou stranu pro Docker hostitelský server má pouze infrastrukturu a operační systém. Kromě toho kontejnerový motor udržuje kontejnery izolované, ale umožňuje jim sdílet služby jednotného operačního systému.

Vzhledem k tomu, že kontejnery vyžadují mnohem méně prostředků (například nepotřebují úplný operační režim), snadno se nasazují a spouštějí se rychle. To vám umožní mít vyšší hustotu, což znamená, že umožňuje spustit více služeb na stejné hardwarové jednotce, čímž se sníží náklady.

Jako vedlejší účinek spuštění na stejném jádru získáte menší izolaci než virtuální počítač.

Hlavním cílem image je zajistit stejné prostředí (závislosti) v různých nasazeních. To znamená, že můžete ladit v počítači a pak jej nasadit do jiného počítače, stejné prostředí zaručena.

Image kontejneru je způsob, jak zabalit aplikaci nebo službu a nasadit ji spolehlivým a reprodukovatelným způsobem. Dalo by se říci, že Docker není jen technologie, ale také filozofie a proces.

Při použití Dockeru neuslyšíte, jak vývojáři říkají: "Funguje to na mém počítači, proč ne ve výrobě?" Mohou jen říct, "Běží na Dockeru", protože zabalená aplikace Dockeru může být spuštěna v libovolném podporovaném prostředí Dockeru a běží tak, jak byla určena pro všechny cíle nasazení (například Dev, QA, staging a production).

## <a name="a-simple-analogy"></a>Jednoduchá analogie

Možná, že jednoduchá analogie může pomoci získat pochopení základní koncepce Docker.

Vraťme se na chvíli zpět v čase do padesátých let. Nebyly tam žádné textové procesory a kopírky byly používány všude (dobře, druh).

Představte si, že jste zodpovědní za rychlé vydávání dávek dopisů podle potřeby, zaslat je zákazníkům pomocí skutečného papíru a obálek, které mají být fyzicky doručeny na adresu každého zákazníka (tehdy nebyl žádný e-mail).

V určitém okamžiku si uvědomíte, že písmena jsou jen složenívelké sady odstavců, které jsou vybírány a uspořádány podle potřeby podle účelu dopisu, takže navrhnete systém, který rychle vydává dopisy a očekává, že dostane statný raise.

Systém je jednoduchý:

1. Začínáte s balíčkem průhledných listů obsahujících každý jeden odstavec.

2. Chcete-li vydat sadu písmen, vyberte listy s odstavci, které potřebujete, pak je stohovat a zarovnat tak, aby vypadaly a četly dobře.

3. Nakonec umístíte sadu do kopírky a stisknutím tlačítka začnete produkovat tolik písmen, kolik je potřeba.

Takže, zjednodušení, to je základní myšlenka Dockeru.

V Dockeru je každá vrstva výslednou sadou změn, ke kterým dojde v souborovém systému po provedení příkazu, například instalace programu.

Takže, když se "podíváte" na souborový systém po zkopírování vrstvy, uvidíte všechny soubory, včetně vrstvy při instalaci programu.

Bitovou kopii si můžete představit jako pomocný pevný disk připravený k instalaci do "počítače", kde je operační systém již nainstalován.

Podobně si můžete představit kontejner jako "počítač" s nainstalovaným pevným diskem bitové kopie. Kontejner, stejně jako počítač, lze zapnout nebo vypnout.

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[další](docker-terminology.md)
