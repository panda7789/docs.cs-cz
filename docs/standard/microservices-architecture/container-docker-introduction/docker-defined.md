---
title: Co je Docker?
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Co je Docker?
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 36a153ca636adbfe7a335d71cc1baef4e213f4c9
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43534686"
---
# <a name="what-is-docker"></a>Co je Docker?

[Docker](https://www.docker.com/) je [open source projektu](https://github.com/docker/docker) pro automatizaci nasazení aplikací jako přenosných a soběstační kontejnerů, které lze spustit v cloudu nebo místně. Docker je také [společnosti](https://www.docker.com/) , který podporuje a vyvíjí tuto technologii. Docker pracuje ve spolupráci s cloudem, Linux a Windows dodavateli, včetně Microsoft.

![](./media/image2.png)

**Obrázek 2-2**. Dockeru nasadí kontejnery na všech úrovních hybridního cloudu

Image kontejnerů dockeru nativně běžet na systému Linux a Windows. Image Windows spusťte jenom na hostitelích s Windows a Linuxové Image spustit jenom na hostitelích systému Linux. Hostitel je server nebo virtuální počítač.

Můžete vyvíjet na Windows, Linux nebo macOS. Vývojovém počítači běží hostitele Docker, ve kterém se nasazují imagí Dockeru, včetně aplikace a jeho závislosti. V systému Linux nebo macOS pomocí hostitele Dockeru, který je a můžete vytvořit Image jenom pro Linuxové kontejnery Linux. (V systému macOS můžete kód upravovat nebo spusťte rozhraní příkazového řádku Dockeru, ale v době době psaní tohoto textu kontejnery nelze spustit přímo v systému macOS.) Ve Windows můžete vytvořit Image pro kontejnery Windows nebo Linuxem.

Na Windows nebo macOS [Docker Community Edition (CE)](https://www.docker.com/community-edition) hostitelem kontejnery ve vývojovém prostředí a poskytuje další vývojářské nástroje. [Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition) používá týmům IT, kteří vytvářejí, dodávat a spouštět velké důležité podnikové aplikace. Oba tyto produkty nainstalujte nezbytné virtuálního počítače (hostitele Dockeru) pro hostování kontejnerů.

[Kontejnery Windows](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview) fungují s dva druhy prostředí runtime:

-   Kontejnery pro Windows Server poskytuje izolace aplikací prostřednictvím technologie izolace procesu a obor názvů. Kontejner Windows serveru sdílí jádro s hostitelem kontejneru a všechny kontejnery, které běží na hostiteli.

-   Technologie Hyper-V Containers doplňovat izolace poskytovaná kontejnery Windows serveru spuštěním jednotlivých kontejnerů ve vysoce optimalizovanému virtuálního počítače. V této konfiguraci nesdílí jádro hostitele kontejneru s kontejnery Hyper-V, poskytuje lepší izolace. Technologie Hyper-V Containers povolit nedůvěryhodné a *nehostinném prostředí více tenantů* aplikace, které poběží na stejném hostiteli. Technologie Hyper-V Containers mít trochu nižší účinnost časy spuštění a s velkou hustotou než kontejnery pro Windows Server.

Image pro tyto kontejnery jsou vytvořeny a fungovat stejným způsobem. Se liší v tom, jak se kontejner vytvoří. Podrobnosti najdete v tématu [Hyper-V Containers](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview).

## <a name="comparing-docker-containers-with-virtual-machines"></a>Porovnání kontejnery Dockeru s virtuálními počítači

Obrázek 2 – 3 ukazuje porovnání mezi virtuálními počítači a Docker kontejnery.

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Virtuální počítače****kontejnery Dockeru** 
                                                                                                                                                                                        
  ![](./media/image3.png)                                                                                                                                ![](./media/image4.png)
                                                                                                                                                                                        
  Virtuální počítače zahrnují aplikace, požadované knihovny nebo binární soubory a úplné hostovaného operačního systému. Kompletních virtualizačních vyžaduje víc prostředků než kontejnerizace. Kontejnery zahrnují aplikace a všechny její závislosti. Ale kontejnery sdílejí jádro operačního systému pomocí jiných kontejnerů. Kontejnery spustit v hostitelském operačním systému jako izolovaných procesech v prostoru uživatele. S výjimkou kontejnery Hyper-V, kde se spouští každý kontejner v rámci speciální virtuální počítač na kontejner.
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Obrázek 2 – 3**. Porovnání tradičních virtuálních počítačů pro kontejnery Dockeru

Vzhledem k tomu, že kontejnery vyžadují mnohem méně prostředků (například nemusí plném operačním systému), rychle se pusťte do a jde snadno nasadit. Využití prostředků nízké umožňuje vyšší hustotou. Můžete spustit další služby na stejné jednotce hardwaru a snížit náklady.

Spuštěná na stejných výsledků jádra v izolace je menší než virtuální počítače mají.

Hlavním cílem obrázku, který je, že je prostředí (závislosti) stejný různých nasazeních. To znamená, že můžete ladění na vašem počítači a potom ji nasadíte do jiného počítače pomocí stejné prostředí zaručeno, že.

Image kontejneru je způsob, jak zabalit aplikace nebo služby a ji nasadit spolehlivé a reprodukovatelné způsobem. Může Řekněme, že je Docker nejen technologie, ale také filozofií a proces.

Není například docker vývojářům "to funguje na mém počítači, případně proč bezpečná není v produkčním prostředí?" Slibují, "Se spustí v Dockeru". Docker zabalené aplikace je možné provést v libovolné podporované prostředí Docker. Docker zabalené aplikace konzistentně spouštět všechny cíle nasazení (vývoj, dotazů a odpovědí, Fázování a výrobu).

>[!div class="step-by-step"]
[Předchozí](index.md)
[další](docker-terminology.md)
