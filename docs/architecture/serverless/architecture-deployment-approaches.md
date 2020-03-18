---
title: Přístupy k nasazení architektury – aplikace bez serveru
description: Průvodce různými způsoby nasazení podnikových architektur do cloudu, s porovnáním mezi IaaS, PaaS, kontejnery a bez serveru.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: c745a4eb1c6f4a00bf139100b02f31cf3327d01e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522724"
---
# <a name="architecture-deployment-approaches"></a>Přístupy k nasazení architektury

Bez ohledu na přístup architektury používaný k návrhu obchodní aplikace se může implementace nebo nasazení těchto aplikací lišit. Firmy hostují aplikace na vše od fyzického hardwaru až po funkce bez serveru.

## <a name="n-tier-applications"></a>N-vrstvé aplikace

[Vzor n-vrstvé architektury](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/n-tier) je vyspělá architektura a jednoduše odkazuje na aplikace, které oddělují různé logické vrstvy do samostatných fyzických vrstev. N-vrstvá architektura je fyzická implementace nvrstvé architektury. Nejběžnější implementace této architektury zahrnuje:

- Prezentační vrstva, například webová aplikace.
- Úroveň přístupu k rozhraní API nebo datům, jako je například rozhraní REST API.
- Datová vrstva, jako je například databáze SQL.

![Architektura n-vrstvé](./media/n-tier-architecture.png)

N-vrstvá řešení mají následující charakteristiky:

- Projekty jsou obvykle zarovnány s úrovněmi.
- Testování může být přistupovat odlišně podle úrovně.
- Vrstvy poskytují vrstvy abstrakce, například prezentační vrstva je obvykle neznalý podrobnosti implementace datové vrstvy.
- Vrstvy obvykle interagují pouze s přilehlými vrstvami.
- Verze jsou často spravovány na úrovni projektu, a proto úroveň, úroveň. Jednoduchá změna rozhraní API může vyžadovat novou verzi celé střední vrstvy.

Tento přístup poskytuje několik výhod, včetně:

- Izolace databáze (často front-end nemá přímý přístup k back-endu databáze).
- Opakované použití rozhraní API (například klienti mobilních zařízení, stolních počítačů a webových aplikací mohou znovu použít stejná rozhraní API).
- Schopnost škálovat úrovně nezávisle na sobě.
- Refaktoring izolace: jedna úroveň může být refaktorován bez dopadu na jiné vrstvy.

## <a name="on-premises-and-infrastructure-as-a-service-iaas"></a>Místní a infrastruktura jako služba (IaaS)

Tradiční přístup k hostování aplikací vyžaduje nákup hardwaru a správu všech softwarových instalací, včetně operačního systému. Původně se jednalo o drahá datová centra a fyzický hardware. Výzvy, které přicházejí s provozem fyzického hardwaru, je mnoho, včetně:

- Potřeba koupit přebytek pro "jen v případě" nebo špičkové poptávky scénáře.
- Zabezpečení fyzického přístupu k hardwaru.
- Odpovědnost za selhání hardwaru (například selhání disku).
- Chlazení.
- Konfigurace směrovačů a prokladů zatížení.
- Redundance napájení.
- Zabezpečení přístupu k softwaru.

![Přístup IaaS](./media/iaas-approach.png)

Virtualizace hardwaru prostřednictvím "virtuálních počítačů" umožňuje infrastrukturu jako službu (IaaS). Hostitelské počítače jsou efektivně rozděleny do oddílů, aby poskytovaly prostředky instancím s přidělením pro vlastní paměť, procesor a úložiště. Tým zřídí potřebné virtuální počítače a nakonfiguruje přidružené sítě a přístup k úložišti.

