---
title: 2576 – TryCatchExceptionFromTry
ms.date: 03/30/2017
ms.assetid: 47e48973-b17c-4a16-8338-c84b54aa0a6e
ms.openlocfilehash: cdc48a1a08e997f7bc6a0ad6b93aa13640af9ed3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755646"
---
# <a name="2576---trycatchexceptionfromtry"></a>2576 – TryCatchExceptionFromTry
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|2576|  
|klíčová slova|WFActivities|  
|úroveň|Informace o|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje, že aktivita TryCatch zachytila výjimku.  
  
## <a name="message"></a>Zpráva  
 Aktivita TryCatch '%1' zachytila výjimku typu '%2'.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|displayName|xs:string|Zobrazovaný název aktivity.|  
|Výjimka|xs:string|Název typu výjimky.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
