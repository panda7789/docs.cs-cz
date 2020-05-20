---
title: ICLRDebugManager::EndConnection – metoda
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.EndConnection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::EndConnection
helpviewer_keywords:
- ICLRDebugManager::EndConnection method [.NET Framework hosting]
- EndConnection method [.NET Framework hosting]
ms.assetid: 89dc7363-2f29-4eb2-8f23-fccdda6a76a6
topic_type:
- apiref
ms.openlocfilehash: f524cadf77caec0823411784c68f339207433601
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615779"
---
# <a name="iclrdebugmanagerendconnection-method"></a>ICLRDebugManager::EndConnection – metoda
Odebere přidružení mezi seznamem úkolů a identifikátorem a popisným názvem.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EndConnection (  
    [in] CONNID dwConnectionId  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwConnectionId`  
 pro Identifikátor konkrétního hostitele pro připojení a přidružený seznam úloh modulu CLR (Common Language Runtime).  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`EndConnection`úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu možné použít. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
|E_INVALIDARG|[BeginConnection –](iclrdebugmanager-beginconnection-method.md) se nikdy nevolal pomocí `dwConnectionId` nebo `dwConnectionId` byl nulový.|  
  
## <a name="remarks"></a>Poznámky  
 [ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md) poskytuje tři metody, `BeginConnection` , [SetConnectionTasks –](iclrdebugmanager-setconnectiontasks-method.md)a `EndConnection` , pro přiřazování seznamů úkolů s identifikátory a popisnými názvy.  
  
> [!IMPORTANT]
> Tyto tři metody musí být volány v určitém pořadí pro každou sadu úkolů. `BeginConnection`se označuje jako první, aby se navázalo nové připojení. `SetConnectionTasks`se volá vedle a poskytne sadu úloh, které se mají přidružit k tomuto připojení. `EndConnection`je volána jako poslední k odebrání přidružení mezi seznamem úkolů a identifikátorem a popisným názvem. Volání různých připojení však mohou být vnořena.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRControl – rozhraní](iclrcontrol-interface.md)
- [ICLRDebugManager – rozhraní](iclrdebugmanager-interface.md)
- [BeginConnection – metoda](iclrdebugmanager-beginconnection-method.md)
- [SetConnectionTasks – metoda](iclrdebugmanager-setconnectiontasks-method.md)
- [IHostControl – rozhraní](ihostcontrol-interface.md)
