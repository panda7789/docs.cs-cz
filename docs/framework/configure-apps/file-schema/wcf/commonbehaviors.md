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
`commonBehaviors`Oddíl lze definovat pouze v souboru Machine. config. Definuje dvě podřízené kolekce s názvem `endpointBehaviors` a `serviceBehaviors` .  Každá kolekce definuje prvky chování spotřebované všemi koncovými body a službami WCF v daném počítači. Chování definovaná v nástroji `endpointBehaviors` se aplikují jenom na klienty a chování definovaná v nástroji `serviceBehaviors` se aplikuje jenom na služby. Pokud je chování definováno v obou `commonBehaviors` částech a `behaviors` , chování v `behaviors` oddílu má přednost.
