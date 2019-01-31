---
title: <commonBehaviors>
ms.date: 03/30/2017
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
ms.openlocfilehash: 73bf759fd3dfa87398aa74de93160a4ffce08eba
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55268753"
---
# <a name="commonbehaviors"></a><span data-ttu-id="0186f-101">\<commonBehaviors></span><span class="sxs-lookup"><span data-stu-id="0186f-101">\<commonBehaviors></span></span>
<span data-ttu-id="0186f-102">`commonBehaviors` Části lze definovat pouze v souboru machine.config.</span><span class="sxs-lookup"><span data-stu-id="0186f-102">The `commonBehaviors` section can only be defined in the machine.config file.</span></span> <span data-ttu-id="0186f-103">Definuje dvě podkolekce s `endpointBehaviors` a `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="0186f-103">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="0186f-104">Každou kolekci definuje chování elementů používané všech koncových bodů WCF a služeb na počítači.</span><span class="sxs-lookup"><span data-stu-id="0186f-104">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span> <span data-ttu-id="0186f-105">Chování definované v `endpointBehaviors` platí pouze pro klienty a chování definované v `serviceBehaviors` platí pouze pro služby.</span><span class="sxs-lookup"><span data-stu-id="0186f-105">Behaviors defined in `endpointBehaviors` are only applied to clients, and behaviors defined in `serviceBehaviors` are only applied to services.</span></span> <span data-ttu-id="0186f-106">Pokud chování je definován v `commonBehaviors` a `behaviors` části, chování `behaviors` části je přednost.</span><span class="sxs-lookup"><span data-stu-id="0186f-106">If a behavior is defined in both `commonBehaviors` and `behaviors` sections, the behavior in the `behaviors` section is given preference.</span></span>
