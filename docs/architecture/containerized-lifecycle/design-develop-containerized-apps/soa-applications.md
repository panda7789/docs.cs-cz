---
title: Aplikace SOA
description: Pamatujte, že kontejnery můžou být také užitečnou možností nasazení pro aplikace SOA.
ms.date: 02/15/2019
ms.openlocfilehash: aa56ada7b14a465fb3dafd02b03b815782ac765b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295273"
---
# <a name="service-oriented-applications"></a>Aplikace orientované na služby

Architektura typu SOA (Service-orientované) byla nepoužitým termínem, který pro různé lidi znamenal mnoho různých věcí. Ale jako společný jmenovatel, záznam SOA znamená, že budete strukturovat architekturu aplikace tím, že ji rozdělíte do několika služeb (nejčastěji jako služby HTTP), které je možné klasifikovat v různých typech, jako jsou subsystémy nebo v jiných případech jako vrstvy.

V současné době můžete tyto služby nasadit jako kontejnery Docker, které řeší problémy související s nasazením, protože všechny závislosti jsou zahrnuty v imagi kontejneru. Pokud ale potřebujete škálovat SOAs, může dojít k problémům při nasazení na základě jednotlivých instancí. Tuto výzvu lze zpracovat pomocí softwaru Docker pro clusteringu nebo produktu Orchestrator. Když prozkoumáme přístupy k mikroslužbám, podíváme se na orchestraci podrobněji v další části.

Kontejnery Docker jsou užitečné (ale nevyžadují se) pro tradiční architektury zaměřené na služby a pokročilejší architektury mikroslužeb.

Na konci dne jsou řešení clusteringu kontejneru užitečná pro tradiční architekturu SOA i pro pokročilejší architekturu mikroslužeb, ve které každá mikroslužba vlastní svůj datový model. A díky více databázím můžete také škálovat datovou vrstvu místo práce s monolitické databázemi sdílenými službami SOA. Diskuze o rozdělení dat je ale čistě o architektuře a návrhu.

>[!div class="step-by-step"]
>[Předchozí](state-and-data-in-docker-applications.md)Další
>[](orchestrate-high-scalability-availability.md)
