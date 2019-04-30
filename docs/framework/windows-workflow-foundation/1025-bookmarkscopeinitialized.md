---
title: 1025 – BookmarkScopeInitialized
ms.date: 03/30/2017
ms.assetid: 63584434-e709-471d-9e96-97d3d99e70d6
ms.openlocfilehash: ddc9b48120b9d31f71bfc99fff19ef252b08e295
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924641"
---
# <a name="1025---bookmarkscopeinitialized"></a>1025 – BookmarkScopeInitialized
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1025|  
|klíčová slova|WFRuntime|  
|úroveň|Podrobnosti|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že rozsah BookmarkScope byl inicializován.  
  
## <a name="message"></a>Zpráva  
 Rozsah BookmarkScope s temporaryid: '%1' byl inicializován s Id: '%2'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|TemporaryId|xs:string|Dočasné id záložky.|  
|InitializedId|xs:string|Inicializované id záložky.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
