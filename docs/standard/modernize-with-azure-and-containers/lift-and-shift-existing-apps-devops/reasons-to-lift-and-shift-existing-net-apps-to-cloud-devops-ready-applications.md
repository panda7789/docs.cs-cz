---
title: "Důvodů, proč navýšení a shift existující aplikace .NET pro DevOps připravené pro cloudové aplikace"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Důvodů, proč navýšení a shift existující aplikace .NET pro DevOps připravené pro cloudové aplikace"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: 941ca8d8fcb4d69f60282737851ab3e86b5782d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="reasons-to-lift-and-shift-existing-net-apps-to-cloud-devops-ready-applications"></a>Důvodů, proč navýšení a shift existující aplikace .NET pro DevOps připravené pro cloudové aplikace

S aplikací DevOps Cloud-Ready abyste mohli rychle a opakovaně zajistit spolehlivé aplikací pro vaše zákazníky. Velká část provozní složitost vaší aplikace pro platformu rozlišením získáte základní flexibility a spolehlivosti.

Pokud nelze získat aplikace na trh rychle v čase dodávají vaší aplikace, které byly cílené na trhu se vyvinuly. Můžete mít příliš pozdní, bez ohledu na to, jak dobře byl navržen nebo analyzovány aplikace. Můžete se nedaří a nedosáhne plného potenciálu, protože nemůže synchronizovat doručení aplikace s potřebami na trhu.

Potřebu průběžné obchodní inovací doručí vývoj a provoz týmy limitu. Jediný způsob, jak dosáhnout flexibility, které potřebujete v průběžné obchodní inovací je modernizing vaše aplikace s technologiemi jako kontejnery a specifické zásady DevOps připravené pro cloudové aplikace.

Důležité je, když organizace sestavení a spravuje aplikace, které jsou připravené pro Cloud DevOps, ho můžete umístit řešení do nesprávných rukou zákazníkům dříve a přepněte nových nápadů na trh, když jsou relevantní.

## <a name="cloud-devops-ready-application-principles-and-tenets"></a>Zásady aplikace připravené pro DevOps cloudu a zásady 

Vylepšení v cloudu se většinou zaměřuje na splňuje dva cíle: snížit náklady a zvýšit růst podniku pomocí zvýšení flexibility. Těchto cílů dosáhnout zjednodušení procesy a omezení třecí uvolníte a odeslání aplikací.

Aplikace je DevOps Cloud-Ready, pokud vám může in agilní způsobem vývoj aplikace samostatně z jiných aplikací na místě a poté uvolněte, nasazení, automatické škálování, sledování a řešení problémů aplikace v cloudu.

Klíč je *flexibility*. Nemůžete dodat s flexibility Pokud snížit na absolutním minimu žádné nasazení na provozní problémy a chyby prostředí pro vývoj/testování. Kontejnery (konkrétně Docker, jako fakticky standard) a spravované služby byly navrženy speciálně pro tento účel.

K dosažení flexibility, musíte taky automatizované procesy DevOps, které jsou založeny na CI/CD kanály, které verze škálovatelné platformy v cloudu. CI/CD platformy (například Visual Studio Team Services nebo volaných), které nasazujete, škálovatelné a odolné cloudové platformy (například Azure Service Fabric nebo Kubernetes) jsou klíčové technologie k dosažení flexibility v cloudu.

Následující seznam popisuje hlavní principů nebo postupy pro DevOps připravené pro cloudové aplikace. Poznámka přijmout všechny nebo pouze některé z těchto zásad, v rámci progresivní nebo přírůstkové přístupu:

-   **Kontejnery**. Kontejnery získáte možnost obsahovat závislosti aplikací, s vlastní aplikace. Rozdělení do kontejnerů významně snižuje počet problémů, které se můžete setkat při nasazování do provozního prostředí nebo testů v pracovním prostředí. Nakonec kontejnery zlepšit flexibility dodání aplikace.

-   **Odolné a škálovatelné cloudové**. Cloud zajišťuje platformu, která je spravovaná, elastické, škálovatelné a pružnější. Tyto vlastnosti jsou nezbytné, aby získali vylepšení náklady a dodávají vysoce dostupné a spolehlivých aplikací v nastavené průběžné doručování. Spravované služby, jako spravované databáze, spravované služby (CaaS) a úložiště spravovaný jsou základní částí jako prostředek pro zmírnění náklady na údržbu aplikace do mezipaměti.

