---
title: Logická architektura versus fyzická architektura
description: Pochopení rozdílů mezi logickými a fyzickými architekturami.
ms.date: 09/20/2018
ms.openlocfilehash: 8d1bfca190eb9b18d46625fa4afdec963eb07054
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834405"
---
# <a name="logical-architecture-versus-physical-architecture"></a>Logická architektura versus fyzická architektura

To je užitečné v tomto okamžiku k zastavení a projednání rozdílu mezi logickou architekturou a fyzickou architekturou a jak to platí pro návrh aplikací založených na mikroslužbách.

Aby bylo možné začít vytvářet mikroslužby, nevyžadují používání žádné konkrétní technologie. Například kontejnery Docker nejsou povinné pro vytvoření architektury založené na mikroslužbách. Tyto mikroslužby můžou být taky spuštěné jako jednoduché procesy. Mikroslužby jsou logickou architekturou.

Kromě toho, i když by mohla být mikroslužba fyzicky implementována jako jediná služba, proces nebo kontejner (z důvodu jednoduchosti, což je postup, který je povedený v počáteční verzi [eShopOnContainers](https://aka.ms/MicroservicesArchitecture)), tato parita v rámci obchodních mikroslužeb a fyzická služba nebo kontejner nemusí nutně vyžadovat ve všech případech, když vytváříte rozsáhlou a složitou aplikaci složenou z mnoha desítek nebo i stovek služeb.

Tady je rozdíl mezi logickou architekturou aplikace a fyzickou architekturou. Logická architektura a logické hranice systému nemusí nutně namapovat 1:1 na fyzickou nebo nasazenou architekturu. K tomu může dojít, ale často ne.

I když jste zjistili určité obchodní mikroslužby nebo ohraničené kontexty, neznamená to, že nejlepší způsob jejich implementace je vždy vytvořením jediné služby (například webové rozhraní API ASP.NET) nebo jednoho kontejneru Docker pro jednotlivé obchodní mikroslužby. Je nutné, aby každé obchodní mikroslužby bylo implementováno pomocí jedné služby nebo kontejneru je příliš pevné.

Proto obchodní mikroslužba nebo ohraničený kontext je logická architektura, která se může shodovat s fyzickou architekturou (nebo ne). Důležitým bodem je, že obchodní mikroslužba nebo ohraničený kontext musí být autonomní tím, že umožňují, aby kód a stav byly nezávislé na verzi, nasazené a škálované.

Jak ukazuje obrázek 4-8, může se v katalogu obchodní mikroslužba skládat z několika služeb nebo procesů. Může se jednat o více služeb webového rozhraní API ASP.NET nebo jakýkoli jiný druh služeb pomocí protokolu HTTP nebo jakéhokoliv jiného protokolu. Důležitější je, že tyto služby můžou sdílet stejná data, pokud jsou tyto služby soudržné s ohledem na stejnou obchodní doménu.

![Diagram obchodních mikroslužeb v katalogu s fyzickými servery](./media/logical-versus-physical-architecture/multiple-physical-services.png)

**Obrázek 4-8**. Obchodní mikroslužba s několika fyzickými službami

Služby v příkladu sdílejí stejný datový model, protože služba webového rozhraní API cílí na stejná data jako vyhledávací služba. V rámci fyzické implementace firemních mikroslužeb tedy rozdělujete tuto funkci, takže každý z těchto interních služeb můžete podle potřeby škálovat směrem nahoru nebo dolů. Služba webového rozhraní API pravděpodobně potřebuje více instancí než vyhledávací služba nebo naopak.

V krátkém případě se logická architektura mikroslužeb vždy nemusí shodovat s architekturou fyzického nasazení. V této příručce se pokaždé, když uvádíme mikroslužbu, rozumíme obchodní nebo logické mikroslužby, která může být namapována na jednu nebo více (fyzických) služeb. Ve většině případů to bude jediná služba, ale může to být víc.

>[!div class="step-by-step"]
>[Předchozí](data-sovereignty-per-microservice.md)@no__t – 1 –[Další](distributed-data-management.md)
