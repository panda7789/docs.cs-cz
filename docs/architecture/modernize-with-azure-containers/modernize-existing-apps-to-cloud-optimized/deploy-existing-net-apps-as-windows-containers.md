---
title: Nasazení existujících aplikací .NET jako kontejnery Windows
description: Modernizace stávajících aplikací .NET pomocí Azure Cloudu a kontejnerů Windows | Nasazení existujících aplikací .NET jako kontejnerů Windows
ms.date: 04/29/2018
ms.openlocfilehash: 15e99e2ec0edd072a3d47d5c212ebbbf6705ecef
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738426"
---
# <a name="deploy-existing-net-apps-as-windows-containers"></a>Nasazení existujících aplikací .NET jako kontejnery Windows

Nasazení založená na kontejnerech Windows se vztahují na aplikace optimalizované pro cloud a aplikace nativní pro cloud.

V této příručce a zejména v následujících částech se však většinou zaměřuje na použití kontejnerů systému Windows pro aplikace *optimalizované pro cloud,* kde není nutné předělat aplikaci.

## <a name="what-are-containers-linux-or-windows"></a>Co jsou kontejnery? (Linux nebo Windows)

Kontejnery jsou způsob, jak zabalit aplikaci do vlastního izolovaného balíčku. Ve svém kontejneru aplikace není ovlivněna aplikace nebo procesy, které existují mimo kontejner. Vše, na co aplikace závisí, aby byla úspěšně spuštěna, protože proces je uvnitř kontejneru. Všude tam, kde se kontejner může přesunout, požadavky aplikace budou vždy splněny, pokud jde o přímé závislosti, protože je dodáván se vším, co potřebuje ke spuštění (závislosti knihovny, runtimes a tak dále).

Hlavní charakteristikou kontejneru je, že umožňuje prostředí stejné v různých nasazeních, protože samotný kontejner je dodáván se všemi závislostmi, které potřebuje. Můžete ladit aplikace v počítači a pak ji nasadit do jiného počítače, se stejným prostředím zaručena.

Kontejner je instancí bitové kopie kontejneru. Image kontejneru je způsob, jak zabalit aplikaci nebo službu (například snímek) a pak ji nasadit spolehlivým a reprodukovatelným způsobem. Dalo by se říci, že Docker není jen technologie-je to také filozofie a proces.

Jak kontejnery denně stávají běžnějšími, stávají se celoprůmyslovou "jednotkou nasazení".

## <a name="benefits-of-containers-docker-engine-on-linux-or-windows"></a>Výhody kontejnerů (Docker Engine na Linuxu nebo Windows)

Vytváření aplikací pomocí kontejnerů- což také může být definováno jako lehké stavební bloky - nabízí významné zvýšení agility pro vytváření, odesílání a spouštění libovolné aplikace v rámci libovolné infrastruktury.

S kontejnery můžete mít libovolnou aplikaci z vývoje do produkčního prostředí s malou nebo žádnou změnou kódu díky integraci Dockeru mezi vývojářskými nástroji Microsoftu, operačními systémy a cloudem.

Když se nasazujete do běžných virtuálních počítačů, pravděpodobně už máte zavedenou metodu pro nasazení ASP.NET aplikací do virtuálních počítačů. Je však pravděpodobné, že vaše metoda zahrnuje více ručních kroků nebo složitých automatizovaných procesů pomocí nástroje pro nasazení, jako je Puppet, nebo podobného nástroje. Může být nutné provádět úlohy, jako je úprava položek konfigurace, kopírování obsahu aplikace mezi servery a spuštění interaktivních instalačních programů založených na nastaveních MSI, následované testováním. Všechny tyto kroky v nasazení přidat čas a riziko pro nasazení. Zobrazí se chyby vždy, když závislost není k dispozici v cílovém prostředí.

V kontejnerech Windows je proces balení aplikací plně automatizovaný. Kontejnery Windows jsou založené na platformě Dockeru, která nabízí automatické aktualizace a vrácení zpět pro nasazení kontejnerů. Hlavní zlepšení, které získáte z použití modulu Docker je, že vytvoříte image, které jsou jako snímky vaší aplikace, se všemi jeho závislostmi. Bitové kopie jsou image Dockeru (v tomto případě bitová kopie kontejneru windows). Obrázky běží ASP.NET aplikace v kontejnerech, aniž by se vrátil ke zdrojovému kódu. Snímek kontejneru se stane jednotkou nasazení.

Mnoho organizací kontejnerizuje existující monolitické aplikace z následujících důvodů:

