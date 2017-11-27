---
title: "Použití zjednodušené CQRS a DDD vzorců mikroslužbu"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Použití zjednodušené CQRS a DDD vzorců mikroslužbu"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 99fd7ce32039742e23f8e01aa4c33cddd7a9f698
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="applying-simplified-cqrs-and-ddd-patterns-in-a-microservice"></a>Použití zjednodušené CQRS a DDD vzorců mikroslužbu

CQRS je architekturní vzor, který odděluje modely pro čtení a zápis dat. Související termín [příkaz dotazu oddělení (CQS)](https://martinfowler.com/bliki/CommandQuerySeparation.html) byl původně definované Bertrand Meyer v jeho kniha *konstrukce softwaru zaměřené na konkrétní objekt*. Základní myšlenkou je operace systému do dvou kategorií prudce oddělených rozdělte:

-   Dotazy. Tyto vrácení výsledku a stav systému nemění a byly bez vedlejší účinky.

-   Příkazy. Tyto změny stavu systému.

CQS je jednoduchý koncept – jde o metod v rámci stejného objektu dotazy nebo příkazy. Každá metoda vrátí stav nebo mění stavu, ale ne obojí. I objekt vzor jednoho úložiště můžete v souladu se CQS. CQS lze považovat za základní princip pro CQRS.

[Příkaz a dotaz odpovědnost oddělení (CQRS)](https://martinfowler.com/bliki/CQRS.html) byl zaváděné Gregu Young a důrazně povýší Udi Dahan a jinými uživateli. I když je více podrobné je založena na principu CQS. Lze ji považovat vzor na základě na příkazy a události a volitelně na asynchronní zprávy. V mnoha případech se týká CQRS pokročilejší scénáře, jako má jiné fyzické databázi pro čtení (dotazy) než pro zápis (aktualizace). Kromě toho může implementovat více evolved systému CQRS [událostí-Sourcing (ES)](http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/) pro vaši databázi aktualizace, proto byste měli jenom ukládat události v modelu domény místo ukládání dat v aktuálním stavu. Je to ale není přístup používané v tomto průvodci; Používáme nejjednodušší CQRS přístup, který se skládá z právě oddělení dotazy z příkazů.

Oddělení aspektů CQRS je dosaženo tím, že operace dotazů v jedné vrstvy a příkazy v jiné vrstvě. Jednotlivé úrovně má svou vlastní datový model (Všimněte si, že říkáme modelu, nemusí nutně jít do jiné databáze) a je sestaven pomocí vlastní kombinace vzory a technologie. Je důležité dvě vrstvy, které může být v rámci stejné úrovně nebo mikroslužbu, jako v příkladu (řazení mikroslužbu) používá pro tento průvodce. Nebo na jinou mikroslužeb nebo procesy jejich možná implementace v tak můžou být optimalizované a škálovat na více systémů samostatně bez ovlivnění jednu na druhou.

CQRS znamená s dva objekty pro operace čtení/zápis, kde v jiných kontextech existuje. Existuje několik důvodů nenormalizované čtení databáze, které se dozvíte v dokumentaci pokročilejší CQRS. Ale nejsou používáme tohoto přístupu v tomto poli, kde cílem je získat větší flexibilitu v dotazech místo omezení dotazů s omezeními od DDD jako agregace.

Příkladem tento druh služby je řazení mikroslužbu z eShopOnContainers odkaz na aplikaci. Tato služba se implementuje mikroslužbu založen na zjednodušené CQRS přístup. Používá jeden zdroj dat nebo databáze, ale dva logické modely plus DDD vzory pro transakční doménu, jak je znázorněno na obrázku 9-2.

![](./media/image2.png)

**Obrázek 9-2**. Zjednodušená na základě CQRS a DDD mikroslužbu

Aplikační vrstvu lze webového rozhraní API sám sebe. Daný důležité návrhu aspekt je, že mikroslužbu se rozdělila dotazy a ViewModels (hlavně pro klientské aplikace vytvořit modely dat) z příkazy, modelu domény a následující vzoru CQRS transakce. Tento přístup zajišťuje dotazy nezávislé na omezení a omezení pocházejících z DDD vzorů, které smysl jenom pro transakce a aktualizace, jak je popsáno v dalších oddílech.


>[!div class="step-by-step"]
[Předchozí] (index.md) [Další] (eshoponcontainers-cqrs-ddd-microservice.md)
