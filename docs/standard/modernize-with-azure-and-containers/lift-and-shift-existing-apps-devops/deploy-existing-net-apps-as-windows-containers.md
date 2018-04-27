---
title: Nasadit existující aplikace .NET jako kontejnery Windows
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Nasadit existující aplikace .NET jako kontejnery Windows
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6c70e30c10674c086e6ad880b97151ae1918ed87
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="deploy-existing-net-apps-as-windows-containers"></a>Nasadit existující aplikace .NET jako kontejnery Windows

Nasazení, které jsou založeny na kontejnery Windows se dají použít pro optimalizovaných Cloudů aplikací, nativní cloudu a DevOps připravené pro cloudové aplikace.

Je pomocí Windows kontejnery pro aktivní v této příručce i v následujících částech *DevOps Cloud-Ready* aplikace, když navýšení a posunutí existující aplikace .NET.

## <a name="what-are-containers-linux-or-windows"></a>Co jsou kontejnery? (Linux nebo Windows)

Kontejnery představují způsob, jak zabalit až do vlastní izolované balíčku aplikace. V jeho kontejneru aplikace nemá vliv aplikace a procesy, které existují mimo kontejneru. Všechno, co aplikace, závisí na spuštění úspěšně jak proces je uvnitř kontejneru. Kdekoli může přesunout kontejneru, požadavky na aplikace bude vždy splnit, z hlediska přímé závislosti, protože je instalován s vše, co je nutné ho spustit (závislosti knihovny, moduly runtime a tak dále).

Hlavní vlastnosti kontejner je, že umožňuje prostředí stejné v různých nasazeních protože kontejneru samotné se dodává s všechny závislosti, které potřebuje. To znamená, že můžete ladění aplikace na počítači a nasadíte ho do jiného počítače s prostředím stejné zaručit.

Kontejner je instance bitovou kopii kontejneru. Bitovou kopii kontejneru je způsob, jak balíčku aplikace nebo služby (např. snímek) a nasadíte ho spolehlivé a reprodukovatelné způsobem. Řekněte, aby Docker není že pouze technologií it je také filozofii a proces.

Kontejnery každý den jsou častější, budou se stávají napříč celým průmyslem "jednotka nasazení."

## <a name="benefits-of-containers-docker-engine-on-linux-or-windows"></a>Výhody kontejnery (Docker stroj na systému Linux nebo Windows)

Sestavení aplikace pomocí kontejnery, které také může být definován jako lightweight stavební bloky nabízí významné zvýšení v flexibility pro vytváření, přesouvání a spuštění jakékoli aplikace, pro všechny infrastruktury.

S kontejnery které můžete vzít žádné aplikace z vývojového do produkčního prostředí s malými či žádnými změnami kódu díky integrace Dockeru napříč vývojové nástroje společnosti Microsoft, operačních systémů a cloud.

Když nasadíte prostý virtuální počítače, pravděpodobně už máte metodu zavedené pro nasazení aplikací ASP.NET do virtuálních počítačů. Je pravděpodobné, ale způsob zahrnuje více Ruční postup nebo komplexní automatizované procesy pomocí nástroje nasazení, jako je Puppet nebo podobného nástroje. Možná budete muset provádět úlohy, jako úprava položky konfigurace, kopírování obsahu aplikace mezi servery a spouštění programů interaktivní instalace na základě v nastavení .msi, za nímž následuje testování. Všechny tyto kroky v nasazení přidat čas a rizika pro nasazení. Zobrazí se selhání vždy, když není k dispozici v cílovém prostředí závislost.

V kontejnerech Windows je plně automatizovat proces vytváření balíčků aplikací. Kontejnery Windows je založena na Docker platforma, která nabízí funkce Automatické aktualizace a odvolání pro nasazení kontejnerů. Hlavní zlepšení, které můžete získat z pomocí modulu Docker je, že vytvořit Image, které jsou jako snímky vaší aplikace, se všemi jeho závislostmi. Bitové kopie jsou imagí Dockeru (kontejner bitové kopie systému Windows, v tomto případě). Bitové kopie spouštět aplikace ASP.NET v kontejnerech, aniž by bylo nutné zpět ke zdrojovému kódu. Snímek kontejneru se změní na jednotku nasazení.

