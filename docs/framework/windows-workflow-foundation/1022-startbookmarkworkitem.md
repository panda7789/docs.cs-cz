---
title: 1022 - StartBookmarkWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4415fbdb-0329-4019-803f-aea66e75f3da
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d7df39bd0f6d6d4d309cf5c599ecd3795eb92067
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="1022---startbookmarkworkitem"></a>1022 - StartBookmarkWorkItem
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1022|  
|Klíčová slova|WFRuntime|  
|úroveň|Verbose|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že že bookmarkworkitem zahajuje provádění.  
  
## <a name="message"></a>Zpráva  
 Spuštění provádění BookmarkWorkItem aktivity %1, DisplayName: %2, identifikátor InstanceId: '%3'.  NázevZáložky: %4, BookmarkScope: %5.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|Aktivita|xs:String|Název typu aktivity.|  
|displayName|xs:String|Zobrazovaný název aktivity.|  
|identifikátor instanceId|xs:String|Id instance aktivity.|  
|NázevZáložky|xs:String|Název záložky|  
|BookmarkScope|xs:String|Rozsah záložky.|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
