---
title: Co je Docker?
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Co je Docker?
ms.date: 08/31/2018
ms.openlocfilehash: a53845d3bbcf24f3eaeb98b9e08b6f35a023c30e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337710"
---
# <a name="what-is-docker"></a>Co je Docker?

[Docker](https://www.docker.com/) je [Open source projekt](https://github.com/docker/docker) pro automatizaci nasazení aplikací jako přenosných a vlastních kontejnerů, které mohou běžet v cloudu nebo místně. Docker je také [Společnost](https://www.docker.com/) , která propaguje a vyvíjí tuto technologii a pracuje ve spolupráci s dodavateli cloudů, Linux a Windows, včetně Microsoftu.

![Diagram znázorňující, že mohou být spuštěny kontejnery Docker na místě.](./media/docker-defined/docker-containers-run-anywhere.png)

**Obrázek 2-2**. Docker nasadí kontejnery ve všech vrstvách hybridního cloudu.

Kontejnery Docker můžou běžet kdekoli, místně v datacentru zákazníka, v externím poskytovateli služeb nebo v cloudu v Azure. Kontejnery imagí Docker mohou běžet nativně v systémech Linux a Windows. Image Windows ale můžou běžet jenom na hostitelích s Windows a image Linux můžou běžet na hostitelích Linux a na hostitelích se systémem Windows (s využitím virtuálního počítače Hyper-V Linux), kde hostitel znamená Server nebo virtuální počítač.

Vývojáři můžou používat vývojová prostředí v systému Windows, Linux nebo macOS. Ve vývojovém počítači Vývojář spustí hostitele Docker, ve kterém jsou nasazené image Docker, včetně aplikace a jejích závislostí. Vývojáři, kteří pracují se systémem Linux nebo na macOS, používají hostitele Docker, který je založený na systému Linux, a mohou vytvářet bitové kopie pouze pro kontejnery Linux. (Vývojáři pracující na macOS můžou upravovat kód nebo spouštět Docker CLI z macOS, ale v době psaní tohoto zápisu se kontejnery nespouštějí přímo na macOS.) Vývojáři, kteří pracují v systému Windows, mohou vytvářet bitové kopie pro kontejnery systému Linux nebo Windows.

Pro hostování kontejnerů ve vývojových prostředích a poskytování dalších vývojářských nástrojů nabízejí Docker dodávané [komunity Docker Edition (CE)](https://www.docker.com/community-edition) pro Windows nebo pro MacOS. Tyto produkty pro hostování kontejnerů nainstalují potřebný virtuální počítač (hostitel Docker). Docker také zpřístupňuje [verzi Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition), která je navržená pro podnikový vývoj a je používána týmy IT, které vytvářejí, dodávají a spouštějí rozsáhlé podnikové aplikace v produkčním prostředí.

Pro spuštění [kontejnerů systému Windows](/virtualization/windowscontainers/about/)existují dva typy modulů runtime:

- Kontejnery Windows serveru poskytují izolaci aplikací prostřednictvím technologie izolace procesů a oboru názvů. Kontejner Windows serveru sdílí jádro s hostitelem kontejneru a se všemi kontejnery běžícími na hostiteli.

- Kontejnery Hyper-V rozšiřují izolaci poskytované kontejnery Windows serveru spuštěním každého kontejneru ve vysoce optimalizovaném virtuálním počítači. V této konfiguraci není jádro hostitele kontejneru sdíleno s kontejnery Hyper-V a zajišťuje lepší izolaci.

Obrázky pro tyto kontejnery jsou vytvářeny stejným způsobem a fungují stejně. Rozdíl spočívá v tom, jak je kontejner vytvořen z image, na které běží kontejner technologie Hyper-V, vyžaduje další parametr. Podrobnosti najdete v tématu [kontejnery Hyper-V](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/hyperv-container).

## <a name="comparing-docker-containers-with-virtual-machines"></a>Porovnání kontejnerů Docker s virtuálními počítači

Obrázek 2-3 ukazuje porovnání mezi virtuálními počítači a kontejnery Docker.

| Virtual Machines | Kontejnery Docker |
| -----------------| ------------------|
|![Diagram znázorňující hardwarový nebo softwarový zásobník tradičního virtuálního počítače](./media/docker-defined/virtual-machine-hardware-software.png)|![Diagram znázorňující hardware/softwarový zásobník kontejnerů Docker.](./media/docker-defined/docker-container-hardware-software.png)|
|Virtuální počítače zahrnují aplikaci, požadované knihovny, binární soubory a úplný hostovaný operační systém. Úplná virtualizace vyžaduje více prostředků než containering. | Kontejnery zahrnují aplikaci a všechny její závislosti. Sdílí ale jádro operačního systému s jinými kontejnery spuštěnými jako izolované procesy v prostoru uživatele v hostitelském operačním systému. (Kromě kontejnerů technologie Hyper-V, kde se každý kontejner spouští ve speciálním virtuálním počítači na kontejner.) |

**Obrázek 2-3**. Porovnání tradičních virtuálních počítačů s kontejnery Docker

Pro virtuální počítače jsou na hostitelském serveru tři základní vrstvy, od dolní části: infrastruktura, hostitelský operační systém a hypervisor a na všech virtuálních počítačích, které mají vlastní operační systém a všechny potřebné knihovny. V případě Docker má hostitelský server jenom infrastrukturu a operační systém a nad ním kontejnerový modul, který udržuje kontejner izolovaný, ale sdílí základní služby operačního systému.

Vzhledem k tomu, že kontejnery vyžadují mnohem méně prostředků (například nepotřebují úplný operační systém), je snadné je snadno nasadit a začít rychle. To vám umožní mít vyšší hustotu, což znamená, že můžete spouštět další služby na stejné hardwarové jednotce a snížit tak náklady.

Jako vedlejší účinky spuštění na stejném jádru získáte menší izolaci než virtuální počítače.

Hlavním cílem obrázku je, že je prostředí (závislosti) stejné v různých nasazeních. To znamená, že ho můžete ladit na svém počítači a pak ho nasadit na jiný počítač se zaručeným prostředím.

Image kontejneru je způsob, jak zabalit aplikaci nebo službu a nasadit ji spolehlivým a rereprodukovatelným způsobem. Je možné, že Docker není jenom technologie, ale také filozofie a proces.

Při použití Docker nebudete vývojářům rozumět, "funguje na mém počítači, proč není v produkčním prostředí?" Můžou jednoduše říci, "běží v Docker", protože zabalená aplikace Docker je možné spustit v jakémkoli podporovaném prostředí Docker a spustí způsob, jakým byl zamýšlený pro všechny cíle nasazení (například vývoj, QA, fázování a produkce).

## <a name="a-simple-analogy"></a>Jednoduchá analogie

Možná jednoduchá analogie může přispět k získání klíčového konceptu Docker.

Pojďme se teď vrátit k 1950s. Neexistovaly žádné textové procesory a fotokopírky byly použity všude (druh).

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
>[Předchozí](index.md)
>[Další](docker-terminology.md)
