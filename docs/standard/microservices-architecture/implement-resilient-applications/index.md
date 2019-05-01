---
title: Implementace odolných aplikací
description: Další informace o odolnost, základní pojmy v architektuře mikroslužeb. Musíte vědět, jak řešit přechodná selhání bez výpadku, protože se k nim dojde.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/16/2018
ms.openlocfilehash: 00724509ba6e027ef73f72bfb6f85b8ec0aa9d25
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61977700"
---
# <a name="implement-resilient-applications"></a>Implementace odolných aplikací

*Částečně neúspěšné, kterým bude určitě nakonec musí využívat mikroslužeb a cloudových aplikací. Je třeba navrhnout aplikaci chcete být odolní vůči selhání v těchto částečné.*

Odolnost proti chybám je schopnost zotavení z chyb a nadále fungovat. Nejedná se o předcházení chybám, ale přijímá skutečnost, že dojde k selhání a reagovat na ně způsobem, který zabraňuje výpadkům nebo ztrátě. Cílem odolnosti proti chybám je plně funkčního stavu aplikace po selhání.

Je náročné dost informací k návrhu a nasazení aplikací založených na mikroslužbách. Ale je také potřeba nechat běžící v prostředí, kde nějaký druh selhání je určitá aplikace. Proto se vaše aplikace by měl být odolný. To by se měly navrhovat pro zvládnutí částečné selhání, jako je výpadek sítě nebo uzly nebo virtuální počítače k chybám v cloudu. Dokonce i mikroslužby (kontejnerů) přesouvá na jiný uzel v rámci clusteru může způsobit krátkodobých krátká selhání v rámci aplikace.

Mnoho jednotlivých komponent vaší aplikace by měly zahrnovat taky funkce monitorování stavu. Pomocí následujících pokynů v této kapitole, můžete vytvořit aplikace, které může fungovat bez problémů, přestože přechodné výpadky nebo normální bude odolný vůči kolísání, ke kterým dochází ve složitých a cloudové nasazení.

>[!div class="step-by-step"]
>[Předchozí](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
>[další](handle-partial-failure.md)