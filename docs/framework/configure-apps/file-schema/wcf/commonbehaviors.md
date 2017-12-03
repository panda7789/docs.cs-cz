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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 06d09763b0281eb7edafadbbd59ff924b751d73e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltcommonbehaviorsgt"></a>&lt;commonBehaviors&gt;
`commonBehaviors` Části lze definovat pouze v souboru machine.config. Definuje dva podřízené kolekce s názvem `endpointBehaviors` a `serviceBehaviors`.  Každá kolekce definuje chování prvky používané ve všech [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] koncových bodů a služeb na počítači v uvedeném pořadí. Chování definované v `endpointBehaviors` se použije pouze na klienty a chování, které jsou definované v `serviceBehaviors` platí pouze pro služby. Pokud chování je definovaný jak v `commonBehaviors` a `behaviors` jejich chování v oddílech `behaviors` část je přednost.
