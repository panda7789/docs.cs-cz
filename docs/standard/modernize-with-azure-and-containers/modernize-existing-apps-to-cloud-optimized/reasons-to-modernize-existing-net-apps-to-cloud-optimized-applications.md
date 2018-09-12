---
title: Důvody pro modernizovat existující aplikace .NET pro aplikace optimalizované pro Cloud
description: Modernizace stávajících aplikací .NET pomocí cloudu Azure a Windows kontejnery | Důvody pro modernizovat existující aplikace .NET pro aplikace optimalizované pro Cloud
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 17838381f42a760caa7fba7e09ab798c6284bccb
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44509957"
---
# <a name="reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications"></a>Důvody pro modernizovat existující aplikace .NET pro aplikace optimalizované pro Cloud

S aplikací optimalizovaných pro Cloud můžete rychle a opakovaně doručovat spolehlivých aplikací pro vaše zákazníky. Nezbytné flexibility a spolehlivosti získáte odložením velkou část provozních složitosti vaší aplikace pro platformu.

Pokud to nejde s vaší aplikací rychle uvedla na trh, době dodejte svou aplikaci, bude se vyvinula, které se cílí na trhu. Je možné, bez ohledu na to, jak dobře navržený nebo analyzovány aplikace příliš pozdě. Můžete být služeb při selhání nebo nedosáhne plný potenciál, protože nemůžou synchronizovat doručování aplikací s potřebami na trhu.

Potřebu nepřetržité podnikové inovace nasdílí do limitu týmy vývoje a provozu. Jediný způsob, jak dosáhnout flexibilitu, které potřebujete v nepřetržité podnikové inovace, je modernizace aplikací pomocí technologie, jako jsou kontejnery a zásady pro konkrétní aplikace optimalizované pro Cloud.

Dolní řádek je, že když organizace vytváří a spravuje aplikace, které jsou optimalizované pro Cloud, můžete vložit řešení v rámci zákazníkům dříve a přinést nové nápady týkající se uvedení na trh, když jsou relevantní.

## <a name="cloud-optimized-application-principles-and-tenets"></a>Principy optimalizovaných pro cloudové aplikace a zásady 

Vylepšení v cloudu se většinou zaměřuje na splňuje dva cíle: snížení nákladů a zvýšení obchodní růst, což zlepšuje flexibilitu. Těchto cílů dosáhnout zjednodušení procesů a omezení případná problémová místa při vydání a dodávání aplikací.

Vaše aplikace je optimalizované pro Cloud při může v agile způsobem vyvíjet aplikace samostatně z jiných místních aplikací a uvolněte, nasazování, automatické škálování, monitorování a řešení potíží s vaší aplikací v cloudu.

Klíč je *flexibilitu*. Nelze odeslat s flexibilitou, není-li snížit na absolutním minimu každý nasazení na produkční problémy a chyby prostředí pro vývoj/testování. Kontejnery (konkrétně Dockeru, jako de facto standardem) a spravované služby byly navrženy speciálně pro tento účel.

Pro dosažení flexibility, musíte také automatizované procesy DevOps, které jsou založeny na kanály CI/CD, které vydané škálovatelné platformy v cloudu. CI/CD platformy (jako je Azure DevOps Services nebo Jenkinse), které nasazujete, škálovatelné a odolné cloudové platformy (jako je Azure App Service, Azure Service Fabric nebo Azure Kubernetes Service) jsou klíčové technologie pro zajištění pružnosti v cloudu.

Následující seznam popisuje hlavní principy nebo postupy pro aplikace optimalizované pro Cloud. Mějte na paměti, přijímat všechny nebo pouze některé z těchto zásad v rámci postupného nebo přírůstkové přístupu:

-   **Kontejnery**. Kontejnery nabízejí možnosti zahrnují závislosti aplikace s vlastní aplikace. Kontejnerizace výrazně snižuje počet problémy, se kterými se můžete setkat při nasazení do produkčního prostředí nebo testování v pracovním prostředí. Nakonec kontejnery, zlepší se pružnost doručování aplikací.

-   **Odolné a škálovatelné cloudové**. Cloud poskytuje platformu, která je spravovaná, pružná, škálovatelnou a odolnou. Tyto vlastnosti jsou zásadní pro získání vylepšení náklady a dodávat vysoce dostupných a spolehlivých aplikací průběžné doručování. Spravované služby, jako jsou spravované databáze spravované mezipaměti jako služby (CaaS) a spravovaného úložiště jsou základní části jako prostředek pro zmírnění náklady na údržbu aplikace.

