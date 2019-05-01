---
title: 1023 – CompleteBookmarkWorkItem
ms.date: 03/30/2017
ms.assetid: fc5dac57-b3eb-4826-b505-c6d269e4774d
ms.openlocfilehash: 8677f25057486247e64879298755fe972bd373d3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008847"
---
# <a name="1023---completebookmarkworkitem"></a>1023 – CompleteBookmarkWorkItem
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1023|  
|klíčová slova|WFRuntime|  
|úroveň|Podrobnosti|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že položka BookmarkWorkItem byla dokončena.  
  
## <a name="message"></a>Zpráva  
 Položka BookmarkWorkItem byla dokončena pro aktivitu %1, DisplayName: %2, InstanceId: '%3'. BookmarkName: %4, BookmarkScope: %5.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|Aktivita|xs:string|Název typu aktivity.|  
|displayName|xs:string|Zobrazovaný název aktivity.|  
|InstanceId|xs:string|Id instance aktivity.|  
|BookmarkName|xs:string|Název záložky|  
|Rozsah BookmarkScope|xs:string|Rozsah záložky.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
