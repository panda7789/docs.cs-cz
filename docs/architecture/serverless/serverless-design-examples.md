---
title: Příklady návrhu bez serveru – aplikace bez serveru
description: Seznamte se s různými scénáři podporovanými architekturami bez serveru, od plánování a zpracování založeného na událostech až po aktivační události souborů a proces datového proudu.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: b4e8fda0c1423c881c0807602e11f7c49ff7cfe4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73093559"
---
# <a name="serverless-design-examples"></a>Příklady bezserverového návrhu

Existuje mnoho návrhových vzorů, které existují pro bezserveru. Tato část zachycuje některé běžné scénáře, které používají bez serveru. Všechny příklady mají společné základní kombinaci aktivační události a obchodní logiky.

## <a name="scheduling"></a>Plánování

Plánování úkolů je běžnou funkcí. Následující diagram znázorňuje starší databázi, která nemá odpovídající kontroly integrity. Databázi je nutné pravidelně odstraňovat. Funkce bez serveru najde neplatná data a vyčistí je. Aktivační událost je časovač, který spouští kód podle plánu.

![Plánování bez serveru](./media/serverless-scheduling.png)

## <a name="command-and-query-responsibility-segregation-cqrs"></a>Command and Query Responsibility Segregation (CQRS)

Oddělení odpovědnosti příkazů a dotazů (CQRS) je vzor, který poskytuje různá rozhraní pro čtení (nebo dotazování) dat a operací, které upravují data. Řeší několik běžných problémů. V tradičních systémech založených na aktualizaci vytvořit číst (CRUD) mohou konflikty vzniknout z velkého objemu čtení i zápisů do stejného úložiště dat. Uzamčení může často dojít a výrazně zpomalit čtení. Data jsou často prezentována jako složený z několika objektů domény a operace čtení musí kombinovat data z různých entit.

Pomocí CQRS čtení může zahrnovat speciální "sloučí" entitu, která modely data tak, jak je spotřebována. Čtení je zpracována jinak, než jak je uložen. Například i když databáze může ukládat kontakt jako záznam záhlaví s podřízeným záznamem adresy, čtení může zahrnovat entitu s vlastnostmi záhlaví i adresy. Existuje nesčetné množství přístupů k vytvoření modelu čtení. Může se zhmotnit z pohledů. Operace aktualizace mohou být zapouzdřeny jako izolované události, které pak aktivují aktualizace dvou různých modelů. Pro čtení a zápis existují samostatné modely.

![Příklad CQRS](./media/cqrs-example.png)

