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
ms.openlocfilehash: 82c6113f4df3334500128df22f7e9ce8d4bf151f
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805277"
---
# <a name="idebuggerthreadcontrol-interface"></a>IDebuggerThreadControl – rozhraní
Poskytuje metody pro upozorňování hostitele na blokování a odblokování vláken pomocí služby ladění.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[ThreadIsBlockingForDebugger – metoda](idebuggerthreadcontrol-threadisblockingfordebugger-method.md)|Upozorní hostitele, že vlákno odesílající toto zpětné volání se chystá blokovat v rámci služby ladění.|  
|[ReleaseAllRuntimeThreads – metoda](idebuggerthreadcontrol-releaseallruntimethreads-method.md)|Upozorňuje hostitele, že se chystá ladicí služby uvolnit všechna blokovaná vlákna.|  
|[StartBlockingForDebugger – metoda](idebuggerthreadcontrol-startblockingfordebugger-method.md)|Upozorňuje hostitele, že se chystá služby ladění zahájit blokování všech vláken.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Rozhraní pro hostování](hosting-interfaces.md)
