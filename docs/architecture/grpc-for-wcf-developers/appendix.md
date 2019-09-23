---
title: Příloha – gRPC pro vývojáře WCF
description: Diskuze nad distribuovanými transakcemi a jejich implementaci v moderních architekturách mikroslužeb.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 10c4e77794c5ffe1aa6d5a629ce0b6cdf92f4ada
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184615"
---
# <a name="appendix-a---transactions"></a>Příloha A – transakce

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Windows Communication Foundation (WCF) podporuje distribuované transakce, což umožňuje provádět atomické operace napříč více službami. Tato funkce je založená na [DTC (Distributed Transaction Coordinator) Microsoftu](https://docs.microsoft.com/previous-versions/windows/desktop/ms684146(v=vs.85)).

V moderních mikroslužbách na šířku není tento typ automatizovaného zpracování distribuované transakce možný. Při hraní je k dispozici příliš mnoho různých technologií, včetně relačních databází, úložišť NoSQL dat a systémů pro zasílání zpráv, a nezmiňujte si kombinaci operačních systémů, programovacích jazyků a platforem, které mohou být použity v jednom prostředí.

Distribuovaná transakce WCF je implementací toho, co se říká dvoufázové [potvrzení (2PC)](https://en.wikipedia.org/wiki/Two-phase_commit_protocol). Transakce 2PC je možné implementovat ručně prostřednictvím koordinace zpráv napříč službami, vytvořením otevřených transakcí v rámci každé služby a odesláním zpráv "commit" nebo "Rollback" v závislosti na úspěchu nebo neúspěchu. Složitost, která je zapojená do správy 2PC, se ale může zvyšovat exponenciálně, jak se budou vyvíjet systémy, a otevřené transakce uchovávají zámky databáze, které mohou negativně ovlivnit výkon nebo horší, způsobit zablokování mezi službami.

Pokud je to možné, je nejlepší vyhnout se distribuovaným transakcím úplně. Pokud jsou tak propojeny dvě položky dat, jako by vyžadovaly atomické aktualizace, zvažte jejich manipulaci se stejnou službou a použití těchto atomických změn pomocí jediné žádosti nebo zprávy do této služby.

Pokud to není možné, pak je jednou alternativou použití [vzoru Saga](https://microservices.io/patterns/data/saga.html). V Saga jsou aktualizace zpracovávány postupně. v případě, že se každá aktualizace zdaří, aktivuje se další. Tyto aktivační události se dají rozšířit ze služby na službu nebo spravovat koordinátor Saga nebo Orchestrator. Pokud se aktualizace v jakémkoli okamžiku v rámci procesu nezdařila, služby, které již dokončí jejich aktualizace, uplatní konkrétní logiku pro jejich vrácení.

Další možností je použití návrhu řízeného doménou (DDD) a oddělení zodpovědnosti příkazů nebo dotazů (CQRS), jak je popsáno v [elektronické knize .NET mikroslužeb](https://docs.microsoft.com/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/). Konkrétně použití doménových událostí nebo [zdrojů událostí](https://martinfowler.com/eaaDev/EventSourcing.html) může pomoci zajistit, že aktualizace budou konzistentně&mdash;, pokud nejsou okamžitě&mdash;použity.

>[!div class="step-by-step"]
>[Předchozí](application-performance-management.md)
