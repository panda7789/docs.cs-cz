---
title: 2577 - TryCatchExceptionDuringCancelation
ms.date: 03/30/2017
ms.assetid: 35ee9f55-227f-4566-bcb4-4c7c75dea85b
ms.openlocfilehash: c272dd91249dfc90e6f4c38a7339919a5a6446e5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="2577---trycatchexceptionduringcancelation"></a>2577 - TryCatchExceptionDuringCancelation
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|2577|  
|Klíčová slova|WFActivities|  
|úroveň|Upozornění|  
|Kanál|Aplikaci Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že podřízené aktivity TryCatch aktivity došlo k výjimce při zrušení.  
  
## <a name="message"></a>Zpráva  
 Aktivita podřízené aktivity TryCatch '%1' došlo k výjimce při zrušení.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datová položka – Typ|Popis|  
|--------------------|--------------------|-----------------|  
|displayName|xs:String|Zobrazovaný název aktivity.|  
|Domény aplikace|xs:String|Řetězec vrácený AppDomain.CurrentDomain.FriendlyName.|
