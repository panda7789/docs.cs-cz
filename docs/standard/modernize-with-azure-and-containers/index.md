---
title: Modernizovat existující aplikace .NET s cloudu Azure a Windows kontejnery
description: Postup navýšení a posunutí existujících aplikací do cloudu Azure a kontejnery s elektronickou knihu.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: 3109cac1bd64587bb096a057f6f4ae99b055352a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="modernize-existing-net-applications-with-azure-cloud-and-windows-containers-v10"></a>Modernizovat existující aplikace .NET s cloudu Azure a Windows kontejnery (1.0)

![Obrázek titulní](./media/cover.png)

PUBLIKOVÁNO  
Společnosti Microsoft Press a Microsoft DevDiv  
Oddělení společnosti Microsoft Corporation  
One Microsoft Way  
Redmond, Washington 98052-6399  

Copyright © Microsoft Corporation 2017  

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

Pokud se rozhodnete modernizovat webových aplikací a přesuňte je do cloudu, nemáte nutně plně přepracování vaší aplikace. Předělávání architektury aplikace pomocí pokročilé přístup jako mikroslužeb není vždy možnost z důvodu omezení náklady a čas. V závislosti na typu aplikace, předělávání architektury aplikace nemusí být také nutné. K optimalizaci nákladová efektivnost strategie migrace cloudu vaší organizace, je důležité vzít v úvahu požadavky aplikací a potřebám vaší firmy. Budete potřebovat k určení:

- Které aplikace vyžadují transformace nebo předělávání architektury.

- Které aplikace musí být modernized pouze částečně.

- Které aplikace můžete "navýšení a posunutí" přímo do cloudu.

## <a name="about-this-guide"></a>Informace o této příručce

Tato příručka se zaměřuje především na "navýšení a posunutí" scénáře a počáteční modernizace existující webové rozhraní Microsoft .NET Framework nebo aplikace orientované na služby. Navýšení a posunutí je akce přechodu zatížení beze změny kódu a základní Architektura aplikace na novější nebo více moderní prostředí.

Tato příručka popisuje, jak přesunout existující rozhraní .NET Framework – aplikace serveru přímo do cloudu tak, že modernizace určitých oblastí bez předělávání architektury nebo změna kódu celé aplikace.

Tato příručka označuje také výhody přesunutí aplikace do cloudu a částečně modernizace aplikace pomocí konkrétní sadu nové technologie a postupy, jako je Windows kontejnery a orchestrators v Azure.

## <a name="path-to-the-cloud-for-existing-net-applications"></a>Cesta ke cloudu pro existující aplikace .NET

Organizace obvykle vybrat přesunout do cloudu pro flexibility a rychlost, kterou můžete získat pro své aplikace. Nastavením tisíci servery (VM) v cloudu v minutách, ve srovnání s týdnů, obvykle trvá nastavit na místních serverech.

