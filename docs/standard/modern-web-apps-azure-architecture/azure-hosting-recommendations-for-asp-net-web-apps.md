---
title: Azure hostování doporučení pro webové aplikace ASP.NET Core
description: Architektury moderních webových aplikací pomocí ASP.NET Core a Azure | Azure hostování doporučení pro webové aplikace ASP.NET
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.openlocfilehash: aea8a54bdee7eebd977f8b67d9888c2288dcd26d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590330"
---
# <a name="azure-hosting-recommendations-for-aspnet-core-web-apps"></a>Azure hostování doporučení pro webové aplikace ASP.NET Core

> "-Obchodní žebříčky všude, kde jsou obcházení IT oddělení získat aplikace z cloudu (neboli SaaS) a platícího pro ně, jako kdyby je sdíleli katalogu předplatné. A pokud služby se už nevyžaduje, můžete zrušit předplatné se žádná zařízení zbývající nepoužité v horním."  
> _\- Daryl Plummer, Gartner analytika_

## <a name="summary"></a>Souhrn

Ať potřebám vaší aplikace a architektura systému Windows Azure může podporovat. Hostování potřeb může být stejně jednoduché jako statické webu velmi sofistikované aplikace skládá z desítek služeb. U monolitický webové aplikace ASP.NET Core a podpůrné služby existuje několik dobře známé konfigurace, které jsou doporučena. Následující doporučení jsou seskupeny podle typu prostředku hostovat, jestli úplné aplikace, jednotlivých procesů nebo data.

## <a name="web-applications"></a>Webové aplikace

Webové aplikace se dají hostovat pomocí:

-   Webové aplikace aplikační služby

-   Kontejnery

-   Azure Service Fabric

-   Virtuální počítače (VM)

App Service Web Apps z nich, se o doporučený postup pro většinu scénářů. Pro architektury mikroslužby zvažte přístup založený na kontejneru nebo service fabric. Pokud potřebujete větší kontrolu nad počítače spuštění aplikace, zvažte virtuálních počítačích Azure.

### <a name="app-service-web-apps"></a>Webové aplikace aplikační služby

Služby App Service Web Apps nabízí plně spravovaná platforma optimalizována pro hostování webových aplikací. Je platform-as-a-service(PaaS), nabídky, že vám umožní soustředit na obchodní logiku, zatímco Azure zajistí infrastruktury potřebné pro spouštění a škálování aplikace. Některé klíčové funkce App Service Web Apps:

-   Optimalizace DevOps (průběžnou integraci a doručení, několika prostředích, A / B testování, podpora skriptování)

-   Globální škálování a vysokou dostupnost

-   Připojení k platformám SaaS a místních dat

-   Zabezpečení a dodržování předpisů

-   integrace sady Visual Studio

Aplikační služba Azure je nejlepší volbou pro většinu webové aplikace. Nasazení a správy se integrují do platformy, lokalit můžete rychle škálovat pro zpracování vysoké přenosové zatížení a poskytovat vysokou dostupnost, Správce vyrovnávání a provoz integrované zatížení. Můžete přesunout existující lokality do služby Azure App Service snadno pomocí nástrojů pro migraci online, použijte open-source aplikace z Galerie webových aplikací nebo vytvoří nový web pomocí framework a nástrojů dle vašeho výběru. Funkci webové úlohy umožňuje snadno přidat úloha na pozadí zpracování do webové aplikace služby App Service.

### <a name="containers-and-azure-container-service"></a>Kontejnery a Azure Container Service

Azure Container Service umožňuje jednodušší můžete vytvářet, konfigurovat a spravovat cluster virtuálních počítačů, které jsou předem nakonfigurován ke spuštění kontejnerizované aplikací. Konfigurace aplikace optimalizované oblíbených open-source plánování a orchestraci nástrojů používá. To umožňuje použití existujících dovedností a kreslení na text velké a stále se rozrůstající komunita odborných znalostí, nasazovat a spravovat aplikace založené na kontejneru v Microsoft Azure.

