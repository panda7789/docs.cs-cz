---
title: Důvody pro modernizaci stávajících aplikací .NET na aplikace optimalizované pro cloud
description: Modernizace stávajících aplikací .NET pomocí Azure Cloudu a kontejnerů Windows | Důvody pro modernizaci stávajících aplikací .NET na aplikace optimalizované pro cloud
ms.date: 04/28/2018
ms.openlocfilehash: 55eb3fb9b0b6c91e25bcdb23056a8a8e51463ef7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73093631"
---
# <a name="reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications"></a>Důvody pro modernizaci stávajících aplikací .NET na aplikace optimalizované pro cloud

S aplikací optimalizovanou pro cloud můžete rychle a opakovaně dodávat spolehlivé aplikace svým zákazníkům. Základní flexibilitu a spolehlivost získáte odložením velké části provozní složitosti aplikace na platformu.

Pokud se vám nepodaří rychle uvést své aplikace na trh, v době odeslání aplikace se trh, na který jste cílili, vyvinul. Můžete být příliš pozdě, bez ohledu na to, jak dobře byla aplikace navržena nebo navržena. Možná se vám nedaří nebo nedosahujete svého plného potenciálu, protože nemůžete synchronizovat doručování aplikací s potřebami trhu.

Potřeba neustálých obchodních inovací posouvá vývojové a provozní týmy na hranici možností. Jediný způsob, jak dosáhnout flexibility, kterou potřebujete při neustálých obchodních inovacích, je modernizace vašich aplikací pomocí technologií, jako jsou kontejnery a specifické principy aplikací optimalizované pro cloud.

Pointa je, že když organizace buduje a spravuje aplikace, které jsou optimalizované pro cloud, může dát řešení do rukou zákazníků dříve a přinést nové nápady na trh, když jsou relevantní.

## <a name="cloud-optimized-application-principles-and-tenets"></a>Principy a principy aplikací optimalizované pro cloud

Vylepšení v cloudu se většinou zaměřují na splnění dvou cílů: Snížení nákladů a zlepšení růstu podnikání zlepšením agility. Těchto cílů je dosaženo zjednodušením procesů a snížením tření při uvolnění a odeslání aplikací.

Vaše aplikace je optimalizovaná pro cloud, pokud můžete agilně rozvíjet aplikaci autonomně z jiných místních aplikací a pak uvolnit, nasadit, automaticky škálovat, monitorovat a řešit problémy s aplikací v cloudu.

Klíčem je *hbitost*. Nelze doručovat s agility, pokud snížit na absolutní minimum všechny problémy nasazení k výrobě a vývoj a testování prostředí problémy. Kontejnery (konkrétně Docker, jako de facto standard) a spravované služby byly navrženy speciálně pro tento účel.

K dosažení agility potřebujete také automatizované procesy DevOps, které jsou založeny na kanálech CI/CD, které se vydávají na škálovatelné platformy v cloudu. Platformy CI/CD (jako jsou Služby Azure DevOps services nebo Jenkins), které se nasazují na škálovatelnou a odolnou cloudovou platformu (jako je Azure App Service nebo Služba Azure Kubernetes) jsou klíčové technologie pro dosažení agility v cloudu.

Následující seznam popisuje hlavní principy nebo postupy pro aplikace optimalizované pro cloud. Všimněte si, že můžete přijmout všechny nebo jen některé z těchto zásad, v postupné nebo přírůstkové přístup:

- **Kontejnery**. Kontejnery poskytují možnost zahrnout závislosti aplikací se samotnou aplikací. Kontejnerizace výrazně snižuje počet problémů, se kterými se může dojít při nasazení do produkčního prostředí nebo testování v pracovních prostředích. Kontejnery nakonec zlepšují agilitu doručení aplikace.

- **Odolný a škálovatelný cloud**. Cloud poskytuje platformu, která je spravovaná, elastická, škálovatelná a odolná. Tyto vlastnosti jsou zásadní pro získání zlepšení nákladů a dodání vysoce dostupných a spolehlivých aplikací v nepřetržitém doručování. Spravované služby, jako jsou spravované databáze, spravovaná mezipaměť jako služba (CaaS) a spravované úložiště, jsou základními částmi pro zmírnění nákladů na údržbu vaší aplikace.

