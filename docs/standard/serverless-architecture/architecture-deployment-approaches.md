---
title: Způsoby nasazení architektury - aplikace bez serveru
description: Tento průvodce různé způsoby podnikové architektury jsou nasazené do cloudu s srovnání IaaS, PaaS, kontejnery a bez serveru.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 6566971d8984ec046b8b5fa2db295c1d48c30b20
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404904"
---
# <a name="architecture-deployment-approaches"></a>Způsoby nasazení architektury

Bez ohledu na architekturu přístup umožňuje navrhovat obchodní aplikace, implementaci a nasazení těchto aplikací se můžou lišit. Podniky hostovat aplikace pro všechno, od fyzického hardwaru a funkce bez serveru.

## <a name="n-tier-applications"></a>N-vrstvé aplikace

[Vzor N-vrstvá architektura](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/n-tier) je vyspělá architektury a jednoduše odkazuje na aplikace, které rozdělují různých logické vrstvy do samostatné fyzické úrovně. N-vrstvou architekturu je fyzická implementace N-vrstvy architektury. Nejběžnější implementace této architektury patří:

* Prezentační vrstva například webové aplikace.
* Rozhraní API nebo data úrovně přístupu, jako je například rozhraní REST API.
* Datová vrstva, jako je SQL database.

![N-vrstvou architekturu](./media/n-tier-architecture.png)

N-vrstvé řešení mají následující vlastnosti:

* Projekty jsou většinou v souladu s úrovní.
* Testování může být dosaženy odlišně podle úrovně.
* Úrovně teď poskytují úrovní abstrakce, je třeba prezentační vrstva obvykle ignorant podrobností implementace v datové vrstvě.
* Obvykle vrstvy pracovat pouze s sousední vrstvy.
* Verze se často spravují v projektu a proto úroveň, úroveň. Jednoduchou změnu rozhraní API může vyžadovat novou verzi sady celý střední vrstvy.

Tento přístup poskytuje několik výhod, včetně:

* Izolace databázi (často front-endu nemá mít přímý přístup do databáze back-endu).
* Opakované použití rozhraní API (například mobilními, desktopovými a webovými klienty aplikace můžete všechny opakované použití stejných rozhraní API).
* Možnost pro horizontální navýšení kapacity vrstvy nezávisle na sobě navzájem.
* Refaktoring izolace: jedna vrstva může být refaktorovány bez dopadu na jiných úrovních.

## <a name="on-premises-and-infrastructure-as-a-service-iaas"></a>On-premises a infrastruktura jako služba (IaaS)

Tradiční přístup k hostování aplikací vyžaduje nákup hardwaru a správa všechny instalace softwaru, včetně operačního systému. Původně to týká nákladných datových centrech a fyzického hardwaru. Řada výzvy související s provozováním fyzického hardwaru, včetně:

* Nemusíte kupovat nadbytečné pro "každý případ" nebo ve špičce poptávky scénáře.
* Zabezpečení fyzický přístup k hardwaru.
* Odpovědnost za selhání hardwaru (jako je například selhání disku).
* Chlazení.
* Konfigurace směrovače a nástroje pro vyrovnávání zatížení.
* Redundantní napájení.
* Zabezpečení přístupu k softwaru.

![Přístup IaaS](./media/iaas-approach.png)

Virtualizace hardwaru, přes "virtuální počítače" umožňuje infrastruktury jako služby (IaaS). Hostitelské počítače dělí efektivně k poskytnutí prostředků pro instance s přidělením pro své vlastní paměti, procesoru a úložiště. Tým zřídí nezbytné virtuální počítače a nakonfiguruje přidružené sítě a přístup k úložišti.

