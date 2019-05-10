---
title: Nasazení existujících aplikací .NET jako kontejnery Windows
description: Modernizace stávajících aplikací .NET pomocí cloudu Azure a Windows kontejnery | Nasazení existujících aplikací .NET jako kontejnery Windows
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/29/2018
ms.openlocfilehash: 0bdab6d8aaaaa9bdddb9e9d55df8bb4850bc2b81
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64614479"
---
# <a name="deploy-existing-net-apps-as-windows-containers"></a>Nasazení existujících aplikací .NET jako kontejnery Windows

Nasazení, které jsou založeny na kontejnery Windows se vztahuje na aplikace optimalizované pro Cloud a aplikací nativních pro Cloud.

Ale v tomto průvodci a zejména v následujících částech, většinou zaměřuje se na použití kontejnerů Windows pro *optimalizovaných Cloudů* aplikací, kde nemusíte úprava architektury aplikace.

## <a name="what-are-containers-linux-or-windows"></a>Co jsou kontejnery? (S Linuxem nebo Windows)

Kontejnery jsou způsob, jak zabalit aplikace do své vlastní izolované balíčku. V jeho kontejneru nemá vliv aplikaci aplikace nebo procesy, které existují mimo svůj kontejner. Všechno, co aplikace závisí na spuštění úspěšně proces je uvnitř kontejneru. Všude, kde může být přesunout kontejneru, aplikace bude vždy být splněny požadavky, z hlediska přímé závislosti, protože je součástí vše, co je nutné ho spustit (závislosti knihovny, moduly runtime a tak dále).

Hlavní charakteristiky kontejner je, že je prostředí stejné různých nasazeních protože samotný kontejner obsahuje všechny potřebné závislé produkty, které potřebuje. Můžete ladit aplikaci na svém počítači a nasadit ho do jiného počítače, s zaručeno, že stejné prostředí.

Kontejner je instance image kontejneru. Image kontejneru je způsob, jak zabalit aplikace nebo služby (např. snímek) a pak ji nasadit spolehlivé a reprodukovatelné způsobem. Může Řekněme, že Docker není že pouze technologií – it společnosti také filozofií a proces.

Kontejnery jsou denně častější, stávají oborové "jednotku nasazení."

## <a name="benefits-of-containers-docker-engine-on-linux-or-windows"></a>Výhody kontejnerů (modul Docker v Linuxu nebo Windows)

Vytváření aplikací pomocí kontejnerů, která může být také podle jako jednoduchý stavební bloky offers výrazné zvýšení flexibility pro vytváření, přesouvání a jakékoli aplikace fungovat v různých žádnou infrastrukturu.

S kontejnery můžete provést všechny aplikace z vývojového do produkčního prostředí s malými či žádnými změnami kódu, díky integraci Docker napříč vývojovými nástroji společnosti Microsoft, operační systémy a cloudu.

Při nasazování do prostého virtuální počítače, pravděpodobně již mít metodu nastavené pro nasazování aplikací technologie ASP.NET k vašim virtuálním počítačům. Je pravděpodobné, ale vaše metoda zahrnuje více vyžadováno provedení ručních kroků nebo komplexní automatizované procesy pomocí nástroje nasazení, jako jsou Puppet, nebo něco podobného. Můžete potřebovat provádět úlohy, jako je změna položky konfigurace, kopírování obsahu aplikace mezi servery a spouštění programů interaktivní instalace v závislosti na nastavení .msi, za nímž následuje testování. Všechny tyto kroky v nasazení přidat času a rizika pro nasazení. Dojde k selhání pokaždé, když se závislost není k dispozici v cílovém prostředí.

V kontejnerech Windows je plně automatizovat proces vytváření balíčků aplikací. Kontejnery Windows se odvíjí platforma Docker, která nabízí automatické aktualizace, vrácení zpět pro nasazení kontejnerů. Hlavní vylepšení, které získáte pomocí modulu Docker je vytvořit Image, které jsou podobné snímek vaší aplikace, se všemi jeho závislostmi. Image jsou Image Dockeru (Windows image kontejneru, v tomto případě). Obrázky spouštění aplikací v ASP.NET v kontejnerech, bez nutnosti vracet se ke zdrojovému kódu. Snímek kontejneru se změní na jednotku nasazení.

Mnoho organizací se kontejnerizování existující monolitických aplikací z následujících důvodů:

