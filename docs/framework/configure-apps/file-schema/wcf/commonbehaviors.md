---
title: '&lt;commonBehaviors&gt;'
ms.date: 03/30/2017
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
ms.openlocfilehash: 0a9fab68ce240fc37d27c42d9feff969b97f93a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33350319"
---
# <a name="ltcommonbehaviorsgt"></a><span data-ttu-id="eb8b6-102">&lt;commonBehaviors&gt;</span><span class="sxs-lookup"><span data-stu-id="eb8b6-102">&lt;commonBehaviors&gt;</span></span>
<span data-ttu-id="eb8b6-103">`commonBehaviors` Části lze definovat pouze v souboru machine.config.</span><span class="sxs-lookup"><span data-stu-id="eb8b6-103">The `commonBehaviors` section can only be defined in the machine.config file.</span></span> <span data-ttu-id="eb8b6-104">Definuje dva podřízené kolekce s názvem `endpointBehaviors` a `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="eb8b6-104">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="eb8b6-105">Každá kolekce definuje chování elementy spotřebovávají všech koncových bodů WCF a služeb na počítači.</span><span class="sxs-lookup"><span data-stu-id="eb8b6-105">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span> <span data-ttu-id="eb8b6-106">Chování definované v `endpointBehaviors` se použije pouze na klienty a chování, které jsou definované v `serviceBehaviors` platí pouze pro služby.</span><span class="sxs-lookup"><span data-stu-id="eb8b6-106">Behaviors defined in `endpointBehaviors` are only applied to clients, and behaviors defined in `serviceBehaviors` are only applied to services.</span></span> <span data-ttu-id="eb8b6-107">Pokud chování je definovaný jak v `commonBehaviors` a `behaviors` jejich chování v oddílech `behaviors` část je přednost.</span><span class="sxs-lookup"><span data-stu-id="eb8b6-107">If a behavior is defined in both `commonBehaviors` and `behaviors` sections, the behavior in the `behaviors` section is given preference.</span></span>
