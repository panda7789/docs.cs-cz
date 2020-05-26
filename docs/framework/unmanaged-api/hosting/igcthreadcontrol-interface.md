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
ms.openlocfilehash: 78e667acf1573769a1a67b4c964d7801f11838fe
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805129"
---
# <a name="igcthreadcontrol-interface"></a>IGCThreadControl – rozhraní
Poskytuje metody pro účast v plánování vláken, která by jinak byla zablokována pro uvolňování paměti.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[SuspensionEnding – metoda](igcthreadcontrol-suspensionending-method.md)|Upozorňuje hostitele, že modul runtime obnovuje vlákna po uvolnění paměti nebo jiném pozastavení.|  
|[SuspensionStarting – metoda](igcthreadcontrol-suspensionstarting-method.md)|Upozorňuje hostitele, že modul runtime zahajuje pozastavení vlákna pro uvolňování paměti nebo jiné pozastavení.|  
|[ThreadIsBlockingForSuspension – metoda](igcthreadcontrol-threadisblockingforsuspension-method.md)|Upozorní hostitele, že vlákno, které provádí volání, je zablokované, třeba pro uvolňování paměti nebo jiné pozastavení.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Rozhraní pro hostování](hosting-interfaces.md)