- **Uvolněte agilitu díky vylepšenému nasazení**. Kontejnery nabízejí konzistentní kontrakt nasazení mezi vývojem a operacemi. Když používáte kontejnery, neuslyšíte vývojáře říkat: "Funguje to na mém počítači, proč ne ve výrobě?" Mohou říci: "Běží jako kontejner, takže poběží ve výrobě." Zabalená aplikace se všemi jeho závislostmi může být spuštěna v libovolném podporovaném prostředí založeném na kontejneru. Bude spuštěn tak, jak byl určen ke spuštění ve všech cílech nasazení (dev, QA, staging, production). Kontejnery eliminují většinu tření, když se pohybují z jedné fáze do druhé, což výrazně zlepšuje nasazení, a můžete doručovat rychleji.

- **Snížení nákladů**. Kontejnery vedou k nižším nákladům, a to buď konsolidací a odebráním stávajícího hardwaru, nebo spuštěním aplikací s vyšší hustotou na jednotku hardwaru.

- **Přenositelnost**: Kontejnery jsou modulární a přenosné. Kontejnery Dockeru jsou podporované na libovolném operačním systému pro servery (Linux a Windows), v jakémkoli větším veřejném cloudu (Microsoft Azure, Amazon AWS, Google, IBM) a v místním i soukromém nebo hybridním cloudovém prostředí.

- **Ovládací prvek**. Kontejnery nabízejí flexibilní a bezpečné prostředí, které je řízeno na úrovni kontejneru. Kontejner může být zabezpečen, izolován a dokonce omezen nastavením zásad omezení spuštění kontejneru. Jak je podrobně popsáno v části o kontejnerech Windows, kontejnery Windows Server 2016 a Hyper-V nabízejí další možnosti podnikové podpory.

Významná zlepšení agility, přenositelnosti a řízení nakonec vedou k významnému snížení nákladů při použití kontejnerů k vývoji a údržbě aplikací.

## <a name="what-is-docker"></a>Co je Docker?

