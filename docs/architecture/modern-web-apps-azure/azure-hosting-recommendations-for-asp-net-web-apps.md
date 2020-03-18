---
title: Doporučení pro hostování Azure pro webové aplikace ASP.NET Core
description: Architekt moderní webové aplikace s ASP.NET core a Azure | Doporučení pro hostování Azure pro ASP.NET webové aplikace
author: ardalis
ms.author: wiwagn
ms.date: 06/06/2019
ms.openlocfilehash: 5587b8b20da8a6801d77b722e9c3326f6e695574
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73416717"
---
# <a name="azure-hosting-recommendations-for-aspnet-core-web-apps"></a>Doporučení pro hostování Azure pro webové aplikace ASP.NET Core

> "Lídři v řadě podniků všude na světě obcházejí IT oddělení, aby získali aplikace z cloudu (také známého jako SaaS) a platili za ně, jako by to bylo předplatné časopisu. A pokud služba již není vyžadována, mohou zrušit předplatné bez zařízení, které by zůstalo v rohu nevyužito."  
> _\-Daryl Plummer, analytik společnosti Gartner_

Ať už vaše aplikace potřebuje a architekturu, microsoft azure ji může podporovat. Vaše hostingové potřeby mohou být stejně jednoduché jako statické webové stránky nebo sofistikované aplikace tvořené desítkami služeb. Pro ASP.NET monolitických webových aplikací core a podpůrných služeb, existuje několik známých konfigurací, které jsou doporučeny. Doporučení k tomuto článku jsou seskupeny na základě druhu prostředku, který má být hostován, zda úplné aplikace, jednotlivé procesy nebo data.

## <a name="web-applications"></a>Webové aplikace

Webové aplikace mohou být hostovány pomocí:

- Webové aplikace služby App Service

- Kontejnery (několik možností)

- Virtuální počítače (virtuální počítače)

Z nich app service web apps je doporučený přístup pro většinu scénářů, včetně jednoduchých aplikací založených na kontejnerech. Pro architektury mikroslužeb zvažte přístup založený na kontejneru. Pokud potřebujete větší kontrolu nad počítači se spuštěnou aplikací, zvažte virtuální počítače Azure.

### <a name="app-service-web-apps"></a>Webové aplikace služby App Service

App Service Web Apps nabízí plně spravovanou platformu optimalizovanou pro hostování webových aplikací. Je to platforma jako služba (PaaS), která vám umožní soustředit se na vaši obchodní logiku, zatímco Azure se postará o infrastrukturu potřebnou ke spuštění a škálování aplikace. Některé klíčové funkce webových aplikací App Service:

- Optimalizace DevOps (průběžná integrace a doručování, více prostředí, testování A/B, podpora skriptování).

- Globální rozsah a vysoká dostupnost.

- Připojení k platformám SaaS a místním datům.

- Bezpečnost a dodržování předpisů.

- Integrace visual studia.

Azure App Service je nejlepší volbou pro většinu webových aplikací. Nasazování a správa jsou integrované přímo do platformy, weby se rychle škálují pro zvládnutí vysokého přenosového zatížení a integrované vyrovnávání zatížení a služba Traffic Manager zajišťují vysokou dostupnost. Do služby Azure App Service můžete snadno přesunout existující weby pomocí online nástroje pro migraci, můžete použít open source aplikaci z galerie webových aplikací nebo vytvořit nový web pomocí rozhraní a nástrojů podle vašeho výběru. Díky funkci WebJobs můžete do své webové aplikace App Service snadno přidat zpracování úloh na pozadí. Pokud máte existující ASP.NET aplikace hostované místně pomocí místní databáze, je tu jasnou cestu k migraci aplikace do webové aplikace služby app service s Azure SQL Database (nebo zabezpečený přístup k místnímu databázovému serveru, pokud je to výhodné).

![Doporučená strategie migrace pro místní aplikace .NET do služby Azure App Service](./media/image1-6.png)

Ve většině případů je přechod z místně hostované ASP.NET aplikace na webovou aplikaci služby App Service jednoduchý proces. Od samotné aplikace by měla být vyžadována malá nebo žádná změna a může rychle začít využívat mnoho funkcí, které azure app service web apps nabízejí.

