---
title: Logická architektura vs. fyzická architektura
description: Pochopte rozdíly mezi logickou a fyzickou architekturou.
ms.date: 09/20/2018
ms.openlocfilehash: 8d1bfca190eb9b18d46625fa4afdec963eb07054
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "71834405"
---
# <a name="logical-architecture-versus-physical-architecture"></a>Logická architektura vs. fyzická architektura

V tomto okamžiku je užitečné zastavit a diskutovat o rozdílu mezi logickou architekturou a fyzickou architekturou a jak to platí pro návrh aplikací založených na mikroslužbách.

Chcete-li začít, vytváření mikroslužeb nevyžaduje použití žádné konkrétní technologie. Například kontejnery Dockeru nejsou povinné k vytvoření architektury založené na mikroslužbách. Tyto mikroslužby lze také spustit jako prosté procesy. Mikroslužeb je logická architektura.

Navíc i v případě, že mikroslužbu může být fyzicky implementována jako jedna služba, proces nebo kontejner (pro jednoduchost, to je přístup přijatý v počáteční verzi [eShopOnContainers](https://aka.ms/MicroservicesArchitecture)), tato parita mezi obchodní mikroslužeb a fyzické služby nebo kontejneru není nutně nutné ve všech případech při vytváření velké a složité aplikace složené z mnoha desítek nebo dokonce stovky služeb.

Toje místo, kde je rozdíl mezi logickou architekturou aplikace a fyzickou architekturou. Logická architektura a logické hranice systému nemusí nutně mapovat 1:1 na fyzickou architekturu nebo architekturu nasazení. Může se to stát, ale často se to nestane.

I když jste možná identifikovali určité obchodní mikroslužeb nebo ohraničené kontexty, neznamená to, že nejlepší způsob, jak je implementovat, je vždy vytvořením jedné služby (například ASP.NET webové rozhraní API) nebo jednoho kontejneru Dockeru pro každou obchodní mikroslužbu. S pravidlo říká, že každá obchodní mikroslužby musí být implementována pomocí jedné služby nebo kontejneru je příliš rigidní.

Proto obchodní mikroslužeb nebo ohraničený kontext je logická architektura, která může shodovat (nebo ne) s fyzickou architekturou. Důležité je, že obchodní mikroslužeb nebo ohraničený kontext musí být autonomní tím, že kód a stav, které mají být nezávisle verzí verzí, nasazení a škálování.

Jak ukazuje obrázek 4-8, obchodní mikroslužba katalogu se může skládat z několika služeb nebo procesů. Může se jedná o více ASP.NET služby webového rozhraní API nebo jakýkoli jiný druh služeb používajících protokol HTTP nebo jiný protokol. Ještě důležitější je, že služby by mohly sdílet stejná data, pokud jsou tyto služby soudržné, pokud jde o stejnou obchodní doménu.

![Diagram obchodní mikroslužby katalogu s fyzickými servery.](./media/logical-versus-physical-architecture/multiple-physical-services.png)

**Obrázek 4-8**. Obchodní mikroservis s několika fyzickými službami

Služby v příkladu sdílejí stejný datový model, protože služba webového rozhraní API cílí na stejná data jako vyhledávací služba. Takže ve fyzické implementaci obchodní mikroslužby, rozdělení této funkce, takže můžete škálovat každou z těchto interních služeb nahoru nebo dolů podle potřeby. Možná, že služba webového rozhraní API obvykle potřebuje více instancí než vyhledávací služby nebo naopak.

Stručně řečeno, logická architektura mikroslužeb nemusí vždy shodovat s architekturou fyzického nasazení. V této příručce vždy, když jsme zmínili mikroslužbu, máme na mysli obchodní nebo logické mikroslužby, které by mohly mapovat na jednu nebo více (fyzické) služby. Ve většině případů to bude jedna služba, ale může to být více.

>[!div class="step-by-step"]
>[Předchozí](data-sovereignty-per-microservice.md)
>[další](distributed-data-management.md)
