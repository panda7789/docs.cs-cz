---
title: 3550 – BufferOutOfOrderMessageNoInstance
ms.date: 03/30/2017
ms.assetid: 1299d294-99b8-430e-98b1-55f5f17002f3
ms.openlocfilehash: 1af943e23aa643c6614b946175c0b1854a7ceb62
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755581"
---
# <a name="3550---bufferoutofordermessagenoinstance"></a>3550 – BufferOutOfOrderMessageNoInstance
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|3550|  
|klíčová slova|WFServices|  
|úroveň|Informace o|  
|Kanál|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Popis  
 Označuje, že ve vyrovnávací paměti receive se nezdařilo. Operace se znovu pokusí, jakmile bude instance služby připravena zpracovat tuto konkrétní operaci.  
  
## <a name="message"></a>Zpráva  
 V tuto chvíli nejde provést operaci '%1'. Další pokus bude proveden, jakmile bude instance služby připravena zpracovat tuto konkrétní operaci.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|OperationName|xs:string|Název operace.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
