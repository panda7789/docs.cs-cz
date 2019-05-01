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
ms.openlocfilehash: 22c3a480e2b68377e300df1083b3178ee4e2d2a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61969855"
---
# <a name="iclrdebugmanager-interface"></a>ICLRDebugManager – rozhraní
Poskytuje metody, které umožňují hostitele do sady úloh přidružit identifikátor a popisný název.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[BeginConnection – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)|Vytvoří nové připojení mezi hostitelem a ladicí program přidružit identifikátor a popisný název úlohy.|  
|[EndConnection – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)|Odebere přidružení mezi seznam úkolů a identifikátor a popisný název.|  
|[GetDacl – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-getdacl-method.md)|Tato metoda není implementována.|  
|[IsDebuggerAttached – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-isdebuggerattached-method.md)|Získá hodnotu určující, zda je připojen ladicí program k procesu.|  
|[SetConnectionTasks – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)|Přidruží seznam [iclrtask –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instance s identifikátorem a popisný název.|  
|[SetDacl – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setdacl-method.md)|Tato metoda není implementována.|  
|[SetSymbolReadingPolicy – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md)|Nastavit zásady pro čtení souborů databáze (PDB) programu. Zásady určuje, zda informace o čísla řádků a souborů je součástí zásobníky volání.|  
  
## <a name="remarks"></a>Poznámky  
 Při ladění scénáře, může být vhodné hostitele pro seskupení úkolů podle vlastní programovou logiku. Například seskupení umožní vývojářům zobrazit pouze úkoly, které vyžadují rozhraní API pro vývojáře, místo toho každá úloha spuštění v procesu, abyste. `ICLRDebugManager` umožňuje hostiteli implementovat tento druh seskupení.  
  
> [!IMPORTANT]
>  Tři `ICLRDebugManager` metody, `BeginConnection`, `SetConnectionTasks` a `EndConnection`, jsou závislé na sebe navzájem. Musí být volána v uvedeném pořadí fungovat podle očekávání.  
  
 Seskupení a identifikátory a popisné názvy, které hostitele přiřadí k seskupení, nemají význam pro modul common language runtime (CLR). Modul CLR pouze předává informace podél do ladicího programu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
