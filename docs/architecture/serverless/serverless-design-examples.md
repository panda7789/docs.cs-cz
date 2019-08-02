---
title: Příklady návrhu bez serveru – aplikace bez serveru
description: Seznamte se s různými scénáři podporovanými architekturami bez serveru, od plánování a zpracování založeného na událostech až po triggery souborů a zpracování datových proudů.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 096dce6ef23bde5ef9c6ca65769f4dcc7e08a904
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68676673"
---
# <a name="serverless-design-examples"></a>Příklady bezserverového návrhu

Existuje mnoho vzorů návrhu, které existují pro bez serveru. V této části jsou uvedené některé běžné scénáře, které používají bez serveru. Všechny příklady mají společnou základní kombinaci triggeru události a obchodní logiky.

## <a name="scheduling"></a>Plánuje

Úlohy plánování jsou společnou funkcí. Následující diagram znázorňuje starší databázi, která nemá vhodné kontroly integrity. Databáze musí být pravidelně naproti čištění. Funkce bez serveru najde neplatná data a vyčistí ji. Trigger je časovač, který spouští kód podle plánu.

![Plánování bez serveru](./media/serverless-scheduling.png)

## <a name="command-and-query-responsibility-segregation-cqrs"></a>CQRS (Command and Query Responsibility Segregation) (CQRS)

CQRS (Command and Query Responsibility Segregation) (CQRS) je vzor, který poskytuje různá rozhraní pro čtení (nebo dotazování) dat a operací, které upravují data. Řeší několik běžných problémů. V tradičních systémech založených na operacích založených na čtení aktualizace pro čtení (CRUD) můžou konflikty vzniknout z vysokého objemu čtení i zápisů do stejného úložiště dat. Může často docházet k uzamčení a výrazně zpomalit čtení. Data se často zobrazují jako složený z několika objektů domény a operace čtení musí kombinovat data z různých entit.

Při použití CQRS může čtení zahrnovat speciální "shrnuté" entity, které modelují data způsobem, jakým jsou spotřebovány. Čtení je zpracováváno jinak, než jak je uloženo. Přestože databáze může například uložit kontakt jako záznam v hlavičce s podřízeným záznamem adresy, čtení může zahrnovat entitu s vlastnostmi záhlaví i adresami. Existují nesčetných přístupy k vytvoření modelu čtení. Může být materializovaná ze zobrazení. Operace aktualizace by mohly být zapouzdřené jako izolované události, které pak spouštějí aktualizace na dva různé modely. Pro čtení a zápis existují samostatné modely.

![Příklad CQRS](./media/cqrs-example.png)

