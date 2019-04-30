---
title: 4211 – QueuingSqlRetry
ms.date: 03/30/2017
ms.assetid: df569f88-c86b-4503-840d-1399b67f4df7
ms.openlocfilehash: ede74eb642c5c2c79b90cf1458db424d9f83b087
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774241"
---
# <a name="4211---queuingsqlretry"></a>4211 – QueuingSqlRetry
## <a name="properties"></a>Vlastnosti  
  
|||  
|-|-|  
|ID|4211|  
|klíčová slova|WFInstanceStore|  
|úroveň|Upozornění|  
|Kanál|Aplikace Microsoft Windows Server – aplikace/Debug|  
  
## <a name="description"></a>Popis  
 Označuje zařazení opětovného pokusu SQL.  
  
## <a name="message"></a>Zpráva  
 Zařazení opětovného pokusu SQL s prodlevou %1 MS.  
  
## <a name="details"></a>Podrobnosti  
  
|Název položky dat|Datový typ položky|Popis|  
|--------------------|--------------------|-----------------|  
|zpoždění|xs:string|Zpoždění mezi opakovanými pokusy.|  
|AppDomain|xs:string|Řetězec vrácený funkcí AppDomain.CurrentDomain.FriendlyName.|
