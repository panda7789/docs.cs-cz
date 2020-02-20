---
title: Implementace odolných aplikací
description: Přečtěte si o odolnosti, klíčové koncepci v architektuře mikroslužeb. Musíte znát, jak plynule řešit přechodné chyby, když k nim dojde.
ms.date: 01/30/2020
ms.openlocfilehash: ccdb2470c727ad4bd89c4e0634da8564b8010e63
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77502658"
---
# <a name="implement-resilient-applications"></a>Implementace odolných aplikací

*Vaše mikroslužby a cloudové aplikace musí vycházet z částečně neúspěšných selhání. Je nutné navrhnout aplikaci, která bude odolná vůči těmto částečným selháním.*

Odolnost proti chybám je schopnost zotavení po selháních a nadále fungovat. Nejedná se o předcházení chybám, ale přijímá skutečnost, že k selhání dojde a reagují na ně způsobem, který brání výpadkům nebo ztrátě dat. Cílem odolnosti proti chybám je vrátit aplikaci do plně funkčního stavu po selhání.

Pro návrh a nasazení aplikace založené na mikroslužbách je to dost náročné. Ale také je potřeba, aby vaše aplikace běžela v prostředí, kde je nějaký konkrétní druh selhání. Proto by vaše aplikace měla být odolná. Měla by být navržená tak, aby se vypořádat s částečnými chybami, jako jsou výpadky sítě nebo uzly nebo selhání virtuálních počítačů v cloudu. Dokonce i mikroslužby (kontejnery), které se přesunou do jiného uzlu v clusteru, můžou v rámci aplikace způsobit přerušované krátké chyby.

Mnohé jednotlivé komponenty vaší aplikace by měly také zahrnovat funkce monitorování stavu. Podle pokynů v této kapitole můžete vytvořit aplikaci, která může hladce fungovat navzdory přechodnému výpadku nebo normálním hiccups, ke kterým dochází ve složitých i cloudových nasazeních.

>[!IMPORTANT]
> eShopOnContainer používala [knihovnu Polly](http://www.thepollyproject.org/) k implementaci odolnosti pomocí [typových klientů](./use-httpclientfactory-to-implement-resilient-http-requests.md) až do vydání 3.0.0.
>
> Od verze 3.0.0 je odolnost volání HTTP implementovaná pomocí [propojovací sítě](https://linkerd.io/), která zpracovává opakované pokusy transparentním a konfigurovatelným způsobem v rámci clusteru Kubernetes, aniž by bylo nutné tyto obavy v kódu zpracovat.
>
> Knihovna Polly se pořád používá k přidání odolnosti do databázových připojení, která jsou speciálně při spouštění služeb.

>[!WARNING]
> Všechny ukázky kódu v této části byly platné před použitím linkeru a nejsou aktualizovány, aby odrážely aktuální vlastní kód. Proto dávají smysl v kontextu této části.

>[!div class="step-by-step"]
>[Předchozí](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
>[Další](handle-partial-failure.md)
