---
title: Logická architektura versus fyzické architektura
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Logická architektura versus fyzické architektura
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: d675ba753903e181c67712e34eea82fed72df0d7
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105432"
---
# <a name="logical-architecture-versus-physical-architecture"></a>Logická architektura versus fyzické architektura

Je užitečné v tomto okamžiku zastavit a diskutovat o rozdíl mezi Logická architektura a architektura fyzických a jak to platí pro návrh aplikace založené na mikroslužby.

Chcete-li začít vytvářet mikroslužeb nevyžaduje použití žádné konkrétní technologie. Například Docker kontejnery nejsou povinné, aby bylo možné vytvořit architektura založená na mikroslužby. Tyto mikroslužeb by bylo možné spustit také jako prostý procesy. Mikroslužeb je logická architektura.

Kromě toho i v případě mikroslužbu může fyzicky implementovaný jako jeden služby, proces nebo kontejneru (pro saké na jednoduchost, která se přístup použitý v původní verzi [eShopOnContainers](http://aka.ms/MicroservicesArchitecture)), tato rozdíly mezi mikroslužbu obchodní a fyzické služby nebo kontejneru nemusí nutně ve všech případech při sestavování rozsáhlých a komplexních aplikace skládá z mnoha desítek nebo dokonce stovky služby.

To je, kdy je rozdíl mezi Logická architektura a architektura fyzických dané aplikace. Logická architektura a logické hranice systému nemapovaly nutně 1: 1 na architektuře fyzický nebo nasazení. K tomu může dojít, ale je často nepoužívá.

I když může být zjištění určitých mikroslužeb firmy nebo ohraničenou kontextů, neznamená to, vždycky je nejlepší způsob, jak je provede vytvořením jedné služby (např. pro ASP.NET Web API) nebo jeden kontejner Docker pro každou obchodní mikroslužby. Pravidlo oznámením každé obchodní mikroslužbu má implementovaný pomocí jedné služby nebo kontejner je příliš pevné.

Proto mikroslužbu firmy nebo ohraničenou kontextu je logická architektura, která může být časově shodují (nebo ne) s architekturou fyzické. Důležité je, že obchodní mikroslužbu nebo ohraničenou kontextu musí být autonomního tím, že kód a stav, který má být nezávisle verzí, nasazení a škálovat.

Jak ukazuje obrázek 4-8, mikroslužbu obchodní katalogu může skládat z několika služeb nebo procesů. Může jít o více služeb ASP.NET Web API nebo jakýkoli jiný druh služeb pomocí protokolu HTTP ani žádný jiný protokol. Služby je důležité, může sdílet stejná data, tak dlouho, dokud tyto služby jsou získá na ucelenosti s ohledem na stejné domény firmy.

![](./media/image8.png)

**Obrázek 4 – 8**. Mikroslužbu obchodní s několika fyzických služeb

Služby v příkladu sdílet stejný datový model, protože webového rozhraní API služby cílem stejná data jako službu vyhledávání. Ano fyzické implementace mikroslužbu firmy, jsou rozdělení které tuto funkci, je možné škálovat, každý z těchto služeb interní nahoru nebo dolů podle potřeby. Možná webového rozhraní API služby obvykle vyžaduje více instancí než službu vyhledávání a naopak.)

Stručně řečeno Logická architektura mikroslužeb vždy nemá se shoduje s architekturou fyzické nasazení. V této příručce vždy, když jsme zmínili mikroslužbu, jsme znamená obchodní nebo logické mikroslužbu, která by mohla mapování na jeden nebo více služeb. Ve většině případů to bude jedné služby, ale může být více.


>[!div class="step-by-step"]
[Předchozí](data-sovereignty-per-microservice.md)
[další](distributed-data-management.md)
