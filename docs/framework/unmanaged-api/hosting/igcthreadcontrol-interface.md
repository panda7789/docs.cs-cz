---
title: IGCThreadControl – rozhraní
ms.date: 03/30/2017
api_name:
- IGCThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCThreadControl
helpviewer_keywords:
- IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 3ff04d75-85ac-4df9-886d-dbaa037c0552
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5c00f401bedc1a2810c4e9b3046a45e53a79f1ea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992768"
---
# <a name="igcthreadcontrol-interface"></a>IGCThreadControl – rozhraní
Poskytuje metody pro účast při plánování vláken, která by se jinak zablokovaly pro uvolnění paměti.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[SuspensionEnding – metoda](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionending-method.md)|Upozorňuje hostitele, že modul runtime obnovuje po uvolnění paměti nebo jiných pozastavení vlákna.|  
|[SuspensionStarting – metoda](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionstarting-method.md)|Upozorňuje hostitele, že modul runtime zahajuje pozastavení vláken pro uvolnění paměti nebo jiných pozastavení.|  
|[ThreadIsBlockingForSuspension – metoda](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md)|Upozorňuje hostitele, že vlákno uskutečněním hovoru se chystáte se zablokovat, případně pro uvolnění paměti nebo jiných pozastavení.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
