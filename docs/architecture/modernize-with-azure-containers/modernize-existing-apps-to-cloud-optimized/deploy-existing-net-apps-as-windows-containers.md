---
title: Nasazení existujících aplikací .NET jako kontejnery Windows
description: Modernizovat stávající aplikace .NET pomocí cloudu Azure a kontejnerů Windows | Nasazení stávajících aplikací .NET jako kontejnerů Windows
ms.date: 04/29/2018
ms.openlocfilehash: 28568ca363bfc8100f78b100f8a7f0242c4f04c9
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/08/2019
ms.locfileid: "73089561"
---
# <a name="deploy-existing-net-apps-as-windows-containers"></a>Nasazení existujících aplikací .NET jako kontejnery Windows

Nasazení založená na kontejnerech Windows se vztahují na cloudově optimalizované aplikace a cloudové nativní aplikace.

V tomto průvodci, a to zejména v následujících částech, se většinou zaměřuje na použití kontejnerů Windows pro *cloudově optimalizované* aplikace, kde nemusíte měnit architekturu aplikace.

## <a name="what-are-containers-linux-or-windows"></a>Co jsou kontejnery? (Linux nebo Windows)

Kontejnery představují způsob, jak zabalit aplikaci do svého samostatného izolovaného balíčku. V kontejneru aplikace nejsou ovlivněny aplikacemi nebo procesy, které existují mimo kontejner. Vše, na kterém je aplikace závislá, se spustí úspěšně, protože proces je uvnitř kontejneru. Bez ohledu na to, jestli se kontejner může přesunout, požadavky aplikace budou vždycky splněné, a to z hlediska přímých závislostí, protože jsou připojené ke všemu, co musí spustit (závislosti knihoven, modul runtime atd.).

Hlavní charakteristika kontejneru spočívá v tom, že prostředí je stejné napříč různými nasazeními, protože kontejner sám obsahuje všechny závislosti, které potřebuje. Aplikaci můžete ladit na svém počítači a pak ji nasadit do jiného počítače se stejnou zaručeným prostředím.

Kontejner je instance image kontejneru. Image kontejneru je způsob, jak zabalit aplikaci nebo službu (například snímek) a jak ji nasadit spolehlivým a rereprodukovatelným způsobem. Je možné, že Docker není pouze technologie – je to také filozofie a proces.

Vzhledem k tomu, že se kontejnery denně stávají častější, stávají se jednotkou nasazení v celém odvětví.

## <a name="benefits-of-containers-docker-engine-on-linux-or-windows"></a>Výhody kontejnerů (Docker Engine v systému Linux nebo Windows)

Vytváření aplikací pomocí kontejnerů – které můžou být taky definované jako zjednodušené stavební kameny – nabízí významné zvýšení flexibility při sestavování, dodávání a spouštění libovolné aplikace v rámci libovolné infrastruktury.

Pomocí kontejnerů můžete libovolnou aplikaci z vývoje převést do produkčního prostředí s využitím téměř nebo bez změny kódu, a to díky integraci Docker napříč Microsoft Developer Tools, operačními systémy a cloudem.

Když nasadíte do jednoduchých virtuálních počítačů, pravděpodobně už máte metodu pro nasazení aplikací ASP.NET na vaše virtuální počítače. V takovém případě je pravděpodobnější, že vaše metoda zahrnuje několik ručních kroků nebo složitých automatizovaných procesů pomocí nástroje pro nasazení, jako je Puppet nebo podobného nástroje. Je možné, že budete muset provádět úlohy, jako je úprava položek konfigurace, kopírování obsahu aplikace mezi servery a spouštění interaktivních instalačních programů na základě instalačních programů. msi, a to následováním testování. Všechny tyto kroky v nasazení přidávají čas a riziko pro nasazení. V případě, že v cílovém prostředí není přítomná závislost, dojde k chybám.

V kontejnerech Windows je proces vytváření balíčků aplikací plně automatizovaný. Kontejnery Windows jsou založené na platformě Docker, která nabízí automatické aktualizace a vrácení zpět pro nasazení kontejnerů. Hlavním vylepšením, které byste získali pomocí modulu Docker, je vytvoření imagí, což jsou například snímky vaší aplikace, a všechny její závislosti. Obrázky jsou image Docker (v tomto případě image kontejneru Windows). Image spouští aplikace ASP.NET v kontejnerech, aniž by se musely vracet ke zdrojovému kódu. Snímek kontejneru se stal jednotkou nasazení.

Mnoho organizací uzavření stávající aplikace monolitické z následujících důvodů:

- **Flexibilita verzí prostřednictvím vylepšeného nasazení**. Kontejnery nabízejí konzistentní smlouvu o nasazení mezi vývojem a provozem. Při použití kontejnerů nebudete vývojářům slyšet "," funguje na mém počítači, proč není v produkčním prostředí? " Můžou vyslovit "spouští se jako kontejner, takže se spustí v produkčním prostředí." Zabalená aplikace se všemi jejími závislostmi se dá spustit v jakémkoli podporovaném prostředí založeném na kontejnerech. Spustí se způsobem, který by měl být spuštěn ve všech cílech nasazení (vývoj, QA, fázování, produkce). Kontejnery eliminují většinu tření při přesunu z jedné fáze na další, což významně zlepšuje nasazení a můžete dodávat rychleji.

- **Snížení nákladů**. Kontejnery vedou k nižším nákladům, a to buď konsolidací, odebráním stávajícího hardwaru, nebo spuštěním aplikací s vyšší hustotou na jednotce hardwaru.

- **Přenositelnost**. Kontejnery jsou modulární a přenosné. Kontejnery Docker jsou podporované na jakémkoli serverovém operačním systému (Linux a Windows), v jakémkoli významném veřejném cloudu (Microsoft Azure, Amazon AWS, Google, IBM) a v místních i privátních nebo hybridních cloudových prostředích.

- **Ovládací prvek**. Kontejnery nabízejí flexibilní a zabezpečené prostředí, které se řídí na úrovni kontejneru. Kontejner může být zabezpečený, izolovaný a dokonce omezený nastavením zásad omezení spouštění na kontejneru. Jak je popsáno v části o kontejnerech Windows, Windows Server 2016 a kontejnery Hyper-V nabízejí další možnosti podnikové podpory.

Významná vylepšení flexibility, přenositelnosti a kontroly nakonec vedou k výraznému snížení nákladů při použití kontejnerů k vývoji a údržbě aplikací.

## <a name="what-is-docker"></a>Co je Docker?

