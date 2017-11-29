---
title: "ICLRDebugManager – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebugManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDebugManager
helpviewer_keywords: ICLRDebugManager interface [.NET Framework hosting]
ms.assetid: e835062c-c7d6-4945-8a44-2de7ebf3928e
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0e537b955524f2721868ddf5da9fccf68f9d4efd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdebugmanager-interface"></a>ICLRDebugManager – rozhraní
Poskytuje metody, které umožňují hostitele k sadu úloh přidružit identifikátor a popisný název.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Beginconnection – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)|Vytvoří nové připojení mezi hostitelem a ladicí program pro přidružení úlohy s identifikátorem a popisný název.|  
|[Endconnection – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)|Odebere přidružení mezi seznamu úloh a identifikátor a popisný název.|  
|[Getdacl – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-getdacl-method.md)|Tato metoda není implementována.|  
|[Isdebuggerattached – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-isdebuggerattached-method.md)|Získá hodnotu, která určuje, zda je pro proces připojen ladicí program.|  
|[Setconnectiontasks – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)|Přidruží seznam [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance s identifikátorem a popisný název.|  
|[Setdacl – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setdacl-method.md)|Tato metoda není implementována.|  
|[Setsymbolreadingpolicy – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md)|Nastavení zásad pro soubory databáze (PDB) program pro čtení. Zásady určuje, zda je informace o čísla řádků a soubory součástí zásobníky volání.|  
  
## <a name="remarks"></a>Poznámky  
 Při ladění scénáře, hostitel chtít úlohy skupiny podle vlastní programovací logiku. Například seskupení by umožnilo vývojář zobrazit pouze úlohy, které vyžadují pomocí rozhraní API pro vývojáře, místo zobrazuje všechny úlohy spuštěné v procesu. `ICLRDebugManager`Umožňuje na hostiteli a implementovat tento druh seskupení.  
  
> [!IMPORTANT]
>  Tři `ICLRDebugManager` metody, `BeginConnection`, `SetConnectionTasks` a `EndConnection`, jsou závislé na sebe navzájem. Musí být voláno v uvedeném pořadí fungoval podle očekávání.  
  
 Seskupení a identifikátory a popisné názvy, které hostitele přiřadí k seskupení, mít žádný význam pro modul CLR (CLR). Modul CLR jenom předává informace podél ladicího programu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
