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
# <a name="ltcommonbehaviorsgt"></a>&lt;commonBehaviors&gt;
`commonBehaviors` Části lze definovat pouze v souboru machine.config. Definuje dva podřízené kolekce s názvem `endpointBehaviors` a `serviceBehaviors`.  Každá kolekce definuje chování prvky používané ve všech [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] koncových bodů a služeb na počítači v uvedeném pořadí. Chování definované v `endpointBehaviors` se použije pouze na klienty a chování, které jsou definované v `serviceBehaviors` platí pouze pro služby. Pokud chování je definovaný jak v `commonBehaviors` a `behaviors` jejich chování v oddílech `behaviors` část je přednost.