- **Monitorování**. Nemůžete mít spolehlivou aplikaci bez nutnosti dobrý způsob, jak zjistit a diagnostikovat výjimky a problémy s výkonem aplikací. Potřebujete získat užitečné přehledy prostřednictvím správy výkonu aplikací a okamžité analýzy.

- **DevOps kultury a průběžné doručování**. Přijetí devOps postupy vyžaduje kulturní změnu, ve kterém týmy již pracují v nezávislých sil. Kanály CI/CD jsou možné pouze v případě, že existuje zvýšená spolupráce mezi vývojovými a it provozními týmy, podporovanými kontejnery a nástroji CI/CD.

Obrázek 4-2 znázorňuje hlavní volitelné pilíře aplikace optimalizované pro cloud. Čím více pilířů implementujete, tím připravenější bude vaše aplikace, aby splnila očekávání vašich zákazníků.

![Diagram s názvem hlavních pilířů aplikace optimalizované pro cloud.](./media/main-pillars-cloud-optimized-application.png)

**Obrázek 4-2.** Hlavní pilíře aplikace optimalizované pro cloud

Abychom to shrnuli, aplikace optimalizovaná pro cloud je přístup k vytváření a správě aplikací, které využívají model cloud computingu, a zároveň používají kombinaci kontejnerů, spravované cloudové infrastruktury, odolných aplikačních technik, monitorování, průběžné doručování a DevOps, to vše bez nutnosti rearchitect a recode vaše stávající aplikace.

Vaše organizace může tyto technologie a přístupy postupně přijímat. Nemusíš je všechny objímat, všechny najednou. Můžete je přijmout postupně v závislosti na prioritách organizace a potřebách uživatelů.

## <a name="benefits-of-a-cloud-optimized-application"></a>Výhody aplikace optimalizované pro cloud

Následující výhody můžete získat převodem existující aplikace na aplikaci optimalizovanou pro cloud (bez rearchitecting nebo kódování):

- **Nižší náklady, protože spravovanou infrastrukturu zpracovává poskytovatel cloudu**. Aplikace optimalizované pro cloud získají výhody cloudu pomocí pružnosti, automatického škálování a vysoké dostupnosti cloudu. Výhody se vztahují nejen k výpočetním funkcím (virtuálnípočítače a kontejnery), ale také závisí na prostředky v cloudu, jako je DBaaS, CaaS a všechny infrastruktury aplikace může potřebovat.

- **Odolné aplikace a infrastruktura**. Když migrujete do cloudu, musíte přijmout přechodná selhání; v cloudu dojde k chybám. Cloudová infrastruktura a hardware jsou také "vyměnitelné", což zvyšuje příležitosti pro přechodné prostoje. Současně funkce vnitřního cloudu a některé techniky vývoje aplikací, které implementují odolnost proti chybám a automatizují obnovení, usnadňují zotavení z neočekávaných selhání v cloudu.

- **Hlubší přehled o výkonu aplikací**. Nástroje pro monitorování cloudu, jako jsou Azure Application Insights, poskytují vizualizaci pro správu stavu, protokolování a oznámení. Protokoly auditu usnadňují ladění a auditování aplikací, což je zásadní pro spolehlivou cloudovou aplikaci.

- **Přenositelnost aplikací s agilnímnasazením**. Kontejnery (linuxové nebo windowskontejnery založené na Docker Engine) nabízejí nejlepší řešení, jak se vyhnout aplikaci uzamčenou v cloudu. Pomocí kontejnerů, hostitelů Dockeru a orchestrátorů s více cloudy můžete snadno přejít z jednoho prostředí nebo cloudu do druhého. Kontejnery eliminují tření, ke kterému obvykle dochází v nasazeních do libovolného prostředí (fáze/test/výroba).

Všechny tyto výhody v konečném důsledku poskytují klíčové snížení nákladů pro váš koncový životní cyklus aplikací.

V následujících částech jsou tyto výhody podrobněji vysvětleny a jsou propojeny s konkrétními technologiemi.

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[další](microsoft-technologies-in-cloud-optimized-applications.md)
