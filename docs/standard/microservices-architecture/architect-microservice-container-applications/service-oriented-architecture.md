---
title: Architektura orientovaná na služby
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Architektura orientovaná na služby
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: ce4addefc7b6b1cf82551bf8304b7f06f1614796
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="service-oriented-architecture"></a>Architektura orientovaná na služby 

Architektura orientovaná na služby (SOA) byl Nepromyšlené termín a je určena různých věcí na jiné osoby. Ale jako společný jmenovatel, SOA znamená, že struktury vaší aplikace pomocí decomposing k více službám (nejčastěji jako služeb HTTP), které můžou být klasifikované jako různé typy jako subsystémy nebo vrstvy.

Tyto služby teď můžou být nasazené jako Docker kontejnery, které řeší problémy při nasazení, protože všechny závislosti jsou součástí image kontejneru. Pokud potřebujete škálování aplikace SOA, můžete mít škálovatelnost a dostupnost výzvy, pokud nasazujete podle jednoho hostitelů Docker. Toto je, kde Docker clustering softwaru nebo orchestrator vám pomůže se, jak je popsáno v pozdějších částech, kde jsme popisují nasazení přístupy k mikroslužeb.

Kontejnery docker jsou užitečné (ale není požadováno) pro tradiční architektury orientované na služby a pokročilejší architektury mikroslužeb.

Mikroslužeb odvozena od SOA, ale SOA se liší od architektura mikroslužeb. Funkce, například velký centrální zprostředkovatelé, centrální orchestrators na úrovni organizace a [Enterprise Service Bus (ESB)](https://en.wikipedia.org/wiki/Enterprise_service_bus) jsou typická ve SOA. Ale ve většině případů se jedná o proti vzory v komunitě mikroslužby. Ve skutečnosti někteří uživatelé uvádějí, že "architektury mikroslužby je SOA pracujete správně."

Tato příručka se zaměřuje na mikroslužeb, protože je doporučený méně než požadavky a postupy používané při architektury mikroslužby SOA přístup. Pokud víte, jak sestavit aplikaci na základě mikroslužbu, také znát postup sestavení jednodušší aplikace orientované na služby.




>[!div class="step-by-step"]
[Předchozí] (docker aplikace stavu data.md) [Další] (mikroslužeb architecture.md)
