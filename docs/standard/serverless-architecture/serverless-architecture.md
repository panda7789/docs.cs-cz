---
title: Architektura bez serveru – aplikace bez serveru
description: Zkoumání různých architekturách a aplikace, které podporuje architektury bez serveru, včetně webových aplikací, mobilních a IoT.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 60d225d9794d5c15b0cd8e42800ccad4d7872756
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967794"
---
# <a name="serverless-architecture"></a>Bezserverová architektura

Existuje celá řada přístupů k použití [bez serveru](http://azure.com/serverless) architektury. Tato kapitola popisuje, příklady běžných architektur, které se integrují bez serveru. Věnuje se také, se kterými můžou představovat další výzvy, nebo vyžadují zvláštní pozornost při provádění bez serveru. Nakonec několik příkladů návrhu jsou k dispozici, které znázorňují různé případy použití bez serveru.

Bez serveru hostitele často používají stávající založených na kontejnerech nebo vrstvu PaaS pro správu instancí bez serveru. Například je Azure Functions na základě [služby Azure App Service](https://docs.microsoft.com/azure/app-service/). App Service umožňuje horizontálně navýšit kapacitu instancí a spravovat modul runtime, která spustí kód Azure Functions. Spuštění hostitele jako PaaS a škálování pro funkce založené na Windows out modul .NET runtime. Pro funkce založené na Linuxu využívá hostitele kontejnery.

![Architektura služby Azure Functions](./media/azure-functions-architecture.png)

Základní WebJobs poskytuje kontext spuštění pro funkci. Language Runtime spustí skripty, provede knihovny a rozhraní pro cílový jazyk je hostitelem. Například Node.js se používá ke spuštění funkce jazyka JavaScript a rozhraní .NET Framework se používá ke spuštění funkcí jazyka C#. Informace o možnostech jazyka a libovolné platformy dále v této kapitole dozvíte.

Některé projekty můžou mít užitek z přesměrujeme "čistě" přístup bez serveru. Aplikace, které často využívají mikroslužeb může implementovat všechny mikroslužby pomocí technologie bez serverů. Většina aplikací jsou hybridní, následující při návrhu N-vrstvé a pomocí bez serveru pro součásti, které dávají smysl, protože se součásti modulární a nezávisle škálovatelné. Abychom pomohli vyznat se tyto scénáře, tato část vás provede několik běžných příkladů architektury, které používají bez serveru.

## <a name="full-serverless-back-end"></a>Bez úplného serveru back-endu

Bez úplného serveru back-endem je ideální pro různé druhy scénářů, zejména v případě, že nové sestavení nebo aplikace "zelené louce". Aplikace s velké plochy rozhraní API můžou mít užitek z implementace každé rozhraní API jako funkce bez serveru. Aplikace, které jsou založené na architektuře mikroslužeb jsou další příklad, který by mohl implementovat jako úplné bez serveru back-end. Mikroslužby komunikují přes různé protokoly, které mezi sebou. Konkrétní scénáře patří:

* Produktů založených na rozhraní API SaaS (například: finanční platby procesoru).
* Aplikace řízené zprávami (Příklad: řešení pro monitorování zařízení).
* Aplikace, zaměřuje na integraci mezi službami (Příklad: aplikace rezervace letenek).
* Procesy, které pravidelně spouštět (Příklad: čištění databáze na základě časovače).
* Aplikace, zaměřuje na transformaci dat (Příklad: import aktivované nahrání souboru).
* Extrakce, transformace a načítání (ETL) procesů.

Existují jiné, konkrétnější případy použití, které jsou popsané dále v tomto dokumentu.

## <a name="monoliths-and-starving-the-beast"></a>Monolitické a "omezují touchdown"

Běžné výzvy je migrace stávající monolitické aplikace do cloudu. Minimální rizikové přístupem je metodou "lift and shift" zcela do virtuálních počítačů. Mnoho kavárnách dávají přednost používání migrace jako příležitost k modernizaci jejich základu kódu. Praktický postup migrace se nazývá "omezují touchdown." V tomto scénáři je migrovat monolitu "tak jak jsou" začít. Potom se modernizovala vybrané služby. V některých případech je totožná s původní podpis služby: jednoduše je hostovaný jako funkce. Klienti jsou aktualizované na používání nové službě, nikoli monolitu koncového bodu. Prozatím povolit kroky, jako třeba replikace databáze mikroslužeb pro hostování své vlastní úložiště i v případě, že transakce jsou stále zpracována monolitu. Nakonec všichni klienti se migrují do nové služby. Monolitu je "vyčerpaná" (jejích služeb už volá) až se nahradil všechny funkce. Kombinace prostředí bez serveru a proxy serverů může usnadnit velkou část této migrace.

![Migrace monolitu bez serveru](./media/serverless-monolith-migration.png)

Další informace o tento přístup, podívejte se na video: [Přeneste svoje aplikace do cloudu s využitím Azure Functions](https://channel9.msdn.com/Events/Connect/2017/E102).

## <a name="web-apps"></a>Webové aplikace

Webové aplikace jsou skvělými kandidáty pro aplikace bez serveru. Existují dva běžné přístupy do webové aplikace ještě dnes: řízené serveru a klienta řízené (například jednostránkové aplikace nebo SPA). Řízených serverem webových aplikací obvykle používají vrstvu middleware vydat volání rozhraní API pro vykreslení ve webovém uživatelském rozhraní. Aplikace SPA volat rozhraní REST API přímo z prohlížeče. V obou případech bez serveru tím, že poskytuje nezbytné obchodní logiku zvládne middleware nebo požadavku REST API. Běžné architektury, je vytvoření statické odlehčeného webového serveru. Jediné stránce aplikace (SPA) slouží HTML, CSS, JavaScript a dalších zdrojů prohlížeče. Webové aplikace se pak připojí k back-end mikroslužeb.

## <a name="mobile-back-ends"></a>Mobilní back-EndY

Založený na událostech paradigma aplikace bez serveru jsou ideální jako mobilní back-endů. Mobilní zařízení se aktivuje události a spustí kód bez serveru ke splnění požadavků. Využití výhod modelu bez serveru umožňuje vývojářům ke zvýšení obchodní logiky bez nutnosti nasazovat aktualizace celou aplikaci. Bez serveru přístup také umožňuje týmům sdílet koncové body a paralelní práci.

Vývojáře mobilních aplikací můžete vytvářet obchodní logiku bez stát odborníci na straně serveru. Tradičně mobilní aplikace připojené k místní služby. Vytvoření vrstvy služby vyžaduje pochopení serverová platforma a programovacího paradigmatu. Vývojáři ve spolupráci s operacemi ke zřízení serverů a správně nakonfigurovat. Někdy dny nebo týdny i byly strávený na vytváření procesních toků pro nasazení. Všechny tyto problémy jsou vyřešeny bez serveru.

Bez serveru abstrahuje závislostí na straně serveru a umožňuje vývojářům soustředit se na obchodní logiku. Například vývojáře mobilních aplikací, který vytváří aplikace s využitím Javascriptové architektury můžete sestavovat funkce bez serveru s použitím jazyka JavaScript také. Bez serveru hostitele spravuje operační systém Node.js instanci k hostování kódu, závislosti balíčků a další. Vývojář se poskytuje jednoduchou sadu vstupů a standardní šablony pro výstupy. Potom můžou soustředit na vytváření a testování obchodní logiku. Proto si mohou využívat stávající dovednosti můžete vytvářet logiku back-end mobilní aplikace bez nutnosti další nové platformy nebo se Staňte "vývojář na straně serveru."

![Bez serveru mobilních back end](./media/serverless-mobile-backend.png)

Většina poskytovatelů cloudu nabízejí bez serveru produktů založených na mobilní zařízení, které Zjednodušte celý vývoj mobilních řešení životního cyklu. Produkty mohou automatizovat zřizování databází pro trvalé uchování dat, zpracování se týká DevOps, poskytovat cloudové sestavení a testování rozhraní a schopnost skript obchodních procesů pomocí vývojáře upřednostňovaného jazyka. Zaměřené na mobilní zařízení bez serveru přístupu může zjednodušit proces. Bez serveru odebere ohromné nároky na zřizování, konfigurace a údržby serverů pro mobilní back-endu.

## <a name="internet-of-things-iot"></a>Internet věcí (IoT)

IoT odkazuje na fyzických objektů, které jsou propojeny. Tyto jsou někdy označovány jako "připojených zařízení" nebo "inteligentní zařízení." Vše od automobilů a automaty může být připojen a odeslat informace od inventáře do data ze senzorů, jako je například teploty a vlhkosti. V podnikové síti IoT poskytuje obchodní proces vylepšení prostřednictvím monitorování a automatizace. IoT data může sloužit k regulovat podnebí velké skladu nebo sledování inventáře prostřednictvím dodavatelský řetězec. IoT můžete smysl chemických rozlévání a volat oddělení fire při zjištění kouře.

K velkému množství zařízení a informace o často přikazuje architektura založená na událostech trasy a zpracování zpráv. Bez serveru je ideálním řešením z několika důvodů:

* Umožňuje škálovat podle objemu zařízení a dat zvyšuje.
* Přizpůsobuje přidání nové koncových bodů pro podporu nové zařízení a senzorů.
* Nezávislé správy verzí usnadňuje vývojářům mohli aktualizovat obchodní logiku pro konkrétní zařízení, aniž byste museli nasadit celý systém.
* Odolnost proti chybám a méně výpadků.

Pronikavostí IoT přinesl několik produktů bez serveru, které se zaměřují konkrétně na IoT obavy, jako například [Azure IoT Hub](https://docs.microsoft.com/azure/iot-hub). Bez serveru automatizuje úlohy, jako je registrace zařízení, vynucení zásad, sledování a dokonce i nasazení kódu do zařízení v *na hraničních zařízeních*. Na hraničních zařízeních odkazuje na zařízení, senzory a Pohony, které jsou připojeny k, avšak není aktivní součástí z Internetu.

>[!div class="step-by-step"]
>[Předchozí](architecture-approaches.md)
>[další](serverless-architecture-considerations.md)