Azure Container Service umožňuje jednodušší můžete vytvářet, konfigurovat a spravovat cluster virtuálních počítačů, které jsou předem nakonfigurován ke spuštění kontejnerizované aplikací. Konfigurace aplikace optimalizované oblíbených open-source plánování a orchestraci nástrojů používá. To umožňuje použití existujících dovedností a kreslení na text velké a stále se rozrůstající komunita odborných znalostí, nasazovat a spravovat aplikace založené na kontejneru v Microsoft Azure.

Jeden cíl Azure Container Service je poskytnout kontejneru hostitelské prostředí pomocí nástroje open source a technologie, které jsou dnes důležitá u zákazníků společnosti Microsoft. Za tímto účelem zpřístupní Azure Container Service standardní koncové body rozhraní API pro vaši zvolenou orchestrator (DC/OS, Docker Swarm nebo Kubernetes). Pomocí těchto koncových bodů, můžete využít veškerý software, který je schopen rozhovoru do těchto koncových bodů. V případě koncového bodu Docker Swarm, můžete například použít Docker rozhraní příkazového řádku (CLI). Pro DC/OS můžete zvolit, rozhraní příkazového řádku orchestrátoru DC/OS. Pro Kubernetes můžete zvolit kubectl. Obrázek 11-1 ukazuje, jak by pomocí těchto koncových bodů pro správu clusterů kontejneru.

![](./media/image11-1.png)

**Obrázek 11-1.** Správa Azure Container Service pomocí Docker, Kubernetes nebo DC/OS koncových bodů.

### <a name="azure-service-fabric"></a>Azure Service Fabric

Service Fabric je vhodný, pokud vytváříte novou aplikaci nebo přepisovat stávající aplikace pro použití architektury mikroslužby. Aplikace, které se spouštějí na sdílenému fondu počítačů, můžete začněte v malém rozsahu a dosáhnout masivním měřítku se stovkami nebo tisíci počítačů podle potřeby. Stavové služby usnadňují konzistentně a spolehlivě uložení stavu aplikace a Service Fabric automaticky spravuje služba rozdělení do oddílů, škálování a dostupnost za vás. Service Fabric podporuje také WebAPI s Open Web Interface pro .NET (OWIN) a ASP.NET Core. Ve srovnání s App Service, Service Fabric taky poskytuje další kontrolu nad nebo přímý přístup k podkladové infrastruktury. Můžete vzdálené do vašich serverů nebo můžete nakonfigurovat úlohy spuštění serveru.

### <a name="azure-virtual-machines"></a>Virtuální počítače Azure

Pokud máte existující aplikace, které by vyžadovaly významné změny ke spuštění v App Service nebo Service Fabric, může zvolit virtuální počítače za účelem zjednodušení migrace do cloudu. Ale správně konfigurace, zabezpečení a údržba virtuální počítače vyžaduje mnohem víc času a IT odborných znalosti ve srovnání s Azure App Service a Service Fabric. Pokud uvažujete o virtuálních počítačích Azure, ujistěte se, že byste vzít v úvahu následné údržbě náročnost opravy, aktualizovat a spravovat prostředí virtuálních počítačů. Virtuální počítače Azure je infrastruktury jako služba (IaaS), zatímco služba App Service a Service Fabric jsou platformy jako služba (Paas).

#### <a name="feature-comparison"></a>Porovnání funkcí