- **Uvolnění pružné vylepšené nasazování**. Kontejnery nabízejí konzistentní nasazování kontrakt mezi vývojem a provozem. Při použití kontejnerů, Řekněme, že vývojáři nebudou slyšet, "to funguje na mém počítači, případně proč bezpečná není v produkčním prostředí?" Můžete říct, "Poběží brána jako kontejner, takže se spustí v produkčním prostředí." Zabalená aplikace se všemi jeho závislostmi, mohou být provedeny v libovolné podporované prostředí založené na kontejnerech. Způsob, jakým byl určen ke spuštění v všechny cíle nasazení (vývoj, dotazů a odpovědí, Fázování a výrobu) se spustí. Kontejnery eliminovat většina frictions, když se přesouvají z jedné fáze do druhého, což výrazně zvyšuje nasazení, a rychlejší dodání.

- **Snížení nákladů**. Kontejnery vést ke snížení nákladů, buď konsolidace a odebrání stávající hardware nebo z aplikace spuštěné ve vyšší hustota na jednotku hardwaru.

- **Přenositelnost**. Kontejnery jsou moduly a přenosné. Kontejnery dockeru jsou podporovány na serverový operační systém (Linux a Windows), v libovolné významnější veřejná Cloudová (Microsoft Azure, Amazon AWS, Google, IBM) a v místní a privátní nebo hybridní Cloudová prostředí.

- **Ovládací prvek**. Kontejnery nabízejí flexibilní a zabezpečené prostředí, které se řídí na úrovni kontejneru. Kontejner můžete zabezpečené, izolované a i omezené tím, že nastavíte zásady omezení spuštění v kontejneru. Podle popisu v části o kontejnerech Windows Windows Server 2016 a Hyper-V kontejnery nabízejí možnosti podpory další organizace.

Významné zlepšení agility, přenositelnost a ovládací prvek s tvorbou snížení nákladů při použití kontejnerů pro vývoj a údržbu aplikace.

## <a name="what-is-docker"></a>Co je Docker?

