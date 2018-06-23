---
title: Modernizovat existující .NET aplikací s Azure Cloud a systém Windows kontejnery (2. edice)
description: Postup navýšení a podržte klávesu shift a modernizovat existující aplikace, aby cloudu Azure a kontejnery s elektronickou knihu.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 4/28/2018
ms.openlocfilehash: 10af3a8ce1b9f501d7b646c8d49fcecab29af821
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/22/2018
ms.locfileid: "36314796"
---
# <a name="modernize-existing-net-applications-with-azure-cloud-and-windows-containers-2nd-edition"></a>Modernizovat existující aplikace .NET s cloudu Azure a Windows kontejnery (2. edice)

![Obrázek titulní](./media/cover.png)

PUBLIKOVÁNO  
Společnosti Microsoft Press a Microsoft DevDiv  
Oddělení společnosti Microsoft Corporation  
One Microsoft Way  
Redmond, Washington 98052-6399  

Copyright © Microsoft Corporation 2018  

Všechna práva vyhrazena. Žádná z částí obsah tato kniha může reprodukovat v žádný formulář nebo prostředky bez písemného souhlasu vydavatele.

Tato kniha je k dispozici zdarma ve formě elektronická kniha (elektronická kniha) k dispozici prostřednictvím více typů komunikačních kanálů v Microsoftu, jako http://dot.net/architecture.

Pokud máte dotazy týkající se tato kniha e-mailu v [dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book)

Tato kniha je k dispozici "jako-je" a vyjadřoval zobrazení a názory vytvářením obsahu. Zobrazení, názory a informace v této příručce, včetně adres URL a dalších odkazů na internetové weby, mohou změnit bez předchozího upozornění.

Některé příklady použité v ukázkách jsou jenom ilustrativní a smyšlené. Žádný skutečný vztah nebo připojení je určený nebo událostmi.

Společnost Microsoft a ochranné známky uvedený na http://www.microsoft.com na webové stránce "Ochranné známky" jsou obchodní známky společností skupiny Microsoft. Všechny ostatní značky jsou vlastnictvím příslušných vlastníků.

Autor:
> **Cesaru členka Torre**, Sr. PM, .NET produktu Team, Microsoft Corp.

Účastníci a recenzenti:
> **Scott Hunter**, ředitel partnera PM, .NET tým Microsoft  
> **Paul Yuknewicz**, hlavní manažer PM, nástroje sady Visual Studio team, Microsoft  
> **Lisa Guthrie**, Sr. PM, nástroje sady Visual Studio team, Microsoft  
> **Ankit Asthana**, hlavní manažer PM, .NET tým Microsoft  
> **Unai Zorrilla**, Developer realizace, prostý koncepty  
> **Javier Valero**, ředitel operační vedoucím v Grupo řešení  

## <a name="introduction"></a>Úvod

Pokud se rozhodnete modernizovat vaší webové aplikace nebo služby a přesuňte je do cloudu, nemusíte nutně plně rearchitect vaše aplikace. Vynaložit aplikace pomocí pokročilé přístup jako mikroslužeb není vždy možnost z důvodu omezení náklady a čas. V závislosti na typu aplikace vynaložit aplikace nemusí být také nezbytné. K optimalizaci nákladová efektivnost strategie migrace cloudu vaší organizace, je důležité vzít v úvahu požadavky aplikací a potřebám vaší firmy. Budete potřebovat k určení:

- Které aplikace vyžadují transformace nebo vynaložit.

- Které aplikace musí být modernized pouze částečně.

- Které aplikace můžete "navýšení a posunutí" přímo do cloudu.

## <a name="about-this-guide"></a>Informace o této příručce

Tato příručka se zaměřují hlavně na počáteční modernizace existující webové rozhraní Microsoft .NET Framework nebo aplikace orientované na služby, což znamená akce přechodu zatížení na novější nebo více moderní prostředí bez výrazně změny kódu aplikace a základní architekturu. 

