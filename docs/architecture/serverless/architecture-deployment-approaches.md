---
title: Přístupy k nasazení architektury – aplikace bez serveru
description: Průvodce různými způsoby, jak podnikové architektury nasadí do cloudu, s porovnáním mezi IaaS, PaaS, kontejnery a bez serveru.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 8a1203ea2fc7089223c03b3a3e02fd3303610272
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68676814"
---
# <a name="architecture-deployment-approaches"></a>Přístupy k nasazení architektury

Bez ohledu na přístup k architektuře, který se používá k návrhu obchodní aplikace, se implementace nebo nasazení těchto aplikací může lišit. Firmy hostují aplikace na vše od fyzického hardwaru až po funkce bez serveru.

## <a name="n-tier-applications"></a>N-vrstvé aplikace

[N-vrstvý model architektury](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/n-tier) je vyspělá architektura a jednoduše odkazuje na aplikace, které oddělují různé logické vrstvy na samostatné fyzické vrstvy. N-vrstvá architektura je fyzická implementace N-vrstvé architektury. Nejběžnější implementace této architektury zahrnuje:

* Prezentační vrstva, například webová aplikace.
* Rozhraní API nebo úroveň přístupu k datům, jako je například REST API.
* Datová vrstva, jako je třeba databáze SQL.

![N-vrstvá architektura](./media/n-tier-architecture.png)

N-vrstvá řešení mají následující vlastnosti:

* Projekty jsou obvykle zarovnány s vrstvami.
* Testování se může nacházet odlišně podle úrovně.
* Vrstvy poskytují vrstvy abstrakce, například prezentační vrstva obvykle ignoruje podrobnosti implementace datové vrstvy.
* Vrstvy obvykle pracují pouze s sousedícími vrstvami.
* Verze jsou často spravovány v projektu a proto úroveň. Jednoduchá změna rozhraní API může vyžadovat nové vydání celé prostřední vrstvy.

Tento přístup přináší několik výhod, včetně:

* Izolace databáze (často front-end nemá přímý přístup k back-endu databáze).
* Opětovné použití rozhraní API (například klientů pro mobilní zařízení, stolní počítače a webové aplikace může používat stejná rozhraní API).
* Možnost škálovat vrstvy nezávisle na sobě.
* Izolace refaktoringu: jedna úroveň může být refaktorovaná, aniž by to ovlivnilo jiné úrovně.

## <a name="on-premises-and-infrastructure-as-a-service-iaas"></a>Místní prostředí a infrastruktura jako služba (IaaS)

Tradiční přístup k hostování aplikací vyžaduje nákup hardwaru a správu všech instalací softwaru, včetně operačního systému. Původně to zahrnovalo náročné datové centra a fyzický hardware. Mezi výzvy, které se dodávají s provozem fyzického hardwaru, patří mnoho, včetně těchto:

* Je potřeba koupit si přebytky pro scénáře "jenom v případě" nebo špičkové poptávky.
* Zabezpečení fyzického přístupu k hardwaru.
* Zodpovědnost za selhání hardwaru (například selhání disku).
* Synchronizovat.
* Konfigurace směrovačů a nástrojů pro vyrovnávání zatížení.
* Redundance napájení.
* Zabezpečení přístupu k softwaru.

![Přístup IaaS](./media/iaas-approach.png)

Virtualizace hardwaru prostřednictvím "virtuálních počítačů" umožňuje infrastrukturu jako službu (IaaS). Hostitelské počítače jsou efektivně rozdělené tak, aby poskytovaly prostředky s přidělením paměti pro vlastní paměť, procesor a úložiště. Tým zřídí nezbytné virtuální počítače a nakonfiguruje přidružené sítě a přístup k úložišti.