Kromě aplikací, které nejsou optimalizované pro cloud, jsou Azure App Service Web Apps vynikajícím řešením pro mnoho jednoduchých monolitických (nedistribuovaných) aplikací, jako je například mnoho ASP.NET základních aplikací. V tomto přístupu je architektura základní a snadno pochopitelná a spravovatelná:

![Základní architektura Azure](./media/image1-5.png)

Malý počet prostředků v jedné skupině prostředků je obvykle dostačující ke správě takové aplikace. Aplikace, které jsou obvykle nasazeny jako jeden celek, nikoli ty aplikace, které se sloučí z mnoha samostatných procesů, jsou dobrými kandidáty pro tento [základní architektonický přístup](https://docs.microsoft.com/azure/architecture/reference-architectures/app-service-web-app/basic-web-app). Ačkoli architektonicky jednoduché, tento přístup stále umožňuje hostované aplikace vertikálně navýšit kapacitu (více prostředků na uzel) a ven (více hostovaných uzlů) k uspokojení jakékoli zvýšení poptávky. Pomocí automatického škálování lze aplikaci nakonfigurovat tak, aby automaticky upravila počet uzlů hostujících aplikaci na základě poptávky a průměrného zatížení mezi uzly.

### <a name="app-service-web-apps-for-containers"></a>Webové aplikace služby App Service pro kontejnery

Kromě podpory pro přímé hostování webových aplikací lze [webové aplikace App Service pro kontejnery](https://azure.microsoft.com/services/app-service/containers/) používat ke spouštění kontejnerizovaných aplikací v systému Windows a Linuxu. Pomocí této služby můžete snadno nasadit a spustit kontejnerizované aplikace, které lze škálovat s vaší firmou. Aplikace mají všechny funkce App Service Web Apps uvedené výše. Kromě toho webové aplikace pro kontejnery podporují zjednodušené CI/CD s Docker Hub, Azure Container Registry a GitHub. Azure DevOps můžete použít k definování kanálů sestavení a nasazení, které publikují změny v registru. Tyto změny pak mohou být testovány v přípravném prostředí a automaticky nasazeny do produkčního prostředí pomocí slotů pro nasazení, což umožňuje upgrady s nulovými prostoji. Vrácení zpět k předchozím verzím lze provést stejně snadno.

Existuje několik scénářů, kde webové aplikace pro kontejnery dávají největší smysl. Pokud máte existující aplikace, které můžete kontejnerizovat, ať už v kontejnerech Windows nebo Linux, můžete je snadno hostovat pomocí této sady nástrojů. Jednoduše publikujte kontejner a pak nakonfigurujte webové aplikace pro kontejnery tak, aby vytahovaly nejnovější verzi této bitové kopie z vybraného registru. Jedná se o přístup "lift and shift" k migraci z klasických modelů hostování aplikací na model optimalizovaný pro cloud.

![Migrace kontejnerizované místní aplikace .NET do Azure Web Apps pro kontejnery](./media/image1-8.png)

Tento přístup funguje také dobře, pokud váš vývojový tým je schopen přejít na proces vývoje na základě kontejneru. "Vnitřní smyčka" vývoje aplikací s kontejnery zahrnuje vytváření aplikace s kontejnery. Změny provedené v kódu, stejně jako konfigurace kontejneru jsou nabízeny do správy zdrojového kódu a automatizované sestavení je zodpovědný za publikování nových ibi kontejnerů do registru, jako je Docker Hub nebo Azure Container Registry. Tyto obrázky se pak používají jako základ pro další vývoj, stejně jako pro nasazení do produkčního prostředí, jak je znázorněno na následujícím diagramu:

![Pracovní postup životního cyklu Koncové do koncového Dockeru](./media/image1-7.png)

Vývoj s kontejnery nabízí mnoho výhod, zejména při použití kontejnerů ve výrobě. Stejná konfigurace kontejneru se používá k hostování aplikace v každém prostředí, ve kterém běží, od místního vývojového počítače až po vytváření a testování systémů až po produkční prostředí. To výrazně snižuje pravděpodobnost závad v důsledku rozdílů v konfiguraci počítače nebo verzí softwaru. Vývojáři mohou také používat jakékoli nástroje, se kterými jsou nejproduktivnější, včetně operačního systému, protože kontejnery lze spustit v libovolném operačním systému. V některých případech distribuované aplikace zahrnující mnoho kontejnerů může být velmi náročné na prostředky spustit na jednom vývojovém počítači. V tomto scénáři může mít smysl upgradovat na using Kubernetes a Azure Dev Spaces, které jsou popsány v další části.

Jako části větších aplikací jsou rozděleny do jejich vlastní menší, nezávislé *mikroslužeb*, další návrhové vzory lze použít ke zlepšení chování aplikací. Namísto přímé práce s jednotlivými službami může *brána rozhraní API* zjednodušit přístup a oddělit klienta od jeho back-endu. S oddělenými servisními back-endy pro různé front-endy také umožňuje, aby se služby vyvíjely ve shodě se svými spotřebiteli. Běžné služby lze přistupovat prostřednictvím samostatného kontejneru *sajdkáru,* který může zahrnovat běžné knihovny připojení klienta pomocí *vzoru ambassador.*

![Mikroslužeb ukázkové architektury s několika běžných vzorů návrhu poznamenal.](./media/image1-10.png)

[Další informace o návrhových vzorech, které je třeba vzít v úvahu při vytváření systémů založených na mikroslužbách.](https://docs.microsoft.com/azure/architecture/microservices/design/patterns)

### <a name="azure-kubernetes-service"></a>Azure Kubernetes Service

Azure Kubernetes Service (AKS) spravuje hostované prostředí Kubernetes a umožňuje tak rychle a snadno nasazovat a spravovat kontejnerizované aplikace bez znalosti orchestrace kontejnerů. Zároveň eliminuje režii spojenou s probíhajícími operacemi a údržbou díky zřizování, upgradování a škálování prostředků na vyžádání bez nutnosti odpojovat aplikace.

AKS zjednodušuje správu clusteru Kubernetes a snižuje provozní režii s tím spojenou díky přenášení většiny zodpovědnosti na Azure. Jako hostovaná služba Kubernetes se za vás Azure stará o důležité úlohy, jako je monitorování stavu a údržba. Také platíte pouze pro uzly agenta v rámci clusterů, nikoli pro předlohy. AKS jako spravovaná služba Kubernetes poskytuje:

- Automatické upgrady a opravy verzí Kubernetes.
- Snadné škálování clusteru.
- Samoopraviteho hostovací řídicí rovinu (mistři).
- Úspora nákladů – platí pouze za spuštění uzlů fondu agenta.

Díky tomu, že se Azure stará o správu uzlů ve vašem clusteru AKS, už řadu úloh, například upgrady clusteru, nemusíte provádět ručně. Vzhledem k tomu, že Azure zpracovává tyto úkoly kritické údržby za vás, AKS neposkytuje přímý přístup (například s SSH) do clusteru.

Týmy, které využívají AKS, můžou taky využít Azure Dev Spaces. Azure Dev Spaces pomáhá týmům zaměřit se na vývoj a rychlou iteraci jejich aplikace mikroslužeb tím, že umožňuje týmům pracovat přímo s celou architekturou mikroslužeb nebo aplikací spuštěnou v AKS. Azure Dev Spaces také poskytuje způsob, jak nezávisle aktualizovat části architektury mikroslužeb izolovaně bez ovlivnění zbytku clusteru AKS nebo jiných vývojářů.

![Příklad pracovního postupu Azure Dev Spaces](./media/image1-9.gif)

Azure Dev Spaces:

- Minimalizace času nastavení místního počítače a požadavků na prostředky
- Umožněte týmům rychleji iterátovat
- Snížení počtu integračních prostředí požadovaných týmem
- Odstranit potřebu zesměšňovat některé služby v distribuovaném systému při vývoji / testování

[Další informace o Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/about)

### <a name="azure-virtual-machines"></a>Azure Virtual Machines

Pokud máte existující aplikaci, která by vyžadovala podstatné změny ke spuštění ve službě App Service, můžete zvolit virtuální počítače, abyste zjednodušili migraci do cloudu. Správná konfigurace, zabezpečení a údržba virtuálních počítačů však vyžaduje mnohem více času a odborných znalostí v oblasti IT ve srovnání se službou Azure App Service. Pokud uvažujete o virtuálních počítačích Azure, ujistěte se, že berete v úvahu probíhající úsilí údržby potřebné k opravě, aktualizaci a správě prostředí virtuálních počítačů. Virtuální počítače Azure je infrastruktura jako služba (IaaS), zatímco služba App Service je PaaS. Měli byste také zvážit, zda nasazení aplikace jako kontejneru Windows do webové aplikace pro kontejnery může být životaschopnou možností pro váš scénář.

## <a name="logical-processes"></a>Logické procesy

Jednotlivé logické procesy, které lze oddělit od zbytku aplikace, mohou být nasazeny nezávisle na Azure Functions způsobem bez serveru. Funkce Azure umožňuje pouze napsat kód, který potřebujete pro daný problém, bez obav o aplikaci nebo infrastrukturu pro jeho spuštění. Můžete si vybrat z různých programovacích\#jazyků, včetně C , F\#, Node.js, Python a PHP, což vám umožní vybrat nejproduktivnější jazyk pro daný úkol. Stejně jako většina cloudových řešení platíte jenom za dobu, po kterou používáte, a můžete důvěřovat funkcím Azure, které se podle potřeby zvětšují.

## <a name="data"></a>Data

Azure nabízí širokou škálu možností úložiště dat, takže vaše aplikace může použít příslušného poskytovatele dat pro příslušná data.

Pro transakční, relační data Azure SQL databases jsou nejlepší volbou. Pro vysoce výkonná data pro čtení je dobrým řešením mezipaměť Redis podporovaná databází Azure SQL Database.

Nestrukturovaná data JSON se můžou ukládat různými způsoby, od sloupců databáze SQL přes objekty BLOB nebo tabulky ve službě Azure Storage až po Azure Cosmos DB. Z nich Azure Cosmos DB nabízí nejlepší funkce dotazování a je doporučená možnost pro velký počet dokumentů založených na JSON, které musí podporovat dotazování.

Přechodná data založená na příkazech nebo událostech, která se používají k orchestraci chování aplikací, můžou používat Azure Service Bus nebo Fronty úložiště Azure. Azure Storage Bus nabízí větší flexibilitu a je doporučená služba pro netriviální zasílání zpráv v rámci aplikací a mezi nimi.

## <a name="architecture-recommendations"></a>Doporučení architektury

Požadavky aplikace by měly určovat její architekturu. K dispozici je mnoho různých služeb Azure. Výběr toho správného je důležité rozhodnutí. Společnost Microsoft nabízí galerii referenčních architektur, které pomáhají identifikovat typické architektury optimalizované pro běžné scénáře. Můžete najít referenční architekturu, která se mapuje úzce na požadavky vaší aplikace, nebo alespoň nabízí výchozí bod.

Obrázek 11-1 znázorňuje ukázkovou referenční architekturu. Tento diagram popisuje doporučený přístup architektury pro web systému správy obsahu Sitecore optimalizovaný pro marketing.

![Obrázek 11-1](./media/image11-2.png)

**Obrázek 11-1.** Referenční architektura webových stránek sitecore marketing.

**Reference – doporučení pro hostování azure**

- Architektury řešení Azure\
  <https://azure.microsoft.com/solutions/architecture/>

- Architektura webových aplikací Azure Basic\
  <https://docs.microsoft.com/azure/architecture/reference-architectures/app-service-web-app/basic-web-app>

- Návrhové vzory pro mikroslužby\
  <https://docs.microsoft.com/azure/architecture/microservices/design/patterns>

- Průvodce vývojáři Azure\
  <https://azure.microsoft.com/campaigns/developer-guide/>

- Přehled webových aplikací\
  <https://docs.microsoft.com/azure/app-service/app-service-web-overview>

- Webová aplikace pro kontejnery\
  <https://azure.microsoft.com/services/app-service/containers/>

- Úvod ke službě Azure Kubernetes (AKS)\
  <https://docs.microsoft.com/azure/aks/intro-kubernetes>

>[!div class="step-by-step"]
>[Předchozí](development-process-for-azure.md)
