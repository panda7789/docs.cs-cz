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
ms.openlocfilehash: 5a408995793caf879f8d5624ab727102c4859195
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959612"
---
# <a name="iclrdebugmanager-interface"></a>ICLRDebugManager – rozhraní
Poskytuje metody, které umožňují hostiteli přidružit sadu úkolů s identifikátorem a popisným názvem.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[BeginConnection – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)|Vytvoří nové propojení mezi hostitelem a ladicím programem k přidružení úkolů k identifikátoru a popisnému názvu.|  
|[EndConnection – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)|Odebere přidružení mezi seznamem úkolů a identifikátorem a popisným názvem.|  
|[GetDacl – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-getdacl-method.md)|Tato metoda není implementována.|  
|[IsDebuggerAttached – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-isdebuggerattached-method.md)|Získá hodnotu, která označuje, zda je k procesu připojen ladicí program.|  
|[SetConnectionTasks – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)|Přidruží seznam instancí [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) s identifikátorem a popisným názvem.|  
|[SetDacl – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setdacl-method.md)|Tato metoda není implementována.|  
|[SetSymbolReadingPolicy – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md)|Nastaví zásadu pro soubory databáze programu pro čtení. Tato zásada určuje, zda jsou do zásobníků volání zahrnuty informace o číslech řádků a souborech.|  
  
## <a name="remarks"></a>Poznámky  
 Ve scénářích ladění může hostitel chtít seskupit úkoly podle vlastní programovací logiky. Například seskupení umožní vývojářům zobrazit jenom úkoly požadované rozhraními API vývojářů místo zobrazení všech úloh spuštěných v procesu. `ICLRDebugManager`umožňuje hostiteli implementovat tento druh seskupení.  
  
> [!IMPORTANT]
> Tři `ICLRDebugManager` metody `BeginConnection` ,a`EndConnection`,jsou závislé na sobě. `SetConnectionTasks` Musí být volány v daném pořadí, aby fungovaly podle očekávání.  
  
 Seskupení a identifikátory a popisné názvy, které hostitel přiřadí seskupení, nemají žádný význam pro modul CLR (Common Language Runtime). Modul CLR pouze předává informace spolu s ladicím programem.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlaviček** MSCorEE. h  
  
 **Knihovna** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