Není k dispozici jeden, univerzálně strategie pro migraci aplikace do cloudu. Strategie správné migrace pro vás bude záviset na potřebám vaší organizace a priority a typ aplikace, ze kterých provádíte migraci. Ne všechny aplikace vlastní investice přechodu na platforma jako služba ([PaaS](https://azure.microsoft.com/overview/what-is-paas/)) modelu nebo vývoj [cloudu nativní](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) aplikačního modelu. V mnoha případech může trvat postupné nebo přírůstkové přístup investovat do přechodu vaše prostředky do cloudu, podle obchodních potřeb.

Pro moderní aplikace se nejlépe dlouhodobé flexibility a hodnotou pro organizaci, může být vhodné Investujete do *optimalizovaných cloudů* a *cloudu nativní* architektury aplikace. Pro aplikace, které jsou existující nebo starší verze prostředky, ale klíč je během jejich přesouvání do cloudu, pokud chcete významné výhody zatěžovat minimální čas a peníze (nemění předělávání architektury nebo kód).

Obrázek 1-1 zobrazuje možné cesty, které můžete provést při přesunutí existující aplikace .NET do cloudu v přírůstkové fáze.

 ![Modernizace cesty pro existující aplikace .NET a služby](./media/image1-1.png)

> **Obrázek 1-1**. Modernizace cesty pro existující aplikace .NET a služby

Má každý přístup migrace různé výhody a důvody pro jejich použití. Můžete zvolit jeden přístup při migrovat aplikace do cloudu, nebo zvolte určité komponenty z více přístupů. Nejsou omezeny na jednoho přístup nebo vyspělosti stavu jednotlivých aplikací. Například běžný postup hybridní by měla mít určité součásti na místě a další součásti, v cloudu.

Na úrovni první dva migrace můžete právě navýšení a posunutí aplikace:

**Úroveň 1: Cloudové infrastruktury připravené**: V tento postup migrace, můžete jednoduše opětovným hostováním nebo přesunout vaší stávající místní aplikace do infrastruktury jako služby ([IaaS](https://azure.microsoft.com/overview/what-is-iaas/)) platformu. Aplikací mít téměř stejný složení jako před, ale nyní je nasadit do virtuálních počítačů v cloudu.

**Úroveň 2: Cloud DevOps-Ready**: na této úrovni až počáteční navýšení a shift a stále bez předělávání architektury nebo změna kódu, můžete získat i další výhody spuštění aplikace v cloudu. Můžete zvýšit flexibility aplikací pro odeslání rychlejší podle upřesnění procesy operací (DevOps) vývoje vaší organizace. Můžete dosáhnout pomocí technologie, jako je Windows kontejnery, která je založena na Docker modul. Kontejnery odebrat třením, která je způsobena závislosti aplikací při nasazení v několika fázích. Kontejnery také používat další spravovanými přes cloud services týkající se dat, monitorování a nepřetržité integrace/průběžné kanály nasazení (CI/CD).

Na třetí úrovni vyspělosti je konečným cílem v cloudu, ale je volitelné pro velký počet aplikací a není hlavním cílem tohoto průvodce:

**Úroveň 3: Optimalizovaných Cloudů**: tuto metodu migrace se obvykle stanovují podle obchodních potřeb a cílů modernizing kritických aplikací. Na této úrovni používáte PaaS služby pro přesun aplikace do PaaS výpočetních platformách. Můžete implementovat [cloudu nativní](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) aplikací a mikroslužeb architektura vyvíjet aplikace s dlouhodobé flexibility a škálování nové limitům. Tento typ modernizace obvykle vyžaduje architektury speciálně pro cloud. Nový kód často musí být napsané, zejména v případě, že můžete přesunout do cloudu nativní aplikaci a na základě mikroslužbu modely. Tento přístup vám může pomoct získat výhody, které je obtížné dosáhnout v prostředí aplikace monolitický a místně.

Tabulka 1-1 popisuje hlavní výhody a důvody pro výběr každý migrace nebo modernizace přístup.

| **Připravené pro infrastruktury cloudu** <br /> *Navýšení a posunutí* | **DevOps připravené cloudu** <br /> *Navýšení a posunutí* | **Optimalizovaných cloudů** *Modernize/refactor/přepisování* |
|---|---|---|
| **Výpočetní cílové aplikace** |
| Aplikace nasazené do virtuálních počítačů v Azure | Kontejnerizované monolitický nebo vícevrstvé aplikace nasazené virtuální počítače, Azure Service Fabric nebo Azure Container Service (Kubernetes) | Kontejnerizované mikroslužeb nebo regulární aplikací založených na PaaS v Azure App Service, Azure Service Fabric, Azure Container Service (Kubernetes) |
| **Cíl dat** |
| SQL nebo jakoukoli relační databázi na virtuálním počítači | Spravované Instance databáze Azure SQL | Databáze Azure SQL, Azure Cosmos DB nebo jiných NoSQL |
| **Výhody**|
| <li>Žádný kód předělávání architektury, nové <li> Minimálně úsilí pro rychlé migrace <li> Jmenovatel nejmenší společný podporují v Azure <li> Záruky základní dostupnosti <li> Po přechodu do cloudu, je snazší i další modernizovat | <li>Žádný kód předělávání architektury, nové <li> Kontejnery nabízejí malé přírůstkové úsilí přes virtuální počítače <li> Vylepšené nasazení a flexibility DevOps uvolnit z důvodu kontejnery <li> Vyšší hustotu a nižší náklady na nasazení <li> Přenositelnost aplikace a závislosti <li> S Azure Container Service (nebo Kubernetes) a Azure Service Fabric, poskytuje vysokou dostupnost a orchestration <li> Opravy uzly nebo virtuálních počítačů v Service Fabric <li> Flexibilita hostitele cílů: sadách škálování virtuální počítač nebo virtuální počítače Azure, Azure Container Service (nebo Kubernetes), Service Fabric a budoucí kontejneru na základě volby | <li>Architekti pro cloud, refactor, nový kód pro potřeby <li> Přístupy Mikroslužeb nativní cloudu <li> Nové webové aplikace, monolitický, N-vrstvá, cloudu odolné a optimalizovaných cloudů <li> Plně spravované služby <li> Automatické opravy <li> Optimalizovaná pro škálování <li> Optimalizovaná pro autonomní flexibility subsystémem <li> Založený na nasazení a DevOps <li> Rozšířené DevOps, jako je sloty a strategie nasazení <li> PaaS a orchestrator cíle: Azure App Service, Azure Container Service (nebo Kubernetes), Azure Service Fabric a budoucí PaaS na základě kontejneru |
| **Problémy** |
| <li> Menší hodnota cloudu, než posunutí v provozní výdaje a zavírání datová centra <li> Velmi málo spravované: Ne OS nebo middleware opravy; řešení může infrastruktury, jako je Terraform, Spinnaker nebo Puppet | <li> Containerizing je vyžadovat další krok v křivku neměnné | <li> Může vyžadovat významné kódu refaktoringu nebo přepisování (vyšší čas a finanční) |
> **Tabulka 1-1.** Výhody a problémy modernizace cest pro existující aplikace .NET a služby

### <a name="key-technologies-and-architectures-by-maturity-level"></a>Klíčové technologie a architektury podle vyspělosti

Aplikace rozhraní .NET framework s rozhraním .NET Framework verze 1.0, která byla vydaná v pozdní 2001 prvním spuštění. Potom společností přesunout směrem novější verze (například 2.0, 3.5 a rozhraní .NET 4.x). Většina těchto aplikací spuštěna v systému Windows Server a Internet Information Server (IIS) a používá relační databázi, jako je SQL Server, Oracle, MySQL nebo jiné relační.

Většina existující aplikace .NET může být v současné době založen na rozhraní .NET Framework 4.x, nebo dokonce i v rozhraní .NET Framework 3.5 a pomocí webového rozhraní jako ASP.NET MVC, webových formulářů ASP.NET, rozhraní ASP.NET Web API, Windows Communication Foundation (WCF), funkce SignalR technologie ASP.NET a webové stránky ASP.NET . Tyto navázat, že rozhraní .NET Framework technologie závisí na systému Windows. Tuto závislost je důležité vzít v úvahu, pokud migrujete jednoduše starší verze aplikace a chcete, aby minimální změny k infrastruktuře aplikace.

Obrázek 1 – 2 ukazuje na primární technologie a architektura stylů použitých na všech úrovních vyspělosti tři cloudu:

![Primární technologie pro každý vyspělosti pro modernizace existující .NET webové aplikace](./media/image1-2.png)

> **Obrázek 1 – 2.** Primární technologie pro každý vyspělosti pro modernizace existující .NET webové aplikace

Obrázek 1 – 2 označuje nejběžnějších scénářů, ale mnoho hybridní a smíšený variace je možné, pokud jde o architektuře. Například modely vyspělosti platí nejen monolitický architektur v existující webové aplikace, ale také orientaci na služby, N-vrstvá a dalších odlišností styl architektury.

Každý vyspělosti v procesu modernizace je přidružen následující klíčové technologie a přístupy:

- **Cloudová infrastruktura připravené** (metody opětovného hostování nebo basic navýšení a posunutí): jako první krok, mnoho organizací má pouze rychle provést strategie migrace na cloud. V takovém případě aplikace jsou jednoduše opětovné hostování nástroje. Většina opětovného hostování je možné automatizovat pomocí [Azure migrovat](https://aka.ms/azuremigrate), služba, která poskytuje pokyny, přehledy a mechanismy pro potřeby pomoc při migraci na Azure založené na cloudu nástroje, například [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/)a [databáze Azure migrace služby](https://azure.microsoft.com/campaigns/database-migration/). Můžete také nastavit tak opětovného hostování ručně, aby se podrobnosti infrastruktury dozvíte vaše prostředky při přesunutí starší verze aplikace do cloudu. Například můžete přesunout aplikace k virtuálním počítačům v Azure s velmi málo úpravy – pravděpodobně s pouze změny menší konfigurace. Sítě v tomto případě je podobná místní prostředí, zejména v případě, že vytvoříte virtuální sítě v Azure.

- **Cloud DevOps připravené** (vylepšené navýšení a shift): Tento model je o tom, jak několik optimalizací důležité nasazení k získání některé významné výhody z cloudu, aniž byste museli měnit Architektura jádra aplikace. Zde základní krokem je přidání [Windows kontejnery](https://docs.microsoft.com/virtualization/windowscontainers/about/) podporu pro existující aplikace rozhraní .NET Framework. Tento krok důležité (rozdělení do kontejnerů) nevyžaduje vůbec měnil kód, takže celkový navýšení a shift úsilí je velmi nízké. Můžete použít nástroje, například [Image2Docker](https://github.com/docker/communitytools-image2docker-win) nebo Visual Studio, s jeho nástroje pro [Docker](https://www.docker.com/). Visual Studio automaticky zvolí inteligentní výchozí nastavení pro aplikace ASP.NET a bitové kopie systému Windows kontejnery. Tyto nástroje nabízejí smyčku rychlé vnitřní i Rychlá cesta pro získání kontejnerů do Azure. Vaše flexibility je vyšší, pokud nasazujete do několika prostředí. Potom přesunutím do produkčního prostředí, můžete nasadit kontejnerů Windows orchestrators jako [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) nebo [Azure Container Service](https://azure.microsoft.com/services/container-service/) (Kubernetes, DC/OS nebo Swarmu). Během této počáteční modernizace, můžete také přidat prostředky z cloudu, jako jsou monitorování pomocí nástrojů, například [Azure Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview); CI/CD kanály pro vaše aplikace životních s [Visual Studio Team Services](https://www.visualstudio.com/team-services/); a mnoho více datových prostředků služeb, které jsou dostupné v Azure. Například můžete upravit monolitický webovou aplikaci, která byla původně vyvinuta pomocí tradiční [webových formulářů ASP.NET](https://www.asp.net/web-forms) nebo [ASP.NET MVC](https://www.asp.net/mvc), ale teď můžete nasadit pomocí Windows kontejnery. Při použití Windows kontejnery, by měl taky migrovat data do databáze v [Azure SQL Database spravované Instance](https://docs.microsoft.com/azure/sql-database/), všechny beze změny základní architektury vaší aplikace.

- **Optimalizovaných cloudů**: Jak jsme uvedli, konečným cílem při modernizovat aplikací v cloudu je vytvoření systém na základě PaaS platformách, jako je [Azure App Service](https://azure.microsoft.com/services/app-service/). PaaS platformy zaměřit na moderních webových aplikací a rozšířit vaše aplikace s nových služeb na základě [bez serveru computing](https://azure.microsoft.com/overview/serverless-computing/) a platformách, jako je [Azure Functions](https://azure.microsoft.com/services/functions/). Druhý a pokročilejší scénáře v tomto modelu vyspělosti je o mikroslužeb architektury a [cloudu nativní](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) aplikace, které se obvykle používají orchestrators jako [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) nebo [Azure Container Service](https://azure.microsoft.com/services/container-service/) (Kubernetes, DC/OS nebo Swarmu). Tyto orchestrators jsou vytvářeny speciálně pro mikroslužeb a více kontejneru aplikace. Všechny tyto přístupy (např. mikroslužeb a PaaS) obvykle vyžadují, abyste zápisu kódu kód, který je přizpůsobený specifické platformy PaaS nebo kód, který zarovnaná s konkrétní architektury, jako je mikroslužeb.

Obrázek 1 – 3 ukazuje interní technologie, můžete použít pro každý vyspělosti:

![Interní technologie pro každé úrovni vyspělosti modernizace](./media/image1-3.png)

> **Obrázek 1 – 3.** Interní technologie pro každé úrovni vyspělosti modernizace

## <a name="lift-and-shift-scenarios"></a>Scénáře navýšení a posunutí

Pro navýšení a shift migrace Uvědomte si, které vaše aplikace scénáře můžete mnoho různých variant navýšení a shift. Pokud jenom opětovným hostováním vaší aplikace, může být scénáři zobrazený v 1 obrázek – 4, kde se budou virtuální počítače v cloudu pouze pro vaši aplikaci a na serveru databáze používat.

![Příklad Čistý scénář IaaS v cloudu](./media/image1-4.png)

> **Obrázek 1 – 4**. Příklad Čistý scénář IaaS v cloudu

Klouzavý dopředu, může mít čistý DevOps připravené pro cloudové aplikace, která používá elementy pouze z této úrovni vyspělosti. Nebo můžete mít aplikace zprostředkující stát s některé prvky z připravené pro infrastruktury cloudu a další elementy z Cloud DevOps-Ready (a "vybrat" nebo smíšeném modelu), jako v obrázku 1-5.

![Příklad "vybrat" scénáři s databází na IaaS, DevOps a rozdělení do kontejnerů prostředky](./media/image1-5.png)

> **Obrázek 1-5.** Příklad "vybrat" scénáři s databází na IaaS, DevOps a rozdělení do kontejnerů prostředky

V dalším kroku jako v ideálním případě pro mnoho existující aplikace rozhraní .NET Framework, které chcete migrovat může migrovat DevOps připravené pro cloudové aplikace, k získání významné výhody z málo práce. Tento přístup také nastaví ke cloudu optimalizace jako možné budoucí krok. Obrázek 1 – 6 ukazuje příklad.

![Ukázkový scénář DevOps připravené pro cloudové aplikace, se Windows kontejnery a spravované služby](./media/image1-6.png)

> **Obrázek 1 – 6.** Ukázkový scénář DevOps připravené pro cloudové aplikace, se Windows kontejnery a spravované služby

Budete i pokračovat, můžete rozšířit stávající aplikaci DevOps Cloud-Ready přidáním několik mikroslužeb u konkrétních scénářů. To by přesunout je částečně na úroveň nativní cloudu v modelu optimalizovaných Cloudů, což není fokus přítomen pokyny.


## <a name="what-this-guide-does-not-cover"></a>Co tato příručka nepopisuje

Tento průvodce pokrývá podmnožinu konkrétní ukázkové scénáře, jak je znázorněno na obrázku 1-7. Tato příručka se zaměřuje jenom na scénáře navýšení a shift a nakonec, na DevOps Cloud-Ready modelu. V modelu DevOps připravené pro cloudové aplikace rozhraní .NET Framework je modernized pomocí Windows kontejnery, plus další komponenty, jako jsou monitorování a CI/CD kanálů. Jednotlivé komponenty, je nezbytné rychlejší nasazení aplikací do cloudu a flexibility.

![Navýšení a shift a počáteční modernizace DevOps Cloud-Ready aplikací](./media/image1-7.png)

> **Obrázek 1-7.** Navýšení a shift a počáteční modernizace DevOps Cloud-Ready aplikací

Cílem tohoto průvodce je konkrétní. Zobrazuje cestu, kterou můžete provést při dosažení shift existující aplikace .NET a navýšení bez předělávání architektury a beze změn kódu. Nakonec ho ukazuje, jak chcete-li aplikace připravené pro DevOps cloudu.

Tato příručka nepodporuje ukazují, jak pracovat s nativní cloudové aplikace, jako je postup momentální mikroslužeb architektury. Přepracování aplikace nebo vytvořit zcela nové aplikace, které jsou založeny na mikroslužeb, najdete v části elektronická kniha [Mikroslužeb .NET: architektura pro kontejnerové aplikace .NET](https://aka.ms/microservicesebook).

### <a name="additional-resources"></a>Další zdroje

- **Kontejnerizované Docker životního cyklu aplikací s Microsoft platforma a nástroje** (ke stažení elektronická kniha): [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)

- **Rozhraní .NET Mikroslužeb: Architektura pro kontejnerové aplikace .NET** (ke stažení elektronická kniha): [*https://aka.ms/microservicesebook*](https://aka.ms/microservicesebook)

- **Architektury moderních webových aplikací pomocí ASP.NET Core a Azure** (ke stažení elektronická kniha): [*https://aka.ms/webappebook*](https://aka.ms/webappebook)

## <a name="who-should-use-this-guide"></a>Tato příručka, kdo by měl používat

Tato příručka je určen pro vývojáře a řešení architektům, kteří chtějí modernizovat existující aplikace ASP.NET, které jsou založeny na rozhraní .NET Framework pro vyšší flexibility v přesouvání a uvolněním aplikace.

Také mohou být užitečné tato příručka Pokud jste technické rozhodovací pravomocí, například na enterprise architekt nebo vývoj realizace/ředitel kdo právě chce přehled výhody, které můžete získat pomocí Windows kontejnery a nasazení do cloudu při použití Microsoft Azure.

## <a name="how-to-use-this-guide"></a>Jak používat tato příručka

Tento průvodce řeší "Proč"-Proč můžete chtít modernizovat existující aplikace a určité výhody můžete získat z použití Windows kontejnerů při přesunutí aplikace do cloudu. Obsah v první několik kapitolám Průvodce je určený pro architekty a technické vedoucím pracovníkům, kteří chtějí přehled, ale který nebudete muset zaměřit na implementaci a technické a podrobné informace.

Poslední kapitol tohoto průvodce zavádí více návody, které se zaměřují na konkrétní nasazení scénáře. Tato příručka nabízí kratší verze názorné postupy, zvýrazněte jejich výhody a shrnout scénáře. Úplné návody k podrobnostem podrobnosti o nastavení a implementace a publikují se jako sadu [wiki příspěvcích](https://github.com/dotnet-architecture/eShopModernizing/wiki) ve stejné veřejné [úložiště GitHub](https://github.com/dotnet-architecture/eShopModernizing) tam, kde se nacházejí související ukázkových aplikací (popsané v dalším část). Poslední kapitoly a wiki podrobné návody na Githubu se další zajímavé pro vývojáře a architektům, kteří chtějí a zaměřit se na podrobnosti implementace.

## <a name="sample-apps-for-modernizing-legacy-apps-eshopmodernizing"></a>Ukázková aplikace pro modernizace starší verze aplikace: eShopModernizing

[EShopModernizing](https://github.com/dotnet-architecture/eShopModernizing) úložišti na Githubu nabízí dva ukázkové aplikace, které simulují starší verze monolitický webových aplikací. Je jeden webové aplikace vyvinuté pomocí rozhraní ASP.NET MVC; je druhý webové aplikace vyvinuté pomocí webových formulářů ASP.NET. Obě webové aplikace jsou založené na tradiční rozhraní .NET Framework. Tyto ukázkové aplikace nepoužívejte .NET Core a ASP.NET Core, jako je mají být existující nebo starší verze rozhraní .NET Framework aplikací mít modernized.

Obě ukázkové aplikace druhá verze modernized kód, a která jsou přímočará. Nejdůležitější rozdíl mezi verzemi aplikace je, že druhá verze používat Windows kontejnery jako možnost nasazení. Existují také několik doplňky druhé verze, podobně jako úložiště objektů BLOB služby Azure ke správě bitových kopií, Azure Active Directory pro správu zabezpečení a Azure Application Insights pro sledování a auditování aplikace.

## <a name="send-your-feedback"></a>Odešlete svůj názor

Tato příručka byla zapsána do vám pomohou pochopit, možnosti pro zlepšení a modernizace existujících webových aplikací .NET. Průvodce a související ukázkové aplikace se vyvíjejí. Vaše zpětná vazba je Vítejte! Pokud máte komentáře o tom, jak tento průvodce může být užitečnější, pošlete prosím, aby [ dotnet-architecture-ebooks-feedback@service.microsoft.com ](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book).

>[!div class="step-by-step"]
[Next](lift-and-shift-existing-apps-azure-iaas.md)
