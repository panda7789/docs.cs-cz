---
title: Co je Docker?
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Co je Docker?
ms.date: 08/31/2018
ms.openlocfilehash: a53845d3bbcf24f3eaeb98b9e08b6f35a023c30e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75337710"
---
# <a name="what-is-docker"></a>Co je Docker?

[Docker](https://www.docker.com/) je [open source projekt](https://github.com/docker/docker) pro automatizaci nasazení aplikací jako přenosných, soběstačných kontejnerů, které lze spustit v cloudu nebo v místním prostředí. Docker je také [společnost,](https://www.docker.com/) která tuto technologii propaguje a vyvíjí a spolupracuje s dodavateli cloudu, Linuxu a Windows, včetně Microsoftu.

![Diagram znázorňující místa, kde mohou být spuštěny kontejnery Dockeru.](./media/docker-defined/docker-containers-run-anywhere.png)

**Obrázek 2-2**. Docker nasazuje kontejnery ve všech vrstvách hybridního cloudu.

Kontejnery Dockeru můžou běžet kdekoli, místně v zákaznickém datovém centru, u externího poskytovatele služeb nebo v cloudu v Azure. Kontejnery image Dockeru můžou běžet nativně v Linuxu a Windows. Bitové kopie systému Windows však mohou běžet pouze na hostitelích systému Windows a bitové kopie Linuxu mohou běžet na hostitelích Linuxu a hostitelích systému Windows (pomocí virtuálního počítače Hyper-V Linux), kde hostitel znamená server nebo virtuální počítač.

Vývojáři můžou používat vývojová prostředí ve Windows, Linuxu nebo macOS. Ve vývojovém počítači vývojář spustí hostitele Dockeru, kde se nasazují ifotky Dockeru, včetně aplikace a jejích závislostí. Vývojáři, kteří pracují na Linuxu nebo macOS, používají hostitele Dockeru, který je založen na Linuxu, a můžou vytvářet obrázky pouze pro linuxové kontejnery. (Vývojáři pracující na macOS můžou upravovat kód nebo spouštět rozhraní příkazového příkazu Dockeru z macOS, ale v době psaní tohoto článku kontejnery neběží přímo v macOS.) Vývojáři, kteří pracují v systému Windows, mohou vytvářet obrázky pro linuxové nebo kontejnery windows.

Aby bylo účelem hostování kontejnerů ve vývojových prostředích a poskytování dalších vývojářských nástrojů, docker dodává [Docker Community Edition (CE)](https://www.docker.com/community-edition) pro Windows nebo macOS. Tyto produkty nainstalují potřebný virtuální hod (hostitele Dockeru) k hostování kontejnerů. Docker také zpřístupňuje [Docker Enterprise Edition (EE),](https://www.docker.com/enterprise-edition)který je určen pro vývoj podniku a používá it týmy, které vytvářejí, doručují a provozují velké důležité podnikové aplikace v produkčním prostředí.

Chcete-li spustit [kontejnery systému Windows](/virtualization/windowscontainers/about/), existují dva typy runtimes:

- Kontejnery windows serveru poskytují izolaci aplikací prostřednictvím technologie izolace procesu a oboru názvů. Kontejner systému Windows Server sdílí jádro s hostitelem kontejneru a se všemi kontejnery spuštěnými na hostiteli.

- Kontejnery Hyper-V se rozšiřují na izolaci poskytovanou kontejnery Windows Server spuštěním každého kontejneru ve vysoce optimalizovaném virtuálním počítači. V této konfiguraci jádro hostitele kontejneru není sdíleno s hyper-v kontejnery, poskytuje lepší izolaci.

Obrázky pro tyto kontejnery jsou vytvořeny stejným způsobem a fungují stejně. Rozdíl je v tom, jak je kontejner vytvořen z bitové kopie se spuštěným kontejnerem Hyper-V, který vyžaduje další parametr. Podrobnosti naleznete v [tématu Hyper-V Containers](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/hyperv-container).

## <a name="comparing-docker-containers-with-virtual-machines"></a>Porovnání kontejnerů Dockeru s virtuálními počítači

Obrázek 2-3 ukazuje porovnání mezi virtuálními a dockerovými kontejnery.

| Virtuální počítače | Kontejnery dockeru |
| -----------------| ------------------|
|![Diagram znázorňující zásobník hardwaru a softwaru tradičního virtuálního počítače.](./media/docker-defined/virtual-machine-hardware-software.png)|![Diagram znázorňující zásobník hardwaru a softwaru pro kontejnery Dockeru.](./media/docker-defined/docker-container-hardware-software.png)|
|Virtuální počítače zahrnují aplikaci, požadované knihovny nebo binární soubory a úplný hostovaný operační systém. Úplná virtualizace vyžaduje více prostředků než kontejnerizace. | Kontejnery obsahují aplikaci a všechny její závislosti. Sdílejí však jádro operačního systému s jinými kontejnery a běží jako izolované procesy v uživatelském prostoru v hostitelském operačním systému. (S výjimkou kontejnerů Hyper-V, kde každý kontejner běží uvnitř speciálního virtuálního počítače na kontejner.) |

**Obrázek 2-3**. Porovnání tradičních virtuálních počítačů s kontejnery Dockeru

Pro virtuální servery existují tři základní vrstvy na hostitelském serveru, zdola nahoru: infrastruktura, hostitelský operační systém a hypervisor a nad tím všem, že každý virtuální počítač má svůj vlastní operační systém a všechny potřebné knihovny. Pro Docker hostitelský server má pouze infrastrukturu a operační systém a navíc modul kontejneru, který udržuje kontejner izolovaný, ale sdílí základní služby operačního systému.

Vzhledem k tomu, že kontejnery vyžadují mnohem méně prostředků (například nepotřebují úplný operační režim), snadno se nasazují a spouštějí se rychle. To vám umožní mít vyšší hustotu, což znamená, že umožňuje spustit více služeb na stejné hardwarové jednotce, čímž se sníží náklady.

Jako vedlejší účinek spuštění na stejném jádru získáte menší izolaci než virtuální počítač.

Hlavním cílem bitové kopie je, že prostředí (závislosti) stejné v různých nasazeních. To znamená, že můžete ladit v počítači a pak ji nasadit do jiného počítače se stejným prostředím zaručena.

Image kontejneru je způsob, jak zabalit aplikaci nebo službu a nasadit ji spolehlivým a reprodukovatelným způsobem. Dalo by se říci, že Docker není jen technologie, ale také filozofie a proces.

Při použití Dockeru neuslyšíte, jak vývojáři říkají: "Funguje to na mém počítači, proč ne ve výrobě?" Mohou jednoduše říci " Běží na Dockeru", protože zabalená aplikace Dockeru může být spuštěna v libovolném podporovaném prostředí Dockeru a běží tak, jak byla určena pro všechny cíle nasazení (například Dev, QA, staging a production).

## <a name="a-simple-analogy"></a>Jednoduchá analogie

Možná, že jednoduchá analogie může pomoci získat pochopení základní koncepce Docker.

Vraťme se na chvíli zpět v čase do padesátých let. Nebyly tam žádné textové procesory a kopírky byly používány všude (druh).

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
