---
title: Důvody pro modernizovatí stávajících aplikací .NET na cloudově optimalizované aplikace
description: Modernizovat stávající aplikace .NET pomocí cloudu Azure a kontejnerů Windows | Důvody pro modernizovatí stávajících aplikací .NET na cloudově optimalizované aplikace
ms.date: 04/28/2018
ms.openlocfilehash: 55eb3fb9b0b6c91e25bcdb23056a8a8e51463ef7
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/08/2019
ms.locfileid: "73093631"
---
# <a name="reasons-to-modernize-existing-net-apps-to-cloud-optimized-applications"></a>Důvody pro modernizovatí stávajících aplikací .NET na cloudově optimalizované aplikace

Díky optimalizované cloudové aplikaci můžete zákazníkům rychle a opakovaně doručovat spolehlivé aplikace. Základní flexibilitu a spolehlivost získáte tak, že odvedete značnou provozní složitost vaší aplikace na platformu.

Pokud nemůžete vašim aplikacím rychle začít na trhu, bude se v době, kdy jste doložili vaši aplikaci, vyvíjet i trh, který jste se zaměřuje. Může být příliš pozdě bez ohledu na to, jak dobře došlo k navržení nebo analýze aplikace. Může se stát, že nebudete mít úplný potenciál, protože nemůžete synchronizovat doručování aplikací s potřebou trhu.

Potřeba průběžných firemních inovací do limitu nabízí vývoj a provozní týmy. Jediným způsobem, jak dosáhnout flexibility, kterou potřebujete při průběžných inovacích, je modernizaci vašich aplikací s využitím technologií jako kontejnerů a specifických principů aplikací optimalizovaných pro Cloud.

Dolním řádkem je, že když organizace sestavuje a spravuje aplikace, které jsou optimalizované pro Cloud, můžou do rukou zákazníků vložit řešení a při jejich relevantních nápadech přinášet nové nápady na trh.

## <a name="cloud-optimized-application-principles-and-tenets"></a>Principy a principy optimalizované pro cloudové aplikace

Vylepšení v cloudu se většinou zaměřují na splnění dvou cílů: Snižte náklady a zvyšte růst podnikání díky vylepšení flexibility. Tyto cíle se dosahují zjednodušením procesů a snížením třením při vydávání a dodávání aplikací.

Vaše aplikace je optimalizovaná pro Cloud, pokud můžete agilní způsob – vyvíjet aplikaci samostatně z jiných místních aplikací a potom vydávat, nasazovat, automaticky škálovat, monitorovat a řešit potíže s aplikací v cloudu.

Klíč je *flexibilita*. Nemůžete dodávat s flexibilitou, pokud se nesnížíte na absolutní minimální problémy s nasazením na produkční prostředí a problémy pro vývoj a testování. Kontejnery (konkrétně Docker jako de facto standard) a spravované služby byly navrženy speciálně pro tento účel.

Pro dosažení flexibility potřebujete také automatizované procesy DevOps, které jsou založeny na kanálech CI/CD, které jsou vydány pro škálovatelné platformy v cloudu. Platformy CI/CD (jako Azure DevOps Services nebo Jenkinse), které se nasazují na škálovatelnou a odolnou cloudovou platformu (jako je Azure App Service nebo Azure Kubernetes), jsou klíčové technologie pro dosažení flexibility v cloudu.

Následující seznam popisuje hlavní principy nebo postupy pro cloudově optimalizované aplikace. Všimněte si, že v progresivním nebo přírůstkovém přístupu můžete přijmout všechny nebo jenom některé z těchto principů:

- **Kontejnery**. Kontejnery umožňují zahrnout závislosti aplikací do samotné aplikace. Vytváření kontejnerů významně snižuje počet problémů, se kterými se můžete setkat při nasazení do produkčních prostředí nebo testování v pracovních prostředích. Kontejnery v konečném důsledku zlepšují flexibilitu doručování aplikací.

- **Odolný a škálovatelný Cloud**. Cloud poskytuje platformu, která je spravovaná, pružná, škálovatelná a odolná. Tyto charakteristiky jsou zásadní pro získání cenových vylepšení a při průběžném doručování vysoce dostupných a spolehlivých aplikací. Spravované služby, jako jsou spravované databáze, spravovaná mezipaměť jako služba (CaaS) a spravované úložiště, jsou základními částmi, které řeší náklady na údržbu vaší aplikace.