Další informace najdete v tématu [virtuálního počítače referenční architekturu N-vrstvé](https://docs.microsoft.com/azure/architecture/reference-architectures/virtual-machines-windows/n-tier).

I když virtualizace a infrastruktura jako služba (IaaS) adres mnoho obavy, ponechá stále mnoho odpovědnosti v rámci infrastruktury. Tým udržuje verze operačního systému, platí oprav zabezpečení a nainstaluje závislostí třetích stran na cílových počítačích. Aplikace často chovat jinak na počítačích produkčního prostředí v porovnání s testovacím prostředí. Vzniku kvůli verze různých závislostí a/nebo úrovní skladová položka operačního systému. Přestože řada organizací nasadit N-vrstvé aplikace na tyto cíle, mnoho společností těžit z výhod nasazení další nativní cloudový model s například [platforma jako služba](#platform-as-a-service-paas). Architektury s využitím mikroslužeb je složitější z důvodu požadavků na pro horizontální navýšení kapacity pro elasticitu a odolnost proti chybám.

Další informace najdete v tématu [virtuálních počítačů](https://docs.microsoft.com/azure/virtual-machines/).

## <a name="platform-as-a-service-paas"></a>Platforma jako služba (PaaS)

Platforma jako služba (PaaS) nabízí nakonfigurované řešení, která vývojářům můžete připojit přímo. PaaS je jiný termín pro spravované hostování. Eliminuje nutnost spravovat základní operační systém, opravy zabezpečení a v mnoha případech případných závislostí třetích stran. Platformy příklady webových aplikací, databází, a mobilních back-endů.

PaaS řeší problémy, které jsou společné pro IaaS. PaaS umožňuje vývojářům soustředit se na kód nebo databázovém schématu místo jak se nasadí. Výhody PaaS patří:

* Platby jenom za použití modelů, které funkce odstraňují režii z investic do nečinnosti počítače.
* Přímé nasazení a vylepšení DevOps, průběžné integrace (CI) a průběžné doručování (CD) kanálů.
* Automatické upgrady, aktualizace a opravy zabezpečení.
* Tlačítka pro horizontální navýšení kapacity a škálování nahoru (elastické škálování).

Hlavní nevýhodou PaaS tradičně bylo fixaci dodavatele. Někteří poskytovatelé PaaS třeba jenom podporu technologie ASP.NET, Node.js, nebo jiné konkrétní jazyky a platformy. Produkty, jako je Azure App Service se vyvinula tak řešit více platforem a podpory různých jazyků a rozhraní pro hostování webových aplikací.

![Platforma jako služba architektury](./media/paas-architecture.png)

## <a name="software-as-a-service-saas"></a>Software jako služba (SaaS)

Software jako služba nebo platformám SaaS je centrálně prostředí a k dispozici bez místní instalace nebo zřizování. SaaS často je umístěn nad PaaS jako platforma pro nasazení softwaru. SaaS poskytuje služby pro spouštění a spojte se s existující software. SaaS je často odvětví a vertikální konkrétní. SaaS je často licenci a obvykle poskytuje model klient/server. Většina moderních nabídky SaaS pomocí webové aplikace pro klienta. Společnosti obvykle považovat za obchodních řešení, které licence nabídky SaaS. Často není implementovaný jako architektura posouzení pro zajištění škálovatelnosti a udržovatelnosti aplikace. Většina řešení SaaS jsou ve skutečnosti založená na IaaS, PaaS a/nebo back-EndY bez serveru.

Další informace o SaaS prostřednictvím [ukázkovou aplikaci](https://docs.microsoft.com/azure/sql-database/saas-tenancy-welcome-wingtip-tickets-app).

## <a name="containers-and-functions-as-a-service-faas"></a>Kontejnery a funguje jako služba (FaaS)

Kontejnery jsou zajímavé řešení, které umožňuje výhody PaaS jako bez režie IaaS. Kontejner je v podstatě modul runtime, který obsahuje nezbytné součásti potřebné ke spuštění aplikace s jedinečnou. Jádra nebo základní součástí hostitelského operačního systému a služeb, jako je úložiště jsou sdíleny napříč hostiteli. Sdílené jádra umožňuje kontejnery být jednoduché (některé jsou pouhou MB. velikost, ve srovnání s velikost GB typické virtuálních počítačů). S hostiteli už běží kontejnery lze spustit rychle, usnadnění vysokou dostupnost. Schopnost rychle zprovozněte kontejnery také poskytuje další vrstvy odolnosti proti chybám. Docker je jedním z další oblíbené implementace kontejnery.

Výhody kontejnerů patří:

* Odlehčená a přenosná
* Samostatná proto není potřeba nainstalovat závislosti
* A nabízejí konzistentní prostředí bez ohledu na hostiteli (spouští na přenosný počítač přesně stejné jako na serveru cloud)
* Můžete rychle zřídit pro horizontální navýšení kapacity
* Můžete rychle restartovat obnovení po selhání

Kontejner spustí na hostiteli (, pak může běžet na holé počítače počítač nebo virtuální počítač). Na jednom hostiteli může spustit více instancí stejné kontejnery nebo kontejnerů. True převzetí služeb při selhání a odolnost proti chybám musí být kontejnery škálovat napříč hostitele.

Další informace o kontejnerech Dockeru najdete v tématu [co je Docker](../microservices-architecture/container-docker-introduction/docker-defined.md)?

Správa kontejnerů napříč hostiteli obvykle vyžaduje nástroj Orchestrace, jako je třeba Kubernetes. Konfigurace a Správa řešení Orchestrace může přidat další režijní náklady a složitost do projektů. Naštěstí mnoho poskytovatelů cloudových služeb poskytují orchestračních službách prostřednictvím řešení PaaS, aby se zjednodušila Správa kontejnerů.

Následující obrázek ukazuje příklad instalace Kubernetes. Uzly v instalaci řešení škálování na více systémů a převzetí služeb při selhání. Spuštění Docker instancí kontejneru, který spravuje hlavní server. *Kubelet* je klient, který předává příkazy z Kubernetes k Dockeru.

![Kubernetes](./media/kubernetes-example.png)

Další informace o orchestraci najdete v tématu [Kubernetes v Azure](https://docs.microsoft.com/azure/aks/intro-kubernetes).

Funkce jako služba (FaaS) je služba specializované kontejneru, který je podobný bez serveru. Konkrétní implementaci FaaS, volá [OpenFaaS](https://github.com/openfaas/faas), je umístěn nad kontejnerů a poskytuje funkce bez serveru. OpenFaaS poskytuje šablony, které všechny potřebné ke spuštění část kódu kontejneru závislosti balíčku. Použití šablon zjednodušuje proces nasazení kódu jako funkční jednotku. OpenFaaS, zaměřuje architektury, které už zahrnují kontejnerů a orchestrátorů, protože ho můžete použít stávající infrastruktury. I když nabízí funkce bez serveru, konkrétně vyžaduje, abyste pomocí Dockeru a produktu orchestrator.

## <a name="serverless"></a>Bez serveru

Využijte architekturu bez serveru poskytuje jasné oddělení mezi kódem a jeho hostitelské prostředí. Implementovat kód v *funkce* , která je vyvolána *aktivační událost*. Po ukončení této funkce může být uvolněna všechny potřebné prostředky. Aktivační událost může být ruční, vypršel časový limit procesu, požadavek HTTP nebo načtení souboru. Výsledkem triggeru je provádění kódu. I když platforem bez serveru liší, většina poskytují přístup k předem definovaných rozhraní API a vazby zjednoduší vám tak úlohy, jako je například zápis do databáze nebo jejich zařazování do fronty výsledky.

Bez serveru je architekturu, která se spoléhá na abstrahovat okamžitě hostitelské prostředí a zaměřte se na kód. To můžete představit jako *méně server*.

Řešení kontejneru poskytují vývojáři existující vytvářet skripty pro publikování kódu bez serveru připravené pro obrázky. V jiných implementacích pomocí stávajících řešení PaaS poskytuje škálovatelnou architekturu.

Abstrakce znamená, že tým DevOps nebude muset zřizovat nebo spravovat servery ani konkrétní kontejnery. Hostitelé kódu platformy bez serveru, ať už jako skript nebo zabalené spustitelné soubory vytvořené pomocí související sady SDK a přiděluje prostředky potřebné pro kód škálování.

Na následujícím obrázku diagramy čtyřem komponentám bez serveru. Požadavek HTTP způsobí, že spuštění kódu rozhraní API Checkout. Rozhraní API pro rezervaci vloží kód do databáze a vložit aktivují několik funkcí a provádět úkoly, jako je výpočetní úlohy a splnění pořadí se spustí.

![Provádění bez serveru](./media/serverless-implementation.png)

Výhody bez serveru patří:

* **Chcete-li s vysokou hustotou.** Velký počet instancí stejného kódu bez serveru můžete spustit na stejném hostiteli ve srovnání s kontejnerů nebo virtuálních počítačů. Instance škálování na více hostitelích horizontální navýšení kapacity a odolnosti proti chybám.
* **Fakturace Micro**. Nejvíce bez serveru vyúčtování poskytovatelé podle provádění bez serveru, umožní to snížit obrovské náklady v některých scénářích.
* **Rychlé škálování**. Bez serveru můžete škálovat tak, aby odpovídaly úlohy automaticky a rychle.
* **Rychlejší uvedení na trh** vývojářům soustředit se na kód a nasadit přímo do platformy bez serveru. Komponenty mohou být vydány nezávisle na sobě.

Bez serveru je popsána nejčastěji v kontextu výpočetního výkonu, ale můžete také použít pro data. Například [Azure SQL](https://docs.microsoft.com/azure/sql-database) a [Cosmos DB](https://docs.microsoft.com/azure/cosmos-db) umožňují cloudových databází, které nevyžadují lze konfigurovat počítače hostitele nebo clustery. Tato příručka se zaměřuje na výpočetní prostředí.

## <a name="summary"></a>Souhrn

Není široké spektrum dostupné možnosti pro architekturu, včetně s hybridním přístupem. Bez serveru zjednodušuje přístup, správy a náklady na aplikaci funkcí za cenu ovládacího prvku a přenositelnost. Řada platforem bez serveru ale vystavit konfigurace pomoci optimalizovat řešení. Programování osvědčených postupů může také vést k větší přenositelnost kódu a méně fixaci platformy bez serveru. Následující tabulka ukazuje architekturu přístupy vedle sebe. Zvolte možnost bez serveru, na základě škálovací potřeby, určuje, jestli chcete spravovat modul runtime a jak dobře vaše úlohy lze rozdělit na malé komponenty. Dozvíte se o potenciálních problémů spojených s architekturou bez serveru a jiné body rozhodnutí v následující kapitole.

|         |IaaS     |PaaS     |Kontejner|Bez serveru|
|---------|---------|---------|---------|----------|
|**Škálování**|VIRTUÁLNÍ POČÍTAČ       |instance |Aplikace      |Funkce  |
|**Přehledů**|Hardware|Platforma|Operační systém hostitele|Modul runtime   |
|**Jednotka** |VIRTUÁLNÍ POČÍTAČ       |Projekt  |Image    |Kód      |
|**Doba platnosti**|Měsíců|Dnů, měsíců|Minut po dny|Počet milisekund minut|
|**Odpovědnosti**|Aplikace, závislostí, modul runtime a operačního systému|Aplikace a závislosti|Aplikace, závislostí a modulu runtime|Funkce

* **Škálování** odkazuje na jednotku, která slouží ke škálování aplikace
* **Abstrahuje** odkazuje na vrstvu, která je abstrahovaný implementace
* **Jednotka** odkazuje na obor co je nasazen
* **Doba života** odkazuje na typické prostředí runtime konkrétní instance
* **Odpovědnosti** odkazuje na režie potřebná k vytvoření, nasazení a údržbě aplikace

Následující kapitoly zaměřit se na architektury bez serveru, případy použití a vzory návrhu.

## <a name="recommended-resources"></a>Doporučené studijní materiály

* [Průvodce architekturou aplikací Azure](https://docs.microsoft.com/azure/architecture/guide/)
* [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db)
* [Azure SQL](https://docs.microsoft.com/azure/sql-database)
* [Vzor N-vrstvou architekturu](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/n-tier)
* [Kubernetes v Azure](https://docs.microsoft.com/azure/aks/intro-kubernetes)
* [Mikroslužby](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)
* [Referenční architekturu N-vrstvou virtuálního počítače](https://docs.microsoft.com/azure/architecture/reference-architectures/virtual-machines-windows/n-tier)
* [Virtuální počítače](https://docs.microsoft.com/azure/virtual-machines/)
* [Co je Docker?](../microservices-architecture/container-docker-introduction/docker-defined.md)
* [Aplikace Wingtip Tickets SaaS](https://docs.microsoft.com/azure/sql-database/saas-tenancy-welcome-wingtip-tickets-app)

>[!div class="step-by-step"]
[Předchozí](architecture-approaches.md)
[další](serverless-architecture.md)