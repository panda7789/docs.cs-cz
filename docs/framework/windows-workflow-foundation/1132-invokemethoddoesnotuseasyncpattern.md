---
title: 1132 – InvokeMethodDoesNotUseAsyncPattern
ms.date: 03/30/2017
ms.assetid: 436b3767-4460-46b0-9ea3-fc2963260c11
ms.openlocfilehash: 64701d4c38c042e8273129be19f9caeb2c442abf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924212"
---
# <a name="1132---invokemethoddoesnotuseasyncpattern"></a>1132 – InvokeMethodDoesNotUseAsyncPattern
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|1132|  
|klíčová slova|WFRuntime|  
|úroveň|Informace o|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Během kroku CacheMetadata aktivity InvokeMethod označuje, že ho nepoužívá asynchronní vzorek, při volání metody.  
  
## <a name="message"></a>Zpráva  
 InvokeMethod '%1' - metoda nepoužívá asynchronní vzorek.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|InvokeMethod|xs:string|Zobrazovaný název aktivity InvokeMethod|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
