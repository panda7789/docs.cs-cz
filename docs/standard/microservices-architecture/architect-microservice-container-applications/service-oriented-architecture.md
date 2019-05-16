---
title: Architektura orientovaná na služby
description: Přečtěte si základní rozdíly mezi mikroslužbami a architektura orientovaná na služby (SOA).
ms.date: 09/20/2018
ms.openlocfilehash: 84786539fbac0e8b38a81a2580232474774cd355
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65640057"
---
# <a name="service-oriented-architecture"></a>Architektura orientovaná na služby

Architektura orientovaná na služby (SOA) byl Nepromyšlené období a má určené různé věci pro různé osoby. Ale jako společným faktorem SOA znamená, že struktury aplikace pomocí rozložení do více služeb (nejčastěji jako služeb HTTP), které se dají považovat za různé typy jako podsystémy nebo úrovní.

Tyto služby můžete nasadit jako kontejnery Dockeru, které řeší problémy s nasazením, protože všechny závislosti jsou součástí image kontejneru. Pokud potřebujete vertikálně navýšit kapacitu aplikace SOA, bude pravděpodobně škálovatelnost a dostupnost výzvy, pokud nasazujete založené na jednoho hostitele Dockeru. To je, kde software clusteru Docker nebo orchestrátor vám umožňují, jak je popsáno v předchozích částech, kde jsou popsány přístupy k nasazení mikroslužeb.

Kontejnery dockeru jsou užitečné (ale nevyžadováno) pro tradiční architektury orientované na služby a pokročilejší architekturu mikroslužeb.

Mikroslužby jsou odvozeny z SOA, ale SOA se liší od architekturu mikroslužeb. Funkce, jako jsou velké centrální zprostředkovatelů, centrální orchestrátorů na úrovni organizace a [Enterprise Service Bus (ESB)](https://en.wikipedia.org/wiki/Enterprise_service_bus) jsou běžná v SOA. Ale ve většině případů Toto jsou antimodely v komunitě mikroslužeb. Ve skutečnosti někteří lidé tvrdí, že "architekturu mikroslužeb je SOA pracujete správně."

Tato příručka se zaměřuje na mikroslužby, protože SOA přístup je méně než požadavky a postupy používané v architektuře mikroslužeb doporučené postupy. Pokud víte, jak vytvářet aplikace založené na mikroslužbách, také víte, jak vytvářet aplikace orientované na služby jednodušší.

>[!div class="step-by-step"]
>[Předchozí](docker-application-state-data.md)
>[další](microservices-architecture.md)