Další informace naleznete v tématu [referenční architektura N-tier virtuálního počítače](https://docs.microsoft.com/azure/architecture/reference-architectures/virtual-machines-windows/n-tier).

Přestože virtualizace a infrastruktura jako služba (IaaS) řeší mnoho problémů, stále ponechává velkou odpovědnost v rukou týmu infrastruktury. Tým udržuje verze operačního systému, používá opravy zabezpečení a instaluje závislosti třetích stran na cílových počítačích. Aplikace se na výrobních počítačích často chovají jinak než testovací prostředí. Problémy vznikají z důvodu různých verzí závislostí nebo úrovně skladové položky operačního systému. Přestože mnoho organizací nasadit n-vrstvé aplikace na tyto cíle, mnoho společností těžit z nasazení do více cloudnativní model, jako je [platforma jako služba](#platform-as-a-service-paas). Architektury s mikroslužeb jsou náročnější z důvodu požadavků na horizontální navýšení kapacity pro pružnost a odolnost proti chybám.

Další informace naleznete v tématu [virtuální počítače](https://docs.microsoft.com/azure/virtual-machines/).

## <a name="platform-as-a-service-paas"></a>Platforma jako služba (PaaS)

Platforma jako služba (PaaS) nabízí nakonfigurovaná řešení, která mohou vývojáři připojit přímo. PaaS je další termín pro spravovaný hosting. Eliminuje potřebu spravovat základní operační systém, opravy zabezpečení a v mnoha případech všechny závislosti třetích stran. Příklady platforem zahrnují webové aplikace, databáze a mobilní back-endy.

PaaS řeší problémy společné IaaS. PaaS umožňuje vývojáři zaměřit se na kód nebo schéma databáze, spíše než jak se nasadí. Výhody PaaS zahrnují:

- Plaťte za použití modelů, které eliminují režii investování do nečinných strojů.
- Přímé nasazení a vylepšené kanály DevOps, průběžnou integraci (CI) a průběžné doručování (CD).
- Automatické upgrady, aktualizace a opravy zabezpečení.
- Tlačítko se škáluje a zvětšuje (elastická stupnice).

Hlavní nevýhodou PaaS tradičně byl dodavatel lock-in. Například někteří poskytovatelé PaaS podporují pouze ASP.NET, Node.js nebo jiné konkrétní jazyky a platformy. Produkty, jako je Azure App Service, se vyvinuly tak, aby řešily různé platformy a podporovaly různé jazyky a architektury pro hostování webových aplikací.

![Platforma jako architektura služeb](./media/paas-architecture.png)

## <a name="software-as-a-service-saas"></a>Software jako služba (SaaS)

Software jako služba nebo SaaS je centrálně hostovaný a dostupný bez místní instalace nebo zřizování. SaaS je často hostován na vrcholu PaaS jako platforma pro nasazení softwaru. SaaS poskytuje služby pro spuštění a připojení ke stávajícímu softwaru. SaaS je často průmysla a vertikální specifické. SaaS je často licencován a obvykle poskytuje model klient/server. Většina moderních nabídek SaaS používá pro klienta webové aplikace. Společnosti obvykle považují SaaS za obchodní řešení pro nabídky licencí. Není často implementována jako ohleduna architekturu pro škálovatelnost a udržovatelnost aplikace. Většina řešení SaaS je postavena na back-endech IaaS, PaaS a/nebo bez serveru.

Další informace o SaaS prostřednictvím [ukázkové aplikace](https://docs.microsoft.com/azure/sql-database/saas-tenancy-welcome-wingtip-tickets-app).

## <a name="containers-and-functions-as-a-service-faas"></a>Kontejnery a funkce jako služba (FaaS)

Kontejnery jsou zajímavé řešení, které umožňuje výhody podobné PaaS bez režie IaaS. Kontejner je v podstatě runtime, který obsahuje holé základy potřebné ke spuštění jedinečné aplikace. Jádro nebo základní část hostitelského operačního systému a služby, jako je úložiště, jsou sdíleny mezi hostiteli. Sdílené jádro umožňuje, aby byly kontejnery zjednodušené (některé jsou pouze megabajty ve velikosti, ve srovnání s velikostí gigabajtu typických virtuálních počítačů). S hostiteli již spuštěné, kontejnery lze spustit rychle, což usnadňuje vysokou dostupnost. Možnost rychle spárovat kontejnery také poskytuje další vrstvy odolnosti. Docker je jednou z nejoblíbenějších implementací kontejnerů.

Mezi výhody kontejnerů patří:

- Lehký a přenosný
- Samostatné, takže není třeba instalovat závislosti
- Poskytněte konzistentní prostředí bez ohledu na hostitele (běží přesně stejně na přenosném počítači jako na cloudovém serveru)
- Lze rychle zřídit pro horizontální navýšení kapacity
- Lze restartovat rychle zotavit se z poruchy

Kontejner běží na hostiteli kontejneru (to zase může běžet na holé matné počítače nebo virtuálního počítače). Více kontejnerů nebo instancí stejné kontejnery může běžet na jednom hostiteli. Pro skutečné převzetí služeb při selhání a odolnost proti chybám musí být kontejnery škálovat napříč hostiteli.

Další informace o kontejnerech Dockeru najdete v tématu [Co je Docker](../microservices/container-docker-introduction/docker-defined.md).

Správa kontejnerů mezi hostiteli obvykle vyžaduje nástroj orchestrace, jako je Například Kubernetes. Konfigurace a správa řešení orchestrace může přidat další režii a složitost projektů. Naštěstí mnoho poskytovatelů cloudu poskytuje služby orchestrace prostřednictvím řešení PaaS pro zjednodušení správy kontejnerů.

Následující obrázek znázorňuje příklad instalace Kubernetes. Uzly v instalační adrese horizontální navýšení kapacity a převzetí služeb při selhání. Spouštějí instance kontejnerů Dockeru, které jsou spravovány hlavním serverem. *Kubelet* je klient, který předává příkazy z Kubernetes do Dockeru.

![Kubernetes](./media/kubernetes-example.png)

Další informace o orchestraci najdete [v tématu Kubernetes v Azure](https://docs.microsoft.com/azure/aks/intro-kubernetes).

Funkce jako služba (FaaS) je specializovaná kontejnerová služba, která je podobná bezserveru. Konkrétní implementace FaaS, nazvaná [OpenFaaS](https://github.com/openfaas/faas), sedí na kontejnerech a poskytuje možnosti bez serveru. OpenFaaS poskytuje šablony, které balí všechny závislosti kontejneru potřebné ke spuštění části kódu. Použití šablon zjednodušuje proces nasazování kódu jako funkční jednotky. OpenFaaS se zaměřuje na architektury, které již obsahují kontejnery a orchestrátory, protože mohou používat stávající infrastrukturu. Přestože poskytuje funkce bez serveru, konkrétně vyžaduje použití Dockeru a orchestrátoru.

## <a name="serverless"></a>Bez serveru

Architektura bez serveru poskytuje jasné oddělení mezi kódem a jeho hostitelským prostředím. Implementovat kód ve *funkci,* která je vyvolána *aktivační událost*. Po ukončení této funkce mohou být uvolněny všechny potřebné prostředky. Aktivační událost může být ruční, časovaný proces, požadavek HTTP nebo nahrání souboru. Výsledkem aktivační události je spuštění kódu. Přestože se platformy bez serveru liší, většina poskytuje přístup k předdefinovaným api a vazbám pro zjednodušení úkolů, jako je zápis do databáze nebo výsledky fronty.

Bez serveru je architektura, která do značné míry závisí na abstrakce pryč hostitelsképrostředí se zaměřit na kód. To může být myšlenka jako *méně server*.

Kontejnerová řešení poskytují vývojářům existující skripty sestavení pro publikování kódu pro bitové kopie připravené pro server. Jiné implementace používají existující řešení PaaS k zajištění škálovatelné architektury.

Abstrakce znamená, že tým DevOps nemusí zřizovat nebo spravovat servery ani konkrétní kontejnery. Platforma bez serveru hostuje kód, buď jako skript nebo zabalené spustitelné soubory vytvořené pomocí související sady SDK, a přiděluje potřebné prostředky pro škálování kódu.

Následující obrázek diagramy čtyři součásti bez serveru. Požadavek HTTP způsobí spuštění kódu rozhraní API pokladny. Rozhraní API pokladny vloží kód do databáze a vložení spustí několik dalších funkcí, které se spustí, aby bylo možné provádět úlohy, jako je výpočetní úlohy a plnění objednávky.

![Implementace bez serveru](./media/serverless-implementation.png)

Mezi výhody bezserveru patří:

- **Vysoká hustota.** Mnoho instancí stejného kódu bez serveru lze spustit na stejném hostiteli ve srovnání s kontejnery nebo virtuálnípočítače. Instance se škálují napříč více hostiteli, aby se škálování a odolnost proti chybám.
- **Mikrofakturace.** Většina poskytovatelů bez serveru účtuje na základě spuštění bez serveru, což v určitých scénářích umožňuje masivní úspory nákladů.
- **Okamžité měřítko.** Bez serveru lze škálovat tak, aby odpovídaly úlohy automaticky a rychle.
- **Rychlejší uvedení na trh.** Vývojáři se zaměřují na kód a nasazují přímo na platformu bez serveru. Komponenty mohou být uvolněny nezávisle na sobě.

Serverless je nejčastěji diskutována v kontextu výpočetních prostředků, ale může také použít pro data. Například [Azure SQL](https://docs.microsoft.com/azure/sql-database) a [Cosmos DB](https://docs.microsoft.com/azure/cosmos-db) poskytují cloudové databáze, které nevyžadují konfiguraci hostitelských počítačů nebo clusterů. Tato kniha se zaměřuje na výpočetní výkon bez serveru.

## <a name="summary"></a>Souhrn

Existuje široké spektrum dostupných možností pro architekturu, včetně hybridního přístupu. Serverless zjednodušuje přístup, správu a náklady na funkce aplikace na úkor řízení a přenositelnosti. Mnoho platforem bez serveru však zpřístupňuje konfiguraci, která pomáhá doladit řešení. Správné postupy programování může také vést k více přenosný kód a méně serverové platformy lock-in. Následující tabulka ilustruje přístupy architektury vedle sebe. Zvolte bez serveru na základě vašich potřeb škálování, bez ohledu na to, zda chcete spravovat runtime a jak dobře můžete rozdělit úlohy na malé součásti. V další kapitole se dozvíte o potenciálních výzvách s body bez serveru a dalšími rozhodovacími body.

|         |IaaS     |PaaS     |Kontejner|Bez serveru|
|---------|---------|---------|---------|----------|
|**Měřítko**|Virtuální počítač       |Instance |Aplikace      |Funkce  |
|**Abstracts**|Hardware|Platforma|Hostitel operačního|Modul runtime   |
|**Jednotka** |Virtuální počítač       |Project  |Image    |kód      |
|**Životnost**|Měsíce|Dny až měsíce|Minuty až dny|Milisekundy až minuty|
|**Odpovědnost**|Aplikace, závislosti, runtime a operační systém|Aplikace a závislosti|Aplikace, závislosti a runtime|Funkce

- **Měřítko** odkazuje na jednotku, která se používá k škálování aplikace
- **Abstrakty** odkazuje na vrstvu, která je abstraktovaná implementací
- **Jednotka** odkazuje na rozsah toho, co je nasazeno
- **Životnost** odkazuje na typickou dobu běhu konkrétní instance.
- **Odpovědnost** odkazuje na režii na sestavení, nasazení a údržbu aplikace

Další kapitola se zaměří na architekturu bez serveru, případy použití a návrhové vzory.

## <a name="recommended-resources"></a>Doporučené zdroje

- [Průvodce architekturou aplikací Azure](https://docs.microsoft.com/azure/architecture/guide/)
- [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db)
- [Azure SQL](https://docs.microsoft.com/azure/sql-database)
- [Vzor architektury N-Tier](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/n-tier)
- [Kubernetes v Azure](https://docs.microsoft.com/azure/aks/intro-kubernetes)
- [Mikroslužeb](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)
- [Referenční architektura N-tier virtuálního počítače](https://docs.microsoft.com/azure/architecture/reference-architectures/virtual-machines-windows/n-tier)
- [Virtuální počítače](https://docs.microsoft.com/azure/virtual-machines/)
- [Co je Docker?](../microservices/container-docker-introduction/docker-defined.md)
- [Wingtip Vstupenky SaaS aplikace](https://docs.microsoft.com/azure/sql-database/saas-tenancy-welcome-wingtip-tickets-app)

>[!div class="step-by-step"]
>[Předchozí](architecture-approaches.md)
>[další](serverless-architecture.md)
