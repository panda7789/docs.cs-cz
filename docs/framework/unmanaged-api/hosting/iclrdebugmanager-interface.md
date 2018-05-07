---
title: ICLRDebugManager – rozhraní
ms.date: 03/30/2017
api_name:
- ICLRDebugManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager
helpviewer_keywords:
- ICLRDebugManager interface [.NET Framework hosting]
ms.assetid: e835062c-c7d6-4945-8a44-2de7ebf3928e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d123177bf9f1b5eee1a2ba4d9b7f2042ddc07aa2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="iclrdebugmanager-interface"></a>ICLRDebugManager – rozhraní
Poskytuje metody, které umožňují hostitele k sadu úloh přidružit identifikátor a popisný název.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[BeginConnection – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)|Vytvoří nové připojení mezi hostitelem a ladicí program pro přidružení úlohy s identifikátorem a popisný název.|  
|[EndConnection – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)|Odebere přidružení mezi seznamu úloh a identifikátor a popisný název.|  
|[GetDacl – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-getdacl-method.md)|Tato metoda není implementována.|  
|[IsDebuggerAttached – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-isdebuggerattached-method.md)|Získá hodnotu, která určuje, zda je pro proces připojen ladicí program.|  
|[SetConnectionTasks – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)|Přidruží seznam [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance s identifikátorem a popisný název.|  
|[SetDacl – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setdacl-method.md)|Tato metoda není implementována.|  
|[SetSymbolReadingPolicy – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md)|Nastavení zásad pro soubory databáze (PDB) program pro čtení. Zásady určuje, zda je informace o čísla řádků a soubory součástí zásobníky volání.|  
  
## <a name="remarks"></a>Poznámky  
 Při ladění scénáře, hostitel chtít úlohy skupiny podle vlastní programovací logiku. Například seskupení by umožnilo vývojář zobrazit pouze úlohy, které vyžadují pomocí rozhraní API pro vývojáře, místo zobrazuje všechny úlohy spuštěné v procesu. `ICLRDebugManager` Umožňuje na hostiteli a implementovat tento druh seskupení.  
  
> [!IMPORTANT]
>  Tři `ICLRDebugManager` metody, `BeginConnection`, `SetConnectionTasks` a `EndConnection`, jsou závislé na sebe navzájem. Musí být voláno v uvedeném pořadí fungoval podle očekávání.  
  
 Seskupení a identifikátory a popisné názvy, které hostitele přiřadí k seskupení, mít žádný význam pro modul CLR (CLR). Modul CLR jenom předává informace podél ladicího programu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
