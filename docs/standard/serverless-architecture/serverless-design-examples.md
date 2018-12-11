---
title: Příklady návrhu bez serveru – aplikace bez serveru
description: Vysvětlení různých scénářích podporovaných architektur bez serveru, od plánování a zpracování na základě událostí triggery souborů a datový proud procesu.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: cf46c601ac6aa401c7c37bd64c1f8981589ebd2e
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53146703"
---
# <a name="serverless-design-examples"></a>Příklady návrhu bez serveru

Existuje mnoho vzorů návrhu, které existují pro bez serveru. Tato část jsou zaznamenané některé běžné scénáře, které používají bez serveru. Co některé příklady mají společnou je základní kombinací události trigger a obchodní logiky.

## <a name="scheduling"></a>Plánování

Plánování úloh je běžné funkce. Následující diagram znázorňuje starší verzi databáze, který nemá odpovídající integrity kontroly. Databáze musí být pravidelně odstranil. Funkce bez serveru neplatná data najde a odstraní. Aktivační událost se časovač, který spouští kód podle plánu.

![Plánování bez serveru](./media/serverless-scheduling.png)

## <a name="command-and-query-responsibility-segregation-cqrs"></a>Příkaz and Query Responsibility Segregation (CQRS)

Příkaz a model dělení zodpovědnosti dotazů (CQRS) je vzor, který poskytuje data jiné rozhraní pro čtení (nebo dotazování) a operací, které upravují data. Zaměřuje se na několik běžných problémů. V tradičních systémech vytvořit čtení aktualizace odstranění (CRUD) na základě může docházet ke konfliktům z velký objem operací čtení a zápisu do stejného úložiště dat. Zámku může dochází často a výrazně zpomalit čtení. Data se často zobrazují jako složeného několik objektů domény a operace čtení musíte sloučit data z různých entit.

Použití modelu CQRS, čtení může zahrnovat zvláštní entita "ploché", který modeluje data tak, jak je využívá. Čtení vyřeší jinak, než jak je uložen. Například i když databáze může ukládat kontakt jako záhlaví záznamu s podřízený záznam adres, může zahrnovat čtení entity se záhlavím a vlastnosti adresy. Existují řadu přístupy k vytváření modelu čtení. Může být vyhodnocena ze zobrazení. Operace aktualizace může být zapouzdřen jako izolovanými událostmi, které potom aktivovat aktualizace do dvou různých modelů. Existují samostatné modely pro čtení a zápis.

![Příklad modelu CQRS](./media/cqrs-example.png)

