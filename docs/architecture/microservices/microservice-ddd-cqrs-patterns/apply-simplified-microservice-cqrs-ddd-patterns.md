---
title: Použití zjednodušených vzorů CQRS a DDD v mikroslužbě
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Seznamte se s celkovým vztahem mezi vzory CQRS a DDD.
ms.date: 10/08/2018
ms.openlocfilehash: f42b553fd30fdffdc6e325b11740fe9162aab7c8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "71834305"
---
# <a name="apply-simplified-cqrs-and-ddd-patterns-in-a-microservice"></a>Použití zjednodušených vzorů CQRS a DDD v mikroslužbě

CQRS je architektonický vzor, který odděluje modely pro čtení a zápis dat. Související termín [Command Query Separation (CQS)](https://martinfowler.com/bliki/CommandQuerySeparation.html) byl původně definován Bertrandmeyer ve své knize Object Oriented Software *Construction*. Základní myšlenkou je, že operace systému můžete rozdělit do dvou ostře oddělených kategorií:

- Dotazy. Ty vrátí výsledek a nemění stav systému a jsou bez vedlejších účinků.

- Příkazy. Ty mění stav systému.

CQS je jednoduchý koncept – jedná se o metody v rámci stejného objektu jsou dotazy nebo příkazy. Každá metoda vrátí stav nebo mutuje stav, ale ne obojí. Dokonce i jeden objekt vzoru úložiště může být v souladu s CQS. CQS lze považovat za základní princip pro CQRS.

[Oddělení odpovědnosti za velení a dotazy (CQRS)](https://martinfowler.com/bliki/CQRS.html) byl zaveden Gregem Youngem a silně podporován Udi Dahanem a dalšími. Je založen na principu CQS, i když je podrobnější. Lze jej považovat za vzor založený na příkazy a události plus volitelně na asynchronní zprávy. V mnoha případech CQRS souvisí s pokročilejší scénáře, jako je mít jinou fyzickou databázi pro čtení (dotazy) než pro zápisy (aktualizace). Kromě toho více vyvinutý systém CQRS může implementovat [Event-Sourcing (ES)](https://martinfowler.com/eaaDev/EventSourcing.html) pro databázi aktualizací, takže by se místo ukládání dat aktuálního stavu ukládala pouze události v modelu domény. To však není přístup použitý v této příručce; používáme nejjednodušší přístup CQRS, který se skládá pouze z oddělení dotazů od příkazů.

Aspekt oddělení CQRS je dosaženo seskupením dotazů v jedné vrstvě a příkazy v jiné vrstvě. Každá vrstva má svůj vlastní datový model (všimněte si, že říkáme model, ne nutně jiná databáze) a je sestaven a používá vlastní kombinaci vzorů a technologií. Ještě důležitější je, že dvě vrstvy může být v rámci stejné vrstvy nebo mikroslužeb, jako v příkladu (řazení mikroslužeb) pro tuto příručku. Nebo mohou být implementovány v různých mikroslužeb nebo procesů, takže mohou být optimalizovány a škálovat samostatně bez ovlivnění navzájem.

CQRS znamená mít dva objekty pro operaci čtení a zápisu, kde v jiných kontextech je jeden. Existují důvody, proč mít nenormalizovanou databázi čtení, o které se můžete dozvědět v pokročilejší literatuře CQRS. Ale nepoužíváme tento přístup zde, kde cílem je mít větší flexibilitu v dotazech namísto omezení dotazů s omezeními z DDD vzory, jako jsou agregace.

Příkladem tohoto druhu služby je řazení mikroslužby z referenční aplikace eShopOnContainers. Tato služba implementuje mikroslužbu založenou na zjednodušeném přístupu CQRS. Používá jeden zdroj dat nebo databázi, ale dva logické modely plus DDD vzory pro transakční doménu, jak je znázorněno na obrázku 7-2.

![Diagram znázorňující vysokou úroveň zjednodušené CQRS a DDD mikroslužby.](./media/apply-simplified-microservice-cqrs-ddd-patterns/simplified-cqrs-ddd-microservice.png)

**Obrázek 7-2**. Zjednodušená mikroslužba založená na CQRS a DDD

Logické "Řazení" Mikroslužba zahrnuje jeho řazení databáze, která může být, ale nemusí být, stejný hostitel Dockeru. Mít databázi ve stejném hostiteli Dockeru je vhodné pro vývoj, ale ne pro produkční prostředí.

Aplikační vrstva může být samotné webové rozhraní API. Důležitým aspektem návrhu je, že mikroslužba rozdělila dotazy a ViewModels (datové modely vytvořené speciálně pro klientské aplikace) z příkazů, modelu domény a transakcí podle vzoru CQRS. Tento přístup udržuje dotazy nezávislé na omezení a omezení pocházející ze vzorů DDD, které mají smysl pouze pro transakce a aktualizace, jak je vysvětleno v dalších částech.

## <a name="additional-resources"></a>Další zdroje

- **Greg young. Správa verzí v systému zdroje událostí** (zdarma ke čtení online e-knihy) \
   <https://leanpub.com/esversioning/read>

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[další](eshoponcontainers-cqrs-ddd-microservice.md)
