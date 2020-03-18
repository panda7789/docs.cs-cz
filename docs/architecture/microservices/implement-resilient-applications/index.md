---
title: Implementace odolných aplikací
description: Seznamte se s odolností, základní koncept v architektuře mikroslužeb. Musíte vědět, jak řádně zacházet s přechodnými chybami, když k nim dojde.
ms.date: 01/30/2020
ms.openlocfilehash: 46276a6b9b36a494bfae657275692ca9d5554d86
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78847229"
---
# <a name="implement-resilient-applications"></a>Implementace odolných aplikací

*Vaše mikroslužby a cloudové aplikace musí zahrnovat částečné chyby, které jistě dojde nakonec. Je nutné navrhnout aplikaci, aby byla odolná vůči těmto částečným selháním.*

Odolnost proti chybám je schopnost zotavit se z chyb a nadále fungovat. Nejde o to vyhnout se chybám, ale přijmout skutečnost, že k selháním dojde, a reagovat na ně způsobem, který zabraňuje výpadkům nebo ztrátě dat. Cílem odolnosti proti chybám je vrátit aplikaci do plně funkčního stavu po selhání.

Je dostatečně náročné navrhnout a nasadit aplikaci založenou na mikroslužbách. Ale také je nutné zachovat aplikace spuštěna v prostředí, kde je jistý nějaký druh selhání. Proto by měla být vaše aplikace odolná. Měl by být navržen tak, aby se vypořádal s částečnými chybami, jako jsou výpadky sítě nebo uzly nebo virtuální počítače, které se v cloudu zhroutí. I mikroslužeb (kontejnery) přesouvána do jiného uzlu v rámci clusteru může způsobit občasné krátké chyby v rámci aplikace.

Mnoho jednotlivých součástí aplikace by měly také obsahovat funkce monitorování stavu. Podle pokynů v této kapitole můžete vytvořit aplikaci, která může pracovat hladce i přes přechodné prostoje nebo normální škytavka, ke kterým dochází ve složitých a cloudových nasazeních.

>[!IMPORTANT]
> EShopOnContainer používal [knihovnu Polly](http://www.thepollyproject.org/) k implementaci odolnosti pomocí [zadaliklientů](./use-httpclientfactory-to-implement-resilient-http-requests.md) až do vydání 3.0.0.
>
> Počínaje verzí 3.0.0 je vynuceno odolnost volání HTTP pomocí [sítě Linkerd](https://linkerd.io/), která zpracovává opakované pokusy transparentním a konfigurovatelným způsobem v rámci clusteru Kubernetes, aniž by bylo třeba zpracovávat tyto problémy v kódu.
>
> Knihovna Polly se stále používá k přidání odolnosti k databázovým připojením, zvláště při spouštění služeb.

>[!WARNING]
> Všechny ukázky kódu v této části byly platné před použitím Linkerd a nejsou aktualizovány tak, aby odrážely aktuální skutečný kód. Takže mají smysl v kontextu této sekce.

>[!div class="step-by-step"]
>[Předchozí](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
>[další](handle-partial-failure.md)
