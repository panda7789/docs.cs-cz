---
title: 1021 - ScheduleBookmarkWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e0da311-b219-4637-9460-90cdafcc4ecd
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 781f4b6d064ac90f762e10e03783422c64a1bf05
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="1021---schedulebookmarkworkitem"></a>1021 - ScheduleBookmarkWorkItem
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1021|  
|Klíčová slova|WFRuntime|  
|úroveň|Verbose|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že bylo naplánováno BookmarkWorkItem.  
  
## <a name="message"></a>Zpráva  
 Bylo naplánováno BookmarkWorkItem aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.  NázevZáložky: %4, BookmarkScope: %5.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|Aktivita|xs:String|Název typu aktivity.|  
|displayName|xs:String|Zobrazovaný název aktivity.|  
|identifikátor instanceId|xs:String|Id instance aktivity.|  
|NázevZáložky|xs:String|Název záložky|  
|BookmarkScope|xs:String|Rozsah záložky.|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
