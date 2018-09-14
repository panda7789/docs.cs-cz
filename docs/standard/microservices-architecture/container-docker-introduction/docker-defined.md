---
title: Co je Docker?
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Co je Docker?
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 08/31/2018
ms.openlocfilehash: 342fd8a4da5f05112e2e0ea85f5b78196ca62fdd
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45589414"
---
# <a name="what-is-docker"></a>Co je Docker?

[Docker](https://www.docker.com/) je [open source projektu](https://github.com/docker/docker) pro automatizaci nasazení aplikací jako přenosných a soběstační kontejnerů, které lze spustit v cloudu nebo místně. Docker je také [společnosti](https://www.docker.com/) , který podporuje a tato technologie funguje ve spolupráci s cloudem, Linux a Windows dodavateli, včetně Microsoft vyvíjí.

![Kontejnery dockeru můžete spustit kdekoli, místní datacentra zákazníků do poskytovatele externích služeb nebo v cloudu, v Azure.](./media/image2.png)

**Obrázek 2-2**. Dockeru nasadí kontejnery na všech úrovních hybridního cloudu

Image kontejnerů dockeru můžete nativně běžet na systému Linux a Windows. Ale imagí Windows můžete spustit pouze na hostitelích s Windows a Linuxové Image můžete spouštět na hostitelé s Linuxem a Windows hostitele (pomocí technologie Hyper-V virtuálního počítače s Linuxem, zatím), kde hostitele znamená, že server nebo virtuální počítač.

Vývojáři mohou pomocí vývojových prostředích Windows, Linux nebo macOS. Ve vývojovém počítači vývojář spouští hostitele Docker, ve kterém se nasazují imagí Dockeru, včetně aplikace a jeho závislosti. Vývojáři, kteří pracují v Linuxu nebo na počítači Mac pomocí hostitele Docker, která je založené na Linuxu a bude možné vytvořit Image pouze pro kontejnery Linuxu. (Vývojáře, kteří pracují na počítači Mac můžete upravit kód, nebo ze systému macOS spusťte rozhraní příkazového řádku Dockeru, ale v době době psaní tohoto textu kontejnery nelze spustit přímo v systému macOS.) Vývojáři, kteří pracují ve Windows můžete vytvořit Image pro kontejnery Windows nebo Linuxem.

K hostování kontejnerů ve vývojových prostředích a poskytují další vývojářské nástroje, Docker dodává [Docker Community Edition (CE)](https://www.docker.com/community-edition) pro Windows nebo macOS. Těchto produktů nainstalujte nezbytné virtuálního počítače (hostitele Dockeru) pro hostování kontejnerů. Docker také zpřístupní [Docker Enterprise Edition (EE)](https://www.docker.com/enterprise-edition), která je určená pro vývoj podnikových a používá týmům IT, kteří vytvářejí, dodávat a spouštět velké nejzásadnější aplikace v produkčním prostředí.

Ke spuštění [kontejnery Windows](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview), existují dva typy modulů runtime:

-   Kontejnery pro Windows Server poskytuje izolace aplikací prostřednictvím technologie izolace procesu a obor názvů. Kontejner Windows serveru sdílí jádro s hostitelem kontejneru a všechny kontejnery, které běží na hostiteli.

-   Technologie Hyper-V Containers doplňovat izolace poskytovaná kontejnery Windows serveru spuštěním jednotlivých kontejnerů ve vysoce optimalizovanému virtuálního počítače. V této konfiguraci nesdílí jádro hostitele kontejneru s kontejnery Hyper-V, poskytuje lepší izolace.

Image pro tyto kontejnery se vytvářejí stejným způsobem a fungovat stejně. Rozdíl je v tom, jak se kontejner vytvoří z této image spouštění kontejneru Hyper-V vyžaduje speciálním parametrem. Podrobnosti najdete v tématu [Hyper-V Containers](https://docs.microsoft.com/virtualization/windowscontainers/manage-containers/hyperv-container).

## <a name="comparing-docker-containers-with-virtual-machines"></a>Porovnání kontejnery Dockeru s virtuálními počítači

Obrázek 2 – 3 ukazuje porovnání mezi virtuálními počítači a Docker kontejnery.

<table>
<tbody>
<tr>
<td style="width:50%"><p><strong>Virtuální počítače</strong></p>
<p><img src="media/image3.png" style="width:100%; vertical-align:top;" alt="For VMs, there are three base layers in the host server, from the bottom-up: infrastructure, Host Operating System and a Hypervisor and on top of all that each VM has its own OS and all necessary libraries"/></p>
<p>Virtuální počítače zahrnují aplikace, požadované knihovny nebo binární soubory a úplné hostovaného operačního systému. Kompletních virtualizačních vyžaduje víc prostředků než kontejnerizace.</p></td>
<td style="width:50%"><p><strong>Kontejnery dockeru</strong></p>
<p><img src="media/image4.png" style="width:100%; vertical-align:top;" alt="For Docker, the host server only has the infrastructure and the OS and on top of that, the container engine, that keeps container isolated but sharing the base OS services."/></p>
<p>Kontejnery zahrnují aplikace a všechny její závislosti. Ale sdílejí jádro operačního systému pomocí jiných kontejnerů jako izolovaných procesech v prostoru uživatele a systémem hostitelského operačního systému. (S výjimkou kontejnery Hyper-V, kde se spouští každý kontejner v rámci speciální virtuální počítač na kontejner.)</p></td>
</tr>
</tbody>
</table>

**Obrázek 2 – 3**. Porovnání tradičních virtuálních počítačů pro kontejnery Dockeru

Vzhledem k tomu, že kontejnery vyžadují mnohem méně prostředků (například nemusí plném operačním systému), je snadné je nasazení a rychlé spuštění. To umožňuje mít vyšší hustota, což znamená, že umožňuje spouštět další služby na stejné jednotce hardwaru, a tím snižuje náklady na.

Vedlejším účinkem spuštěných na stejném jádra že získáte izolace je menší než virtuální počítače.

Hlavním cílem obrázku, který je, že je prostředí (závislosti) stejný různých nasazeních. To znamená, že můžete ladění na vašem počítači a potom ji nasadíte do jiného počítače pomocí stejné prostředí zaručeno, že.

Image kontejneru je způsob, jak zabalit aplikace nebo služby a ji nasadit spolehlivé a reprodukovatelné způsobem. Může Řekněme, že je Docker nejen technologie, ale také filozofií a proces.

Při použití Dockeru, Řekněme, že vývojáři nebudou slyšet, "to funguje na mém počítači, případně proč bezpečná není v produkčním prostředí?" Jednoduše můžete říct, "Se spustí v Dockeru", protože zabalené aplikace Dockeru se dá provést na všech podporovaných prostředí Dockeru, a tok se spustí tak, jak bylo zamýšleno na všechny cíle nasazení (vývoj, dotazů a odpovědí, Fázování importu, výroby, atd.).

# <a name="a-simple-analogy"></a>Jednoduché přirovnání

Jednoduché přirovnání možná může pomoct získat pochopit její podstatu základními koncepty Dockeru.

Vraťme se zpět v čase k 50's na chvíli zastavíme. Nebyly žádné textových editorů a kopírkách byly použity kdekoli (druh).

Představte si, že máte za rychle vystavování balíků písmen podle potřeby odeslání zákazníkům, skutečné dokument a obálky, fyzicky doručit na adresu každého zákazníka (neexistovala žádná e-mailu zpět pak).

V určitém okamžiku zjistíte, že písmena jsou právě složení velkou sadu odstavců, které jsou vydány a uspořádané podle potřeby podle účelu písmeno, takže navrhnout systému vydat písmena velmi rychle, očekává se získat hefty vyvolat.

Systém je opravdu jednoduché:

1.  Začněte u balíčku transparentní listy obsahující jeden odstavec

2.  K vydání sady písmena, vyberte listy s odstavců potřebujete a pak zásobníku a přizpůsobit je tak vyhledat a přečíst bez problémů a

3.  A konečně umístíte sada kopírky a stiskněte klávesu start k vytvoření tolik písmena podle potřeby.

Zjednodušení, je základní představu o Dockeru

Každá vrstva v Dockeru, je výslednou sadu změn, ke kterým dochází k systému souborů po spuštění příkazu, například instalaci programu.

Takže když jste "tvářit" jako v systému souborů po byl zkopírován vrstvy, zobrazí všechny soubory zahrnuty vrstvě při instalaci programu.

Si můžete představit bitovou kopii jako pomocné jen pro čtení pevný disk s připravených k instalaci v "počítač" kde je již nainstalován operační systém.

Obdobně, si můžete představit kontejneru jako "počítač" s pevným diskem bitové kopie nainstalovány. Kontejner, stejně jako počítač, můžete s využitím zapnutí nebo vypnutí.

>[!div class="step-by-step"]
[Předchozí](index.md)
[další](docker-terminology.md)
