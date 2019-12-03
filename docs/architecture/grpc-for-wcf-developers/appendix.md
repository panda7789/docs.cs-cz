---
title: Příloha – gRPC pro vývojáře WCF
description: Diskuze nad distribuovanými transakcemi a jejich implementaci v moderních architekturách mikroslužeb.
ms.date: 09/02/2019
ms.openlocfilehash: 9931681727f921e007c2f80852ad0e69cd7288de
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711472"
---
# <a name="appendix-a---transactions"></a>Příloha A – transakce

Windows Communication Foundation (WCF) podporuje distribuované transakce, což umožňuje provádět atomické operace v rámci více služeb. Tato funkce je založená na [DTC (Distributed Transaction Coordinator) Microsoftu](https://docs.microsoft.com/previous-versions/windows/desktop/ms684146(v=vs.85)).

V novějších mikroslužbách na šířku není tento typ automatizovaného zpracování distribuované transakce možný. Existuje příliš mnoho různých technologií, včetně relačních databází, NoSQL úložišť dat a systémů zasílání zpráv. Může být také kombinace operačních systémů, programovacích jazyků a platforem používaných v jednom prostředí.

Distribuovaná transakce WCF je implementací toho, co se říká dvoufázové [potvrzení (2PC)](https://en.wikipedia.org/wiki/Two-phase_commit_protocol). Transakce 2PC můžete implementovat ručně prostřednictvím koordinace zpráv napříč službami, vytvořením otevřených transakcí v rámci každé služby a odesláním zpráv potvrzení nebo vrácení změn v závislosti na úspěšnosti nebo selhání. Složitost týkající se správy 2PC se ale může zvyšovat exponenciálně, jak se budou vyvíjet systémy. Otevřené transakce uchovávají zámky databáze, které můžou negativně ovlivnit výkon, nebo horší, což způsobí zablokování mezi službami.

Pokud je to možné, je nejlepší vyhnout se distribuovaným transakcím úplně. Pokud jsou tak propojeny dvě položky dat, jako by vyžadovaly atomické aktualizace, zvažte jejich zpracování pomocí stejné služby. Tyto atomické změny použijte při použití jediné žádosti nebo zprávy do této služby.

Pokud to není možné, pak je jednou alternativou použití [vzoru Saga](https://microservices.io/patterns/data/saga.html). Ve Saga se aktualizace zpracovávají postupně. Po úspěšném dokončení každé aktualizace se aktivuje další. Tyto aktivační události se dají rozšířit ze služby na službu nebo spravovat koordinátor Saga nebo Orchestrator. Pokud se aktualizace v jakémkoli okamžiku v rámci procesu nezdařila, služby, které již dokončí jejich aktualizace, uplatní konkrétní logiku pro jejich vrácení.

Další možností je použití návrhu řízeného doménou (DDD) a oddělení zodpovědnosti příkazů nebo dotazů (CQRS), jak je popsáno v [elektronické knize .NET mikroslužeb](https://docs.microsoft.com/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/). Konkrétně použití doménových událostí nebo [zdrojů událostí](https://martinfowler.com/eaaDev/EventSourcing.html) může pomoci zajistit, že aktualizace budou konzistentně, pokud nejsou okamžitě použity.

>[!div class="step-by-step"]
>[Předchozí](application-performance-management.md)
