---
title: Použití zjednodušených vzorů CQRS a DDD v mikroslužbě
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Seznamte se s celkový vztah mezi vzorů CQRS a DDD.
ms.date: 10/08/2018
ms.openlocfilehash: a5df8ce495b308df63af47ef1ec2ed26be2b5e37
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65875892"
---
# <a name="apply-simplified-cqrs-and-ddd-patterns-in-a-microservice"></a>Použít zjednodušený vzorů CQRS a DDD v mikroslužbě

CQRS je schéma architektury, který odděluje modely pro čtení a zápis dat. Související výraz [příkaz dotazu oddělení (CQS)](https://martinfowler.com/bliki/CommandQuerySeparation.html) bylo původně určené Bertrand Meyer ve své knize *objekt orientované konstrukce softwaru*. Základní myšlenka je, že můžete rozdělit operací systému do dvou kategorií prudce oddělených:

- Dotazy. Tyto vrácení výsledku a nemění stav systému, a jsou bez vedlejších účinků.

- Příkazy. Tato změna stavu systému.

CQS je jednoduchý koncept – jde o metod v rámci stejného objektu dotazy nebo příkazy. Každá metoda vrátí stav nebo mění stav, ale ne obojí. Můžete dokonce objekt vzor jednoho úložiště v souladu s CQS. CQS lze považovat za základní princip pro modelu CQRS.

[Příkaz a model dělení zodpovědnosti dotazů (CQRS)](https://martinfowler.com/bliki/CQRS.html) byla zavedená Grega Younga a důrazně přesunuty Udi Dahan a další. Je založen na principu CQS, i když je podrobnější. To lze považovat za vzor založený na příkazy a události a volitelně v asynchronních zpráv. V mnoha případech se týká modelu CQRS pokročilejší scénáře, jako byste měli různé fyzické databáze pro čtení (dotazy), než pro zápis (aktualizace). Kromě toho může implementovat více evolved systému CQRS [modelu Event Sourcing (ES)](https://martinfowler.com/eaaDev/EventSourcing.html) aktualizace databáze, proto byste měli pouze ukládat události v doménovém modelu místo ukládání dat aktuální stav. Ale to není použitý v tomto průvodci; přístup Používáme nejjednodušší přístup modelu CQRS, který se skládá z právě oddělení dotazů z příkazů.

Oddělení aspektů modelu CQRS se dosahuje prostřednictvím seskupování operace dotazů v jedné vrstvě a příkazy v jiné vrstvě. Každá vrstva má svůj vlastní datový model (Všimněte si, že říkáme model, ne tedy nutně jinou databázi) a je vytvořená pomocí svou vlastní kombinaci vzorů a technologie. Důležitější je může být dvě vrstvy v rámci stejné vrstvy nebo mikroslužeb, jako v příkladu (řazení mikroslužeb) použít pro tohoto průvodce. Nebo na jiný mikroslužby nebo procesy jejich možná implementace v tak může být optimalizováno a škálovat samostatně bez ovlivnění mezi sebou.

CQRS znamená, že s dva objekty pro operace čtení a zápis, kde v jiném kontextu existuje. Je důvodů, proč jste Nenormalizovaná čte databázi, která se dozvíte v pokročilejší CQRS dokumentace. Ale nepoužíváme tento přístup zde, kde je k dispozici větší flexibilitu v dotazech místo omezení dotazů s omezeními ze vzorů DDD, jako jsou agregace.

Příklad tohoto druhu služby je řazení mikroslužeb v aplikaci eShopOnContainers referenční aplikace. Tato služba implementuje mikroslužeb podle zjednodušený přístup modelu CQRS. Použije jeden zdroj dat nebo databáze, ale dvě logické modely a vzorů DDD transakční domény, jak je znázorněno v obrázku 7-2.

![Logické řazení mikroslužeb zahrnuje řazení databázi, která může být nebo není ve stejném Docker hostovat. U stejného hostitele Docker s databáze je dobrá pro vývoj, ale nikoli pro produkční účely.](./media/image2.png)

**Obrázek 7-2**. Zjednodušená založené na modelu CQRS a DDD mikroslužeb

Samotné webové rozhraní API může být aplikační vrstvu. Tady aspekt návrhu důležité je, že mikroslužbách rozdělil dotazy a modely ViewModel (zejména pro klientské aplikace vytvořit modely dat) z příkazů, doménový model a transakce po model CQRS. Tento přístup zajišťuje dotazy nezávisle na omezení a omezení pocházejí z vzorů DDD, které smysl jenom pro transakce a aktualizací, jak je popsáno v předchozích částech.

## <a name="additional-resources"></a>Další zdroje

 - **Grega Younga:. Správa verzí v systému zdrojem událostí** (přečíst online e kniha zdarma) \
   <https://leanpub.com/esversioning/read>

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[další](eshoponcontainers-cqrs-ddd-microservice.md)