-   **Monitorování**. Spolehlivé aplikace nemůže mít bez nutnosti vhodný způsob, jak najít a diagnostikovat výjimky a problémy s výkonem aplikace. Budete muset získat prakticky uplatnitelných informací prostřednictvím správy výkonu aplikací a rychlé analýzy.

-   **DevOps jazykovou verzi a nastavené průběžné doručování**. Přijetí DevOps Cloud-Ready postupy vyžaduje kulturního změnu, ve kterém týmy přestane fungovat v nezávislých sila. CI/CD kanálů je možné, jenom v případě, že je zvýšené spolupráce mezi vývojovým týmem a IT oddělení, podporuje kontejnery a CI/CD Nástroje.

Obrázek 4-2 je znázorněný hlavní volitelné pilíře DevOps připravené pro cloudové aplikace. Další pilíře implementujete, tím lepší bude vaše aplikace při splnění vašich zákazníků očekávání úspěšná.

> ![Hlavní pilíře DevOps připravené pro cloudové aplikace](./media/image2.png)
>
> **Obrázek 4-2.** Hlavní pilíře DevOps připravené pro cloudové aplikace

To Shrneme, DevOps připravené pro cloudové aplikace je přístup k vytváření a Správa aplikací, který využívá cloud computing model, při použití kombinace kontejnery, spravovanou cloudovou infrastrukturu, techniky odolná aplikace monitorování, nastavené průběžné doručování a DevOps, všechny bez nutnosti přepracování a recode existující aplikace.

Vaše organizace může přijmout tyto technologie a přístupy postupně. Nemáte všechny z nich, kde všechny najednou. Vám může přijmout je postupně, v závislosti na uživatele potřeb a priorit enterprise.

## <a name="benefits-of-a-cloud-devops-ready-application"></a>Výhody DevOps připravené pro cloudové aplikace

Převedením stávající aplikace do aplikace DevOps připravené cloudu (bez předělávání architektury nebo kódování) můžete získat následující výhody:

-   **Nižší náklady, protože spravované infrastruktury je zpracována poskytovatelem cloudu**. Cloudové aplikace připravené pro DevOps získat výhody cloudu, pomocí pružnost se na pole v cloudu, škálování a vysokou dostupnost. Výhody souvisejí ne jenom k funkcím výpočetní (virtuální počítače a kontejnerů), ale také závisí na prostředky v cloudu, jako DBaaS, CaaS a jakékoliv infrastruktury, může být potřeba aplikace.

-   **Odolné aplikace a infrastrukturu**. Když provádíte migraci do cloudu, je nutné zapojení přechodných chyb; bude docházet k chybám v cloudu. Cloudové infrastruktury a hardwaru je také "replaceable," to zvyšuje příležitosti pro přechodný výpadku. Ve stejnou dobu vnitřní cloudovými funkcemi a některé techniky vývoj aplikace, které implementovat odolnost proti chybám a automatizovat obnovení bylo mnohem snazší zotavit po neočekávané selhání v cloudu.

-   **Podrobnější přehled o výkonu aplikací**. Nástroje pro sledování jako Azure Application Insights zadejte vizualizace pro správu stavu, protokolování a oznámení v cloudu. Protokoly auditu zpřístupnit aplikace usnadňuje ladění a auditování. Toto je základní pro spolehlivé cloudové aplikace.

-   **Přenositelnost aplikace s agilní nasazení**. Kontejnery (Linux nebo Windows kontejnery založené na modulu Docker) nabízí nejlepší řešení pro vyloučení je uzamčena cloudové aplikace. Pomocí kontejnery, hostitelů Docker a orchestrators více cloudu, můžete snadno přesouvat z jednoho prostředí nebo cloudu do jiného. Kontejnery eliminovat tření, který obvykle probíhá v nasazeních k libovolnému prostředí (fáze/testovací/produkční).

Všechny tyto výhody nakonec zadejte snížení nákladů klíče životním cyklu aplikací začátku do konce.

V následujících částech tyto výhody jsou vysvětlené podrobněji a jsou propojeny s konkrétní technologie.

>[!div class="step-by-step"]
[Předchozí](index.md)
[další](microsoft-technologies-in-cloud-devops-ready-applications.md)
