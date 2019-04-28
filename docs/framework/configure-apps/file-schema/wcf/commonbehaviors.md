---
title: <commonBehaviors>
ms.date: 03/30/2017
ms.assetid: 5260aeca-388d-4e82-94c0-124fa8054cf5
ms.openlocfilehash: 73bf759fd3dfa87398aa74de93160a4ffce08eba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704359"
---
# <a name="commonbehaviors"></a>\<commonBehaviors>
`commonBehaviors` Části lze definovat pouze v souboru machine.config. Definuje dvě podkolekce s `endpointBehaviors` a `serviceBehaviors`.  Každou kolekci definuje chování elementů používané všech koncových bodů WCF a služeb na počítači. Chování definované v `endpointBehaviors` platí pouze pro klienty a chování definované v `serviceBehaviors` platí pouze pro služby. Pokud chování je definován v `commonBehaviors` a `behaviors` části, chování `behaviors` části je přednost.
