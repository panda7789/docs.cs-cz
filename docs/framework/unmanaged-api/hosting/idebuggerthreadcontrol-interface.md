---
title: IDebuggerThreadControl – rozhraní
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IDebuggerThreadControl
helpviewer_keywords:
- IDebuggerThreadControl interface [.NET Framework hosting]
ms.assetid: 0a270c42-a7d1-45f1-a64d-fa3e84d14532
topic_type:
- apiref
ms.openlocfilehash: a65f9f0f29a43cf3d26b4b2bc5f6f594f0557009
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133163"
---
# <a name="idebuggerthreadcontrol-interface"></a>IDebuggerThreadControl – rozhraní
Poskytuje metody pro upozorňování hostitele na blokování a odblokování vláken pomocí služby ladění.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ThreadIsBlockingForDebugger – metoda](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-threadisblockingfordebugger-method.md)|Upozorní hostitele, že vlákno odesílající toto zpětné volání se chystá blokovat v rámci služby ladění.|  
|[ReleaseAllRuntimeThreads – metoda](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-releaseallruntimethreads-method.md)|Upozorňuje hostitele, že se chystá ladicí služby uvolnit všechna blokovaná vlákna.|  
|[StartBlockingForDebugger – metoda](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-startblockingfordebugger-method.md)|Upozorňuje hostitele, že se chystá služby ladění zahájit blokování všech vláken.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