Velký počet organizace jsou containerizing stávající monolitický aplikace z následujících důvodů:

-   **Verze flexibility prostřednictvím vylepšené nasazení**. Kontejnery nabízejí konzistentní nasazení smlouva mezi vývoj a provoz. Pokud použijete kontejnery, nebude uslyšíte vývojáři Řekněme, "Ho pracuje na můj počítač, proč ne v produkčním prostředí?" Můžete jednoduše říká, "Běží jako kontejner, takže se spustí v produkčním prostředí." Zabalené aplikace, se všemi jeho závislostmi, mohou být provedeny v jakémkoli podporovaných prostředí, na základě kontejneru. Způsob, jakým se má spouštět ve všech cílů nasazení (vývoj, kontrolu kvality, pracovní produkční), bude fungovat. Kontejnery eliminovat většina frictions, když se přesouvají z jedné fáze na další, což výrazně zvyšuje nasazení, a můžete zaslat rychlejší.

-   **Snížení nákladů**. Kontejnery vést k nižším nákladům, buď konsolidace a odebrání stávající hardware nebo z spouštění aplikací na vyšší hustotu na jednotku hardwaru.

-   **Přenositelnost**. Kontejnery jsou modulární a přenosné. Kontejnery docker jsou podporovány na všech serverových operačních systémů (Linux a Windows), v jakékoli hlavní veřejného cloudu (Microsoft Azure, Amazon AWS, Google, IBM) a v místní a privátní nebo hybridní Cloudová prostředí.

-   **Ovládací prvek**. Kontejnery nabízejí flexibilní a zabezpečení prostředí, které řídí na úrovni kontejneru. Kontejner můžete zabezpečené, izolované a i omezena nastavení omezení zásady provádění na kontejneru. Podle popisu v části o Windows kontejnery kontejnery systému Windows Server 2016 a Hyper-V nabízí možnosti podpory dalších enterprise.

Významná vylepšení v flexibility, přenositelnost a řízení se nakonec vést ke snížení nákladů při použití kontejnery pro vývoj a udržovat aplikace.

## <a name="what-is-docker"></a>Co je Docker?

