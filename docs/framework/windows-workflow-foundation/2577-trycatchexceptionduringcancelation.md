---
title: 2577 – TryCatchExceptionDuringCancelation
ms.date: 03/30/2017
ms.assetid: 35ee9f55-227f-4566-bcb4-4c7c75dea85b
ms.openlocfilehash: c272dd91249dfc90e6f4c38a7339919a5a6446e5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755620"
---
# <a name="2577---trycatchexceptionduringcancelation"></a>2577 – TryCatchExceptionDuringCancelation
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|2577|  
|klíčová slova|WFActivities|  
|úroveň|Upozornění|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že podřízená aktivita aktivity TryCatch generovala výjimku při stornování.  
  
## <a name="message"></a>Zpráva  
 Podřízená aktivita aktivity TryCatch '%1' vyvolal výjimku při stornování.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|displayName|xs:string|Zobrazovaný název aktivity.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
