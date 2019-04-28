---
title: 3551 – BufferOutOfOrderMessageNoBookmark
ms.date: 03/30/2017
ms.assetid: 7930d6c4-c843-4a83-933a-cecd71b80d1e
ms.openlocfilehash: 89643edde5856688c762b0cf0d188bd4e7ba8a24
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755529"
---
# <a name="3551---bufferoutofordermessagenobookmark"></a>3551 – BufferOutOfOrderMessageNoBookmark
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|3551|  
|klíčová slova|WFServices|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Označuje, že záložku obnovení se nezdařilo. Operace přijetí ve vyrovnávací paměti se znovu pokusí Jakmile bude instance služby připravena zpracovat tuto konkrétní operaci.  
  
## <a name="message"></a>Zpráva  
 V tuto chvíli nejde provést operaci "%2" na instanci služby '%1'. Další pokus bude proveden, jakmile bude instance služby připravena zpracovat tuto konkrétní operaci.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|OperationName|xs:string|Název operace.|  
|ServiceInstanceId|xs:string|Id instance služby.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