[Docker](https://www.docker.com/) je [open source projektu](https://github.com/docker/docker) který automatizuje nasazení aplikací jako přenosné, soběstačný kontejnery, které můžou běžet v cloudu nebo místně. Je také docker [společnosti](https://www.docker.com/) zvýší úroveň a zpracovaní tuto technologii. Společnost funguje ve spolupráci s cloudu, Linux a Windows dodavateli, včetně Microsoft.

![](./media/image6.png)

> **Obrázek 4 až 6.** Docker nasadí kontejnery na všechny vrstvy hybridního cloudu

Někomu obeznámeni s virtuálními počítači, kontejnery, může vypadat jako pozoruhodně podobný. Kontejner běží operační systém, systém souborů a přístupná přes síť, stejně jako fyzický nebo virtuální počítač systému. Však technologie a koncepty za kontejnery se významně liší od virtuálních počítačů. Z vývojáře hlediska musí být kontejner považované více jako jeden proces. Ve skutečnosti kontejner obsahuje jeden vstupní bod pro jeden proces.

Kontejnery docker (pro jednoduchost, *kontejnery*) můžete spustit nativně na Linuxu a Windows. Když spustíte regulární kontejnery, kontejnery Windows můžete spustit pouze na hostitelích systému Windows (hostitelský server nebo virtuální počítač) a kontejnery Linux lze spustit pouze na hostitelích systému Linux. Však v posledních verzích systému Windows Server a Hyper-V kontejnery kontejner Linux můžete spustit také nativně na Windows Server pomocí izolace technologie Hyper-V, která je aktuálně k dispozici pouze v systému Windows Server kontejnery.

Smíšená prostředí, které mají kontejnery Linux a Windows v blízké budoucnosti bude možné a i běžné.

## <a name="benefits-of-windows-containers-for-your-existing-net-applications"></a>Výhody Windows kontejnery pro existující aplikace .NET

Výhody použití Windows kontejnery jsou zásadně stejné výhody, které můžete získat z kontejnerů obecně. Použití kontejnerů Windows je výrazně zvýšení flexibility, přenositelnost a řízení.

Když mluvíme o existující aplikace .NET, jsme nejčastěji znamená tradiční aplikace, které byly vytvořeny pomocí rozhraní .NET Framework. Například může být tradiční webové aplikace ASP.NET-nemáte používají .NET Core, který je novější a spouští různé platformy v systému MacOS, Linux a Windows.

Hlavní závislostí v rozhraní .NET Framework je systém Windows. Je také sekundární závislosti, jako je služba IIS a System.Web v tradiční ASP.NET.

Aplikace rozhraní .NET Framework musí spustit v systému Windows, období. Pokud chcete containerize existujících aplikací rozhraní .NET Framework, a proto nemůžete nebo nechcete investovat do migrace .NET Core ("Pokud funguje správně, nemusíte migrovat"), jedinou možností, které máte pro kontejnery je použití Windows kontejnerů.

Tím, že jeden z největších výhod kontejnery Windows je, že tyto funkce poskytují způsob, jak modernizovat existujících aplikací rozhraní .NET Framework, které běží na systému Windows prostřednictvím rozdělení do kontejnerů. Nakonec kontejnery Windows získá výhody, které hledáte, pomocí kontejnery flexibility, přenositelnost a lepší řízení.

## <a name="choose-an-os-to-target-with-net-based-containers"></a>Vyberte operační systém k cíli s. Na základě NET kontejnery

S ohledem na různorodost operační systémy, které jsou podporovány nástrojem Docker a také rozdíly mezi rozhraní .NET Framework a .NET Core, by měl cílové konkrétní operační systém a konkrétní verze založené na rozhraní framework, který používáte.

Pro systém Windows můžete použít Windows Server Core nebo Nano Server systému Windows. Tyto verze systému Windows poskytují různé charakteristiky (jako jsou například služby IIS a vlastním hostováním webového serveru jako Kestrel), které mohou být potřebné aplikace rozhraní .NET Framework nebo .NET Core.

Pro systémy Linux více distribucích jsou dostupné a podporované v oficiální imagí Dockeru .NET (například Debian).

Obrázek 4-7 znázorňuje verze operačního systému, které můžete vybrat, v závislosti na verzi aplikace rozhraní .NET Framework.

![](./media/image7.png)

> **Obrázek 4-7.** Operační systémy k cíli na základě verze rozhraní .NET Framework

Ve scénářích migrace pro stávající nebo starší verze aplikace, které jsou založené na rozhraní .NET Framework – aplikace hlavní závislosti jsou v systémech Windows a služby IIS. Jedinou možností je použití Docker Image založené na Windows Server Core a rozhraní .NET Framework.

Když přidáte název bitové kopie do souboru soubor Docker, můžete vybrat verzi operačního systému a pomocí značky, jako v následujících příkladech založené na rozhraní .NET Framework kontejneru bitových kopií systému Windows:

> | **Značka** | **Systém a verze** |
> |---|---|
> | **microsoft/dotnet-framework:4.x-windowsservercore** | Rozhraní .NET framework 4.x na jádru serveru Windows |
> | **microsoft/aspnet:4.x-windowsservercore** | Rozhraní .NET framework 4.x pomocí dalších úprav ASP.NET na jádru serveru Windows |

Pro .NET Core (napříč platformami operačních systémů Linux a Windows) značek bude vypadat takto:

> | **Značka** | **Systém a verze**
> |---|---|
> | **microsoft/dotnet:2.0.0-runtime** | Rozhraní .NET 2.0 core runtime jen v systému Linux |
> | **microsoft/dotnet:2.0.0-runtime-nanoserver** | Rozhraní .NET 2.0 core runtime jen v systému Windows Nano Server |

### <a name="multi-arch-images"></a>Více architektury bitové kopie

Počínaje mid 2017, můžete taky použít novou funkci v nástroji Docker názvem [více architektura](https://github.com/moby/moby/issues/15866) bitové kopie. Imagí Dockeru .NET core pomocí více architektury značek. Váš soubor Docker souborů již nadále potřeba definovat operačního systému, který cílení. Více architektury funkce umožňuje jedinou značku pro použití na celém konfigurací s více počítači. Například s více architektura, můžete použít jeden společné značky: **microsoft/dotnet:2.0.0-runtime**. Pokud jste pro vyžádání obsahu této značky z kontejneru prostředí Linux, získáte bitovou kopii na základě Debian. Pokud jste pro vyžádání obsahu této značky z kontejneru prostředí systému Windows, získáte bitovou kopii na základě Nano Server.

Pro rozhraní .NET Framework bitové kopie protože tradiční rozhraní .NET Framework podporuje pouze systém Windows, nelze použít funkci více architektury.

## <a name="windows-container-types"></a>Typy kontejneru systému Windows

Jako kontejnery Linux Windows Server kontejnery jsou spravovány pomocí modulu Docker. Na rozdíl od kontejnery Linux Windows kontejnery zahrnují dva typy jiný kontejner nebo spuštěním časy Windows Server kontejnery a izolaci technologie Hyper-V.

**Windows Server kontejnery**: poskytuje izolace aplikací prostřednictvím technologie izolace, proces a obor názvů. Kontejner systému Windows Server sdílí jádro s hostitelem kontejneru a všechny kontejnery, které běží na hostiteli. Tyto kontejnery neposkytují hranici k tomuto účelu zabezpečení a neměli použít k izolování nedůvěryhodnými. Z důvodu místa sdílené jádra tyto kontejnery vyžadují stejnou verzi jádra a konfigurace.

**Technologie Hyper-V izolaci**: rozšíří na izolaci poskytované Windows Server kontejnery spuštěním každý kontejner na vysoce optimalizovaného virtuálního počítače. V této konfiguraci není jádra hostitele kontejneru sdílet s další kontejnery na stejném hostiteli. Tyto kontejnery jsou navrženy pro nepřátelských víceklientské hostování s stejné záruky zabezpečení virtuálního počítače. Protože tyto kontejnery Nesdílejte jádra s hostitele nebo jiných kontejnerů na hostiteli, mohou spouštět jádra s různými verzemi a konfigurace (s podporovanou verzí). Například všechny kontejnery Windows ve Windows 10 pomocí technologie Hyper-V izolaci využívat verze jádra systému Windows Server a konfigurace.

Kontejner systémem Windows s nebo bez izolace technologie Hyper-V je spuštění rozhodnutí. Můžete rozhodnout původně vytvořit kontejner s izolací technologie Hyper-V a v době běhu, vyberte ji spustit jako kontejner systému Windows Server.

### <a name="additional-resources"></a>Další zdroje

-   **Dokumentaci k Windows kontejnery**

    [https://docs.microsoft.com/virtualization/windowscontainers/](https://docs.microsoft.com/virtualization/windowscontainers/)

-   **Základy Windows kontejnery**

    [https://docs.microsoft.com/virtualization/windowscontainers/about/](https://docs.microsoft.com/virtualization/windowscontainers/about/)

-   **Infografice: Společnost Microsoft a kontejnery**

    [https://info.microsoft.com/rs/157-GQE-382/images/Container%20infographic%201.4.17.pdf](https://info.microsoft.com/rs/157-GQE-382/images/Container%20infographic%201.4.17.pdf)

>[!div class="step-by-step"]
[Předchozí](how-to-deploy-existing-net-apps-to-azure-app-service.md)
[další](when-not-to-deploy-to-windows-containers.md)
