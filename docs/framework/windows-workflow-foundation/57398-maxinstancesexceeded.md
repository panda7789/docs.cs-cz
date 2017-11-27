---
title: 57398 - MaxInstancesExceeded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f943d209-dfeb-43e5-b572-c9a06217936e
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7417d2e0e850017e65910be32e7449255f0761c3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="57398---maxinstancesexceeded"></a>57398 - MaxInstancesExceeded
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|57398|  
|Klíčová slova|WFServices|  
|úroveň|Upozornění|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace nebo analytické|  
  
## <a name="description"></a>Popis  
 Označuje, že systém dosáhl limit nastavený pro omezení 'MaxConcurrentInstances'.  
  
## <a name="message"></a>Zpráva  
 Systém dosáhl limit nastavený pro omezení 'MaxConcurrentInstances'. Limit pro toto omezení byla nastavena na %1. Hodnota omezení lze změnit úpravou atribut 'maxConcurrentInstances' v omezení ServiceThrottle s hodnotou elementu nebo úpravou vlastnosti 'MaxConcurrentInstances' na chování třídy ServiceThrottlingBehavior.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|Název|xs:String|Název položky.|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
