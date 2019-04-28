---
title: Logická architektura vs. fyzická architektura
description: Znát rozdíly mezi logické a fyzické architektury.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/20/2018
ms.openlocfilehash: e8ed375899637d06db8eb9b12a0e1cb0c05591f9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756832"
---
# <a name="logical-architecture-versus-physical-architecture"></a>Logická architektura vs. fyzická architektura

To je užitečné v tuto chvíli zastavit a diskutovat o rozdíl mezi logickou architekturu a fyzická architektura a jak to platí pro návrh aplikací založených na mikroslužbách.

Pokud chcete začít, vytváření mikroslužeb nevyžaduje použití libovolné konkrétní technologie. Kontejnery Dockeru, nejsou povinné pro vytvoření architektury založené na mikroslužbách. Tyto mikroslužeb může také spustit jako obyčejný procesy. Mikroslužby jsou logickou architekturu.

Kromě toho i v případě mikroslužba by mohl fyzicky implementované jako jedinou službou, procesu nebo kontejneru (pro saké na jednoduchost, který je přístup provedených v počáteční verzi [aplikaci eShopOnContainers](https://aka.ms/MicroservicesArchitecture)), tento rozdíly mezi obchodní mikroslužeb a fyzické služby nebo kontejner nemusí nutně ve všech případech při sestavování rozsáhlý a komplexní aplikace složené z mnoha desítky nebo stovky služeb.

Tady je rozdíl mezi logickou architekturu a fyzická architektura aplikací. Logická architektura a logické hranice systému nemapovaly nutně architektury fyzických nebo nasazení 1: 1. K tomu může dojít, ale často nestalo.

I když možná jste našli určité obchodní mikroslužby nebo ohraničených kontextech, neznamená, vždycky je nejlepší způsob, jak je implementovat vytvořením jedné služby (například rozhraní ASP.NET Web API) nebo u jednotlivých mikroslužeb obchodní jediným kontejnerem Dockeru. S oznámením o jednotlivých mikroslužeb obchodní pravidla musí implementovat s využitím jedné služby nebo kontejner je příliš přísné.

Proto mikroslužeb firmy nebo ohraničená kontext je logická architektura, která se může shodovat (nebo nemusíte) s fyzická architektura. Důležité je, že je obchodní mikroslužeb nebo ohraničená kontext autonomní tím, že kód a stav nezávisle vyvíjených, nasadit a škálovat.

Jak ukazuje obrázek 4. – 8 mikroslužeb obchodní katalogu může obsahovat několik služeb nebo procesů. Může se jednat víc služeb ASP.NET Web API nebo jakýkoli jiný druh služby přes protokol HTTP nebo libovolného protokolu. Důležitější je služby může sdílet stejná data, pokud jsou tyto služby získá na ucelenosti s ohledem na stejné obchodní domény.

![Diagram mikroslužbě obchodní katalog, který obsahuje rozhraní API služby search service a k databázi SQL serveru.](./media/image8.png)

**Obrázek 4. – 8**. Obchodní mikroslužeb fyzické službami

Služby v příkladu sdílet stejný datový model, protože služba webového rozhraní API, zaměřuje stejná data jako službu Search. Proto ve fyzické implementaci mikroslužeb firmy už rozdělení, které tuto funkci, můžete škálovat každá z těchto interních služeb směrem nahoru nebo dolů podle potřeby. Možná službou webového rozhraní API obvykle vyžaduje více instancí služby vyhledávání, nebo naopak.

Stručně řečeno logickou architekturu mikroslužeb vždy nemusí shodovat s architekturou fyzického nasazení. V této příručce se pokaždé, když jsme zmínili, mikroslužby, představuje obchodní nebo logické mikroslužeb, která může mapovat na jednu nebo víc služeb (fyzické). Ve většině případů to bude jedinou službou, ale může být více.

>[!div class="step-by-step"]
>[Předchozí](data-sovereignty-per-microservice.md)
>[další](distributed-data-management.md)