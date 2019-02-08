---
title: Doporučení pro webové aplikace ASP.NET Core hostování Azure
description: Navrhování moderních webových aplikací pomocí ASP.NET Core a Azure | Doporučení pro webové aplikace ASP.NET hostování Azure
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: cda4c002c73e2dd0db1b2d5d1fa8bc76903c5c62
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/07/2019
ms.locfileid: "55828381"
---
# <a name="azure-hosting-recommendations-for-aspnet-core-web-apps"></a>Doporučení pro webové aplikace ASP.NET Core hostování Azure

> "Řádku obchodní vedení všude, kde jsou obcházení oddělení IT získat aplikace z cloudu (označuje se také jako SaaS) a platit za ně je stejně, jako kdyby je sdíleli předplatné magazine. A když služby se už nevyžaduje, se předplatné zrušit se žádná zařízení left nepoužívané v pravém rohu."  
> _\- Daryl Plummer, analytik společnosti Gartner_

Všechno, co vaše aplikace potřebám a architekturu, Windows Azure může podporovat. Hostování potřeb může být stejně snadné jako statický web sofistikované aplikace tvořené řadě služeb. Monolitické webové aplikace ASP.NET Core a podpůrných služeb existují některé známé konfigurace, které se doporučují. Doporučení v tomto článku se seskupují podle druhu prostředku hostovat, zda celé aplikace, jednotlivé procesy nebo data.

## <a name="web-applications"></a>Webové aplikace

Pomocí se dají hostovat webové aplikace:

- App Service Web Apps

- Kontejnery

- Azure Service Fabric

- Virtuální počítače (VM)

App Service Web Apps z nich je doporučený postup pro většinu scénářů. Pro architektury mikroslužeb zvažte přístupu založených na kontejnerech nebo Service Fabric. Pokud potřebujete větší kontrolu nad počítače spuštěné aplikace, zvažte Azure Virtual Machines.

### <a name="app-service-web-apps"></a>App Service Web Apps

App Service Web Apps nabízí plně spravovaná platforma optimalizovaná pro hostování webových aplikací. Je platforma jako služba (PaaS), nabídky, že vám umožní soustředit na obchodní logiku, zatímco Azure zajistí infrastrukturu potřebné k spouštění a škálování aplikace. Některé klíčové funkce služby App Service Web Apps:

- Optimalizace DevOps (průběžná integrace a doručování, více prostředí, A / B testování, podpora skriptování).

- Globální škálování a vysokou dostupnost.

- Připojení k platformám SaaS a firemními daty.

- Zabezpečení a dodržování předpisů.

- Integrace se sadou Visual Studio.

Azure App Service je nejlepší volbou pro většinu webových aplikací. Nasazení a správa jsou integrované do platformy, weby se rychle škálují pro zvládnutí vysokého přenosového zatížení a integrované zatížení vyrovnávání a traffic manager zajišťují vysokou dostupnost. Můžete přesunout existující weby do služby Azure App Service snadno se online nástroje pro migraci, použijte open source aplikaci z Galerie webových aplikací nebo vytvoření nového webu pomocí rozhraní a nástrojů podle vašeho výběru. Funkce WebJobs umožňuje snadno přidat úlohy na pozadí zpracování do webové aplikace služby App Service.

### <a name="azure-kubernetes-service"></a>Azure Kubernetes Service

Azure Kubernetes Service (AKS) spravuje hostované prostředí Kubernetes, tak rychle a snadno nasazovat a spravovat kontejnerizované aplikace bez znalosti Orchestrace kontejnerů. Také odstraní starosti související s probíhajícími operacemi a údržbou díky zřizování, upgradování a škálování prostředků na vyžádání, bez nutnosti přepínat aplikace do offline režimu.

AKS snižuje složitost a provozní režií při správě clusteru Kubernetes tím spojenou díky přenášení většiny zodpovědnosti na Azure. Jako hostovaná služba Kubernetes, Azure stará o důležité úlohy jako sledování stavu a údržby za vás. Navíc Platíte pouze za agentské uzly v rámci vašich clusterů, ne za hlavní uzly. Jako spravovaná služba Kubernetes poskytuje AKS:

- Automatické upgrady verzí Kubernetes a opravy chyb.
- Snadné škálování clusterů.
- Hostovanou rovinu řízení (hlavní uzly).
- Úspory nákladů – Platíte pouze za spuštěné uzly fondu agentů.

S Azure stará o správu uzlů ve vašem clusteru AKS už nepotřebujete provádět mnoho úloh ručně, například upgrady clusteru. Protože Azure stará o tyto důležité úlohy údržby za vás, neposkytuje AKS přímý přístup (například pomocí protokolu SSH) do clusteru.

### <a name="azure-service-fabric"></a>Azure Service Fabric

Service Fabric je dobrou volbou, pokud už vytváříte nové aplikace nebo přepsáním stávající aplikace pro využívají architekturu mikroslužeb. Aplikace spouštěné ve sdíleném fondu počítačů, můžete začít v malém a dosáhnout masivně škálovat na stovky nebo tisíce počítačů podle potřeby. Stavové služby usnadňují konzistentní a spolehlivé ukládání stavu aplikace a Service Fabric automaticky spravuje dělení, škálování a dostupnost za vás. Service Fabric také podporuje webová rozhraní API s Open Web Interface pro .NET (OWIN) a ASP.NET Core. Ve srovnání s App Service, Service Fabric také poskytuje další kontrolu nad nebo přímý přístup k základní infrastruktury. Můžete vzdáleně připojit do vašich serverů nebo konfigurace úloh při spuštění serveru.

### <a name="azure-virtual-machines"></a>Azure Virtual Machines

