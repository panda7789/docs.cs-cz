---
title: ICLRErrorReportingManager::EndCustomDump – metoda
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager.EndCustomDump
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager::EndCustomDump
helpviewer_keywords:
- ICLRErrorReportingManager::EndCustomDump method [.NET Framework hosting]
- EndCustomDump method [.NET Framework hosting]
ms.assetid: 88a5da04-8729-4108-82c4-af206a7d483e
topic_type:
- apiref
ms.openlocfilehash: 704d8d0921e671e4172fa6e0ae3f14c4908f289a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615654"
---
# <a name="iclrerrorreportingmanagerendcustomdump-method"></a>ICLRErrorReportingManager::EndCustomDump – metoda
Odstraní vlastní konfiguraci výpisu zásobníku, která byla zadána ve starším volání metody [ICLRErrorReportingManager:: BeginCustomDump –](iclrerrorreportingmanager-begincustomdump-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EndCustomDump ();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`EndCustomDump`úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu možné použít. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 `EndCustomDump`Metoda vymaže vlastní konfiguraci výpisu paměti zásobníku nastavenou dřívějším voláním `BeginCustomDump` metody a uvolní všechny přidružené stavy. Tato metoda by měla být volána poté, co je dokončen vlastní výpis zásobníku.  
  
> [!IMPORTANT]
> Selhání volání `EndCustomDump` způsobuje nevrácení paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [CustomDumpItem – struktura](customdumpitem-structure.md)
- [ECustomDumpFlavor – výčet](ecustomdumpflavor-enumeration.md)
- [ICLRErrorReportingManager – rozhraní](iclrerrorreportingmanager-interface.md)