Další informace najdete v tématu [Referenční architektura N-vrstvých virtuálních počítačů](https://docs.microsoft.com/azure/architecture/reference-architectures/virtual-machines-windows/n-tier).

I když virtualizace a infrastruktura jako služba (IaaS) řeší mnoho otázek, stále ještě výrazně ponese odpovědnost za praktického týmu infrastruktury. Tým udržuje verze operačních systémů, používá opravy zabezpečení a instaluje závislosti třetích stran na cílových počítačích. Aplikace se často chovají odlišně na produkčních počítačích v porovnání s testovacím prostředím. Problémy vznikají v důsledku různých verzí závislosti a úrovní SKU operačního systému. I když mnoho organizací nasazuje v těchto cílech N-vrstvé aplikace, mnohé společnosti využívají výhod nasazení do více cloudových nativních modelů, jako [je například platforma jako služba](#platform-as-a-service-paas). Architektury s mikroslužbami jsou náročnější z důvodu požadavků na horizontální navýšení kapacity pro pružnost a odolnost.

Další informace najdete v tématu [virtuální počítače](https://docs.microsoft.com/azure/virtual-machines/).

## <a name="platform-as-a-service-paas"></a>Platforma jako služba (PaaS)

Platforma jako služba (PaaS) nabízí konfigurovaná řešení, která můžou vývojáři přímo připojit. PaaS je další termín pro spravované hostování. Eliminuje nutnost spravovat základní operační systém, opravy zabezpečení a v mnoha případech jakékoli závislosti třetích stran. Mezi příklady platforem patří webové aplikace, databáze a mobilní back-endy.

PaaS řeší výzvy společné pro IaaS. PaaS umožňuje vývojářům soustředit se na kód nebo schéma databáze místo nasazení. Mezi výhody PaaS patří:

* Platíte za použití modelů, které eliminují režijní náklady na investice do nečinných počítačů.
* Přímé nasazení a vylepšené kanály pro DevOps, kontinuální integrace (CI) a průběžné doručování (CD).
* Automatické upgrady, aktualizace a opravy zabezpečení.
* Horizontální navýšení kapacity a navýšení kapacity (Elastické škálování).

Hlavní nevýhodou PaaS tradičně byl uzamčen dodavatel. Někteří poskytovatelé PaaS například podporují ASP.NET, Node. js nebo jiné konkrétní jazyky a platformy. Produkty, jako Azure App Service, se vyvinuly k řešení více platforem a podporují různé jazyky a architektury pro hostování webových aplikací.

![Platforma jako architektura služby](./media/paas-architecture.png)

## <a name="software-as-a-service-saas"></a>Software jako služba (SaaS)

Software jako služba nebo SaaS je centrálně hostovaný a dostupný bez místní instalace nebo zřizování. SaaS se často hostuje jako platforma pro nasazování softwaru na PaaS. SaaS poskytuje služby pro spouštění a připojení k existujícímu softwaru. SaaS je často specifická pro odvětví a vertikálně specifické. SaaS je často licencovaná a obvykle poskytuje model klient/server. Většina moderních SaaS nabídek pro klienta používá webové aplikace. Společnosti obvykle uvažují SaaS jako obchodní řešení pro nabídky licencí. Není často implementována jako aspekt architektury pro zajištění škálovatelnosti a udržovatelnosti aplikace. Většina řešení SaaS je ve skutečnosti postavená na IaaS, PaaS a/nebo back-endy bez serveru.

Další informace o SaaS najdete v [ukázkové aplikaci](https://docs.microsoft.com/azure/sql-database/saas-tenancy-welcome-wingtip-tickets-app).

## <a name="containers-and-functions-as-a-service-faas"></a>Kontejnery a funkce jako služba (FaaS)

Kontejnery jsou zajímavé řešení, které umožňuje PaaSům podobných výhod bez režie IaaS. Kontejner je v podstatě modul runtime, který obsahuje úplné základy potřebné ke spuštění jedinečné aplikace. Jádro nebo jádro operačního systému hostitele a služby, jako je úložiště, se sdílejí napříč hostitelem. Sdílený jádro umožňuje, aby kontejnery byly odlehčené (některé jsou ve velikosti pouze megabajtů, v porovnání s velikostí gigabajtu typických virtuálních počítačů). S již spuštěnými hostiteli lze kontejnery rychle spustit, což usnadňuje vysokou dostupnost. Možnost rychlého zprovoznění kontejnerů také poskytuje další vrstvy odolnosti. Docker je jednou z nejoblíbenějších implementací kontejnerů.

Mezi výhody kontejnerů patří:

* Odlehčené a přenosné
* Samostatně obsažený, takže není nutné instalovat závislosti
* Poskytněte konzistentní prostředí bez ohledu na to, co je hostitel (spouští se přesně na přenosném počítači jako na cloudovém serveru).
* Dá se rychle zřídit pro horizontální navýšení kapacity
* Se dá rychle restartovat, aby se obnovila chyba.

Kontejner se spouští na hostiteli kontejneru (který zase může běžet na holém počítači nebo virtuálním počítači). V jednom hostiteli může běžet více kontejnerů nebo instancí stejných kontejnerů. Pro skutečné převzetí služeb při selhání a odolnost musí být kontejnery škálované napříč hostiteli.

Další informace o kontejnerech Docker najdete v tématu [co je Docker](../microservices/container-docker-introduction/docker-defined.md)?

Správa kontejnerů mezi hostiteli obvykle vyžaduje nástroj orchestrace, jako je Kubernetes. Konfigurace a Správa řešení orchestrace může do projektů přidat další režijní náklady a složitost. Naštěstí mnoho poskytovatelů cloudových služeb nabízí služby orchestrace prostřednictvím řešení PaaS, které zjednodušují správu kontejnerů.

Následující obrázek znázorňuje příklad instalace Kubernetes. Uzly na instalační adrese škálovat a převzetí služeb při selhání. Spouštějí instance kontejneru Docker spravované hlavním serverem. *Kubelet* je klient, který přenáší příkazy z Kubernetes do Docker.

![Kubernetes](./media/kubernetes-example.png)

Další informace o orchestraci najdete v tématu [Kubernetes v Azure](https://docs.microsoft.com/azure/aks/intro-kubernetes).

Functions as a Service (FaaS) je specializovaná služba kontejneru, která se podobá bez serveru. Konkrétní implementace FaaS, která se nazývá [OpenFaaS](https://github.com/openfaas/faas), je umístěná na kontejnerech a poskytuje možnosti bez serveru. OpenFaaS poskytuje šablony, které zabalí všechny závislosti kontejneru nezbytné ke spuštění části kódu. Použití šablon zjednodušuje proces nasazení kódu jako funkční jednotky. OpenFaaS cílí na architektury, které už obsahují kontejnery a orchestrace, protože můžou používat stávající infrastrukturu. I když poskytuje funkce bez serveru, konkrétně vyžaduje, abyste používali Docker a Orchestrator.

## <a name="serverless"></a>Bez serveru

Architektura bez serveru poskytuje jasné oddělení kódu a jeho hostitelského prostředí. Implementujete kód ve *funkci* , která je vyvolána triggerem. Po ukončení této funkce mohou být všechny potřebné prostředky uvolněny. Trigger může být manuální, časový proces, požadavek HTTP nebo nahrání souboru. Výsledek triggeru je spuštění kódu. I když se platformy bez serveru liší, většina poskytuje přístup k předdefinovaným rozhraním API a vazbám, aby se zjednodušily úlohy, jako je zápis do databáze nebo zařazení výsledků do fronty.

Bez serveru je architektura, která spoléhá na abstrakci, když se hostitelské prostředí zaměřuje na kód. Lze si představit jako *méně serveru*.

Řešení kontejneru poskytují vývojářům existující skripty sestavení pro publikování kódu na obrázky připravené pro server bez serveru. Jiné implementace využívají stávající řešení PaaS k zajištění škálovatelné architektury.

Abstrakce znamená, že tým DevOps nemusí zřizovat ani spravovat servery ani konkrétní kontejnery. Platforma bez serveru hostuje kód, a to buď jako skript nebo zabalený spustitelný soubor sestavený pomocí související sady SDK, a přiděluje nezbytné prostředky pro škálování kódu.

Následující ilustrace znázorňuje čtyři součásti bez serveru. Požadavek HTTP způsobí, že se spustí kód rozhraní API pro rezervaci. Rozhraní API pro rezervaci vloží kód do databáze a vložení spustí několik dalších funkcí, které mají být spuštěny k provádění úkolů, jako jsou výpočetní úkoly a plnění objednávky.

![Implementace bez serveru](./media/serverless-implementation.png)

Mezi výhody nástroje bez serveru patří:

* **Vysoká hustota** Mnoho instancí stejného kódu bez serveru může běžet na stejném hostiteli v porovnání s kontejnery nebo virtuálními počítači. Instance se škálují napříč více hostiteli a odolnostně se škálují.
* Mikrofakturaci. Většina poskytovatelů bez serveru se fakturuje na základě provádění bez serveru a umožňuje v určitých scénářích obrovské úspory nákladů.
* **Okamžité škálování**. Škálování bez serveru se dá škálovat tak, aby se automaticky shodovala s úlohami.
* **Rychlejší uvedení na trh** Vývojáři se zaměřují na kód a nasazují se přímo na platformu bez serveru. Součásti lze uvolnit nezávisle na sobě.

Servery bez serveru se nejčastěji projednávají v kontextu COMPUTE, ale můžou se vztahovat i na data. Například [Azure SQL](https://docs.microsoft.com/azure/sql-database) a [Cosmos DB](https://docs.microsoft.com/azure/cosmos-db) poskytují cloudové databáze, které nevyžadují konfiguraci hostitelských počítačů nebo clusterů. Tato kniha se zaměřuje na výpočetní prostředky bez serveru.

## <a name="summary"></a>Souhrn

K dispozici je široké spektrum dostupných možností architektury, včetně hybridního přístupu. Bez serveru se zjednodušuje přístup, Správa a náklady na funkce aplikací na úkor řízení a přenositelnosti. Mnoho platforem bez serveru ale zveřejňuje konfiguraci, která vám pomůžou řešení ladit. Dobré postupy programování můžou také vést k většímu přenositelnému kódu a menšímu zamykání platforem bez serveru. Následující tabulka ilustruje přístup architektury vedle sebe. Vyberte možnost bez serveru v závislosti na potřebách škálování, bez ohledu na to, jestli chcete modul runtime spravovat a jak dobře můžete úlohy rozdělit do malých součástí. Seznámíte se s potenciálními výzvami bez serveru a dalšími rozhodovacími body v další kapitole.

|         |IaaS     |PaaS     |Kontejner|Bez serveru|
|---------|---------|---------|---------|----------|
|**Kapacity**|Virtuální počítač       |instance |Aplikace      |Funkce  |
|**Abstrahuje**|Hardware|Platforma|Hostitel operačního systému|Modul runtime   |
|**Jednotce** |Virtuální počítač       |Project  |Image    |Kód      |
|**Doba platnosti**|Měsíci|Dny do měsíců|Počet minut do dnů|Milisekundy na minuty|
|**Zodpovědní**|Aplikace, závislosti, modul runtime a operační systém|Aplikace a závislosti|Aplikace, závislosti a modul runtime|Funkce

* **Škálování** odkazuje na jednotku, která se používá ke škálování aplikace.
* **Abstraktnís** odkazuje na vrstvu, která je abstraktní implementací.
* **Jednotka** odkazuje na rozsah toho, co je nasazeno.
* **Doba platnosti** odkazuje na typický modul runtime konkrétní instance.
* **Zodpovědnost** závisí na režii při sestavování, nasazování a údržbě aplikace.

Další kapitola se soustředí na architekturu bez serveru, případy použití a vzory návrhu.

## <a name="recommended-resources"></a>Doporučené prostředky

* [Průvodce architekturou aplikací Azure](https://docs.microsoft.com/azure/architecture/guide/)
* [Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db)
* [Azure SQL](https://docs.microsoft.com/azure/sql-database)
* [N-vrstvý model architektury](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/n-tier)
* [Kubernetes v Azure](https://docs.microsoft.com/azure/aks/intro-kubernetes)
* [Mikroslužeb](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)
* [Referenční architektura N-vrstvých virtuálních počítačů](https://docs.microsoft.com/azure/architecture/reference-architectures/virtual-machines-windows/n-tier)
* [Virtuální počítače](https://docs.microsoft.com/azure/virtual-machines/)
* [Co je Docker?](../microservices/container-docker-introduction/docker-defined.md)
* [Aplikace SaaS lístky Wingtip](https://docs.microsoft.com/azure/sql-database/saas-tenancy-welcome-wingtip-tickets-app)

>[!div class="step-by-step"]
>[Předchozí](architecture-approaches.md)Další
>[](serverless-architecture.md)