Pokud máte existující aplikace, které by vyžadovaly výrazné změny ke spuštění ve službě App Service nebo Service Fabric, můžete zvolením služby Virtual Machines pro zjednodušení migrace do cloudu. Ale správně konfigurace, zabezpečení a údržba virtuálních počítačů vyžaduje mnohem více času a znalosti v oboru IT ve srovnání s Azure App Service a Service Fabric. Pokud zvažujete Azure Virtual Machines, nezapomeňte že vzít v úvahu náročnost průběžné údržby vyžaduje opravu, aktualizovat a spravovat prostředí virtuálních počítačů. Azure Virtual Machines je infrastruktura jako služba (IaaS), služby App Service a Service Fabric jsou PaaS.

#### <a name="feature-comparison"></a>Porovnání funkcí

| Funkce                                                                                    | App Service | Kontejnery (AKS) | Service Fabric | Virtuální počítač |
| ------------------------------------------------------------------------------------------ | ----------- | ---------------- | -------------- | --------------- |
| Téměř okamžité nasazení                                                                    | X           | X                | X              |                 |
| Vertikálně navýšit kapacitu na větší počítače bez opětovného nasazení                                               | X           | X                | X              |                 |
| Instance sdílejí obsah a konfiguraci. bez nutnosti opětovného nasazení nebo překonfigurujte při horizontálním škálování | X           | X                | X              |                 |
| Více prostředí pro nasazení (produkční, pracovní)                                     | X           | X                | X              |                 |
| Automatická správa aktualizací operačního systému                                                             | X           | X                |                |                 |
| Bezproblémové přepínání mezi 32 a 64bitové platformy                                             | X           | X                |                |                 |
| Nasazení kódu pomocí Gitu a protokolu FTP                                                                  | X           | X                |                | X               |
| Nasazení kódu pomocí nasazení webu                                                                 | X           | X                |                | X               |
| Nasazení kódu pomocí TFS                                                                       | X           | X                | X              | X               |
| Hostitelský web nebo webovou vrstvu služby vícevrstvé architektury                                    | X           | X                | X              | X               |
| Přístup ke službám Azure, jako je Service Bus, Storage, SQL Database                              | X           | X                | X              | X               |
| Instalace jakékoli vlastní instalační služby MSI                                                                     |             | X                | X              | X               |

## <a name="logical-processes"></a>Logické procesy

Jednotlivé logické procesy, které mohou být oddělené od zbytku aplikace může nezávisle nasadit do služby Azure Functions v podobě "bez serveru". Azure Functions umožňuje stačí napsat kód, který budete potřebovat pro daný problém, ale nemusíme se starat o aplikaci nebo infrastrukturu k jeho spuštění. Můžete si vybrat z nejrůznějších programovacích jazyků, včetně C\#, F\#, Node.js, Python a PHP, umožní vám vybrat nejproduktivnější jazyk pro úlohy po ruce. Jako většina řešení založené na cloudu platíte jenom po zadanou dobu používání a Azure Functions vertikálně navýšit kapacitu podle potřeby můžete důvěřovat.

## <a name="data"></a>Data

Azure nabízí širokou škálu možnosti ukládání dat, tak, aby aplikace můžete používat poskytovatele příslušná data pro dotyčný data.

Pro transakční, relační data Azure SQL Database se nejlepší možností. Pro vysoký výkon pro čtení – většinou data mezipaměti Redis se opírá o službě Azure SQL Database je dobrým řešením.

Nestrukturovaná data JSON mohou být uloženy v různými způsoby, z databáze SQL sloupců pro objekty BLOB nebo tabulek ve službě Azure Storage k DocumentDB. Z těchto DocumentDB nabízí nejlepší funkcích pro dotazování a možnost se doporučuje pro velké počty dokumentů založenými na JSON, které musí podporovat dotazování.

Přechodné příkazu - nebo založený na událostech data použít k orchestrování chování aplikace pomocí Azure Service Bus nebo front Azure Storage. Azure Service Bus úložiště nabízí větší flexibilitu a je doporučenou službu pro netriviální zasílání zpráv v rámci a mezi aplikacemi.

## <a name="architecture-recommendations"></a>Doporučení pro architekturu

Podle požadavků vaší aplikace by měly určovat jeho architektura. Nejsou k dispozici mnoho různých služeb Azure. Důležité rozhodnutí je výběr ten správný. Společnost Microsoft nabízí Galerie referenční architektury, které pomáhají identifikovat typických architekturách, které jsou optimalizované pro běžné scénáře. Může se stát referenční architekturu, map, pečlivě sledují a podle požadavků vaší aplikace nebo na nejméně nabízí, počáteční bod.

Obrázek 11-2 je znázorněný příklad referenční architekturu. Tento diagram znázorňuje postup doporučené architektury pro web systém správy obsahu Sitecore optimalizované pro uvedení na trh.

![](./media/image11-2.png)

**Obrázek 11-1.** Sitecore marketingový web referenční architekturu.

**Odkazy – hostování doporučení pro Azure**

- Architectures\ řešení Azure
  <https://azure.microsoft.com/solutions/architecture/>

- Azure Developer Guide\
  <https://azure.microsoft.com/campaigns/developer-guide/>

- Overview\ webové aplikace
  <https://docs.microsoft.com/azure/app-service/app-service-web-overview>

- Azure App Service, Virtual Machines, Service Fabric a Cloud Services comparison\
  <https://docs.microsoft.com/azure/app-service-web/choose-web-site-cloud-service-vm>

- Úvod do služby Azure Kubernetes Service (AKS) \
  <https://docs.microsoft.com/azure/aks/intro-kubernetes>

>[!div class="step-by-step"]
>[Předchozí](development-process-for-azure.md)