[Docker](https://www.docker.com/) je [open source projekt,](https://github.com/docker/docker) který automatizuje nasazení aplikací jako přenosné, soběstačné kontejnery, které lze spustit v cloudu nebo v místním prostředí. Docker je také [společnost,](https://www.docker.com/) která podporuje a vyvíjí tuto technologii. Společnost spolupracuje s dodavateli cloudu, Linuxu a Windows, včetně microsoftu.

![Diagram znázorňující, jak Docker nasazuje kontejnery v hybridním cloudu.](./media/deploy-existing-net-apps-as-windows-containers/docker-deploys-containers-all-layers.png)

**Obrázek 4-6.** Docker nasazuje kontejnery ve všech vrstvách hybridního cloudu

Pro někoho obeznámený s virtuálními počítači kontejnery může zdát pozoruhodně podobné. Kontejner běží operační systém, má systém souborů a lze k němu přistupovat přes síť, stejně jako systém fyzického nebo virtuálního počítače. Technologie a koncepty za kontejnery se však diametrálně liší od virtuálních počítačů. Z pohledu vývojáře musí být kontejner ošetřen spíše jako jeden proces. Ve skutečnosti kontejner má jeden vstupní bod pro jeden proces.

Kontejnery Dockeru (pro jednoduchost, *kontejnery*) lze spustit nativně na Linuxu a Windows. Při spuštění běžných kontejnerů mohou kontejnery systému Windows běžet pouze na hostitelích systému Windows (hostitelský server nebo virtuální počítač) a kontejnery Linuxu lze spustit pouze na hostitelích Linuxu. V posledních verzích kontejnerů Windows Server a Hyper-V však může kontejner Linuxu běžet nativně v systému Windows Server pomocí technologie izolace Hyper-V, která je v současné době k dispozici pouze v kontejnerech windows serveru.

V blízké budoucnosti budou možná a dokonce běžná smíšená prostředí, která mají kontejnery Linux i Windows.

## <a name="benefits-of-windows-containers-for-your-existing-net-applications"></a>Výhody kontejnerů windows pro stávající aplikace .NET

Výhody používání kontejnerů systému Windows jsou v zásadě stejné výhody, které získáte z kontejnerů obecně. Použití kontejnerů systému Windows je o výrazně zlepšit agilitu, přenositelnost a řízení.

Existující aplikace .NET odkazují na aplikace, které byly vytvořeny pomocí rozhraní .NET Framework. Mohou se například jedná o tradiční ASP.NET webových aplikací - nepoužívají .NET Core, který je novější a běží napříč platformami na Linuxu, Windows a MacOS.

Hlavní závislost v rozhraní .NET Framework je systém Windows. Má také sekundární závislosti, jako je iis a System.Web v tradiční ASP.NET.

Aplikace rozhraní .NET Framework musí být spuštěna v systému Windows, tečka. Pokud chcete kontejnerizovat existující aplikace rozhraní .NET Framework a nemůžete nebo nechcete investovat do migrace na .NET Core ("Pokud funguje správně, nemigrujte ji"), jedinou možností, kterou máte pro kontejnery, je použití kontejnerů windows.

Takže jednou z hlavních výhod kontejnerů systému Windows je, že nabízejí způsob, jak modernizovat stávající aplikace rozhraní .NET Framework, které jsou spuštěny v kontejnerizaci systémem Windows až po kontejnerizaci. Kontejnery windows vám nakonec zajistí výhody, které hledáte, pomocí flexibility kontejnerů, přenositelnosti a lepší kontroly.

## <a name="choose-an-os-to-target-with-net-based-containers"></a>Vyberte operační systém, na který chcete cílit. Kontejnery založené na NET

Vzhledem k rozmanitosti operačních systémů, které jsou podporovány Docker, stejně jako rozdíly mezi rozhraním .NET Framework a .NET Core, měli byste cílit na konkrétní operační systém a konkrétní verze na základě rozhraní, které používáte.

V systému Windows můžete použít Windows Server Core nebo Windows Nano Server. Tyto verze systému Windows poskytují různé charakteristiky (například službu IIS versus webový server hostovaný s vlastním hostitelem, jako je Kestrel), které mohou být potřebné rozhraním .NET Framework nebo .NET Core.

Pro Linux je k dispozici více distribucí a podporováno v oficiálních obrázcích .NET Docker (jako debian).

Obrázek 4-7 ukazuje verze operačního systému, na které můžete cílit, v závislosti na verzi rozhraní .NET Framework aplikace.

![Diagram znázorňující, na co má být operační systém cílit na základě verze rozhraní .NET Framework.](./media/deploy-existing-net-apps-as-windows-containers/dotnet-framework-operating-systems.png)

**Obrázek 4-7.** Operační systémy, na které se má cílit na základě verze rozhraní .NET Framework

Ve scénářích migrace pro existující nebo starší aplikace, které jsou založeny na aplikacích rozhraní .NET Framework, jsou hlavní závislosti v systému Windows a IIS. Jedinou možností je použití iložek Dockeru založených na Windows Server Core a rozhraní .NET Framework.

Když přidáte název bitové kopie do souboru Dockerfile, můžete vybrat operační systém a verzi pomocí značky, jako v následujících příkladech pro bitové kopie kontejnerů systému Windows založené na rozhraní .NET Framework:

> | **Tag** | **Systém a verze** |
> |---|---|
> | **Microsoft/dotnet-Framework:4.x-windowsservercore** | Rozhraní .NET Framework 4.x v jádru systému Windows Server |
> | **microsoft/aspnet:4.x-windowsservercore** | Rozhraní .NET Framework 4.x s dalším přizpůsobením ASP.NET v systému Windows Server Core |

Pro .NET Core (cross-platformpro Linux a Windows) by značky vypadaly takto:

> | **Tag** | **Systém a verze**
> |---|---|
> | **microsoft/dotnet:2.0.0-runtime** | Pouze runtimes rozhraní .NET Core 2.0 na Linuxu |
> | **microsoft/dotnet:2.0.0-runtime-nanoserver** | Pouze runtime rozhraní .NET Core 2.0 na serveru Windows Nano Server |

### <a name="multi-arch-images"></a>Víceobloukové obrazy

Od poloviny roku 2017 můžete také použít novou funkci v Dockeru nazvanou [multiobloukové](https://github.com/moby/moby/issues/15866) obrazy. Bitové kopie .NET Core Docker umějí používat víceobloukové značky. Soubory Dockerfile již není nutné definovat operační systém, který cílíte. Funkce více oblouků umožňuje použití jedné značky ve více konfiguracích strojů. Například s multi-arch, můžete použít jednu společnou značku: **microsoft/dotnet:2.0.0-runtime**. Pokud tuto značku vytáhnete z prostředí kontejneru Linuxu, získáte bitovou kopii založenou na Debianu. Pokud tuto značku vytáhnete z prostředí kontejneru Windows, získáte bitovou kopii založenou na serveru Nano Server.

Pro bitové kopie rozhraní .NET Framework, protože tradiční rozhraní .NET Framework podporuje pouze systém Windows, nelze použít funkci více oblouků.

## <a name="windows-container-types"></a>Typy kontejnerů systému Windows

Stejně jako kontejnery Linux, kontejnery Windows Server jsou spravovány pomocí Docker Engine. Na rozdíl od kontejnerů Linuxu obsahují kontejnery systému Windows dva různé typy kontejnerů nebo kontejnery run times-Windows Server a izolaci Hyper-V.

**Kontejnery systému Windows Server**: Poskytuje izolaci aplikací prostřednictvím technologie izolace procesu a oboru názvů. Kontejner systému Windows Server sdílí jádro s hostitelem kontejneru a všemi kontejnery, které jsou spuštěny na hostiteli. Tyto kontejnery neposkytují nepřátelskou hranici zabezpečení a neměly by být použity k izolování nedůvěryhodného kódu. Z důvodu sdíleného prostoru jádra vyžadují tyto kontejnery stejnou verzi jádra a konfiguraci.

**Izolace Hyper-V**: Rozšiřuje izolaci poskytovanou kontejnery Windows Server spuštěním každého kontejneru na vysoce optimalizovaném virtuálním počítači. V této konfiguraci jádro hostitele kontejneru není sdíleno s jinými kontejnery na stejném hostiteli. Tyto kontejnery jsou navržené pro nepřátelský víceklientský hosting se stejnými zárukami zabezpečení virtuálního počítače. Vzhledem k tomu, že tyto kontejnery nesdílejí jádro s hostitelem nebo jinými kontejnery na hostiteli, mohou spouštět jádra s různými verzemi a konfiguracemi (s podporovanými verzemi). Například všechny kontejnery Windows v systému Windows 10 používají izolaci Technologie Hyper-V k využití verze a konfigurace jádra windows serveru.

Spuštění kontejneru v systému Windows s izolací hyper-V nebo bez ní je rozhodnutí za běhu. Můžete se rozhodnout vytvořit kontejner s izolací Technologie Hyper-V zpočátku a za běhu jej místo toho spustit jako kontejner windows serveru.

### <a name="additional-resources"></a>Další zdroje

- **Dokumentace k kontejnerům windows**

    <https://docs.microsoft.com/virtualization/windowscontainers/>

- **Základy kontejnerů Windows**

    <https://docs.microsoft.com/virtualization/windowscontainers/about/>

- **Infografika: Microsoft a kontejnery**

    <https://info.microsoft.com/rs/157-GQE-382/images/Container%20infographic%201.4.17.pdf>

## <a name="the-container-ecosystem-in-azure"></a>Ekosystém kontejnerů v Azure

V předchozích částech bylo vysvětleno, jaké jsou výhody kontejnerů Dockeru, stejně jako podrobnosti o konkrétních irecích kontejnerů pro aplikace .NET. Všechny obecné informace jsou zásadní pro vývoj nebo kontejnerizaci aplikace.
Když však microsoft Azure přemýšlí o produkčním prostředí nasazení nebo dokonce o prostředích qa a dev/test, poskytuje otevřenou a širokou škálu možností, ekosystém plných kontejnerů v cloudu (viz obrázek níže). V závislosti na potřebách vaší konkrétní aplikace byste měli zvolit jeden nebo jiný produkt Azure.

![Diagram ekosystému kontejnerů v Azure.](./media/deploy-existing-net-apps-as-windows-containers/azure-container-ecosystem.png)

**Obrázek 4-7.5.** Ekosystém kontejnerů v Azure

Z ekosystému kontejnerů v Azure podporují následující produkty podporující kontejnery, které jsou považovány za infrastrukturu:

- **Azure Container Instances (ACI)**
- **Virtuální počítače Azure** (s podporou kontejneru)
- **Škálovací sady virtuálních strojů Azure** (s podporou kontejneru)

Z těchto tří, ACI poskytuje velkou výhodu, což je skutečnost, že nemusíte udržovat základní OS, není třeba pro vás upgrade / patch, atd., ale ACI je stále umístěn na úrovni infrastruktury, jak lépe vysvětleno v nadcházejících částech této knihy.

Produkty v Azure podpůrné kontejnery, které jsou ve stejnou dobu umístěny více na úrovni PaaS (Platformas a Service) jsou:

- **Azure App Service**
- **Služba Azure Kubernetes (AKS a ACS)**
- **Azure Batch**

Pak Azure Container Registry je vysoce škálovatelný kontejner registru hostované v Azure, které můžete použít ze všech předchozích produktů při registraci a nasazení vlastní image kontejneru.

Kromě toho z vašich kontejnerů můžete využívat další spravované služby v Azure, jako je Azure SQL Database, azure redis cache, Azure Cosmos DB atd. navíc na Azure Marketplace jsou dostupná řešení/platformy třetích stran, jako je Cloud Foundry a OpenShift, kde můžete taky používat kontejnery v Azure.

V dalších částech se můžete zabývat doporučeními microsoftu, kdy použít jednotlivé z těchto produktů a řešení Azure konkrétně při cílení na kontejnery Windows.

>[!div class="step-by-step"]
>[Předchozí](what-about-cloud-native-applications.md)
>[další](when-not-to-deploy-to-windows-containers.md)
