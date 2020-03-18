---
title: Architektura bez serveru – aplikace bez serveru
description: Zkoumání různých architektur a aplikací, které jsou podporovány architekturami bez serveru, včetně webových aplikací, mobilních zařízení a IoT.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 838dcd7b41df0d8297e1ae10f9c04a8d5b83b332
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522405"
---
# <a name="serverless-architecture"></a>Bezserverová architektura

Existuje mnoho přístupů k použití architektur [bez serveru.](https://azure.com/serverless) Tato kapitola popisuje příklady běžných architektur, které integrují bezserveru. Zahrnuje také obavy, které mohou představovat další problémy nebo vyžadují další pozornost při implementaci bezserveru. Nakonec je k dispozici několik příkladů návrhu, které ilustrují různé případy použití bez serveru.

Hostitelé bez serveru často používají ke správě instancí bez serveru existující vrstvu založené na kontejnerech nebo PaaS. Například Azure Functions je založen na [Azure App Service](https://docs.microsoft.com/azure/app-service/). Služba App Service se používá k horizontálnímu navýšení kapacity instancí a správě runtime, který spouští kód Azure Functions. Pro funkce založené na systému Windows hostitel běží jako PaaS a škáluje runtime .NET. Pro linuxové funkce hostitel využívá kontejnery.

![Architektura Azure Functions](./media/azure-functions-architecture.png)

Jádro webjobs poskytuje kontext spuštění funkce. Jazyk runtime spouští skripty, spouští knihovny a hostuje rámec pro cílový jazyk. Soubor Node.js se například používá ke spuštění funkcí jazyka JavaScript a rozhraní .NET Framework se používá ke spuštění funkcí jazyka C#. Další informace o možnostech jazyka a platformy najdete dále v této kapitole.

Některé projekty mohou mít prospěch z přijetí "all-in" přístup k bezserveru. Aplikace, které jsou silně závislé na mikroslužbách, mohou implementovat všechny mikroslužby pomocí technologie bez serveru. Většina aplikací jsou hybridní, po n-vrstvé návrhu a pomocí bez serveru pro komponenty, které dávají smysl, protože komponenty jsou modulární a nezávisle škálovatelné. Chcete-li pomoci smysl těchto scénářů, tato část prochází některé běžné architektury příklady, které používají bez serveru.

## <a name="full-serverless-back-end"></a>Full serverless back-end

Full serverless back-end je ideální pro několik typů scénářů, zejména při vytváření nových nebo "zelené pole" aplikace. Aplikace s velkou plochou rozhraní API může mít prospěch z implementace každého rozhraní API jako funkce bez serveru. Aplikace, které jsou založeny na architektuře mikroslužeb, jsou dalším příkladem, který by mohl být implementován jako úplný back-end bez serveru. Mikroslužby komunikovat přes různé protokoly mezi sebou. Konkrétní scénáře zahrnují:

- Produkty SaaS založené na rozhraní API (například procesor finančních plateb).
- Aplikace řízené zprávami (příklad: řešení monitorování zařízení).
- Aplikace zaměřené na integraci mezi službami (například aplikace pro rezervace leteckých společností).
- Procesy, které běží pravidelně (příklad: čištění databáze založené na časovači).
- Aplikace zaměřené na transformaci dat (příklad: import spuštěný nahráváním souborů).
- Extrahovat transformace a zatížení (ETL) procesy.

Existují další, konkrétnější případy použití, které jsou zahrnuty dále v tomto dokumentu.

## <a name="monoliths-and-starving-the-beast"></a>Monolity a "hladovění šelmy"

Běžnou výzvou je migrace existující monolitické aplikace do cloudu. Nejméně riskantní přístup je "výtah a posun" zcela na virtuální stroje. Mnoho obchodů raději využít migraci jako příležitost k modernizaci jejich základ kódu. Praktický přístup k migraci se nazývá "hladovění šelmy". V tomto scénáři monolit je migrována "tak, jak je" začít. Poté jsou vybrané služby modernizovány. V některých případech je podpis služby shodný s originálem: je jednoduše hostován jako funkce. Klienti jsou aktualizovány používat novou službu, nikoli koncový bod monolitu. V mezidobí kroky, jako je replikace databáze povolit mikroslužeb k hostování vlastní úložiště i v případě, že transakce jsou stále zpracovávámonolit. Nakonec jsou všichni klienti migrována do nových služeb. Monolit je "hladověl" (jeho služby již volána), dokud všechny funkce byla nahrazena. Kombinace bezserveru a proxy serverů může usnadnit velkou část této migrace.

![Migrace monolitu bez serveru](./media/serverless-monolith-migration.png)

Další informace o tomto přístupu najdete ve videu: [Přeneste svou aplikaci do cloudu pomocí funkcí Azure bez serveru](https://channel9.msdn.com/Events/Connect/2017/E102).

## <a name="web-apps"></a>Webové aplikace

Webové aplikace jsou skvělými kandidáty pro aplikace bez serveru. Existují dva běžné přístupy k webovým aplikacím dnes: řízený serverem a řízený klientem (například jednostránková aplikace nebo SPA). Webové aplikace řízené serverem obvykle používají vrstvu middlewaru k vydávání volání rozhraní API k vykreslení webového uživatelského rozhraní. Spa aplikace provádět REST API volání přímo z prohlížeče. V obou scénářích bez serveru může vyhovět middleware nebo rest api požadavek poskytnutím potřebné obchodní logiky. Běžnou architekturou je postavit se lehkému statickému webovému serveru. Jednostránková aplikace (SPA) obsluhuje html, CSS, JavaScript a další datové zdroje prohlížeče. Webová aplikace se pak připojí k back-endu mikroslužeb.

## <a name="mobile-back-ends"></a>Mobilní zadní konce

Paradigma aplikací bez serveru založené na událostech z nich dělá ideální jako mobilní back-endy. Mobilní zařízení spustí události a kód bez serveru se spustí, aby vyhověl požadavkům. Využití modelu bez serveru umožňuje vývojářům vylepšit obchodní logiku bez nutnosti nasazení úplné aktualizace aplikace. Přístup bez serveru také umožňuje týmům sdílet koncové body a pracovat paralelně.

Mobilní vývojáři mohou vytvářet obchodní logiku, aniž by se stali odborníky na straně serveru. Mobilní aplikace připojené k místním službám jsou tradičně připojené. Vytvoření vrstvy služby vyžaduje pochopení serverové platformy a programovacího paradigmatu. Vývojáři pracovali s operacemi pro zřizování serverů a jejich vhodnou konfiguraci. Někdy byly dny nebo dokonce týdny vynaloženy na vytváření kanálu nasazení. Všechny tyto problémy jsou řešeny bez serveru.

Serverless abstrahuje závislosti na straně serveru a umožňuje vývojáři zaměřit se na obchodní logiku. Například mobilní vývojář, který vytváří aplikace pomocí javascriptového frameworku, může vytvářet funkce bez serveru také s JavaScriptem. Hostitel bez serveru spravuje operační systém, instanci Node.js pro hostování kódu, závislostí balíčků a další. Vývojáři je poskytnuta jednoduchá sada vstupů a standardní šablona pro výstupy. Poté se mohou zaměřit na vytváření a testování obchodní logiky. Jsou proto schopni využít stávající dovednosti k vytvoření back-end logiky pro mobilní aplikaci, aniž by se museli učit nové platformy nebo se stát "vývojářem na straně serveru".

![Mobilní back-end bez serveru](./media/serverless-mobile-backend.png)

Většina poskytovatelů cloudu nabízí mobilní produkty bez serveru, které zjednodušují celý životní cyklus mobilního vývoje. Produkty mohou automatizovat zřizování databází pro uchování dat, zpracování problémů DevOps, poskytování cloudových sestavení a testovacích architektur a možnost skriptovat obchodní procesy pomocí upřednostňovaného jazyka vývojáře. Po přístupu bez mobilního serveru může tento proces zjednodušit. Serverless odstraňuje obrovské režie zřizování, konfigurace a údržby serverů pro mobilní back-end.

## <a name="internet-of-things-iot"></a>Internet věcí (IoT)

IoT odkazuje na fyzické objekty, které jsou propojeny do sítě. Někdy se označují jako "připojená zařízení" nebo "chytrá zařízení". Vše od automobilů a prodejních automatů může být připojeno a odesílat informace od inventáře až po data senzorů, jako je teplota a vlhkost. IoT v podniku poskytuje vylepšení podnikových procesů prostřednictvím monitorování a automatizace. Údaje ioT mohou být použity k regulaci klimatu ve velkém skladu nebo ke sledování zásob prostřednictvím dodavatelského řetězce. IoT dokáže vycítit chemické skvrny a zavolat hasiče, když je detekován kouř.

Naprostý objem zařízení a informací často určuje architekturu řízenou událostmi pro směrování a zpracování zpráv. Bez serveru je ideálním řešením z několika důvodů:

- Umožňuje škálování s nárůstem objemu zařízení a dat.
- Umožňuje přidávat nové koncové body pro podporu nových zařízení a senzorů.
- Usnadňuje nezávislou správu verzí, takže vývojáři mohou aktualizovat obchodní logiku pro konkrétní zařízení bez nutnosti nasazovat celý systém.
- Odolnost proti chybám a méně prostojů.

Všudypřítomnost IoT má za následek několik bezserverových produktů, které se zaměřují konkrétně na problémy IoT, jako je [azure IoT Hub](https://docs.microsoft.com/azure/iot-hub). Bez serveru automatizuje úlohy, jako je registrace zařízení, vynucení zásad, sledování a dokonce i nasazení kódu do zařízení na *hraničních zařízeních*. Hrana odkazuje na zařízení, jako jsou senzory a akční současně, které jsou připojeny k internetu, ale nejsou aktivní součástí internetu.

>[!div class="step-by-step"]
>[Předchozí](architecture-approaches.md)
>[další](serverless-architecture-considerations.md)
