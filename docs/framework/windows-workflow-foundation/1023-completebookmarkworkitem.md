---
title: 1023 - CompleteBookmarkWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc5dac57-b3eb-4826-b505-c6d269e4774d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 920935e8842058029c3ef151422a0a29609075e9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="1023---completebookmarkworkitem"></a>1023 - CompleteBookmarkWorkItem
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1023|  
|Klíčová slova|WFRuntime|  
|úroveň|Verbose|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že je dokončená BookmarkWorkItem.  
  
## <a name="message"></a>Zpráva  
 BookmarkWorkItem dokončení aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'. NázevZáložky: %4, BookmarkScope: %5.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|Aktivita|xs:String|Název typu aktivity.|  
|displayName|xs:String|Zobrazovaný název aktivity.|  
|identifikátor instanceId|xs:String|Id instance aktivity.|  
|NázevZáložky|xs:String|Název záložky|  
|BookmarkScope|xs:String|Rozsah záložky.|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
