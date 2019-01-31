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
# <a name="commonbehaviors"></a>\<commonBehaviors>
`commonBehaviors` Části lze definovat pouze v souboru machine.config. Definuje dvě podkolekce s `endpointBehaviors` a `serviceBehaviors`.  Každou kolekci definuje chování elementů používané všech koncových bodů WCF a služeb na počítači. Chování definované v `endpointBehaviors` platí pouze pro klienty a chování definované v `serviceBehaviors` platí pouze pro služby. Pokud chování je definován v `commonBehaviors` a `behaviors` části, chování `behaviors` části je přednost.
