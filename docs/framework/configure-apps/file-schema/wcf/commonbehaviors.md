---
title: <commonBehaviors>
ms.date: 03/30/2017
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
ms.openlocfilehash: 73bf759fd3dfa87398aa74de93160a4ffce08eba
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "61704359"
---
# \<commonBehaviors>
<span data-ttu-id="81691-101">`commonBehaviors`Oddíl lze definovat pouze v souboru Machine. config.</span><span class="sxs-lookup"><span data-stu-id="81691-101">The `commonBehaviors` section can only be defined in the machine.config file.</span></span> <span data-ttu-id="81691-102">Definuje dvě podřízené kolekce s názvem `endpointBehaviors` a `serviceBehaviors` .</span><span class="sxs-lookup"><span data-stu-id="81691-102">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="81691-103">Každá kolekce definuje prvky chování spotřebované všemi koncovými body a službami WCF v daném počítači.</span><span class="sxs-lookup"><span data-stu-id="81691-103">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span> <span data-ttu-id="81691-104">Chování definovaná v nástroji `endpointBehaviors` se aplikují jenom na klienty a chování definovaná v nástroji `serviceBehaviors` se aplikuje jenom na služby.</span><span class="sxs-lookup"><span data-stu-id="81691-104">Behaviors defined in `endpointBehaviors` are only applied to clients, and behaviors defined in `serviceBehaviors` are only applied to services.</span></span> <span data-ttu-id="81691-105">Pokud je chování definováno v obou `commonBehaviors` částech a `behaviors` , chování v `behaviors` oddílu má přednost.</span><span class="sxs-lookup"><span data-stu-id="81691-105">If a behavior is defined in both `commonBehaviors` and `behaviors` sections, the behavior in the `behaviors` section is given preference.</span></span>