[Docker](https://www.docker.com/) je [open source projektu](https://github.com/docker/docker) , který automatizuje nasazení aplikací jako přenosných a soběstační kontejnerů, které můžou běžet v cloudu nebo místně. Docker je také [společnosti](https://www.docker.com/) , který podporuje a vyvíjí tuto technologii. Společnost funguje ve spolupráci s cloudem, Linux a Windows dodavateli, včetně Microsoft.

![](./media/image6.png)

> **Obrázek 4 až 6.** Dockeru nasadí kontejnery na všech úrovních hybridního cloudu

Někomu obeznámeni s virtuálními počítači, kontejnerů může zobrazit pozoruhodně podobné. Kontejner běží operační systém, je systém souborů a je přístupný přes síť, stejně jako fyzický nebo virtuální počítač systému. Technologie a principy kontejnery jsou ale výrazně liší od virtuálních počítačů. Z developer hlediska musí kontejner více zacházet jako s jeden proces. Ve skutečnosti kontejner má jeden vstupní bod pro jeden proces.

Kontejnery dockeru (pro zjednodušení *kontejnery*) můžou nativně běžet na systému Linux a Windows. Při spuštění regulárního kontejnery, kontejnery Windows lze použít pouze v hostitelích Windows (hostitelský server nebo virtuální počítač) a kontejnery Linuxu lze spustit pouze na hostitelích systému Linux. Ale v posledních verzích systému Windows Server a Hyper-V containers kontejneru Linuxu také můžete spustit nativně v systému Windows Server s použitím technologie izolace Hyper-V, která je aktuálně k dispozici pouze v systému Windows Server kontejnery.

Hybridní prostředí, které mají kontejnerů Linuxu a Windows v blízké budoucnosti bude možné a dokonce i běžné.

## <a name="benefits-of-windows-containers-for-your-existing-net-applications"></a>Výhody kontejnerů Windows pro existující aplikace .NET

Mezi výhody používání kontejnerů Windows jsou v podstatě stejné výhody, které získáte obecně z kontejnerů. Pomocí kontejnerů Windows je výrazně zlepšuje agilitu, přenositelnost a ovládací prvek.

Stávající aplikace .NET najdete v těchto aplikací, které byly vytvořeny pomocí rozhraní .NET Framework. Například může být tradiční webové aplikace ASP.NET-, nepoužívejte .NET Core, která je novější a spouští různé platformy v systému Linux, Windows a MacOS.

Hlavní závislost v rozhraní .NET Framework je Windows. Má také sekundární závislosti, jako jsou služby IIS a System.Web v tradiční technologie ASP.NET.

Aplikace rozhraní .NET Framework, musíte spustit na Windows, období. Pokud chcete kontejnerizace existující aplikace rozhraní .NET Framework a nemůžete nebo nechcete investovat do migrace až po .NET Core ("Pokud funguje správně, nemusíte migrovat"), pouze pro kontejnery je používání kontejnerů Windows.

Takže jeden z největších výhod kontejnerů Windows je, že tyto funkce poskytují způsob, jak modernizaci stávajících aplikací rozhraní .NET Framework, které běží na Windows prostřednictvím kontejnerizace. Nakonec kontejnery Windows získáte výhody, které hledáte, s využitím flexibility kontejnerů, přenositelnost a lepší kontrolu.

## <a name="choose-an-os-to-target-with-net-based-containers"></a>Vyberte operační systém na cíl. Kontejnery založené na NET

Zadaný spektrum operačních systémů, které podporuje Docker, stejně jako rozdíly v rozhraní .NET Framework a .NET Core, by měl cíl konkrétní operační systém a konkrétní verze založené na rozhraní .NET framework, které používáte.

Pro Windows můžete použít Windows Server Core nebo Windows Nano Server. Tyto verze Windows poskytují různé vlastnosti (např. IIS a v místním prostředí webového serveru, jako Kestrel), které mohou být potřebné aplikace rozhraní .NET Framework nebo .NET Core.

Více distribuce pro Linux, jsou dostupné a podporované v oficiální Image .NET Dockeru (např. Debian).

Obrázek 4 – 7 znázorňuje verze operačního systému, které chcete, můžete vybrat, v závislosti na verzi aplikace rozhraní .NET Framework.

![](./media/image7.png)

> **Obrázek 4 – 7.** Operační systémy do cíle založené na verzi rozhraní .NET Framework

Ve scénářích migrace pro existující nebo starší verzi aplikace, které jsou založeny na rozhraní .NET Framework aplikace hlavní závislosti jsou na Windows a služby IIS. Jedinou možností je použití imagí Dockeru založených na Windows Server Core a .NET Framework.

Když přidáte název bitové kopie do souboru Dockerfile, můžete vybrat verzi operačního systému a s použitím značky, stejně jako v následujících příkladech týkajících imagí kontejnerů Windows založené na rozhraní .NET Framework:

> | **Značka** | **Systém a verze** |
> |---|---|
> | **microsoft/dotnet-framework:4.x-windowsservercore** | Rozhraní .NET framework 4.x na jádru Windows serveru |
> | **microsoft/aspnet:4.x-windowsservercore** | Rozhraní .NET framework 4.x s další vlastní nastavení technologie ASP.NET, v systému Windows Server Core |

Pro .NET Core (pro různé platformy pro systémy Linux a Windows) značky by vypadat nějak takto:

> | **Značka** | **Systém a verze**
> |---|---|
> | **microsoft/dotnet:2.0.0-runtime** | .NET core 2.0 v Linuxu pouze modul runtime |
> | **microsoft/dotnet:2.0.0-runtime-nanoserver** | .NET core 2.0 pouze modul runtime Windows Nano server |

### <a name="multi-arch-images"></a>Více architektury imagí

Od poloviny 2017, také můžete použít novou funkci v Dockeru volá [více arch](https://github.com/moby/moby/issues/15866) bitové kopie. Více architektury značky můžete použít Image Dockeru .NET core. Váš soubor Dockerfile souborů už potřeba definovat operační systém, který cílíte. Více architektury funkce umožňuje jedné značky, který se má použít napříč konfiguracemi s více počítači. Pro instanci s více arch, můžete použít jednu značku common: **microsoft/dotnet:2.0.0-runtime**. Pokud si vyžádáte dané klíčové slovo z prostředí kontejnerů Linux, získáte imagí založených na Debian. Pokud si vyžádáte dané klíčové slovo z prostředí kontejneru Windows, získáte imagí založených na Nano serveru.

Pro rozhraní .NET Framework bitové kopie protože tradiční rozhraní .NET Framework podporuje pouze Windows nelze použít funkci více architektury.

## <a name="windows-container-types"></a>Typy kontejnerů Windows

Jako kontejnery Linux se spravují kontejnery Windows serveru s využitím modulu Docker. Na rozdíl od kontejnery Linuxu kontejnery Windows zahrnují dva typy jiný kontejner nebo spustit doby než Windows Server containers a izolace Hyper-V.

**Kontejnery Windows serveru**: Poskytuje izolace aplikací prostřednictvím technologie izolace procesu a obor názvů. Kontejner Windows Server se sdílí jádro s hostitel s kontejnerem a všechny kontejnery, které běží na hostiteli. Tyto kontejnery neposkytují hranice nebezpečný zabezpečení a by neměl být použít k izolaci nedůvěryhodného kódu. Z důvodu místa sdílené jádra tyto kontejnery vyžadují stejné verze jádra a konfigurace.

**Izolace Hyper-V**: Rozšiřuje možnosti izolace poskytovaná kontejnery Windows serveru spuštěním jednotlivých kontejnerů na virtuálním počítači s vysoce optimalizovaný. V této konfiguraci nesdílí jádro hostitele kontejneru s dalších kontejnerů ve stejném hostiteli. Tyto kontejnery jsou navržené pro nebezpečný víceklientské hostování, se stejnou míru záruky zabezpečení virtuálního počítače. Protože tyto kontejnery Nesdílejte jádro s hostitelem nebo jiných kontejnerů na hostiteli, můžou běžet jader s různými verzemi a konfigurace (s podporovanou verzí). Například všechny kontejnery Windows ve Windows 10 pomocí izolace Hyper-V pro využití verze jádra systému Windows Server a konfiguraci.

Spouštění kontejneru na Windows s nebo bez izolace Hyper-V je za běhu rozhodnutí. Může být zpočátku vytvořit kontejner izolace Hyper-V a v době běhu, zvolte možnost pro spuštění jako kontejner Windows Server.

### <a name="additional-resources"></a>Další zdroje

- **Dokumentace ke službě kontejnery Windows**

    <https://docs.microsoft.com/virtualization/windowscontainers/>

- **Základy kontejnery Windows**

    <https://docs.microsoft.com/virtualization/windowscontainers/about/>

- **Infografika: Microsoft a kontejnery**

    <https://info.microsoft.com/rs/157-GQE-382/images/Container%20infographic%201.4.17.pdf>

## <a name="the-container-ecosystem-in-azure"></a>Ekosystém kontejneru v Azure

V předchozích částech byla vysvětlení, jaké jsou výhody kontejnerů Dockeru a také podrobnosti o imagí kontejneru pro konkrétní pro aplikace .NET. Všechno, obecné informace jsou zásadní pro vývoj nebo kontejnerizace aplikace.
Však při posuzování nasazení prostředí nebo dokonce i prostředí pro řízení kvality a pro vývoj/testování, Microsoft Azure poskytuje otevřít a širokou řadu možností, ekosystém úplné kontejneru v cloudu (viz následující diagram). V závislosti na potřebách vaší konkrétní aplikaci měli byste zvolit jeden nebo druhý produkt Azure.

![](./media/image7.5.png)

> **Obrázek 4 – 7.5.** Ekosystém kontejneru v Azure

Z ekosystému kontejneru v Azure, podporuje kontejnery, které jsou považovány za infrastrukturu následující produkty:
- **Azure Container Instances (ACI)**
- **Azure Virtual Machines** (s podporou kontejneru)
- **Azure Virtual Machine Scale Sets** (s podporou kontejneru)

Z těchto tří ACI poskytuje skvělé výhody, které je skutečnost, že není nutné k údržbě základní operační systém, nemusíte za vás upgradování, opravování a podobně, ale ACI stále je umístěn na úrovni infrastruktury, jak bylo vysvětleno lépe v nadcházejících částech této příručky.

Produkty v podpůrných kontejnery služby Azure, které jsou ve stejnou dobu více umístěn v modelu PaaS (platforma jako služba) úrovně jsou:

- **Azure App Service**
- **Azure Kubernetes Service (AKS a ACS)**
- **Azure Service Fabric** 
- **Azure Batch** 

Azure Container Registry je vysoce škálovatelná kontejneru registru hostované v Azure, které můžete použít ze všech předchozích produktů při registrací a nasazením vlastního kontejneru obrázků.

Kromě toho můžete ze své kontejnery využívat další spravované služby v Azure jako Azure SQL Database, Azure Redis cache, Azure Cosmos DB, atd. Kromě webu Azure Marketplace, jako je Cloud Foundry a OpenShift, kde můžete také použít kontejnery v Azure jsou k dispozici řešení třetích stran/platformy. 

V následujících částech si můžete projít doporučení Microsoftu týkající se použití každé z těchto řešení a produkty Azure konkrétně při cílení na kontejnery Windows.

>[!div class="step-by-step"]
>[Předchozí](what-about-cloud-native-applications.md)
>[další](when-not-to-deploy-to-windows-containers.md)
