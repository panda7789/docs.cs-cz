---
title: Distribuovaná data
description: Architekt cloudových nativních aplikací .NET pro Azure | Distribuovaná data pro nativní cloudové aplikace
ms.date: 06/30/2019
ms.openlocfilehash: 92086c52b02360e90461aea9ad23a2068224e187
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183131"
---
# <a name="distributed-data-for-cloud-native-apps"></a>Distribuovaná data pro cloudové nativní aplikace

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Při sestavování nativního cloudového systému, který se skládá z mnoha nezávislých mikroslužeb, si myslíte, jak si myslíte o změnách v úložišti dat.

Tradiční aplikace monolitické přilákat centralizované úložiště dat zobrazené na obrázku 5-1. 

![Jedna databáze monolitické](./media/single-monolithic-database.png)

**Obrázek 5-1**. Jedna databáze monolitické

Všimněte si na předchozím obrázku, jak všechny součásti aplikace využívají jednu relační databázi.

Tento přístup má spoustu výhod. Je jednoduché dotazování na data rozložená mezi více tabulek a je jednoduché implementovat [transakce kyseliny](https://docs.microsoft.com/windows/desktop/cossdk/acid-properties) , které zajistí konzistenci dat. Vždy se dokončí *okamžitou konzistencí*: buď všechny aktualizace dat, nebo žádná z nich.

Systémy nativní pro Cloud jsou upřednostněny datovou architekturu na obrázku 5-2, ve které každá mikroslužba vlastní a zapouzdřuje své vlastní data.

![Více databází napříč mikroslužbami](./media/data-across-microservices.png)

**Obrázek 5-2**. Více databází napříč mikroslužbami

Všimněte si, jak je předchozí obrázek vlastníkem každé mikroslužby, a zapouzdřuje úložiště dat IT a zpřístupňuje data na vnějším světě z jeho veřejného rozhraní API.
 
Tento model umožňuje, aby se každá mikroslužba nezávisle vyvinula bez nutnosti koordinovat změny schématu dat s ostatními mikroslužbami. Každá mikroslužba je bezplatná pro implementaci úložiště dat (relační databáze, databáze dokumentů, úložiště hodnot typu klíč-hodnota), který nejlépe odpovídá jeho potřebám. V době běhu může každá mikroslužba odpovídajícím způsobem škálovat data. To je znázorněno na obrázku 5-3:

![Trvalost dat Polyglot](./media/polyglot-data-persistence.png)

**Obrázek 5-3**. Trvalost dat Polyglot

Všimněte si, jak ukazuje předchozí obrázek katalog produktů a mikroslužby inventáře, které přijímají relační databáze, objednávání mikroslužeb, databázi dokumentů NoSql a službu nákupní košík, což je externí úložiště hodnot klíčů. I když relační databáze zůstávají důležité pro mikroslužby se složitými daty, databáze NoSQL získaly značnou oblíbenou službu, která nabízí přizpůsobivost, rychlé vyhledávání a vysokou dostupnost. Bez jejich schématu umožňuje vývojářům přesunout se od architektury typových datových tříd a ORMs, které vedou ke změně nákladného a časově náročného.

>[!div class="step-by-step"]
>[Předchozí](service-mesh-communication-infrastructure.md)
>[Další](data-patterns.md)
