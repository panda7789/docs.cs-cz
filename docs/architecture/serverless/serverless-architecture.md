---
title: Architektura bez serveru – aplikace bez serveru
description: Průzkum různých architektur a aplikací, které podporují architektury bez serveru, včetně webových aplikací, mobilních zařízení a IoT.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 838dcd7b41df0d8297e1ae10f9c04a8d5b83b332
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522405"
---
# <a name="serverless-architecture"></a>Bezserverová architektura

K dispozici je mnoho přístupů k používání architektury bez [serveru](https://azure.com/serverless) . Tato kapitola popisuje příklady běžných architektur, které integrují bez serveru. Týká se taky otázek, které mohou při implementaci bez serveru způsobovat další výzvy nebo vyžadují další pozornost. Nakonec jsou k dispozici několik příkladů návrhů, které ilustrují různé případy použití bez serveru.

Hostitelé bez serveru často používají ke správě instancí bez serveru existující vrstvu založenou na kontejnerech nebo PaaS. Například Azure Functions je založen na [Azure App Service](https://docs.microsoft.com/azure/app-service/). App Service slouží k horizontálnímu navýšení kapacity instancí a ke správě modulu runtime, který spouští kód Azure Functions. Pro funkce založené na systému Windows hostitel běží jako PaaS a škáluje prostředí .NET Runtime. Pro funkce založené na systému Linux hostitel využívá kontejnery.

![Architektura Azure Functions](./media/azure-functions-architecture.png)

Jádro WebJobs poskytuje kontext spuštění funkce. Modul runtime jazyka spouští skripty, spouští knihovny a hostuje rozhraní pro cílový jazyk. Například Node. js slouží ke spouštění funkcí jazyka JavaScript a .NET Framework slouží ke spouštění C# funkcí. Další informace o možnostech jazyka a platformy najdete dále v této kapitole.

Některé projekty můžou využít přístup "všechny" k serveru bez serveru. Aplikace, které se spoléhají na mikroslužby, můžou implementovat všechny mikroslužby pomocí technologie bez serveru. Většina aplikací je hybridní, za použití N-vrstvého návrhu a používání serveru bez serveru pro součásti, které dává smysl, protože komponenty jsou modulární a nezávisle škálovatelné. Tato část vás seznámí s některými běžnými příklady architektury, které používají bez serveru. Tyto scénáře vám pomůžou.

## <a name="full-serverless-back-end"></a>Úplný back-end bez serveru

Úplný back-end bez serveru je ideální pro několik typů scénářů, zejména při sestavování nových nebo "zelených" polí "aplikací. Aplikace s velkou plochou rozhraní API může přinést implementaci jednotlivých rozhraní API jako funkce bez serveru. Aplikace, které jsou založené na architektuře mikroslužeb, jsou další příklad, který by se mohl implementovat jako úplný back-end Server bez serveru. Mikroslužby komunikují přes různé protokoly navzájem. Mezi konkrétní scénáře patří:

- SaaS produkty založené na rozhraní API (příklad: procesor finančních plateb).
- Aplikace řízené zprávami (příklad: řešení monitorování zařízení).
- Aplikace zaměřené na integraci mezi službami (příklad: aplikace pro rezervaci letenek).
- Procesy, které se spouštějí pravidelně (například: vyčištění databáze na základě časovače).
- Aplikace zaměřené na transformaci dat (příklad: import aktivovaný při nahrávání souboru)
- Extrakce procesů transformace a načítání (ETL).

Existují další, konkrétnější případy použití, které jsou pokryty dále v tomto dokumentu.

## <a name="monoliths-and-starving-the-beast"></a>Monolitů a "omezují The touchdown"

Běžným problémem je migrace stávající aplikace v monolitické do cloudu. Minimální rizikový přístup je "zaznamenání a posunutí" výhradně na virtuální počítače. Řada prodejen preferuje použití migrace jako příležitosti k modernizovatí jejich základu kódu. Praktický přístup k migraci se nazývá "omezují The touchdown". V tomto scénáři se monolitu migruje "tak, jak je", aby se spouštěl. Pak jsou vybrané služby moderní. V některých případech je podpis služby stejný jako původní: stačí ho hostovat jako funkce. Klienti se aktualizují, aby používali novou službu, a ne koncový bod monolitu. V předběžných krocích, jako je třeba replikace databáze, umožňují mikroslužbám hostovat své vlastní úložiště i v případě, že monolitu transakce stále zpracovává. Nakonec se všechny klienty migrují na nové služby. Monolitu je "nedostatek" (jeho služby již nejsou volány), dokud nebudou nahrazeny všechny funkce. V kombinaci bez serveru a proxy serverů se dá tato migrace zjednodušit.

![Migrace monolitu bez serveru](./media/serverless-monolith-migration.png)

Další informace o tomto přístupu najdete v tomto videu: [převedení aplikace do cloudu s využitím Azure Functions bez serveru](https://channel9.msdn.com/Events/Connect/2017/E102).

## <a name="web-apps"></a>Webové aplikace

Webové aplikace jsou skvělými kandidáty pro aplikace bez serveru. Existují dva běžné přístupy k webovým aplikacím v dnešní době: na základě serveru a na straně klienta (například aplikace s jednou stránkou nebo SPA). Webové aplikace řízené serverem obvykle používají vrstvu middlewaru k vystavení volání rozhraní API pro vykreslení webového uživatelského rozhraní. Aplikace SPA vyvolají REST API volání přímo z prohlížeče. V obou scénářích může server bez serveru pojmout middleware nebo REST API požadavek poskytnutím potřebné obchodní logiky. Běžnou architekturou je vytvoření jednoduchého statického webového serveru. Jednostránkové aplikace (SPA) obsluhuje HTML, CSS, JavaScript a další prostředky prohlížeče. Webová aplikace se pak připojí k back-endu mikroslužeb.

## <a name="mobile-back-ends"></a>Mobilní back-endy

Paradigma aplikace bez serveru, které jsou založené na událostech, jsou ideální jako mobilní back-endy. Mobilní zařízení spustí události a kód bez serveru se spustí, aby splňoval požadavky. Využití modelu bez serveru umožňuje vývojářům vylepšit obchodní logiku, aniž by museli nasazovat úplnou aktualizaci aplikace. Přístup bez serveru taky umožňuje týmům sdílet koncové body a pracovat paralelně.

Mobilní vývojáři můžou sestavovat obchodní logiku bez toho, aby se na straně serveru stali odborníky. Obvykle se jedná o mobilní aplikace připojené k místním službám. Sestavování vrstvy služby vyžaduje porozumění serverové platformě a paradigmatu programování. Vývojáři pracovali s operacemi pro zřízení serverů a jejich správné konfiguraci. Při vytváření kanálu nasazení byly někdy vyčerpány dny nebo dokonce týdny. Všechny tyto výzvy jsou řešeny bez serveru.

Server bez serveru vyabstrakce závislosti na straně serveru a umožňuje vývojářům soustředit se na obchodní logiku. Například mobilní vývojář, který sestavuje aplikace pomocí rozhraní JavaScript Framework, může také sestavovat funkce bez serveru pomocí JavaScriptu. Hostitel bez serveru spravuje operační systém, instanci Node. js, která hostuje kód, závislosti balíčků a další. Vývojář poskytuje jednoduchou sadu vstupů a standardní šablonu pro výstup. Pak se můžou soustředit na vytváření a testování obchodní logiky. Díky tomu je možné využít stávající dovednosti k sestavení logiky back-endu pro mobilní aplikaci, aniž by se museli učit nové platformy nebo se stát vývojářem na straně serveru.

![Mobilní back-end bez serveru](./media/serverless-mobile-backend.png)

Většina poskytovatelů cloudových služeb nabízí mobilní produkty bez serveru, které zjednodušují celý životní cyklus vývoje mobilních aplikací. Produkty mohou automatizovat zřizování databází pro uchovávání dat, zpracovávat DevOps obavy a poskytovat cloudová sestavení a testovací architektury a možnost skriptování obchodních procesů pomocí preferovaného jazyka vývojáře. Tento proces může zjednodušit následující přístup k serveru, který je zaměřený na mobilní zařízení. Server bez serveru odebírá obrovské nároky na zřizování, konfiguraci a údržbu serverů pro mobilní back-end.

## <a name="internet-of-things-iot"></a>Internet věcí (IoT)

IoT odkazuje na fyzické objekty, které jsou propojeny společně. Někdy se označují jako "připojená zařízení" nebo "inteligentní zařízení". Všechno od auta a prodejní automaty se může propojit a odesílat informace od inventáře až po data senzorů, jako je teplota a vlhkost. V podniku nabízí IoT vylepšení obchodních procesů prostřednictvím monitorování a automatizace. Data IoT se dají použít k regulaci klimatu ve velkém skladu nebo sledování inventáře prostřednictvím dodavatelského řetězce. IoT může pochopit chemické neoblasti a vyvolat požární oddělení, když se zjistí kouř.

Sheer objem zařízení a informací často vykazuje architekturu řízenou událostmi pro směrování a zpracování zpráv. Neserveru je ideální řešení z několika důvodů:

- Umožňuje škálování při zvyšování objemu zařízení a dat.
- Přizpůsobí přidávání nových koncových bodů pro podporu nových zařízení a senzorů.
- Usnadňuje nezávislé správy verzí, takže vývojáři můžou aktualizovat obchodní logiku pro konkrétní zařízení, aniž by museli nasazovat celý systém.
- Odolnost a méně výpadků.

Výsledkem pronikavostí IoT je několik produktů bez serveru, které se zaměřují konkrétně na problematiku IoT, jako je třeba [Azure IoT Hub](https://docs.microsoft.com/azure/iot-hub). Bez serveru se automatizují úlohy, jako je registrace zařízení, vynucování zásad, sledování a dokonce nasazení kódu do zařízení na *hraničních*zařízeních. Tato hrana odkazuje na zařízení, jako jsou senzory a poháněcí zařízení, která jsou připojená k Internetu, ale nejsou aktivní součástí.

>[!div class="step-by-step"]
>[Předchozí](architecture-approaches.md)
>[Další](serverless-architecture-considerations.md)