-   **Monitorování**. Nemůže mít spolehlivé aplikace bez nutnosti vhodný způsob, jak detekovat a diagnostikovat výjimky a problémy s výkonem aplikací. Budete muset získat užitečné přehledy prostřednictvím správy výkonu aplikací a okamžitých analýz.

-   **DevOps jazykovou verzi a průběžné doručování**. Přijetí postupy DevOps vyžaduje kulturní změnu, ve kterém týmy už nebude fungovat v nezávislých sila. Kanály CI/CD jsou možné pouze v případě, že je lepší spolupráce mezi vývojovou a provozní týmy IT, podporuje kontejnery a nástroje CI/CD.

Obrázek 4-2 je znázorněný hlavní pilíře volitelná aplikace optimalizované pro Cloud. Další pilíře implementujete, tím lepší bude vaše aplikace k úspěšnému v souladu s očekávání vašich zákazníků.

> ![Hlavní pilíře z aplikace optimalizované pro Cloud](./media/image2.png)
>
> **Obrázek 4-2.** Hlavní pilíře z aplikace optimalizované pro Cloud

Souhrnně řečeno, aplikace optimalizované pro Cloud je takový přístup k vytváření a správu aplikací, která využívá výhod cloud computingu model, při použití kombinace kontejnerů, spravovanou cloudovou infrastrukturu, techniky odolné aplikace monitorování, průběžné doručování a DevOps, vše bez nutnosti úprava architektury a recode svoje stávající aplikace.

Vaše organizace může přijmout tyto technologie a přístupy postupně. Není nutné využívat všechny z nich, všechny najednou. Můžete přijmout jejich přírůstkově, v závislosti na enterprise priority a potřebám uživatelů.

## <a name="benefits-of-a-cloud-optimized-application"></a>Výhody aplikace optimalizované pro Cloud

Převod existující aplikace do optimalizovaných Cloudů (bez změna architektury nebo kódování), můžete získat následující výhody:

-   **Nižší náklady, protože je spravovaná infrastruktura zpracována od poskytovatele cloudu**. Aplikace optimalizované pro cloud získáte výhody cloudu s využitím elasticity out-of-the-box v cloudu, automatické škálování a vysokou dostupnost. Výhody se vztahují pouze k funkcím výpočetní prostředky (virtuální počítače a kontejnery), ale také závisí na prostředky v cloudu, jako DBaaS CaaS a jakékoliv infrastruktury mohou potřebné aplikace.

-   **Odolné aplikace a infrastrukturu**. Když provádíte migraci do cloudu, budete potřebovat pro zpracování přechodných selhání; dojde k chybám v cloudu. Cloudové infrastruktury a hardware jsou také "nahraditelné," což zvyšuje úroveň příležitosti pro přechodné výpadky. Ve stejnou dobu vývojářských technik určité aplikace, které implementují odolnost proti chybám a automatizovat obnovení a možnosti vnitřní cloudu to značně zjednodušují zotavení z neočekávaných chyb v cloudu.

-   **Podrobnější přehled o výkonu aplikace**. Monitorování nástroje, jako je Azure Application Insights poskytuje vizualizace pro správu stavu, protokolování a oznámení v cloudu. Protokoly auditu vytvářejte aplikace snadno ladit a auditovat, základní spolehlivých cloudových aplikací.

-   **Přenositelnost aplikací s agilním nasazení**. Kontejnery (Linux nebo Windows kontejnerů na základě modul Docker) nabízí nejlepší řešení pro vyloučení je uzamčen cloudové aplikace. Pomocí kontejnerů, hostitelů Docker a multicloudové orchestrátory můžete snadno přesouvat z jednoho prostředí nebo cloudu do jiného. Kontejnery eliminovat řešit zádrhele spojené s, který obvykle probíhá nasazení do libovolného prostředí (fáze/testovací/produkční).

Všechny tyto výhody nakonec zadejte snížení nákladů klíče pro váš životní cyklus aplikace začátku do konce.

V následující části tyto výhody jsou vysvětlené podrobněji a jsou spojeny s konkrétní technologie.

>[!div class="step-by-step"]
[Předchozí](index.md)
[další](microsoft-technologies-in-cloud-optimized-applications.md)
