---
title: 2578 – TryCatchExceptionFromCatchOrFinally
ms.date: 03/30/2017
ms.assetid: 4803fee6-b8d8-4937-9907-d5c5fd5299db
ms.openlocfilehash: 46fb52e665d49ed7a0336dbeeb6ed07f0d479fb0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755607"
---
# <a name="2578---trycatchexceptionfromcatchorfinally"></a>2578 – TryCatchExceptionFromCatchOrFinally
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|2578|  
|klíčová slova|WFActivities|  
|úroveň|Upozornění|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje bloku Catch nebo Finally aktivita byla vyvolána výjimka.  
  
## <a name="message"></a>Zpráva  
 Aktivita Catch nebo Finally, která je přidružená k aktivitě TryCatch '%1' byla vyvolána výjimka.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|displayName|xs:string|Zobrazovaný název aktivity.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
