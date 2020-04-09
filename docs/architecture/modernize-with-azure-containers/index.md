---
title: Modernizace existujících aplikací .NET pomocí Azure Cloudu a kontejnerů Windows (2. vydání)
description: Naučte se zvedat a přesouvat a modernizovat stávající aplikace do cloudu Azure a kontejnerů pomocí této elektronické knihy.
ms.date: 04/28/2018
ms.openlocfilehash: 95a5870254481a4c6c9eed82b5be5e1eb10be346
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2020
ms.locfileid: "80987943"
---
# <a name="modernize-existing-net-applications-with-azure-cloud-and-windows-containers-2nd-edition"></a>Modernizace stávajících aplikací .NET pomocí cloudu Azure a kontejnerů S Windows (2. vydání)

![Obrázek obálky průvodce Modernizovat aplikace .NET.](./media/index/web-application-guide-cover-image.png)

PUBLIKOVAL(A)  
Microsoft Press a Microsoft DevDiv  
Divize společnosti Microsoft Corporation  
One Microsoft Way  
Redmond, Washington 98052-6399  

Autorská práva © 2020 společností Microsoft Corporation  

Všechna práva vyhrazena. Žádná část obsahu této knihy nesmí být reprodukována v jakékoli formě nebo jakýmkoli způsobem bez písemného souhlasu vydavatele.

Tato kniha je k dispozici zdarma ve formě elektronické knihy (e-knihy) <https://dot.net/architecture>k dispozici prostřednictvím více kanálů v Microsoftu, jako je .

Máte-li dotazy týkající se této [dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book)knihy, e-mail na adrese .

Tato kniha je poskytována "tak, jak je" a vyjadřuje názory a názory autora. Názory, názory a informace vyjádřené v této knize, včetně url a dalších odkazů na internetové stránky, se mohou změnit bez předchozího upozornění.

Některé zde uvedené příklady slouží pouze k znázornění a jsou smyšlené. Neměli byste z nich vyvozovat žádné skutečné vztahy či spojení.

Společnost Microsoft a ochranné <https://www.microsoft.com> známky uvedené na webové stránce "Ochranné známky" jsou ochrannými známkami skupiny společností Microsoft. Všechny ostatní ochranné známky jsou majetkem příslušných vlastníků.

Autor:
> **Cesar de la Torre**, Sr. PM, .NET produktový tým, Microsoft Corp.

Účastníci a recenzenti:
> **Scott Hunter**, partnerský ředitel PM, .NET tým, Microsoft  
> **Paul Yuknewicz**, hlavní pm manažer, tým Visual Studio Tools, Microsoft  
> **Lisa Guthrie**, Sr. PM, Visual Studio Tools tým, Microsoft  
> **Ankit Asthana**, hlavní pm manažer, .NET tým, Microsoft  
> **Unai Zorrilla**, vedoucí vývojář, Plain Koncepty  
> **Javier Valero**, provozní ředitel společnosti Grupo Solutio  

## <a name="introduction"></a>Úvod

Když se rozhodnete modernizovat webové aplikace nebo služby a přesunout je do cloudu, nemusíte nutně plně rearchitect vaše aplikace. Rearchitecting aplikace pomocí pokročilý přístup, jako jsou mikroslužeb není vždy možnost z důvodu nákladů a omezení času. V závislosti na typu aplikace nemusí být nutná také úprava aplikace. Chcete-li optimalizovat nákladovou efektivitu strategie migrace do cloudu vaší organizace, je důležité zvážit potřeby vaší firmy a požadavky vašich aplikací. Budete muset určit:

- Které aplikace vyžadují transformaci nebo rearchitecting.

- Které aplikace je třeba modernizovat pouze částečně.

- Které aplikace můžete "zvednout a přesunout" přímo do cloudu.

## <a name="about-this-guide"></a>O této příručce