| Funkce služby App Service | Service Fabric | Virtuální počítač |
|---------|----------|----------|
| Téměř rychlých nasazení | X | X | |
| Škálování na větší počítače bez znovu ho zaveďte | X | X | |
| Instance sdílet obsah a konfiguraci; není nutné znovu ho zaveďte nebo reconfigure při změně měřítka | X | X | |
| Prostředí s více nasazení (produkční, pracovní) | X | X | |
| Automatická správa aktualizací operačního systému | X | | |
| Bezproblémové přepínání mezi platformami 32 nebo 64bitový | X | | |
| Nasaďte kód prostřednictvím Git, FTP | X | | X |
| Nasazení kódu do Web Deploy | X | | X |
| Nasazení kódu do sady TFS | X | X | X |
| Hostitele web nebo webovou vrstvu služby vícevrstvé architektury | X | X | X |
| Přístup k Azure služby, jako je Service Bus, úložiště, databáze SQL | X | X | X |
| Nainstalujte všechny vlastní MSI | | X | X |

## <a name="logical-processes"></a>Logické procesy

Jednotlivé logické procesy, které může být odděleno od zbývající aplikace dá nasadit nezávisle na Azure Functions "bez serveru" způsobem. Azure Functions umožňuje právě psát kód, který je nutné pro daný problém, bez starostí o aplikace nebo infrastruktury ji spustit. Můžete vybrat z různých programovacích jazyků, včetně C\#, F\#, Node.js a Python, PHP, umožní vám vybrat nejvíce produktivní jazyk pro úlohu po ruce. Podobně jako většina cloudové řešení platíte jenom po určenou dobu používání a důvěřujete Azure Functions škálování podle potřeby.

## <a name="data"></a>Data

Azure nabízí širokou škálu možností úložiště dat, tak, aby vaše aplikace můžete použít poskytovatele příslušná data pro dotyčné údaje.

Databáze SQL Azure pro transakční, relační data, jsou nejlepší možnost. Mezipaměť Redis založenou na Azure SQL Database pro vysoký výkon pro čtení – většinou data, je vhodné řešení.

Nestrukturovaných dat JSON může být uložená mnoha různými způsoby, z databáze SQL sloupců do objektů BLOB nebo tabulek, ve službě Azure Storage, do DocumentDB. Z těchto DocumentDB nabízí nejlepší funkcích pro dotazování a možnost se doporučuje pro velké počty dokumentů na základě JSON, které musí podporovat dotazování.

Přechodný příkaz - nebo na základě událostí data použít k orchestrování chování aplikace můžete použít služeb Azure Storage nebo Azure Service Bus. Azure sběrnice úložiště nabízí větší flexibilitu a je služba doporučené pro netriviální zasílání zpráv v rámci i mezi aplikacemi.

## <a name="architecture-recommendations"></a>Architektura doporučení

Požadavky na vaše aplikace by měly určovat jeho architektura. Nejsou k dispozici, a vybrat že ten správný je důležité rozhodnutí řadou různých služeb Azure. Společnost Microsoft nabízí Galerie architektur odkaz k identifikaci typické architektury optimalizované pro běžné scénáře. Referenční architektura mapy úzce požadavky na aplikace, nebo v nejméně nabízí výchozí bod může vytvořit vazbu.

Obrázek 11-2 je znázorněný příklad referenční architekturu. Tento diagram znázorňuje doporučené architektura přístup pro web systém správy obsahu Sitecore optimalizované pro marketing.

![](./media/image11-2.png)

**Obrázek 11-2.** Sitecore marketing webu referenční architektura.

**Odkazy – Azure hostování doporučení**

-   Architectures\ řešení služby Azure
    <https://azure.microsoft.com/solutions/architecture/>

-   Guide\ vývojáře pro službu Azure
    <https://azure.microsoft.com/campaigns/developer-guide/>

-   Co je Azure App Service? \
    <https://docs.microsoft.com/azure/app-service/app-service-value-prop-what-is>

-   Služby Azure App Service, Virtual Machines, Service Fabric a Comparison\ cloudové služby
    <https://docs.microsoft.com/azure/app-service-web/choose-web-site-cloud-service-vm>

>[!div class="step-by-step"]
[Předchozí] (development-process-for-azure.md)
