---
title: Co je Docker?
description: Životní cyklus aplikace kontejnerizovaných Dockeru s platformou a nástroji Microsoft
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.openlocfilehash: 360a404e38651b78acc3a52d8102a4dae71f3e30
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152706"
---
# <a name="what-is-docker"></a>Co je Docker?

[Docker](https://www.docker.com/) je [open source projektu](https://github.com/docker/docker) pro automatizaci nasazení aplikací jako přenosných a soběstační kontejnerů, které můžou běžet v cloudu nebo místně (viz obrázek 1 – 2). Docker je také [společnosti](https://www.docker.com/) , který podporuje a tato technologie funguje ve spolupráci s cloudem, Linux a Windows dodavateli, včetně Microsoft vyvíjí.

![](./media/image2.png)

Obrázek 1 – 2: Dockeru nasadí kontejnery na všech úrovních hybridního cloudu

Image kontejnerů dockeru můžete nativně běžet na systému Linux a Windows. Však imagí Windows můžete spustit pouze na hostitelích s Windows a Linuxové Image lze spustit pouze na hostitelích systému Linux, což znamená hostitelský server nebo virtuální počítač.

Vývojáři mohou pomocí vývojových prostředích Windows, Linux nebo macOS. Vývojář ve vývojovém počítači, spouští hostitele Docker k Dockeru, které jsou nasazené bitové kopie, včetně aplikace a jeho závislosti. Vývojáři, kteří pracují v Linuxu nebo na počítači Mac pomocí hostitele Docker, která je založené na Linuxu a bude možné vytvořit Image pouze pro kontejnery Linuxu. (Vývojáře, kteří pracují na počítači Mac můžete upravit kód, nebo spusťte rozhraní příkazového řádku Dockeru \[rozhraní příkazového řádku\] ze systému macOS, ale v době psaní tohoto návodu, kontejnery nelze spustit přímo v systému macOS.) Vývojáři, kteří pracují ve Windows můžete vytvořit Image pro kontejnery Windows nebo Linuxem.

K hostování kontejnerů ve vývojových prostředích a poskytují další vývojářské nástroje, Docker dodává [Docker Community Edition (CE)](https://www.docker.com/community-edition) pro Windows nebo macOS. Těchto produktů nainstalujte nezbytné virtuálního počítače (hostitele Dockeru) pro hostování kontejnerů. Docker také zpřístupní [Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition), která je určená pro vývoj podnikových a používá týmům IT, kteří vytvářejí, dodávat a spouštět velké nejzásadnější aplikace v produkčním prostředí.

Ke spuštění [kontejnery Windows](/virtualization/windowscontainers/about/), existují dva typy modulů runtime:

-   **Kontejner Windows Server** tento modul runtime poskytuje izolace aplikací prostřednictvím technologie izolace procesu a obor názvů. Kontejner Windows serveru sdílí jádro s hostitelem kontejneru a všechny kontejnery, které běží na hostiteli.

-   **Technologie Hyper-V kontejneru** to rozšiřuje možnosti izolace poskytovaná kontejnery Windows serveru spuštěním jednotlivých kontejnerů ve vysoce optimalizovanému virtuálního počítače. V této konfiguraci nesdílí jádro hostitele kontejneru s kontejnery Hyper-V, poskytuje lepší izolace.

Image pro tyto kontejnery jsou vytvořeny stejným způsobem a fungovat stejně. Rozdíl je v jak se vytvoří kontejner z image – spouštění kontejneru Hyper-V vyžaduje speciálním parametrem. Podrobnosti najdete v tématu [Hyper-V Containers](/virtualization/windowscontainers/about/).

## <a name="comparing-docker-containers-with-vms"></a>Porovnání kontejnerů Dockeru pomocí virtuálních počítačů

Obrázek 1 – 3 ukazuje porovnání mezi virtuálními počítači a Docker kontejnery.

Vzhledem k tomu, že kontejnery vyžadují mnohem méně prostředků (například nemusí plném operačním systému), je snadné je nasazení a rychlé spuštění. Díky tomu budete moct mít vyšší hustota, což znamená, že můžete spustit další služby na stejné jednotce hardwaru a snižují náklady.

Jako vedlejší účinek spuštěných na stejném jádra dosáhnout izolace je menší než virtuální počítače.

Hlavním cílem obrázku, který je, že je prostředí (závislosti) stejný různých nasazeních. To znamená, že můžete ladění na vašem počítači a potom ji nasadíte do jiného počítače pomocí stejné prostředí zaručeno, že.

Image kontejneru je způsob, jak zabalit aplikace nebo služby a ji nasadit spolehlivé a reprodukovatelné způsobem. V tomto ohledu Docker není pouze technologie, je také filozofií a proces.

Při použití Dockeru, Řekněme, že vývojáři nebudou slyšet, "to funguje na mém počítači, případně proč bezpečná není v produkčním prostředí?" Můžete jednoduše slibují, "Se spustí v Dockeru," protože zabalené aplikace Dockeru můžete spustit na všech podporovaných prostředí Docker, a tok se spustí tak, jak bylo zamýšleno na všech cílů nasazení (vývoj, dotazů a odpovědí, Fázování importu, výroby, atd.).

![](./media/image3.png)

Obrázek 1 – 3: Porovnání tradičních virtuálních počítačů pro kontejnery Dockeru

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[další](docker-terminology.md)