Tato příručka označuje také výhody přesunutí aplikace do cloudu a částečně modernizace aplikace pomocí konkrétní sadu nové technologie a postupy, jako je Windows kontejnery a související výpočetních platforem v podpora kontejnerů Windows Azure.

## <a name="path-to-the-cloud-for-existing-net-applications"></a>Cesta ke cloudu pro existující aplikace .NET

Organizace obvykle vybrat přesunout do cloudu pro flexibility a rychlost, kterou můžete získat pro své aplikace. Nastavením tisíci servery (VM) v cloudu v minutách, ve srovnání s týdnů, obvykle trvá nastavit na místních serverech.

Není k dispozici jeden, univerzálně strategie pro migraci aplikace do cloudu. Strategie správné migrace pro vás bude záviset na potřebám vaší organizace a priority a typ aplikace, ze kterých provádíte migraci. Ne všechny aplikace vlastní investice přechodu na platforma jako služba ([PaaS](https://azure.microsoft.com/overview/what-is-paas/)) modelu nebo vývoj [cloudu nativní](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) aplikačního modelu. V mnoha případech může trvat postupné nebo přírůstkové přístup investovat do přechodu vaše prostředky do cloudu, podle obchodních potřeb.

Pro moderní aplikace se nejlépe dlouhodobé flexibility a hodnotou pro organizaci, může být vhodné Investujete do *cloudu nativní* architektury aplikace. Pro aplikace, které jsou existující nebo starší verze prostředky, ale klíč je během jejich přesouvání do cloudu, pokud chcete významné výhody zatěžovat minimální čas a peníze (nemění vynaložit nebo kód).

Obrázek 1-1 zobrazuje možné cesty, které můžete provést při přesunutí existující aplikace .NET do cloudu v přírůstkové fáze.

 ![Modernizace cesty pro existující aplikace .NET a služby](./media/image1-1.png)

> **Obrázek 1-1**. Modernizace cesty pro existující aplikace .NET a služby

Má každý přístup migrace různé výhody a důvody pro jejich použití. Můžete zvolit jeden přístup při migrovat aplikace do cloudu, nebo zvolte určité komponenty z více přístupů. Nejsou omezeny na jednoho přístup nebo vyspělosti stavu jednotlivých aplikací. Například běžný postup hybridní by měla mít určité součásti na místě a další součásti, v cloudu.

Definice a krátké vysvětlení každé úrovni vyspělosti aplikace jsou následující:

**Úroveň 1: Cloudové infrastruktury připravené** aplikací: V tento postup migrace, můžete jednoduše migrovat nebo opětovným hostováním aktuální místní aplikace a infrastruktury jako služby ([IaaS](https://azure.microsoft.com/overview/what-is-iaas/)) platformu. Aplikací mít téměř stejný složení jako před, ale nyní je nasadit do virtuálních počítačů v cloudu.
Tento jednoduchý typ migrace se obvykle označuje v odvětví jako "Navýšení & posunutí."

**Úroveň 2: Cloudu optimalizovaný** aplikací: na této úrovni a stále bez vynaložit nebo změnou významné kódu můžete získat další výhody spuštění aplikace v cloudu pomocí moderní technologie, jako jsou kontejnery a další spravované cloudové služby. Můžete zvýšit flexibility aplikací pro odeslání rychlejší podle upřesnění procesy operací (DevOps) vývoje vaší organizace. Můžete toho dosáhnout pomocí technologie, jako je Windows kontejnery, která je založena na Docker modul. Kontejnery odebrat třením, která je způsobena závislosti aplikací při nasazení v několika fázích. V tomto modelu splatnosti můžete nasadit kontejnery na IaaS nebo PaaS při použití další spravovanými přes cloud services související s databází, mezipaměti jako služba, monitorování a nepřetržité integrace/průběžné nasazování kanály (CI/CD).

Na třetí úrovni vyspělosti je konečným cílem v cloudu, ale je volitelné pro velký počet aplikací a není hlavním cílem tohoto průvodce:

**Úroveň 3: Cloudu nativní** aplikací: tuto metodu migrace se obvykle stanovují podle potřeby podniku a cíle modernizing kritické aplikace. Na této úrovni používáte PaaS služby pro přesun aplikace do PaaS výpočetních platformách. Můžete implementovat [cloudu nativní](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) aplikací a mikroslužeb architektura vyvíjet aplikace s dlouhodobé flexibility a škálování nové limitům. Tento typ modernizace obvykle vyžaduje architektury speciálně pro cloud. Nový kód často musí být napsané, zejména v případě, že můžete přesunout do cloudu nativní aplikaci a na základě mikroslužbu modely. Tento přístup vám může pomoct získat výhody, které je obtížné dosáhnout v prostředí aplikace monolitický a místně.

Tabulka 1-1 popisuje hlavní výhody a důvody pro výběr každý migrace nebo modernizace přístup.

| **Připravené pro infrastruktury cloudu** <br /> *Navýšení a posunutí* | **Optimalizovaných cloudů** <br /> *Modernizovat* | **Nativní cloudu** <br /> *Modernizovat, rearchitect a přepsání* |
|---|---|---|
| **Výpočetní cílové aplikace** |
| Aplikace nasazené do virtuálních počítačů v Azure | Monolitické nebo vícevrstvé aplikace nasazené do služby Azure App Service, Azure kontejneru Instance (ACI), virtuální počítače s kontejnery, Azure Service Fabric nebo AKS (služba Kubernetes Azure) | Kontejnerizované mikroslužeb Azure Kubernetes služby (AKS), Service Fabric a bez serveru mikroslužeb založené na Azure Functions. |
| **Cíl dat** |
| SQL nebo jakoukoli relační databázi na virtuálním počítači | Azure SQL Database spravované Instance nebo jiné spravované databáze v cloudu. | Databáze pokutu intervalem za mikroslužbu, na základě databáze SQL Azure, Azure Cosmos DB nebo jiné spravované databáze v cloudu |
| **Výhody**|
| <li>Žádný kód vynaložit, nové <li> Minimálně úsilí pro rychlé migrace <li> Jmenovatel nejmenší společný podporují v Azure <li> Záruky základní dostupnosti <li> Po přechodu do cloudu, je snazší i další modernizovat | <li> Žádné vynaložit <li> Změny minimální kódu/konfigurace <li> Vylepšené nasazení a flexibility DevOps uvolnit z důvodu kontejnery <li> Vyšší hustotu a nižší náklady na nasazení <li> Přenositelnost aplikace a závislosti <li> Flexibilita hostitele cílů: PaaS přístupy nebo IaaS | <li> Architekti pro cloud, získáte nejlepší výhod z cloudu, ale je potřeba nový kód <li> Přístupy Mikroslužeb nativní cloudu <li> Moderní kritické aplikace cloudu odolné škálovatelný <li> Plně spravované služby <li> Optimalizovaná pro škálování <li> Optimalizovaná pro autonomní flexibility subsystémem <li> Založený na nasazení a DevOps |
| **Problémy** |
| <li> Menší hodnota cloudu, než posunutí v provozní výdaje a zavírání datová centra <li> Málo spravované: žádné operačního systému nebo middleware opravy; může použít řešení infrastruktury, jako je Terraform, Spinnaker nebo Puppet | <li> Containerizing je další krok v křivku pro vývojáře a IT oddělení <li> DevOps a CI/CD kanálů je obvykle 'musí"pro tuto metodu. Není-li aktuálně nachází v jazykovou verzi organizace, může to být další výzvy| <li> Vyžaduje rearchitecture pro nativní cloudových aplikací a architektury mikroslužby a obvykle vyžaduje významné kódu refaktoringu nebo přepisování při modernizace (vyšší čas a finanční) <li> DevOps a CI/CD kanálů je obvykle 'musí"pro tuto metodu. Není-li aktuálně nachází v jazykovou verzi organizace, může to být další výzvy|
> **Tabulka 1-1.** Výhody a problémy modernizace cest pro existující aplikace .NET a služby

### <a name="key-technologies-and-architectures-by-maturity-level"></a>Klíčové technologie a architektury podle vyspělosti

Aplikace rozhraní .NET framework s rozhraním .NET Framework verze 1.0, která byla vydaná v pozdní 2001 prvním spuštění. Potom společností přesunout směrem novější verze (například 2.0, 3.5 a rozhraní .NET 4.x). Většina těchto aplikací spuštěna v systému Windows Server a Internet Information Server (IIS) a používá relační databázi, jako je SQL Server, Oracle, MySQL nebo jiné relační.

Většina existující aplikace .NET může být v současné době založen na rozhraní .NET Framework 4.x, nebo dokonce i v rozhraní .NET Framework 3.5 a pomocí webového rozhraní jako ASP.NET MVC, webových formulářů ASP.NET, rozhraní ASP.NET Web API, Windows Communication Foundation (WCF), funkce SignalR technologie ASP.NET a webové stránky ASP.NET . Tyto navázat, že rozhraní .NET Framework technologie závisí na systému Windows. Tuto závislost je důležité vzít v úvahu, pokud migrujete jednoduše starší verze aplikace a chcete, aby minimální změny k infrastruktuře aplikace.

Obrázek 1 – 2 ukazuje na primární technologie a architektura stylů použitých na všech úrovních vyspělosti tři cloudu:

![Primární technologie pro každý vyspělosti pro modernizace existující .NET webové aplikace](./media/image1-2.png)

> **Obrázek 1 – 2.** Primární technologie pro každý vyspělosti pro modernizace existující .NET webové aplikace

Obrázek 1 – 2 označuje nejběžnějších scénářů, ale mnoho hybridní a smíšený variace je možné, pokud jde o architektuře. Například modely vyspělosti platí nejen monolitický architektur v existující webové aplikace, ale také orientaci na služby, N-vrstvá a dalších odlišností styl architektury. Vyšší fokus nebo procenta v architektura jednoho nebo jiný typ a souvisejících technologiích Určuje celkový vyspělosti aplikací.

Každý vyspělosti v procesu modernizace je přidružen následující klíčové technologie a přístupy:

- **Cloudová infrastruktura připravené** (metody opětovného hostování nebo basic navýšení & posunutí): jako první krok, mnoho organizací má pouze rychle provést strategie migrace na cloud. V takovém případě aplikace jsou opětovné hostování nástroje. Většina opětovného hostování je možné automatizovat pomocí [Azure migrovat](https://aka.ms/azuremigrate), služba, která poskytuje pokyny, přehledy a mechanismy pro potřeby pomoc při migraci na Azure založené na cloudu nástroje, například [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/)a [databáze Azure migrace služby](https://azure.microsoft.com/campaigns/database-migration/). Můžete také nastavit tak opětovného hostování ručně, aby se podrobnosti infrastruktury dozvíte vaše prostředky při přesunutí starší verze aplikace do cloudu. Například můžete přesunout aplikace k virtuálním počítačům v Azure s malým úpravy – pravděpodobně s pouze změny menší konfigurace. Sítě v tomto případě je podobná místní prostředí, zejména v případě, že vytvoříte virtuální sítě v Azure.

- **Optimalizovaných cloudů** (spravované služby a Windows kontejnery): Tento model je o tom, jak několik optimalizací důležité nasazení k získání některé významné výhody z cloudu, aniž byste museli měnit Architektura jádra aplikace. Zde základní krokem je přidání [Windows kontejnery](https://docs.microsoft.com/virtualization/windowscontainers/about/) podporu pro existující aplikace rozhraní .NET Framework. Tento krok důležité (rozdělení do kontejnerů) nevyžaduje vůbec měnil kód, tak, aby celkový úsilí navýšení a shift light. Můžete použít nástroje, například [Image2Docker](https://github.com/docker/communitytools-image2docker-win) nebo Visual Studio, s jeho nástroje pro [Docker](https://www.docker.com/). Visual Studio automaticky zvolí inteligentní výchozí nastavení pro aplikace ASP.NET a bitové kopie systému Windows kontejnery. Tyto nástroje nabízejí smyčku rychlé vnitřní i Rychlá cesta pro získání kontejnerů do Azure. Vaše flexibility je vyšší, pokud nasazujete do několika prostředí. Potom přesunutím do produkčního prostředí, můžete nasadit Windows kontejnery [webové aplikace Azure pro kontejnery](https://azure.microsoft.com/en-us/services/app-service/containers/), [Azure kontejner instancí (ACI) a virtuální počítače Azure se systémem Windows Server 2016 a kontejnerů, pokud dáváte přednost IaaS přístup. Pro trochu složitější více – aplikace typu kontejner, do orchestrators jako [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) nebo [Kubernetes služby Azure (AKS/ACS)](https://azure.microsoft.com/en-us/services/container-service/). Během této počáteční modernizace, můžete také přidat prostředky z cloudu, jako jsou monitorování pomocí nástrojů, například [Azure Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview); CI/CD kanály pro vaše aplikace životních s [Visual Studio Team Services](https://visualstudio.microsoft.com/team-services/); a mnoho více datových prostředků služeb, které jsou dostupné v Azure. Například můžete upravit monolitický webovou aplikaci, která byla původně vyvinuta pomocí tradiční [webových formulářů ASP.NET](https://www.asp.net/web-forms) nebo [ASP.NET MVC](https://www.asp.net/mvc), ale teď můžete nasadit pomocí Windows kontejnery. Při použití Windows kontejnery, by měl taky migrovat data do databáze v [Azure SQL Database spravované Instance](https://docs.microsoft.com/azure/sql-database/), všechny beze změny základní architektury vaší aplikace.

- **Nativní cloudu**: zavedeném, měli zamyslet architektury [cloudu nativní](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) aplikace, pokud cílíte velké a složité aplikace s více nezávislých vývojové týmy pracující na různé mikroslužeb, které je možné vyvinuté a nasadit samostatně. Také kvůli škálovatelnosti granularized a nezávislé na mikroslužby. Tyto architektury přístupy čelí velmi důležité problémy a složité kroky, ale můžete výrazně zjednodušit pomocí cloudových PaaS, a jako orchestrators [Kubernetes služby Azure (AKS/ACS)](https://azure.microsoft.com/en-us/services/container-service/) (spravované Kubernetes), [služba Azure Prostředky infrastruktury, a [Azure Functions](https://azure.microsoft.com/services/functions/) bez serveru přístup. Všechny tyto přístupy (např. mikroslužeb a bez serveru) obvykle vyžadují, abyste architektury pro cloud a zadat nový kód – kódu, který je přizpůsobené pro konkrétní platformy PaaS nebo kód, který zarovnaná s konkrétní architektury, jako je mikroslužeb.

Obrázek 1 – 3 ukazuje interní technologie, můžete použít pro každý vyspělosti:

![Interní technologie pro každé úrovni vyspělosti modernizace](./media/image1-3.png)

> **Obrázek 1 – 3.** Interní technologie pro každé úrovni vyspělosti modernizace

## <a name="lift-and-shift-scenario"></a>Scénář navýšení a posunutí

Pro navýšení a shift migrace Uvědomte si, které vaše aplikace scénáře můžete mnoho různých variant navýšení a shift. Pokud jenom opětovným hostováním vaší aplikace, může být scénáři zobrazený v 1 obrázek – 4, kde se budou virtuální počítače v cloudu pouze pro vaši aplikaci a na serveru databáze používat.

![Příklad Čistý scénář IaaS v cloudu](./media/image1-4.png)

> **Obrázek 1 – 4**. Příklad Čistý scénář IaaS v cloudu

## <a name="modernization-scenarios"></a>Modernizace scénáře

Pro scénáře modernizace může mít čistý aplikace optimalizovaných Cloudů, která používá elementy pouze z této úrovni vyspělosti. Nebo můžete mít aplikace zprostředkující stát s některé prvky z připravené pro infrastruktury cloudu a další elementy z optimalizovaných Cloudů (a "vybrat" nebo smíšeném modelu), jako v obrázku 1-5.

![Příklad "vybrat" scénáři s databází na IaaS, DevOps a rozdělení do kontejnerů prostředky](./media/image1-5.png)

> **Obrázek 1-5.** Příklad "vybrat" scénáři s databází na IaaS, DevOps a rozdělení do kontejnerů prostředky

V dalším kroku jako v ideálním případě pro mnoho existující aplikace rozhraní .NET Framework, které chcete migrovat může migrovat do optimalizovaných Cloudů aplikace, k získání významné výhody z málo práce. Tento přístup také nastaví ke cloudu nativní jako možný budoucí vývoj. Obrázek 1 – 6 ukazuje příklad.

![Příklad scénáře optimalizovaný pro cloudové aplikace, s kontejnery Windows a spravované služby](./media/image1-6.png)

> **Obrázek 1 – 6.** Příklad scénáře optimalizovaný pro cloudové aplikace, s kontejnery Windows a spravované služby

Budete i pokračovat, můžete rozšířit stávající aplikaci optimalizovaných Cloudů přidáním několik mikroslužeb u konkrétních scénářů. To by přesuňte je částečně na úroveň cloudu nativní modelu, který není hlavním účelem přítomen pokyny.


## <a name="what-this-guide-does-not-cover"></a>Co tato příručka nepopisuje

Tento průvodce pokrývá podmnožinu konkrétní ukázkové scénáře, jak je znázorněno na obrázku 1-7. Tato příručka se zaměřuje jenom na scénáře navýšení a shift a nakonec, na modelu optimalizovaných Cloudů. V modelu optimalizovaných Cloudů pomocí systému Windows kontejnery, plus další komponenty, jako jsou monitorování je modernized aplikace rozhraní .NET Framework a CI/CD kanálů. Jednotlivé komponenty, je nezbytné rychlejší nasazení aplikací do cloudu a flexibility.

![Nativní cloudu není součástí této příručky](./media/image1-7.png)

> **Obrázek 1-7.** Nativní cloudu není součástí této příručky

Cílem tohoto průvodce je konkrétní. Zobrazuje cestu, kterou můžete provést při dosažení shift existující aplikace .NET a navýšení bez vynaložit a beze změn kódu. Nakonec, ukazuje, jak chcete-li aplikace optimalizovaných Cloudů.

Tato příručka nepodporuje ukazují, jak vytvořit nativní cloudové aplikace, jako je postup momentální mikroslužeb architektury. Rearchitect aplikace nebo vytvořit zcela nové aplikace, které jsou založeny na mikroslužeb naleznete v tématu elektronická kniha [Mikroslužeb .NET: architektura pro kontejnerové aplikace .NET](https://aka.ms/microservicesebook).

### <a name="additional-resources"></a>Další zdroje

- **Kontejnerizované Docker životního cyklu aplikací s Microsoft platforma a nástroje** (ke stažení elektronická kniha): [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)

- **Rozhraní .NET Mikroslužeb: Architektura pro kontejnerové aplikace .NET** (ke stažení elektronická kniha): [*https://aka.ms/microservicesebook*](https://aka.ms/microservicesebook)

- **Architektury moderních webových aplikací pomocí ASP.NET Core a Azure** (ke stažení elektronická kniha): [*https://aka.ms/webappebook*](https://aka.ms/webappebook)

## <a name="who-should-use-this-guide"></a>Tato příručka, kdo by měl používat

Tato příručka je určen pro vývojáře a řešení architektům, kteří chtějí modernizovat existující webové aplikace ASP.NET nebo služby WCF, které jsou založeny na rozhraní .NET Framework pro vyšší flexibility v přesouvání a uvolněním aplikace.

Také mohou být užitečné tato příručka Pokud jste technické rozhodovací pravomocí, například na enterprise architekt nebo vývoj realizace/ředitel kdo právě chce přehled výhody, které můžete získat pomocí Windows kontejnery a nasazení do cloudu při použití Microsoft Azure.

## <a name="how-to-use-this-guide"></a>Jak používat tato příručka

Tento průvodce řeší "Proč"-Proč můžete chtít modernizovat existující aplikace a určité výhody můžete získat z použití Windows kontejnerů při přesunutí aplikace do cloudu. Obsah v první několik kapitolám Průvodce je určený pro architekty a technické vedoucím pracovníkům, kteří chtějí přehled, ale který nebudete muset zaměřit na implementaci a technické a podrobné informace.

Poslední kapitol tohoto průvodce zavádí více návody, které se zaměřují na konkrétní nasazení scénáře. Tato příručka nabízí kratší verze názorné postupy, zvýrazněte jejich výhody a shrnout scénáře. Úplné návody k podrobnostem podrobnosti o nastavení a implementace a publikují se jako sadu [wiki příspěvcích](https://github.com/dotnet-architecture/eShopModernizing/wiki) ve stejné veřejné [úložiště GitHub](https://github.com/dotnet-architecture/eShopModernizing) tam, kde se nacházejí související ukázkových aplikací (popsané v dalším část). Poslední kapitoly a wiki podrobné návody na Githubu se další zajímavé pro vývojáře a architektům, kteří chtějí a zaměřit se na podrobnosti implementace.

## <a name="sample-apps-for-modernizing-legacy-apps-eshopmodernizing"></a>Ukázková aplikace pro modernizace starší verze aplikace: eShopModernizing

[EShopModernizing](https://github.com/dotnet-architecture/eShopModernizing) úložišti na Githubu nabízí dva ukázkové aplikace, které simulují starší verze monolitický webových aplikací. Je jeden webové aplikace vyvinuté pomocí rozhraní ASP.NET MVC; je druhý webové aplikace vyvinuté pomocí webových formulářů ASP.NET a třetí aplikace je vícevrstvé aplikace s WinForms klienta aplikace na ploše využívání back-end služby WCF. Všechny tyto aplikace jsou založené na tradiční rozhraní .NET Framework. Tyto ukázkové aplikace nepoužívejte .NET Core a ASP.NET Core, jako je mají být existující nebo starší verze rozhraní .NET Framework aplikací mít modernized.

Tyto ukázkové aplikace druhá verze modernized kód, a která jsou přímočará. Nejdůležitější rozdíl mezi verzemi aplikace je, že druhá verze používat Windows kontejnery jako možnost nasazení. Existují také několik doplňky druhé verze, podobně jako úložiště objektů BLOB služby Azure ke správě bitových kopií, Azure Active Directory pro správu zabezpečení a Azure Application Insights pro sledování a auditování aplikace.

## <a name="send-your-feedback"></a>Odešlete svůj názor

Tato příručka byla zapsána do vám pomohou pochopit, možnosti pro zlepšení a modernizace existujících webových aplikací .NET. Průvodce a související ukázkové aplikace se vyvíjejí. Vaše zpětná vazba je Vítejte! Pokud máte komentáře o tom, jak tento průvodce může být užitečnější, pošlete prosím, aby [ dotnet-architecture-ebooks-feedback@service.microsoft.com ](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book).

>[!div class="step-by-step"]
[Next](lift-and-shift-existing-apps-azure-iaas.md)
