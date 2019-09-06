---
title: Co je Docker?
description: Podrobnější informace najdete v tématu o tom, jak vám to může porozumět.
ms.date: 02/15/2019
ms.openlocfilehash: 7747c4985af27be0a073fad2f22622f697f4ce27
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295610"
---
# <a name="what-is-docker"></a>Co je Docker?

[Docker](https://www.docker.com/) je [Open source projekt](https://github.com/docker/docker) pro automatizaci nasazení aplikací jako přenosných a vlastních kontejnerů, které mohou běžet v cloudu nebo místně. Docker je také [Společnost](https://www.docker.com/) , která propaguje a vyvíjí tuto technologii a pracuje ve spolupráci s dodavateli cloudů, Linux a Windows, včetně Microsoftu.

![Kontejnery Docker můžou běžet kdekoli, místně v datacentru zákazníka, v externím poskytovateli služeb nebo v cloudu v Azure.](./media/image2.png)

**Obrázek 1-2**. Docker nasazuje kontejnery ve všech vrstvách hybridního cloudu.

Kontejnery imagí Docker mohou běžet nativně v systémech Linux a Windows. Image Windows ale můžou běžet jenom na hostitelích s Windows a image Linux můžou běžet na hostitelích Linux a na hostitelích se systémem Windows (s využitím virtuálního počítače Hyper-V Linux), kde hostitel znamená Server nebo virtuální počítač.

Vývojáři můžou používat vývojová prostředí v systému Windows, Linux nebo macOS. Ve vývojovém počítači Vývojář spustí hostitele Docker, ve kterém jsou nasazené image Docker, včetně aplikace a jejích závislostí. Vývojáři, kteří pracují se systémem Linux nebo na Macu, používají hostitele Docker se systémem Linux a mohou vytvářet pouze image pro kontejnery Linux. (Vývojáři pracující na Macu můžou upravovat kód nebo spouštět rozhraní příkazového řádku Docker (CLI) z macOS, ale v tomto zápisu se kontejnery nespouštějí přímo v macOS.) Vývojáři, kteří pracují v systému Windows, mohou vytvářet bitové kopie pro kontejnery systému Linux nebo Windows.

Pro hostování kontejnerů ve vývojových prostředích a poskytování dalších vývojářských nástrojů nabízejí Docker dodávané [komunity Docker Edition (CE)](https://www.docker.com/community-edition) pro Windows nebo pro MacOS. Tyto produkty pro hostování kontejnerů nainstalují potřebný virtuální počítač (hostitel Docker). Docker také zpřístupňuje [verzi Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition), která je navržená pro podnikový vývoj a je používána týmy IT, které vytvářejí, dodávají a spouštějí rozsáhlé podnikové aplikace v produkčním prostředí.

Pro spuštění [kontejnerů systému Windows](/virtualization/windowscontainers/about/)existují dva typy modulů runtime:

- **Kontejnery Windows serveru** poskytují izolaci aplikací prostřednictvím technologie izolace procesů a oboru názvů. Kontejner Windows serveru sdílí jádro s hostitelem kontejneru a se všemi kontejnery běžícími na hostiteli.

- **Kontejnery Hyper-V** rozšiřují izolaci poskytované kontejnery Windows serveru spuštěním každého kontejneru ve vysoce optimalizovaném virtuálním počítači. V této konfiguraci není jádro hostitele kontejneru sdíleno s kontejnery Hyper-V a zajišťuje lepší izolaci.

Obrázky pro tyto kontejnery jsou vytvořeny a fungují stejným způsobem. Rozdíl je v tom, jak je kontejner vytvořen z image – spuštění kontejneru technologie Hyper-V vyžaduje další parametr. Podrobnosti najdete v tématu [kontejnery Hyper-V](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/hyperv-container).

## <a name="comparing-docker-containers-with-virtual-machines"></a>Porovnání kontejnerů Docker s virtuálními počítači

Obrázek 1-3 ukazuje porovnání mezi virtuálními počítači a kontejnery Docker.

![Pro virtuální počítače jsou na hostitelském serveru tři základní vrstvy, od dolní části: infrastruktura, hostitelský operační systém a hypervisor a na všech virtuálních počítačích, které mají vlastní operační systém a všechny potřebné knihovny. Na druhé straně má hostitelský server pouze infrastrukturu a operační systém a nad ním modul kontejnerů, který udržuje kontejner izolovaný, ale sdílí základní služby operačního systému.](./media/image3.png)

**Obrázek 1-3**. Porovnání tradičních virtuálních počítačů s kontejnery Docker

Vzhledem k tomu, že kontejnery vyžadují mnohem méně prostředků (například nepotřebují úplný operační systém), je snadné je snadno nasadit a začít rychle. To vám umožní mít vyšší hustotu, což znamená, že můžete spouštět další služby na stejné hardwarové jednotce a snížit tak náklady.

Jako vedlejší účinky spuštění na stejném jádru získáte menší izolaci než virtuální počítače.

Hlavním cílem obrázku je zajistit stejné prostředí (závislosti) napříč různými nasazeními. To znamená, že ho můžete ladit na svém počítači a pak ho nasadit na jiný počítač, což je stejné jako zaručené prostředí.

Image kontejneru je způsob, jak zabalit aplikaci nebo službu a nasadit ji spolehlivým a rereprodukovatelným způsobem. Je možné, že Docker není jenom technologie, ale také filozofie a proces.

Při použití Docker nebudete vývojářům rozumět, "funguje na mém počítači, proč není v produkčním prostředí?" Můžou jen vyslovit "běží v Docker", protože zabalená aplikace Docker je možné spustit v jakémkoli podporovaném prostředí Docker a spustí způsob, jakým byl zamýšlený pro všechny cíle nasazení (například vývoj, QA, fázování a produkce).

## <a name="a-simple-analogy"></a>Jednoduchá analogie

Možná jednoduchá analogie může přispět k získání klíčového konceptu Docker.

Pojďme se teď vrátit k 1950s. Neexistovaly žádné textové procesory a fotokopírky byly použity všude (včetně druhu).

Představte si, že zodpovídáte za rychlé vystavování dávek dopisů, aby je bylo možné poslat zákazníkům, a to pomocí reálného dokumentu a obálek, aby se fyzicky doručily na adresu každého zákazníka (pak se nepoužil e-mail).

V určitém okamžiku si myslíte, že písmena jsou pouze sestavou velké sady odstavců, které jsou vydány a uspořádány podle potřeby podle účelu písmen, takže budete mít k dispozici systém pro rychlé vydávání písmen, který očekává, že získá Hefty.

Systém je jednoduchý:

1. Začnete s balíčkem průhledných listů, které obsahují jeden odstavec.

2. Chcete-li vydat sadu písmen, vybíráte listy s požadovanými odstavci a pak je zaznamenáte a zařadíte, aby vypadaly a bylo možné je přečíst.

3. Nakonec umístíte sadu do kopírky a stisknutím klávesy Start vytvoříte tolik písmen podle potřeby.

Proto se zjednodušuje, což je základní nápad Docker.

V Docker je každá vrstva výslednou sadou změn, které se po spuštění příkazu stanou systémem souborů, jako je například instalace programu.

Takže když v systému souborů po zkopírování vrstvy kliknete, zobrazí se všechny soubory, včetně vrstvy při instalaci programu.

Obrázek si můžete představit jako pomocný pevný disk jen pro čtení, který je připravený k instalaci v počítači, kde je již nainstalován operační systém.

Podobně můžete představit kontejner jako počítač s nainstalovaným pevným diskem image. Kontejner, stejně jako počítač, lze zapnout nebo vypnout.

>[!div class="step-by-step"]
>[Předchozí](index.md)Další
>[](docker-terminology.md)
