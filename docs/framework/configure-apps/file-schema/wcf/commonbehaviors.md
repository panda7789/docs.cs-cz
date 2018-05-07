---
title: '&lt;commonBehaviors&gt;'
ms.date: 03/30/2017
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
ms.openlocfilehash: 0a9fab68ce240fc37d27c42d9feff969b97f93a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ltcommonbehaviorsgt"></a>&lt;commonBehaviors&gt;
`commonBehaviors` Části lze definovat pouze v souboru machine.config. Definuje dva podřízené kolekce s názvem `endpointBehaviors` a `serviceBehaviors`.  Každá kolekce definuje chování elementy spotřebovávají všech koncových bodů WCF a služeb na počítači. Chování definované v `endpointBehaviors` se použije pouze na klienty a chování, které jsou definované v `serviceBehaviors` platí pouze pro služby. Pokud chování je definovaný jak v `commonBehaviors` a `behaviors` jejich chování v oddílech `behaviors` část je přednost.
