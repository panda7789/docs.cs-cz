---
title: Implementace odolných aplikací
description: Přečtěte si o odolnosti, klíčové koncepci v architektuře mikroslužeb. Musíte znát, jak plynule řešit přechodné chyby, protože k nim dojde.
ms.date: 10/16/2018
ms.openlocfilehash: 766349e72389f848b0a741b020707cc7acf3410d
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296058"
---
# <a name="implement-resilient-applications"></a>Implementace odolných aplikací

*Vaše mikroslužby a cloudové aplikace musí vycházet z částečně neúspěšných selhání. Je nutné navrhnout aplikaci, která bude odolná vůči těmto částečným selháním.*

Odolnost proti chybám je schopnost zotavení po selháních a nadále fungovat. Nejedná se o předcházení chybám, ale přijímá skutečnost, že k selhání dojde a reagují na ně způsobem, který brání výpadkům nebo ztrátě dat. Cílem odolnosti proti chybám je vrátit aplikaci do plně funkčního stavu po selhání.

Pro návrh a nasazení aplikace založené na mikroslužbách je to dost náročné. Ale také je potřeba, aby vaše aplikace běžela v prostředí, kde je nějaký konkrétní druh selhání. Proto by vaše aplikace měla být odolná. Měla by být navržená tak, aby se vypořádat s částečnými chybami, jako jsou výpadky sítě nebo uzly nebo selhání virtuálních počítačů v cloudu. Dokonce i mikroslužby (kontejnery), které se přesunou do jiného uzlu v clusteru, můžou v rámci aplikace způsobit přerušované krátké chyby.

Mnohé jednotlivé komponenty vaší aplikace by měly také zahrnovat funkce monitorování stavu. Podle pokynů v této kapitole můžete vytvořit aplikaci, která může hladce fungovat navzdory přechodnému výpadku nebo normálním hiccups, ke kterým dochází ve složitých i cloudových nasazeních.

>[!div class="step-by-step"]
>[Předchozí](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
>[Další](handle-partial-failure.md)
