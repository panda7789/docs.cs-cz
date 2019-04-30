---
title: 1020 – CreateBookmark
ms.date: 03/30/2017
ms.assetid: 4bee948d-816f-4803-85cc-3883b5e23d10
ms.openlocfilehash: 2a382a2f12f4800cd70286a553af253e2af64c9b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924745"
---
# <a name="1020---createbookmark"></a>1020 – CreateBookmark
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1020|  
|klíčová slova|WFRuntime|  
|úroveň|Podrobnosti|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že byla záložka vytvořena pro aktivitu.  
  
## <a name="message"></a>Zpráva  
 Záložka byla vytvořena pro aktivitu %1, DisplayName: %2, InstanceId: '%3'.  BookmarkName: %4, BookmarkScope: %5.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|Aktivita|xs:string|Název typu aktivity.|  
|displayName|xs:string|Zobrazovaný název aktivity.|  
|InstanceId|xs:string|Id instance aktivity.|  
|BookmarkName|xs:string|Název záložky|  
|Rozsah BookmarkScope|xs:string|Rozsah záložky.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
