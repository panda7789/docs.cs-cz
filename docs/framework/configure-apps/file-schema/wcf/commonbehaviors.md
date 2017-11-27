---
title: '&lt;commonBehaviors&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fceca3c1cf0cc980310b1c4fbf85f6bce5ad1a0d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ltcommonbehaviorsgt"></a><span data-ttu-id="1c8df-102">&lt;commonBehaviors&gt;</span><span class="sxs-lookup"><span data-stu-id="1c8df-102">&lt;commonBehaviors&gt;</span></span>
<span data-ttu-id="1c8df-103">`commonBehaviors` Části lze definovat pouze v souboru machine.config.</span><span class="sxs-lookup"><span data-stu-id="1c8df-103">The `commonBehaviors` section can only be defined in the machine.config file.</span></span> <span data-ttu-id="1c8df-104">Definuje dva podřízené kolekce s názvem `endpointBehaviors` a `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="1c8df-104">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="1c8df-105">Každá kolekce definuje chování prvky používané ve všech [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] koncových bodů a služeb na počítači v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="1c8df-105">Each collection defines behavior elements consumed by all [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] endpoints and services on the machine respectively.</span></span> <span data-ttu-id="1c8df-106">Chování definované v `endpointBehaviors` se použije pouze na klienty a chování, které jsou definované v `serviceBehaviors` platí pouze pro služby.</span><span class="sxs-lookup"><span data-stu-id="1c8df-106">Behaviors defined in `endpointBehaviors` are only applied to clients, and behaviors defined in `serviceBehaviors` are only applied to services.</span></span> <span data-ttu-id="1c8df-107">Pokud chování je definovaný jak v `commonBehaviors` a `behaviors` jejich chování v oddílech `behaviors` část je přednost.</span><span class="sxs-lookup"><span data-stu-id="1c8df-107">If a behavior is defined in both `commonBehaviors` and `behaviors` sections, the behavior in the `behaviors` section is given preference.</span></span>
