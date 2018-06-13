---
title: Co je Docker?
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Co je Docker?
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: fadd2611283f0a7dadbf1734fe48f7d1a13096ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33576190"
---
# <a name="what-is-docker"></a>Co je Docker?

[Docker](https://www.docker.com/) je [open source projektu](https://github.com/docker/docker) pro automatizaci nasazení aplikací jako přenosné, soběstačný kontejnery, které můžou běžet v cloudu nebo místně. Je také docker [společnosti](https://www.docker.com/) zvýší úroveň a zpracovaní tuto technologii. Docker funguje ve spolupráci s cloudu, Linux a Windows dodavateli, včetně Microsoft.

![](./media/image2.png)

**Obrázek 2-2**. Docker nasadí kontejnery na všechny vrstvy hybridního cloudu

Kontejnery image docker spustit nativně na Linuxu a Windows. Bitových kopií systému Windows spustit pouze na hostitelích systému Windows a Linux Image spustit pouze na hostitelích systému Linux. Hostitel je server nebo virtuální počítač.

Můžete vyvíjet v systému Windows, Linux nebo systému macOS. Vývojovém počítači spustí hostitelů Docker, kde jsou nasazeny imagí Dockeru, včetně aplikace a jeho závislosti. V systému macOS nebo Linux použijete Docker hostitele, který je Linux a můžete vytvořit Image jenom pro kontejnery Linux. (V systému macOS můžete upravit kód nebo spuštění příkazového řádku Dockeru, ale od době psaní tohoto textu kontejnery nelze spustit přímo v systému macOS.) V systému Windows, můžete vytvořit Image pro Linux nebo Windows kontejnery.

V systému Windows nebo systému macOS [Docker Community Edition (CE)](https://www.docker.com/community-edition) hostuje kontejnery v prostředí pro vývoj a poskytuje další developer tools. [Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition) slouží týmy IT, kteří vytvoření, odeslání a spuštění velké podnikové aplikace. ~ Oba produkty nainstalujte nezbytné virtuálního počítače (Docker hostitele) k hostování kontejnery. ~ 

[Kontejnery Windows](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview) práce s moduly runtime dva typy:

-   Windows Server kontejnery zadejte izolace aplikací prostřednictvím technologie izolace, proces a obor názvů. Kontejner Windows serveru sdílí jádro s hostitelem kontejneru a všechny kontejnery spuštěných na hostiteli.

-   Kontejnery technologie Hyper-V rozbalte na izolaci poskytované Windows Server kontejnery spuštěním každý kontejner ve vysoce optimalizovaného virtuálního počítače. V této konfiguraci není jádra hostitele kontejneru sdílet s kontejnery technologie Hyper-V, poskytuje lepší izolace. Kontejnery technologie Hyper-V povolit nedůvěryhodných a *nepřátelských víceklientské* aplikace, které poběží na stejném hostiteli. Technologie Hyper-V kontejnery mít o něco menší efektivitu v časy spuštění a s velkou hustotou než Windows Server kontejnery.

Pro obrázky těchto kontejnerů jsou vytvářeny a fungovat stejným způsobem. Liší se v tom, jak se kontejner vytvoří. Podrobnosti najdete v tématu [kontejnery technologie Hyper-V](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview).

## <a name="comparing-docker-containers-with-virtual-machines"></a>Porovnání Docker kontejnery s virtuálními počítači

Obrázek 2 – 3 ukazuje porovnání mezi virtuální počítače a Docker kontejnerů.

  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Virtuální počítače****Docker kontejnery** 
                                                                                                                                                                                        
  ![](./media/image3.png)                                                                                                                                ![](./media/image4.png)
                                                                                                                                                                                        
  Virtuální počítače zahrnují aplikace, požadované knihovny nebo binárních souborů a úplné hostovaného operačního systému. Úplné virtualizace vyžaduje více prostředků než rozdělení do kontejnerů. Kontejnery zahrnují aplikace a všechny jeho závislé součásti. Kontejnery však sdílet jádra operačního systému s jiných kontejnerů. Kontejnery spustit jako izolovaných procesech v prostoru uživatele na hostitelský operační systém. S výjimkou kontejnery technologie Hyper-V, kde se spouští každý kontejner uvnitř speciální virtuální počítač na kontejneru.
  ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

**Obrázek 2 – 3**. Porovnání tradiční virtuálních počítačů do kontejnerů Docker

Protože kontejnery vyžadují mnohem méně prostředků (například nepotřebují úplném operačním systému), začít rychle a snadno nasadit. Využití prostředků nízké umožňuje vyšší hustotu. Můžete spustit další služby na stejné jednotce hardwaru a snižovat náklady.

Na stejné výsledky jádra izolovaně menší než virtuální počítače nabízejí spuštěna.

Hlavním cílem bitové kopie je, že umožňuje prostředí (závislosti) stejná napříč různých nasazení. To znamená, že můžete ladění na váš počítač a poté ji nasadit do jiného počítače s prostředím stejné zaručit.

Bitovou kopii kontejneru je způsob, jak balíčku aplikace nebo služby a nasaďte ho spolehlivé a reprodukovatelné způsobem. Může Řekněme, že Docker je nejen technologie, ale také filozofii a proces.

Nemáte vyslovení docker vývojáři "Ho pracuje na můj počítač, proč ne v produkčním prostředí?" Říká se, "Je spuštěna na Docker". Docker zabalené aplikace mohou být provedeny na všech podporovaných Docker prostředí. Docker zabalené aplikace spustit konzistentně na všechny cíle nasazení (vývoj, kontrolu kvality, pracovní produkční).

>[!div class="step-by-step"]
[Předchozí] (index.md) [Další] (docker-terminology.md)