- **Monitorování**. Nemůžete mít spolehlivou aplikaci, aniž byste měli dobrý způsob, jak detekovat a diagnostikovat výjimky a problémy s výkonem aplikací. Potřebujete získat užitečné poznatky prostřednictvím správy výkonu aplikací a okamžitých analýz.

- **DevOps kultura a průběžné doručování**. Přijetí postupů DevOps vyžaduje kulturní změnu, ve které týmy již nefungují v nezávislých silech. Kanály CI/CD jsou možné jenom v případě, že se zvýšila spolupráce mezi vývojovými a provozními týmy, které podporují kontejnery a nástroje CI/CD.

Obrázek 4-2 ukazuje hlavní volitelné pilíře aplikace optimalizované pro Cloud. U více sloupků, které implementujete, bude mít připravenost vaší aplikace po splnění očekávání vašich zákazníků úspěch.

![Diagram pojmenovává hlavní pilíře aplikace optimalizované pro Cloud.](./media/main-pillars-cloud-optimized-application.png)

**Obrázek 4-2.** Hlavní pilíře aplikace optimalizované pro Cloud

Cloudově optimalizovaná aplikace představuje přístup k vytváření a správě aplikací, které využívají model cloud computingu, a přitom využívají kombinaci kontejnerů, spravované cloudové infrastruktury, odolných aplikačních technik, monitorování, průběžné doručování a DevOps, a to vše bez nutnosti rearchitektovat a Recode vaše stávající aplikace.

Vaše organizace může tyto technologie a přístupy postupně přijmout. Nemusíte je vůbec využívat, a to vše najednou. Můžete je přijmout přírůstkově v závislosti na prioritách Enterprise a uživatelských potřebách.

## <a name="benefits-of-a-cloud-optimized-application"></a>Výhody aplikace optimalizované pro Cloud

Následující výhody můžete získat převodem existující aplikace do aplikace optimalizované pro Cloud (bez nutnosti opětovného vytváření architektů nebo kódování):

- **Nižší náklady, protože spravovaná infrastruktura je zpracovávána poskytovatelem cloudu**. Cloudově optimalizované aplikace získají výhody cloudu s využitím špičkové pružnosti, automatického škálování a vysoké dostupnosti cloudu. Výhody se týkají nejen výpočetních funkcí (virtuálních počítačů a kontejnerů), ale také závisí na prostředcích v cloudu, jako je DBaaS, CaaS a jakékoli infrastruktuře, které může aplikace potřebovat.

- **Odolná aplikace a infrastruktura** Když migrujete do cloudu, budete muset zamezit přechodným selháním. v cloudu dojde k selhání. Cloudová infrastruktura a hardware jsou taky "nahraditelný", což zvyšuje možnosti přechodného výpadku. Funkce vnitřního cloudu a některé techniky vývoje aplikací, které implementují odolnost a automatizované obnovení, výrazně usnadňují zotavení z neočekávaných chyb v cloudu, a to ve stejnou chvíli.

- **Hlubší přehledy o výkonu aplikace**. Nástroje pro monitorování cloudu, jako je Azure Application Insights, poskytují vizualizaci pro správu stavu, protokolování a oznámení. Protokoly auditu umožňují aplikacím snadné ladění a audit, základní pro spolehlivou cloudovou aplikaci.

- **Přenositelnost aplikací s agilními nasazeními**. Kontejnery (v kontejnerech Linux nebo Windows na základě Docker Engine) nabízejí nejlepší řešení pro zamezení aplikace uzamčené pro Cloud. Díky kontejnerům, hostitelům Docker a orchestraci více cloudů můžete snadno přesouvat z jednoho prostředí nebo cloudu do jiného. Kontejnery odstraňují tření, ke kterému obvykle dochází v nasazeních do jakéhokoli prostředí (fáze/testování/produkce).

Všechny tyto výhody nakonec poskytují klíčové snížení nákladů pro celý životní cyklus aplikace.

V následujících částech jsou tyto výhody vysvětleny podrobněji a jsou propojeny s konkrétními technologiemi.

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[Další](microsoft-technologies-in-cloud-optimized-applications.md)