[Docker](https://www.docker.com/) je [Open source projekt](https://github.com/docker/docker) , který automatizuje nasazení aplikací jako přenosných a vlastních kontejnerů, které mohou běžet v cloudu nebo místně. Docker je také [Společnost](https://www.docker.com/) , která propaguje a vyvíjí tuto technologii. Společnost funguje ve spolupráci s dodavateli pro Cloud, Linux a Windows, včetně Microsoftu.

![Diagram znázorňující, jak Docker nasazuje kontejnery v hybridním cloudu.](./media/deploy-existing-net-apps-as-windows-containers/docker-deploys-containers-all-layers.png)

**Obrázek 4-6.** Docker nasazuje kontejnery ve všech vrstvách hybridního cloudu.

Pro uživatele, kteří se s virtuálními počítači seznámili, se kontejnery můžou zdát jako výjimečně podobné. Kontejner spouští operační systém, který má systém souborů a je k němu možné přistupovat přes síť, stejně jako fyzický nebo virtuální počítač. Technologie a koncepce za kontejnery se ale výrazně liší od virtuálních počítačů. Z pohledu vývojáře musí být kontejner zpracován podobně jako jeden proces. Ve skutečnosti má kontejner jeden vstupní bod pro jeden proces.

Kontejnery Docker (pro jednoduchost, *kontejnery*) můžou běžet nativně v systémech Linux a Windows. Při spouštění běžných kontejnerů se kontejnery Windows můžou spouštět jenom na hostitelích s Windows (hostitelský server nebo virtuální počítač) a kontejnery Linux můžou běžet jenom na hostitelích se systémem Linux. V posledních verzích kontejnerů Windows Server a Hyper-V se ale kontejner Linux taky dá spustit nativně na Windows serveru pomocí technologie izolace Hyper-V, která je teď dostupná jenom v kontejnerech Windows serveru.

V blízké budoucnosti budou existovat smíšená prostředí, která mají kontejnery pro Linux i Windows, a dokonce i běžnou.

## <a name="benefits-of-windows-containers-for-your-existing-net-applications"></a>Výhody kontejnerů Windows pro stávající aplikace .NET

Výhody použití kontejnerů Windows jsou zásadními výhodami, které získáte obecně z kontejnerů. Pomocí kontejnerů Windows se výrazně zlepšuje flexibilita, přenositelnost a řízení.

Stávající aplikace .NET odkazují na aplikace, které byly vytvořeny pomocí .NET Framework. Můžou to být například tradiční webové aplikace v ASP.NET – nepoužívají .NET Core, které jsou novější a spouštějí různé platformy v systémech Linux, Windows a MacOS.

Hlavní závislost ve .NET Framework je Windows. Má také sekundární závislosti, jako je IIS, a System. Web v tradičních ASP.NET.

.NET Framework aplikace musí běžet ve Windows, tečka. Pokud chcete kontejnerizace stávající aplikace .NET Framework a nemůžete nebo nechcete investovat do migrace do .NET Core ("Pokud funguje správně, Nemigrujte"), jedinou volbou, kterou máte v kontejnerech, je použití kontejnerů Windows.

Jedna z hlavních výhod kontejnerů Windows proto nabízí způsob, jak modernizovat své stávající aplikace .NET Framework spuštěné v systému Windows prostřednictvím kontejneru. Kontejnery Windows vám nakonec poskytují výhody, které hledáte, pomocí kontejnerů – flexibilita, přenositelnost a lepší řízení.

## <a name="choose-an-os-to-target-with-net-based-containers"></a>Vyberte operační systém, se kterým chcete cílit. Kontejnery založené na síti

Vzhledem k rozmanitosti operačních systémů, které podporuje Docker, a rozdílů mezi .NET Framework a .NET Core, byste měli cílit na konkrétní operační systém a konkrétní verze na základě rozhraní, které používáte.

Pro Windows můžete použít jádro Windows serveru nebo Windows nano Server. Tyto verze systému Windows poskytují různé charakteristiky (například službu IIS oproti webovému serveru v místním prostředí, jako je Kestrel), které mohou být vyžadovány aplikacemi .NET Framework nebo .NET Core.

Pro Linux je k dispozici několik distribuce a podporují se v oficiálních bitových kopiích .NET Docker (jako Debian).

Obrázek 4-7 ukazuje verze operačních systémů, které lze cílit, v závislosti na verzi .NET Framework aplikace.

![Diagram znázorňující, jaký operační systém má cílit na základě verze .NET Framework.](./media/deploy-existing-net-apps-as-windows-containers/dotnet-framework-operating-systems.png)

**Obrázek 4-7.** Operační systémy cílí na základě verze .NET Framework

Ve scénářích migrace pro existující nebo starší aplikace, které jsou založené na .NET Framework aplikacích, jsou hlavní závislosti ve Windows a IIS. Jedinou možností je použít image Docker na základě jádra Windows serveru a .NET Framework.

Když přidáte název Image do souboru souboru Dockerfile, můžete vybrat operační systém a verzi pomocí značky, jako v následujících příkladech pro .NET Framework imagí kontejnerů Windows na bázi:

> | **Inteligentní** | **Systém a verze** |
> |---|---|
> | **Microsoft/DotNET-Framework: 4. x – windowsservercore** | .NET Framework 4. x v jádru Windows serveru |
> | **Microsoft/ASPNET: 4. x – windowsservercore** | .NET Framework 4. x s dalšími přizpůsobeními ASP.NET v jádru Windows serveru |

Pro .NET Core (pro různé platformy pro Linux a Windows) by značky vypadaly takto:

> | **Inteligentní** | **Systém a verze**
> |---|---|
> | **Microsoft/dotNET: 2.0.0-Runtime** | .NET Core 2,0 Runtime – pouze v systému Linux |
> | **Microsoft/dotNET: 2.0.0-Runtime – nanoserver** | .NET Core 2,0 Runtime – jenom na Windows nano serveru |

### <a name="multi-arch-images"></a>Obrázky s více archy

Od Mid-2017 můžete použít také novou funkci v Docker s názvem [vícestránkové](https://github.com/moby/moby/issues/15866) obrázky. Image Docker .NET Core můžou používat více značek. Vaše soubory souboru Dockerfile už nepotřebují definovat operační systém, který cílíte. Funkce vícenásobného archu umožňuje používat jednu značku v rámci více konfigurací počítačů. U více instancí můžete například použít jednu běžnou značku: **Microsoft/dotNET: 2.0.0-Runtime**. Pokud tuto značku vyžádáte z prostředí s kontejnery pro Linux, získáte image založenou na Debian. Pokud tuto značku vyžádáte z prostředí kontejneru Windows, dostanete image založenou na nano serveru.

U .NET Framework imagí, protože tradiční .NET Framework podporuje jenom Windows, nemůžete použít funkci vícenásobného archu.

## <a name="windows-container-types"></a>Typy kontejnerů Windows

Například kontejnery systému Linux jsou kontejnery Windows serveru spravovány pomocí modulu Docker. Na rozdíl od kontejnerů Linux zahrnují kontejnery Windows dva různé typy kontejnerů, nebo dobu běhu – kontejnery Windows serveru a izolaci technologie Hyper-V.

**Kontejnery Windows serveru**: poskytuje izolaci aplikací prostřednictvím technologie izolace procesů a oboru názvů. Kontejner Windows serveru sdílí jádro s hostitelem kontejneru a všemi kontejnery, které jsou spuštěné na hostiteli. Tyto kontejnery neposkytují nepřátelský bezpečnostní hranici a neměly by se používat k izolaci nedůvěryhodného kódu. Z důvodu sdíleného prostoru jádra vyžaduje tyto kontejnery stejnou verzi jádra a konfiguraci.

**Izolace Hyper-V**: rozbalí na izolaci poskytovanou kontejnery Windows serveru spuštěním každého kontejneru na vysoce OPTIMALIZOVANém virtuálním počítači. V této konfiguraci není jádro hostitele kontejneru sdíleno s jinými kontejnery na stejném hostiteli. Tyto kontejnery jsou navržené pro nepřátelské hostování víceklientské architektury se stejnými bezpečnostními zárukami virtuálního počítače. Vzhledem k tomu, že tyto kontejnery nesdílejí jádro s hostitelem nebo jinými kontejnery na hostiteli, mohou spouštět jádra s různými verzemi a konfiguracemi (s podporovanými verzemi). Všechny kontejnery Windows ve Windows 10 například využívají izolaci technologie Hyper-V k využití konfigurace a verze jádra Windows serveru.

Spuštění kontejneru ve Windows s nebo bez izolace Hyper-V je rozhodnutí za běhu. Je možné, že se nejdříve vytvoří kontejner s izolací technologie Hyper-V a v době běhu se místo toho dá spustit jako kontejner Windows serveru.

### <a name="additional-resources"></a>Další zdroje

- **Dokumentace k kontejnerům Windows**

    <https://docs.microsoft.com/virtualization/windowscontainers/>

- **Základní informace o kontejnerech Windows**

    <https://docs.microsoft.com/virtualization/windowscontainers/about/>

- **Infografika: Microsoft a Containers**

    <https://info.microsoft.com/rs/157-GQE-382/images/Container%20infographic%201.4.17.pdf>

## <a name="the-container-ecosystem-in-azure"></a>Ekosystém kontejnerů v Azure

V předchozích částech bylo vysvětleno, jaké jsou výhody kontejnerů Docker a také podrobnosti o konkrétních imagích kontejnerů pro aplikace .NET. Všechny obecné informace jsou zásadním účelem pro vývoj nebo kontejnerizaceí aplikace.
Při zvažování prostředí produkčního nasazení nebo dokonce řešení pro řešení QA a vývoj a testování ale Microsoft Azure poskytuje otevřenou a širokou škálu voleb, úplný ekosystém kontejnerů v cloudu (viz diagram níže). V závislosti na potřebách konkrétní aplikace byste měli zvolit jeden nebo jiný produkt Azure.

![Diagram ekosystému kontejnerů v Azure](./media/deploy-existing-net-apps-as-windows-containers/azure-container-ecosystem.png)

**Obrázek 4 – 7.5** Ekosystém kontejnerů v Azure

Z ekosystému kontejnerů v Azure tyto produkty podporují kontejnery považované za infrastrukturu:

- **Azure Container Instances (ACI)**
- **Azure Virtual Machines** (s podporou kontejneru)
- **Azure Virtual Machine Scale Sets** (s podporou kontejneru)

Od těchto tří ACI přináší skvělé výhody, což je fakt, že nepotřebujete spravovat základní operační systém, nemusíte upgradovat/opravovat atd., ale ACI pořád je umístěný na úrovni infrastruktury, jak je to vhodnější v nadcházejících částech této knihy.

U produktů v Azure podporujících kontejnery, které jsou na úrovni PaaS (platforma jako služba) Další:

- **Azure App Service**
- **Služba Azure Kubernetes (AKS a ACS)**
- **Azure Batch**

Pak Azure Container Registry je vysoce škálovatelný registr kontejnerů hostovaný v Azure, který můžete použít ze všech předchozích produktů při registraci a nasazení vlastních imagí kontejneru.

Z vašich kontejnerů navíc můžete využívat jiné spravované služby v Azure, jako je Azure SQL Database, Azure Redis Cache, Azure Cosmos DB atd. k dispozici jsou řešení/platformy třetích stran, které jsou dostupné v Azure Marketplace jako Cloud Foundry a OpenShift, kde můžete také používat kontejnery v Azure.

V dalších částech můžete prozkoumat doporučení Microsoftu, kdy používat jednotlivé produkty a řešení Azure konkrétně při cílení na kontejnery Windows.

>[!div class="step-by-step"]
>[Předchozí](what-about-cloud-native-applications.md)
>[Další](when-not-to-deploy-to-windows-containers.md)
