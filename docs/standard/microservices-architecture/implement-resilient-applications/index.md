---
title: Implementace odolných aplikací
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Implementace odolných aplikací
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/08/2018
ms.openlocfilehash: ec79221f0238d61f1ca1b2b7c58b1e16be7f4df4
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130791"
---
# <a name="implementing-resilient-applications"></a>Implementace odolných aplikací

*Částečně neúspěšné, kterým bude určitě nakonec musí využívat mikroslužeb a cloudových aplikací. Je třeba navrhnout aplikace tak bude odolné vůči selhání v těchto částečné.*

Odolnost proti chybám je schopnost zotavení z chyb a nadále fungovat. Nejedná se o předcházení chybám, ale přijímá skutečnost, že dojde k selhání a reagovat na ně způsobem, který zabraňuje výpadkům nebo ztrátě. Cílem odolnosti proti chybám je plně funkčního stavu aplikace po selhání.

Je náročné dost informací k návrhu a nasazení aplikací založených na mikroslužbách. Ale je také potřeba nechat běžící v prostředí, kde nějaký druh selhání je určitá aplikace. Proto se vaše aplikace by měl být odolný. To by se měly navrhovat pro zvládnutí částečné selhání, jako je výpadek sítě nebo uzly nebo virtuální počítače k chybám v cloudu. Dokonce i mikroslužby (kontejnerů) přesouvá na jiný uzel v rámci clusteru může způsobit krátkodobých krátká selhání v rámci aplikace.

Mnoho jednotlivých komponent vaší aplikace by měly zahrnovat taky funkce monitorování stavu. Pomocí následujících pokynů v této kapitole, můžete vytvořit aplikace, které může fungovat bez problémů, přestože přechodné výpadky nebo normální bude odolný vůči kolísání, ke kterým dochází ve složitých a cloudové nasazení.

>[!div class="step-by-step"]
>[Předchozí](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
>[další](handle-partial-failure.md)