Tato příručka se zaměřuje především na počáteční modernizaci existujících webových aplikací microsoft .NET Framework nebo aplikací orientovaných na služby, což znamená akci přesunutí úlohy do novějšího nebo modernějšího prostředí bez výrazné změny kódu aplikace a základní architektury.

Tato příručka také upozorňuje na výhody přesunutí aplikací do cloudu a částečné modernizace aplikací pomocí konkrétní sady nových technologií a přístupů, jako jsou Kontejnery Windows a související výpočetní platformy v Azure podporující kontejnery Windows.

## <a name="path-to-the-cloud-for-existing-net-applications"></a>Cesta ke cloudu pro existující aplikace .NET

Organizace se obvykle rozhodnou přejít do cloudu pro flexibilitu a rychlost, kterou mohou získat pro své aplikace. Můžete nastavit tisíce serverů (VM) v cloudu během několika minut, ve srovnání s týdny obvykle trvá nastavení místních serverů.

Neexistuje jediná strategie pro migraci aplikací do cloudu. Správná strategie migrace pro vás bude záviset na potřebách a prioritách vaší organizace a na druhu migrujících aplikací. Ne všechny aplikace vyžadují investici přechodu na platformu jako model služby[(PaaS)](https://azure.microsoft.com/overview/what-is-paas/)nebo vývoji modelu aplikace [nativní pro cloud.](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) V mnoha případech můžete postupně nebo přírůstkově přistupovat k investicím do přesunu vašich aktiv do cloudu na základě vašich obchodních potřeb.

Pro moderní aplikace s nejlepší dlouhodobou agilitou a hodnotou pro organizaci můžete těžit z investic do architektur aplikací *nativních* pro cloud. Pro aplikace, které jsou existující nebo starší prostředky, je však klíčem strávit minimální čas a peníze (bez rearchitecting nebo změny kódu) při jejich přesunutí do cloudu, realizovat významné výhody.

Obrázek 1-1 ukazuje možné cesty, které můžete provést při přesunutí existujících aplikací .NET do cloudu v přírůstkových fázích.

 ![Cesty modernizace pro existující aplikace a služby rozhraní .NET](./media/image1-1.png)

**Obrázek 1-1**. Cesty modernizace pro existující aplikace a služby rozhraní .NET

Každý přístup migrace má různé výhody a důvody pro jeho použití. Můžete zvolit jeden přístup při migraci aplikací do cloudu nebo zvolte určité součásti z více přístupů. Jednotlivé aplikace nejsou omezeny na jeden přístup nebo stav splatnosti. Například společný hybridní přístup by měl určité místní součásti a další součásti v cloudu.

Definice a krátké vysvětlení pro každou úroveň splatnosti aplikace jsou následující:

**Úroveň 1: Aplikace připravené pro cloudovou infrastrukturu:** V tomto přístupu migrace jednoduše migrovat nebo rehostovat aktuální místní aplikace na platformu infrastruktury jako služby[(IaaS).](https://azure.microsoft.com/overview/what-is-iaas/) Vaše aplikace mají téměř stejné složení jako předtím, ale teď je nasazujete do virtuálních počítačů v cloudu.
Tento jednoduchý typ migrace je v oboru obvykle označován jako "Lift & Shift".

**Úroveň 2:** Cloud optimalizované aplikace: Na této úrovni a stále bez rearchitecting nebo změny významného kódu, můžete získat další výhody ze spuštění aplikace v cloudu s moderními technologiemi, jako jsou kontejnery a další služby spravované cloudem. Můžete zlepšit agilitu vašich aplikací k rychlejšímu domování tím, že zpřesníte procesy podnikových vývojových operací (DevOps). Toho dosáhnete pomocí technologií, jako jsou kontejnery Windows, které jsou založeny na Docker Engine. Kontejnery odeberte tření, které je způsobeno závislostmi aplikací při nasazení ve více fázích. V tomto modelu splatnosti můžete nasadit kontejnery na IaaS nebo PaaS při použití dalších cloudových spravovaných služeb souvisejících s databázemi, mezipaměti jako služby, monitorování a průběžné integrace/průběžného nasazení (CI/CD) kanály.

Třetí úroveň vyspělosti je konečným cílem v cloudu, ale je volitelná pro mnoho aplikací a není hlavním zaměřením této příručky:

**Úroveň 3: Aplikace nativní pro cloud:** Tento přístup migrace je obvykle řízen obchodními potřebami a zaměřuje se na modernizaci klíčových aplikací. Na této úrovni používáte služby PaaS k přesunutí aplikací na výpočetní platformy PaaS. Implementujete [cloudnativní](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) aplikace a architekturu mikroslužeb, abyste vyvíjeli aplikace s dlouhodobou agilitou a škálovali na nová omezení. Tento typ modernizace obvykle vyžaduje architektonizaci speciálně pro cloud. Nový kód často musí být zapsány, zejména při přechodu na cloud nativní aplikace a mikroslužeb založené modely. Tento přístup vám může pomoci získat výhody, které je obtížné dosáhnout ve vašem monolitickém a místním aplikačním prostředí.

Tabulka 1-1 popisuje hlavní výhody a důvody pro výběr každého přístupu migrace nebo modernizace.

| **Připraveno pro cloudovou infrastrukturu** <br /> *Metoda „lift and shift“* | **Optimalizováno pro cloud** <br /> *Modernizovat* | **Nativní pro cloud** <br /> *Modernizace, rearchitect a přepsat* |
|---|---|---|
| **Výpočetní cíl aplikace** |
| Aplikace nasazené do virtuálních počítačů v Azure | Monolitické nebo Nvrstvé aplikace nasazené do služby Azure App Service, Instance kontejneru Azure (ACI), Virtuální počítače s kontejnery nebo AKS (služba Azure Kubernetes) | Kontejnerizované mikroslužby ve službě Azure Kubernetes Service (AKS) a/nebo mikroslužeb bez serveru na základě funkcí Azure. |
| **Cíl dat** |
| SQL nebo jakákoli relační databáze na virtuálním počítači | Spravovaná instance Azure SQL Database nebo jiná spravovaná databáze v cloudu. | Databáze s pokutou za jedno mikroslužby založené na Azure SQL Database, Azure Cosmos DB nebo jiné spravované databázi v cloudu |
| **Výhody**|
| <li>Žádné rearchitecting, žádný nový kód <li> Nejmenší úsilí pro rychlou migraci <li> Nejméně společný jmenovatel podporovaný v Azure <li> Základní záruky dostupnosti <li> Po přechodu do cloudu je jednodušší ještě více modernizovat | <li> Žádné rearchitecting <li> Minimální změny kódu/konfigurace <li> Vylepšená flexibilita nasazení a devOps, která se uvolní kvůli kontejnerům <li> Zvýšená hustota a nižší náklady na nasazení <li> Přenositelnost aplikací a závislostí <li> Flexibilita hostitelských cílů: Přístupy PaaS nebo IaaS | <li> Architekt pro cloud, získáte nejlepší výhody z cloudu, ale je potřeba nový kód <li> Přístupy mikroslužeb nativní pro cloud <li> Moderní klíčové aplikace, hyperškálovatelné odolné vůči cloudu <li> Plně spravované služby <li> Optimalizováno pro měřítko <li> Optimalizováno pro autonomní agilitu podle subsystému <li> Postaveno na nasazení a devops |
| **Výzvy** |
| <li> Menší hodnota cloudu, jiná než posun provozních výdajů nebo uzavření datových center <li> Málo se spravuje: Žádné opravy operačního e-nosu nebo middlewaru; mohou používat infrastrukturní řešení, jako je Terraform, Spinnaker nebo Puppet | <li> Kontejnerizace je dalším krokem v učení křivky pro vývojáře a IT operace <li> DevOps a CI/CD kanály jsou obvykle 'musí' pro tento přístup. Pokud není v současné době přítomen v kultuře organizace, může to být další výzvou| <li> Vyžaduje přearchitekturu pro cloudové nativní aplikace a architektury mikroslužeb a obvykle vyžaduje významné refaktoring kódu nebo přepisování při modernizaci (prodloužení času a rozpočtu)|
> **Tabulka 1-1.** Výhody a výzvy modernizačních cest pro stávající aplikace a služby .NET

### <a name="key-technologies-and-architectures-by-maturity-level"></a>Klíčové technologie a architektury podle úrovně vyspělosti

Aplikace rozhraní .NET Framework byly původně spuštěny s rozhraním .NET Framework verze 1.0, která byla vydána koncem roku 2001. Společnosti pak přešly k novějším verzím (například 2.0, 3.5 a .NET 4.x). Většina těchto aplikací byla spuštěna na systémech Windows Server a Internet Information Server (IIS) a používala relační databázi, například SQL Server, Oracle, MySQL nebo jakýkoli jiný rdbms.

Většina existujících aplikací .NET může být v dnešní době založena na rozhraní .NET Framework 4.x nebo dokonce na rozhraní .NET Framework 3.5 a používat webové architektury jako ASP.NET MVC, ASP.NET Web Forms, ASP.NET Web API, Windows Communication Foundation (WCF), ASP.NET SignalR a ASP.NET webPages. Tyto zavedené technologie rozhraní .NET Framework závisí na systému Windows. Tuto závislost je důležité zvážit, pokud jednoduše migrujete starší aplikace a chcete provést minimální změny infrastruktury aplikací.

Obrázek 1–2 znázorňuje primární technologie a styly architektury používané na každé ze tří úrovní splatnosti cloudu:

![Primární technologie pro každou úroveň vyspělosti pro modernizaci stávajících webových aplikací .NET](./media/image1-2.png)

**Obrázek 1-2.** Primární technologie pro každou úroveň vyspělosti pro modernizaci stávajících webových aplikací .NET

Obrázek 1-2 zvýrazňuje nejběžnější scénáře, ale mnoho hybridních a smíšených variant je možné, pokud jde o architekturu. Modely vyspělosti se například vztahují nejen na monolitické architektury ve stávajících webových aplikacích, ale také na orientaci služby, n-vrstvu a další varianty stylu architektury. Vyšší zaměření nebo procento na jeden nebo jiný typ architektury a související technologie určuje celkovou úroveň vyspělosti vašich aplikací.

Každá úroveň vyspělosti v procesu modernizace je spojena s následujícími klíčovými technologiemi a přístupy:

- **Cloud Infrastructure-Ready** (rehost nebo základní výtah & posun): Jako první krok, mnoho organizací chcete pouze rychle provést strategii migrace do cloudu. V tomto případě jsou aplikace rehosted. Většinu rehostingu lze automatizovat pomocí [služby Azure Migrate](https://aka.ms/azuremigrate), která poskytuje pokyny, přehledy a mechanismy potřebné k migraci do Azure na základě cloudových nástrojů, jako je [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/) a Azure Database Migration [Service](https://azure.microsoft.com/campaigns/database-migration/). Rehosting můžete taky nastavit ručně, abyste se při přesunu starších aplikací do cloudu dozvěděli podrobnosti o infrastruktuře o svých datových tocích. Například můžete přesunout aplikace do virtuálních počítačů v Azure s malou úpravou pravděpodobně s pouze drobné změny konfigurace. Sítě v tomto případě je podobný místní prostředí, zejména pokud vytvoříte virtuální sítě v Azure.

- **Optimalizované pro cloud** (spravované služby a kontejnery systému Windows): Tento model je o provedení několika důležitých optimalizací nasazení, abyste získali některé významné výhody z cloudu, aniž byste změnili základní architekturu aplikace. Základním krokem je přidání podpory [kontejnerů systému Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) do stávajících aplikací rozhraní .NET Framework. Tento důležitý krok (kontejnerizace) nevyžaduje dotýká kódu, takže celkové zvedání a posun úsilí je lehký. Můžete použít nástroje, jako [je Image2Docker](https://github.com/docker/communitytools-image2docker-win) nebo Visual Studio, s jeho nástroje pro [Docker](https://www.docker.com/). Visual Studio automaticky vybere inteligentní výchozí hodnoty pro ASP.NET aplikace a bitové kopie kontejnerů windows. Tyto nástroje nabízejí jak rychlou vnitřní smyčku, tak rychlou cestu k získání kontejnerů do Azure. Vaše agilita je lepší při nasazení do více prostředí.
Potom, přechod na produkční prostředí, můžete nasadit kontejnery Windows do [Azure Web App pro kontejnery](https://azure.microsoft.com/services/app-service/containers/), Azure Container [Instances (ACI)](https://azure.microsoft.com/services/container-instances/)a Azure virtuální počítače s Windows Server 2016 a kontejnery, pokud dáváte přednost přístupu IaaS. Pro složitější aplikace s více kontejnery zvažte použití orchestrátorů, jako je [služba Azure Kubernetes Service (AKS/ACS).](https://azure.microsoft.com/services/container-service/)

Během této počáteční modernizace můžete také přidat prostředky z cloudu, jako je například monitorování pomocí nástrojů, jako jsou [Azure Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview); Kanály CI/CD pro životní cykly aplikací pomocí [služeb Azure DevOps Services](https://azure.microsoft.com/services/devops/); a mnoho dalších služeb datových prostředků, které jsou dostupné v Azure. Můžete například upravit monolitickou webovou aplikaci, která byla původně vyvinuta pomocí tradičních [ASP.NET webových formulářů](https://www.asp.net/web-forms) nebo [ASP.NET MVC](https://www.asp.net/mvc), ale nyní ji nasadíte pomocí kontejnerů windows. Při použití kontejnerů windows, měli byste také migrovat data do databáze v [Azure SQL Database Managed Instance](https://docs.microsoft.com/azure/sql-database/), to vše beze změny základní architektury vaší aplikace.

- **Cloud-Native**: Jak bylo zavedeno, měli byste přemýšlet o navrhování [aplikací nativní pro cloud,](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) když se zaměřujete na velké a složité aplikace s více nezávislými vývojovými týmy pracujícími na různých mikroslužbách, které lze vyvíjet a nasadit autonomně. Také z důvodu podrobné a nezávislé škálovatelnosti na mikroslužbu. Tyto architektonické přístupy čelí velmi důležitým výzvám a složitostem, ale lze je značně zjednodušit pomocí cloudových paasů a orchestrátorů, jako je [služba Azure Kubernetes Service (AKS/ACS)](https://azure.microsoft.com/services/container-service/) (spravované Kubernetes) a [Funkce Azure](https://azure.microsoft.com/services/functions/) pro přístup bez serveru. Všechny tyto přístupy (jako mikroslužeb a serverless) obvykle vyžadují architekt pro cloud a napsat nový kód – kód, který je přizpůsoben pro konkrétní platformy PaaS nebo kód, který je zarovnán s konkrétní architektury, jako jsou mikroslužby.

Obrázek 1-3 ukazuje interní technologie, které můžete použít pro každou úroveň splatnosti:

![Interní technologie pro každou úroveň modernizace](./media/image1-3.png)

**Obrázek 1-3.** Interní technologie pro každou úroveň modernizace

## <a name="lift-and-shift-scenario"></a>Scénář zvedání a řazení

Pro migrace výtahu a směny mějte na paměti, že ve scénářích aplikace můžete použít mnoho různých variant výtahu a posunu. Pokud jste pouze rehost aplikace, můžete mít scénář, jako je znázorněno na obrázku 1-4, kde se používá virtuální počítače v cloudu pouze pro vaši aplikaci a pro databázový server.

![Příklad čistého scénáře IaaS v cloudu](./media/image1-4.png)

**Obrázek 1-4**. Příklad čistého scénáře IaaS v cloudu

## <a name="modernization-scenarios"></a>Scénáře modernizace

Pro scénáře modernizace můžete mít čistě cloudově optimalizovanou aplikaci, která používá prvky pouze z této úrovně vyspělosti. Nebo můžete mít aplikaci pro střední stav s některými prvky z cloudové infrastruktury připravené a další prvky z optimalizované pro cloud ("vybrat a vybrat" nebo smíšený model), jako na obrázku 1-5.

![Příklad scénáře "vybrat a vybrat" s databází na iaaS, DevOps a containerization assets](./media/image1-5.png)

**Obrázek 1-5.** Příklad scénáře "vybrat a vybrat" s databází na iaaS, DevOps a containerization assets

Dále jako ideální scénář pro mnoho existujících aplikací rozhraní .NET Framework k migraci můžete migrovat do aplikace optimalizované pro cloud, abyste získali významné výhody z malé práce. Tento přístup také nastaví vás pro Cloud-Native jako možný budoucí vývoj. Obrázek 1-6 ukazuje příklad.

![Příklad scénáře aplikací optimalizovaných pro cloud s kontejnery Windows a spravovanými službami](./media/image1-6.png)

**Obrázek 1-6.** Příklad scénáře aplikací optimalizovaných pro cloud s kontejnery Windows a spravovanými službami

Chystáte se ještě dále, můžete rozšířit stávající cloudoptimalizované aplikace přidáním několika mikroslužeb pro konkrétní scénáře. To by přesunout částečně na úroveň modelu Cloud Nativní, což není hlavním zaměřením současné pokyny.

## <a name="what-this-guide-does-not-cover"></a>Co tato příručka nezahrnuje

Tato příručka popisuje konkrétní podmnožinu ukázkových scénářů, jak je znázorněno na obrázku 1-7. Tato příručka se zaměřuje pouze na výtah a posun scénáře a nakonec na cloud-optimalizované modelu. V modelu optimalizovaném pro cloud je aplikace .NET Framework modernizována pomocí kontejnerů systému Windows a dalších součástí, jako je monitorování a kanály CI/CD. Každá komponenta je zásadní pro nasazení aplikací do cloudu, rychlejší a s agilitou.

![Cloud-Native není zahrnuta v této příručce](./media/image1-7.png)

**Obrázek 1-7.** Cloud-Native není zahrnuta v této příručce

Zaměření této příručky je specifické. Ukazuje cestu, kterou můžete podniknout k dosažení výtahu a posunu stávajících aplikací .NET, bez rearchitectingu a bez změn kódu. Nakonec vám ukáže, jak vytvořit aplikaci optimalizovanou pro cloud.

Tato příručka neukazuje, jak vytvářet aplikace nativní pro cloud, například jak se vyvíjet na architekturu mikroslužeb. Chcete-li předělat aplikace nebo vytvořit zcela nové aplikace založené na mikroslužbách, přečtěte si e-knihy [.NET Microservices: Architektura pro kontejnerizované aplikace .NET](https://aka.ms/microservicesebook).

### <a name="additional-resources"></a>Další zdroje

- **Kontejnerizovaný životní cyklus aplikací Dockeru s platformou microsoftu a nástroji** (e-kniha ke stažení) \
  <https://aka.ms/dockerlifecycleebook>

- **.NET Microservices: Architektura pro kontejnerizované aplikace .NET** (e-kniha ke stažení) \
  <https://aka.ms/microservicesebook>

- **Navrhování moderních webových aplikací s ASP.NET Core a Azure** (e-kniha ke stažení) \
  <https://aka.ms/webappebook>

## <a name="who-should-use-this-guide"></a>Kdo by měl používat tuto příručku

Tato příručka byla napsána pro vývojáře a architekty řešení, kteří chtějí modernizovat stávající ASP.NET webových aplikací nebo wcf služeb, které jsou založeny na rozhraní .NET Framework, pro lepší flexibilitu v odesílání a vydávání aplikací.

Tuto příručku můžete také považovat za užitečnou, pokud jste technický rozhodovací pravomocí, jako je například podnikový architekt nebo vedoucí vývoje nebo ředitel, který chce pouze přehled výhod, které můžete získat pomocí kontejnerů windows a nasazením do cloudu při používání Microsoft Azure.

## <a name="how-to-use-this-guide"></a>Jak používat tohoto průvodce

Tato příručka se zabývá "proč"- proč budete chtít modernizovat stávající aplikace a konkrétní výhody, které získáte z používání kontejnerů windows při přesunutí aplikací do cloudu. Obsah v prvních kapitolách příručky je určen architektům a technickým činitelům, kteří chtějí přehled, ale nemusí se soustředit na implementaci a technické, podrobné detaily.

Poslední kapitola této příručky představuje více návodů, které se zaměřují na konkrétní scénáře nasazení. Tato příručka nabízí kratší verze návodů, shrnout scénáře a zvýraznit jejich výhody. Úplné návody přejít k podrobnostem nastavení a implementace a jsou publikovány jako sada [wiki příspěvků](https://github.com/dotnet-architecture/eShopModernizing/wiki) ve stejném veřejném [úložišti GitHub,](https://github.com/dotnet-architecture/eShopModernizing) kde se nacházejí související ukázkové aplikace (popsané v další části). Poslední kapitola a podrobné návody na wiki na GitHubu budou zajímavější pro vývojáře a architekty, kteří se chtějí zaměřit na podrobnosti implementace.

## <a name="sample-apps-for-modernizing-legacy-apps-eshopmodernizing"></a>Ukázkové aplikace pro modernizaci starších aplikací: eShopModernizing

[EShopModernizing](https://github.com/dotnet-architecture/eShopModernizing) repo na GitHubu nabízí dvě ukázkové aplikace, které simulují starší monolitické webové aplikace. Jedna webová aplikace je vyvíjena pomocí ASP.NET MVC; Druhá webová aplikace je vyvinuta pomocí ASP.NET webových formulářů a třetí aplikace je N-Tier aplikace s desktopovou aplikací klienta WinForms, která spotřebovává back-end služby WCF. Všechny tyto aplikace jsou založeny na tradiční rozhraní .NET Framework. Tyto ukázkové aplikace nepoužívají .NET Core nebo ASP.NET Core, protože mají být existující/starší aplikace rozhraní .NET Framework, které mají být modernizovány.

Tyto ukázkové aplikace mají druhou verzi s modernizovaným kódem a které jsou poměrně jednoduché. Nejdůležitější rozdíl mezi verzemi aplikace je, že druhá verze používá kontejnery systému Windows jako volbu nasazení. Existuje také několik dodatků k druhé verze, jako je Azure Storage Objekty BLOB pro správu inicia, Azure Active Directory pro správu zabezpečení a Azure Application Insights pro monitorování a auditování aplikací.

## <a name="send-your-feedback"></a>Pošlete svůj názor

Tato příručka byla napsána, aby vám pomohla pochopit možnosti pro zlepšení a modernizaci stávajících webových aplikací .NET. Příručka a související ukázkové aplikace se vyvíjejí. Vítáme vaše připomínky a názory. Máte-li připomínky k tomu, jak by tato [dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book)příručka mohla být užitečnější, pošlete je na .

>[!div class="step-by-step"]
>[Další](lift-and-shift-existing-apps-azure-iaas.md) <!-- Next Chapter -->