Bez serveru může pojmout vzor CQRS tím, že poskytuje oddělené koncové body. Jedna funkce bez serveru umožňuje dotazy nebo čtení a jiná funkce bez serveru nebo sada funkcí zpracovává operace aktualizace. Funkce bez serveru může být také zodpovědná za udržování modelu čtení aktuální a může být spuštěna [zdrojem změn](https://docs.microsoft.com/azure/cosmos-db/change-feed)databáze . Vývoj front-endu je zjednodušen pro připojení k potřebným koncovým bodům. Zpracování událostí je zpracováno na back-endu. Tento model také škáluje pro velké projekty, protože různé týmy mohou pracovat na různých operacích.

## <a name="event-based-processing"></a>Zpracování založené na událostech

V systémech založených na zprávy jsou události často shromažďovány ve frontách nebo tématech vydavatele/odběratele, které mají být zpracovány. Tyto události mohou aktivovat funkce bez serveru pro spuštění části obchodní logiky. Příkladem zpracování založeného na událostech jsou systémy se zdroji událostí. "Událost" je aktivována k označení úkolu jako dokončeného. Funkce bez serveru spuštěná událostí aktualizuje příslušný databázový dokument. Druhá funkce bez serveru může použít událost k aktualizaci modelu čtení pro systém. [Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview) poskytuje způsob, jak integrovat události s funkcemi jako předplatitelé.

> Události jsou informační zprávy. Další informace naleznete v [tématu Event Sourcing pattern](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing).

## <a name="file-triggers-and-transformations"></a>Aktivační události a transformace souborů

Extrakce, transformace a zatížení (ETL) je běžná obchodní funkce. Bez serveru je skvělé řešení pro ETL, protože umožňuje kód, který má být spuštěn jako součást kanálu. Jednotlivé součásti kódu mohou řešit různé aspekty. Jedna funkce bez serveru může stáhnout soubor, jiný použije transformaci a jiný načte data. Kód lze testovat a nasadit nezávisle, což usnadňuje údržbu a škálování v případě potřeby.

![Aktivační události a transformace souborů bez serveru](./media/serverless-file-triggers.png)

V diagramu "cool storage" poskytuje data, která je analyzována v [Azure Stream Analytics](https://docs.microsoft.com/azure/stream-analytics). Všechny problémy, které se vyskytují v datovém proudu, aktivují funkci Azure k řešení anomálie.

## <a name="asynchronous-background-processing-and-messaging"></a>Asynchronní zpracování na pozadí a zasílání zpráv

Asynchronní zasílání zpráv a zpracování na pozadí umožňují aplikacím zahájit procesy bez nutnosti čekání. Příkladem asynchronního zpracování je aplikace OCR. Obrázek je odeslán a zařazen do fronty ke zpracování. Skenování obrázku za účelem extrahování textu může nějakou dobu trvat a po jeho dokončení je odesláno oznámení. Bez serveru může zpracovat vyvolání a výsledek v tomto scénáři.

## <a name="web-apps-and-apis"></a>Webové aplikace a rozhraní API

Oblíbeným scénářem pro serverbez serveru jsou n-vrstvé aplikace, nejčastěji ty, kde vrstva uživatelského portálu je webová aplikace. Popularita jednostránkových aplikací (SPA) se v poslední době zvýšila. Aplikace SPA vykreslují jednu stránku a pak se spoléhají na volání rozhraní API a vrácená data, aby dynamicky vykreslovaly nové rozhraní, aniž by bylo znovu načítáno celou stránku. Vykreslování na straně klienta poskytuje koncovému uživateli mnohem rychlejší a citlivější aplikaci.

Koncové body bez serveru spouštěné voláním HTTP lze použít ke zpracování požadavků rozhraní API. Společnost poskytující reklamní služby může například volat funkci bez serveru s informacemi o profilu uživatele a požadovat vlastní reklamu. Funkce bez serveru vrátí vlastní reklamu a webová stránka ji vykreslí.

![Webové rozhraní API bez serveru](./media/serverless-web-api.png)

## <a name="data-pipeline"></a>Data Pipeline

Funkce bez serveru lze použít k usnadnění datového kanálu. V tomto příkladu soubor aktivuje funkci pro překlad dat v souboru CSV do datových řádků v tabulce. Uspořádaná tabulka umožňuje řídicímu panelu Power BI prezentovat analýzy koncovému uživateli.

![Datový kanál bez serveru](./media/serverless-data-pipeline.png)

## <a name="stream-processing"></a>Zpracování streamů

Zařízení a senzory často generují proudy dat, které musí být zpracovány v reálném čase. Existuje celá řada technologií, které mohou zachytit zprávy a datové proudy z centra událostí a [služby](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs) [IoT Hub](https://docs.microsoft.com/azure/iot-hub) do [service bus](https://docs.microsoft.com/azure/service-bus). Bez ohledu na přenos je bezserveru ideálním mechanismem pro zpracování zpráv a datových proudů dat při jejich příchozích. Bez serveru lze škálovat rychle tak, aby splňovaly požadavky na velké objemy dat. Kód bez serveru můžete použít obchodní logiku analyzovat data a výstup ve strukturovaném formátu pro akce a analýzy.

![Zpracování datového proudu bez serveru](./media/serverless-stream-processing.png)

## <a name="api-gateway"></a>Brána rozhraní API

Brána rozhraní API poskytuje klientům jeden vstupní bod a pak inteligentně směruje požadavky na back-endové služby. Je užitečné spravovat velké sady služeb. Dokáže také zpracovat správu verzí a zjednodušit vývoj snadným připojením klientů k různorodým prostředím. Bez serveru může zpracovat back-end škálování jednotlivých mikroslužeb při prezentaci jednoho front-endu prostřednictvím brány rozhraní API.

![Brána rozhraní API bez serveru](./media/serverless-api-gateway.png)

## <a name="recommended-resources"></a>Doporučené zdroje

- [Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview)
- [Azure IoT Hub](https://docs.microsoft.com/azure/iot-hub)
- [Výzvy a řešení správy distribuovaných dat](../microservices/architect-microservice-container-applications/distributed-data-management.md)
- [Navrhování mikroslužeb: identifikace hranic mikroslužeb](https://docs.microsoft.com/azure/architecture/microservices/microservice-boundaries)
- [Centra událostí](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs)
- [Vzor získávání událostí](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)
- [Implementace vzoru Circuit Breaker](../microservices/implement-resilient-applications/implement-circuit-breaker-pattern.md)
- [IoT Hub](https://docs.microsoft.com/azure/iot-hub)
- [Service Bus](https://docs.microsoft.com/azure/service-bus)
- [Práce s podporou kanálu změn v Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/change-feed)

>[!div class="step-by-step"]
>[Předchozí](serverless-architecture-considerations.md)
>[další](azure-serverless-platform.md)