Bez serveru zvládne model CQRS tím, že poskytuje koncové body oddělené. Jednu funkci bez serveru obsáhne dotazy nebo čtení a jiné funkce bez serveru nebo sady funkcí zpracovává operace aktualizace. Funkce bez serveru může být také odpovídá za pořízení aktuální model čtení a v databázi se dá spouštět [kanálu změn](https://docs.microsoft.com/azure/cosmos-db/change-feed). K připojení ke koncovým bodům nezbytné je zjednodušený vývoj front-endu. Zpracování událostí, které se zpracovává v back-endu. Tento model je také vhodná u velkých projektů, protože různé týmy mohou pracovat na různých operací.

## <a name="event-based-processing"></a>Zpracování na základě událostí

V systémech zprávy jsou často události shromážděné při front nebo témat vydavatel/odběratel k reagovali na ni. Tyto události můžete aktivovat funkce bez serveru spustit část obchodní logiky. Příklad zpracování na základě událostí je zdrojem událostí systémy. "Událost" je vyvolávána s cílem označí úlohu jako dokončenou. Funkce bez serveru, který se aktivuje událost aktualizuje dokument příslušné databáze. Druhá funkce bez serveru může použít k aktualizaci modelu čtení pro systém události. [Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview) poskytuje způsob, jak integrace se službou functions jako předplatitelé události.

> Události jsou informační zprávy. Další informace najdete v tématu [model Event Sourcing](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing).

## <a name="file-triggers-and-transformations"></a>Triggery souborů a transformace

Extrakce, transformace a načítání (ETL) je běžné obchodní funkce. Bez serveru je skvělým řešením pro ETL protože umožňuje kód, který se dá spouštět jako součást kanálu. Jednotlivé komponenty můžete řešit různé aspekty. Jednu funkci bez serveru si stáhnout soubor, jiné použije transformaci a jiné načte data. Kód můžete otestovat a nasadit nezávisle, snadněji spravovat a škálovat místech.

![Triggery souborů bez serveru a transformace](./media/serverless-file-triggers.png)

V diagramu, "studené úložiště" poskytuje data, která je analyzován v [Azure Stream Analytics](https://docs.microsoft.com/azure/stream-analytics). Všechny problémy v datovém proudu došlo k aktivaci funkce Azure k vyřešení anomálii.

## <a name="asynchronous-background-processing-and-messaging"></a>Zpracování na pozadí asynchronní a zasílání zpráv

Asynchronní zasílání zpráv a zpracování na pozadí umožňují aplikacím bez nutnosti čekat pusťte se do procesů. Příklad asynchronní zpracování je OCR aplikace. Obrázek je odeslána a zařadily do fronty ke zpracování. Vyhledávání obrázků k extrakci textu může nějakou dobu trvat a po jeho dokončení oznámení se odešle. Volání a výsledek v tomto scénáři dokáže zpracovat bez serveru.

## <a name="web-apps-and-apis"></a>Webové aplikace a rozhraní API

Oblíbené scénáře bez serveru je N-vrstvé aplikace, nejčastěji těch, ve kterém vrstvě uživatelského rozhraní je webová aplikace. Popularita z jedné stránky aplikace (SPA) má dozvěděli nedávno o nastalé. Aplikace SPA vykreslení na jedné stránce a Spolehněte se na volání rozhraní API a vrácená data dynamicky vykreslit nové uživatelské rozhraní bez opětovné načítání celou stránku. Vykreslování na straně klienta poskytuje mnohem rychlejší a rychleji reagující aplikace koncovým uživatelům.

Bez serveru koncové body, které aktivuje volání HTTP lze použít ke zpracování požadavků rozhraní API. Například společnosti služby ad může volat funkci bez serveru s informace o profilu uživatele o vlastní reklamy. Vlastní ad vrací funkci bez serveru a ji vykreslí webovou stránku.

![Bez serveru webového rozhraní API](./media/serverless-web-api.png)

## <a name="data-pipeline"></a>Data Pipeline

Funkce bez serveru je možné pro usnadnění datového kanálu. V tomto příkladu soubor aktivuje funkci pro převod data v souboru CSV do datových řádků v tabulce. Uspořádané tabulky umožňuje řídicí panel Power BI analytics prezentovat koncovému uživateli.

![Bez serveru datového kanálu](./media/serverless-data-pipeline.png)

## <a name="stream-processing"></a>Zpracování streamů

Zařízení a senzorů často generovat datové proudy dat, které je potřeba zpracovat v reálném čase. Existuje mnoho technologií, které můžete zaznamenat zprávy a datové proudy [Event Hubs](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs) a [služby IoT Hub](https://docs.microsoft.com/azure/iot-hub) k [služby Service Bus](/service-bus). Bez ohledu na přenos je ideální mechanismu pro zpracování zpráv a datových proudů, jak ve bez serveru. Bez serveru se rychle škálují podle potřeby velkých svazků s daty. Kód bez serveru můžete použít obchodní logiku k analýze dat a výstupu předává ve strukturovaném formátu pro akce a analýzy.

![Zpracování datových proudů bez serveru](./media/serverless-stream-processing.png)

## <a name="api-gateway"></a>Brána rozhraní API

Brány rozhraní API poskytuje jeden vstupní bod pro klienty a monetizace směruje žádosti do back endové služby. Je užitečné ke správě velkých sad služeb. Můžete také zpracování správy verzí a zjednodušte vývoj snadno propojíte klientů s různorodými prostředími. Bez serveru, dokáže zpracovat back-end škálování jednotlivých mikroslužeb zároveň jediného front-endu přes bránu rozhraní API.

![Bez serveru brány rozhraní API](./media/serverless-api-gateway.png)

## <a name="recommended-resources"></a>Doporučené studijní materiály

* [Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview)
* [Azure IoT Hub](https://docs.microsoft.com/azure/iot-hub)
* [Výzvy a řešení správy distribuovaných dat](../microservices-architecture/architect-microservice-container-applications/distributed-data-management.md)
* [Návrh mikroslužeb: identifikace hranic mikroslužby](https://docs.microsoft.com/azure/architecture/microservices/microservice-boundaries)
* [Event Hubs](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs)
* [Model Event Sourcing](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)
* [Implementace vzoru Circuit Breaker](../microservices-architecture/implement-resilient-applications/implement-circuit-breaker-pattern.md)
* [IoT Hub](https://docs.microsoft.com/azure/iot-hub)
* [Service Bus](https://docs.microsoft.com/azure/service-bus)
* [Práce s změnu podpora kanálu ve službě Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/change-feed)

>[!div class="step-by-step"]
>[Předchozí](serverless-architecture-considerations.md)
>[další](azure-serverless-platform.md)