Bez serveru můžete přizpůsobit vzor CQRS zadáním oddělených koncových bodů. Jedna funkce bez serveru se vejde na dotazy nebo čtení a jiná funkce bez serveru nebo sada funkcí zpracovává operace aktualizace. Funkce bez serveru může být také zodpovědná za udržování modelu čtení a je možné ho aktivovat pomocí [kanálu změn](https://docs.microsoft.com/azure/cosmos-db/change-feed)databáze. Vývoj front-endu je zjednodušený pro připojení k potřebným koncovým bodům. Zpracování událostí se zpracovává na back-endu. Tento model je také dobře škálný pro velké projekty, protože různé týmy mohou pracovat na různých operacích.

## <a name="event-based-processing"></a>Zpracování založené na událostech

V systémech založených na zprávách se události často shromažďují ve frontách nebo témata vydavatelů nebo účastníků, na kterých se mají pracovat. Tyto události mohou aktivovat funkce bez serveru pro spuštění obchodní logiky. Příkladem zpracování událostí jsou systémy založené na událostech. Událost "Event" je vyvolána k označení úlohy jako dokončené. Funkce bez serveru aktivovaná událostí aktualizuje příslušný databázový dokument. Druhá funkce bez serveru může tuto událost použít k aktualizaci modelu čtení pro systém. [Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview) poskytuje způsob, jak integrovat události s funkcemi jako předplatitelé.

> Události jsou informativní zprávy. Další informace najdete v tématu [vzor zdroje událostí](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing).

## <a name="file-triggers-and-transformations"></a>Aktivační události a transformace souborů

Extrakce, transformace a načítání (ETL) je společná obchodní funkce. Bez serveru je skvělé řešení pro ETL, protože umožňuje spuštění kódu jako součásti kanálu. Jednotlivé komponenty kódu mohou řešit různé aspekty. Jedna funkce bez serveru může soubor stáhnout, další použije transformaci a další načte data. Kód lze testovat a nasazovat nezávisle, což usnadňuje údržbu a škálování tam, kde je to potřeba.

![Aktivační události a transformace souborů bez serveru](./media/serverless-file-triggers.png)

V diagramu "studené úložiště" poskytuje data, která jsou analyzována v [Azure Stream Analytics](https://docs.microsoft.com/azure/stream-analytics). Všechny problémy zjištěné v datovém proudu aktivují funkci Azure Functions, která řeší anomálii.

## <a name="asynchronous-background-processing-and-messaging"></a>Asynchronní zpracování a zasílání na pozadí

Asynchronní zasílání zpráv a zpracování na pozadí umožňuje aplikacím odkázat procesy bez nutnosti čekat. Příkladem asynchronního zpracování je aplikace OCR. Obrázek se odešle a zařadí do fronty pro zpracování. Skenování obrázku pro extrakci textu může chvíli trvat a po jeho dokončení se pošle oznámení. Bez serveru může v tomto scénáři zpracovávat vyvolání i výsledek.

## <a name="web-apps-and-apis"></a>Webové aplikace a rozhraní API

Oblíbený scénář pro bez serveru je N-vrstvé aplikace, nejčastěji ty, kde je vrstva uživatelského rozhraní webová aplikace. V poslední době došlo k přepětí na oblíbenosti Jednostránkovéch aplikací (SPA). Aplikace SPA vykreslí jednu stránku a potom se spoléhají na volání rozhraní API a vracená data, aby bylo možné dynamicky vykreslovat nové uživatelské rozhraní bez opětovného načtení celé stránky. Vykreslování na straně klienta poskytuje mnohem rychlejší a spolehlivější aplikaci, která reaguje na koncového uživatele.

Pro zpracování požadavků rozhraní API se dají použít koncové body bez serveru aktivované voláními HTTP. Například společnost služby AD Services může volat funkci bez serveru s informacemi o profilu uživatele a požádat o vlastní reklamu. Funkce bez serveru vrátí vlastní reklamu a webová stránka ji vykreslí.

![Webové rozhraní API bez serveru](./media/serverless-web-api.png)

## <a name="data-pipeline"></a>Data Pipeline

Funkce bez serveru se dají použít k usnadnění datového kanálu. V tomto příkladu soubor aktivuje funkci pro překlad dat ze souboru CSV na řádky dat v tabulce. Uspořádaná tabulka umožňuje řídicímu panelu Power BI prezentovat analýzy koncovému uživateli.

![Datový kanál bez serveru](./media/serverless-data-pipeline.png)

## <a name="stream-processing"></a>Zpracování streamů

Zařízení a senzory často generují proudy dat, která se musí zpracovat v reálném čase. Existuje řada technologií, které mohou zachytit zprávy a datové proudy ze [Event Hubs](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs) a [IoT Hub](https://docs.microsoft.com/azure/iot-hub) na [Service Bus](https://docs.microsoft.com/azure/service-bus). Bez ohledu na přenos není server bez serveru ideálním mechanismem pro zpracování zpráv a datových proudů, jak jsou součástí. Bez serveru se dá rychle škálovat, aby se splnila poptávka s velkými objemy dat. Kód bez serveru může použít obchodní logiku k analýze dat a výstupu ve strukturovaném formátu pro akce a analýzy.

![Zpracování datových proudů bez serveru](./media/serverless-stream-processing.png)

## <a name="api-gateway"></a>Brána API

Brána API poskytuje pro klienty jediný bod zadávání a pak inteligentně směruje požadavky na back-endové služby. Je užitečné spravovat velké sady služeb. Může také zpracovávat správu verzí a zjednodušit vývoj díky snadnému propojení klientů s různorodými prostředími. Bez serveru může zpracovávat back-end škálování jednotlivých mikroslužeb a současně prezentují jeden front-end přes bránu API.

![Brána API bez serveru](./media/serverless-api-gateway.png)

## <a name="recommended-resources"></a>Doporučené prostředky

* [Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview)
* [Azure IoT Hub](https://docs.microsoft.com/azure/iot-hub)
* [Výzvy a řešení správy distribuovaných dat](../microservices/architect-microservice-container-applications/distributed-data-management.md)
* [Navrhování mikroslužeb: identifikace hranic mikroslužeb](https://docs.microsoft.com/azure/architecture/microservices/microservice-boundaries)
* [Event Hubs](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs)
* [Vzor zdroje událostí](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)
* [Implementace vzoru Circuit Breaker](../microservices/implement-resilient-applications/implement-circuit-breaker-pattern.md)
* [IoT Hub](https://docs.microsoft.com/azure/iot-hub)
* [Service Bus](https://docs.microsoft.com/azure/service-bus)
* [Práce s změnu podpora kanálu ve službě Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/change-feed)

>[!div class="step-by-step"]
>[Předchozí](serverless-architecture-considerations.md)Další
>[](azure-serverless-platform.md)
