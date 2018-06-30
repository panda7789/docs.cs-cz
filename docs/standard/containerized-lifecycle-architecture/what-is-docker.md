---
title: Co je Docker?
description: Kontejnerizované Docker životního cyklu aplikací s Microsoft platforma a nástroje
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.openlocfilehash: 2dfff13f00d4ea0e57161c21d7773eead41c28ee
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105382"
---
# <a name="what-is-docker"></a>Co je Docker?

[Docker](https://www.docker.com/) je [open source projektu](https://github.com/docker/docker) pro automatizaci nasazení aplikací jako přenosné, soběstačný kontejnery, které můžou běžet v cloudu nebo na místní (viz obrázek 1 – 2). Je také docker [společnosti](https://www.docker.com/) zvýší úroveň a sama vyvinula tuto technologii, práce ve spolupráci s cloudu, Linux a Windows dodavateli, včetně Microsoft.

![](./media/image2.png)

Obrázek 1 – 2: Docker nasadí kontejnery na všechny vrstvy hybridního cloudu

Kontejnery docker bitové kopie můžete spustit nativně na Linuxu a Windows. Ale bitových kopií systému Windows lze spustit pouze na hostitelích systému Windows a Linux Image můžete spustit pouze na hostitelích systému Linux, což znamená hostitelský server nebo na virtuální počítač.

Vývojáři mohou použít vývojové prostředí v systému Windows, Linux nebo systému macOS. Vývojář na vývojovém počítači, spouští Docker hostitele, na které Docker jsou nasazené bitové kopie, včetně aplikace a jeho závislosti. Vývojáři, kteří pracují v systému Linux nebo na Mac použijte Docker hostitele, který je založenými na systému Linux, a mohou vytvářet bitové kopie pouze pro kontejnery Linux. (Vývojáře, kteří pracují na Mac můžete upravit kód nebo spustit rozhraní příkazového řádku Dockeru \[rozhraní příkazového řádku\] ze systému macOS, ale době psaní tohoto textu, kontejnery nelze spustit přímo v systému macOS.) Vývojáři, kteří pracují v systému Windows, můžete vytvořit Image pro Linux nebo Windows kontejnery.

Pro hostování kontejnery ve vývojovém prostředí a poskytnout další vývojářské nástroje, dodává Docker [Docker Community Edition (CE)](https://www.docker.com/community-edition) pro systém Windows nebo pro systému macOS. Tyto produkty nainstalujte nezbytné virtuálního počítače (Docker hostitele) k hostování kontejnerů. Docker také zpřístupní [Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition), který je určený pro vývoj enterprise a je používána týmy IT, kteří sestavení, odeslání a spusťte velké důležitými obchodními aplikacemi v produkčním prostředí.

Ke spuštění [Windows kontejnery](https://msdn.microsoft.com/virtualization/windowscontainers/about/about_overview), existují dva typy moduly Runtime:

-   **Windows Server kontejneru** tento modul runtime poskytuje izolace aplikací prostřednictvím technologie izolace, proces a obor názvů. Kontejner Windows serveru sdílí jádro s hostitelem kontejneru a všechny kontejnery spuštěných na hostiteli.

-   **Technologie Hyper-V kontejneru** tím se rozšíří na izolaci poskytované Windows Server kontejnery spuštěním každý kontejner ve vysoce optimalizovaného virtuálního počítače. V této konfiguraci není jádra hostitele kontejneru sdílet s kontejnery technologie Hyper-V, poskytuje lepší izolace.

Pro obrázky těchto kontejnerů, vytvoří se stejným způsobem a stejné funkce. Rozdíl je v tom, jak se kontejner vytvoří z bitové kopie – spuštění kontejner technologie Hyper-V vyžaduje další parametr. Podrobnosti najdete v tématu [kontejnery technologie Hyper-V](https://msdn.microsoft.com/virtualization/windowscontainers/about/about_overview).

## <a name="comparing-docker-containers-with-vms"></a>Porovnání Docker kontejnery s virtuálními počítači

Obrázek 1 – 3 uvádí srovnání mezi virtuálními počítači a Docker kontejnerů.

Protože kontejnery vyžadují mnohem méně prostředků (například nepotřebují úplném operačním systému), jsou snadno nasadit a rychlé spuštění. Díky tomu je možné mít vyšší hustotu, což znamená, že můžete spustit další služby na stejné jednotce hardwaru, čímž se sníží náklady.

Jako vedlejším účinkem spuštěných na stejné jádra můžete izolujte menší než virtuální počítače.

Hlavním cílem bitové kopie je, že umožňuje prostředí (závislosti) stejná napříč různých nasazení. To znamená, že můžete ladění na váš počítač a poté ji nasadit do jiného počítače s prostředím stejné zaručit.

Bitovou kopii kontejneru je způsob, jak balíčku aplikace nebo služby a nasaďte ho spolehlivé a reprodukovatelné způsobem. V tomto ohledu Docker není pouze technologie, je také filozofii a proces.

Při použití Docker, nebude uslyšíte vývojáři Řekněme, "Ho pracuje na můj počítač, proč ne v produkčním prostředí?" Se jednoduše řekněte, "Je spuštěna na Docker," protože zabalené aplikace Docker lze spustit na všech podporovaných Docker prostředí, a způsob, jakým mělo být na všech cílů nasazení (vývoj, kontrolu kvality, pracovní produkční atd.), poběží.

![](./media/image3.png)

Obrázek 1 – 3: porovnání tradiční virtuálních počítačů do kontejnerů Docker


>[!div class="step-by-step"]
[Předchozí](index.md)
[další](docker-terminology.md)
