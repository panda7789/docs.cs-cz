---
title: ICLRDebugManager::BeginConnection – metoda
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.BeginConnection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::BeginConnection
helpviewer_keywords:
- ICLRDebugManager::BeginConnection method [.NET Framework hosting]
- BeginConnection method [.NET Framework hosting]
ms.assetid: bdd98146-ff4d-4150-a264-a4c1a32d31f3
topic_type:
- apiref
ms.openlocfilehash: 98e4efe149cab1b822c9993e4df28806f773c61d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504248"
---
# <a name="iclrdebugmanagerbeginconnection-method"></a>ICLRDebugManager::BeginConnection – metoda
Vytvoří nové propojení mezi hostitelem a ladicím programem k přidružení seznamu úkolů s identifikátorem a popisným názvem.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT BeginConnection (  
    [in] CONNID dwConnectionId,  
    [in, string] wchar_t* szConnectionName  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwConnectionId`  
 pro Identifikátor, který se má přidružit k seznamu úloh modulu CLR (Common Language Runtime).  
  
 `szConnectionName`  
 pro Popisný název, který chcete přidružit k seznamu úkolů CLR.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`BeginConnection`úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu možné použít. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
|E_INVALIDARG|`dwConnectionId`byla nulová nebo `BeginConnection` již byla volána pomocí této `dwConnectionId` hodnoty, nebo `szConnectionName` měla hodnotu null.|  
|E_OUTOFMEMORY|Nebylo možné přidělit dostatek paměti pro uložení seznamu úkolů přidružených k tomuto připojení.|  
  
## <a name="remarks"></a>Poznámky  
 [ICLRDebugManager](iclrdebugmanager-interface.md) poskytuje tři metody, `BeginConnection` , [SetConnectionTasks –](iclrdebugmanager-setconnectiontasks-method.md)a [EndConnection –](iclrdebugmanager-endconnection-method.md)pro přiřazování seznamů úkolů s identifikátory a popisnými názvy.  
  
> [!IMPORTANT]
> Tyto tři metody musí být volány v určitém pořadí pro každou sadu úkolů. `BeginConnection`se označuje jako první, aby se navázalo nové připojení. `SetConnectionTasks`se volá vedle a poskytne sadu úloh, které se mají přidružit k tomuto připojení. `EndConnection`je volána jako poslední k odebrání přidružení mezi seznamem úkolů a identifikátorem a popisným názvem. Volání různých připojení však mohou být vnořena.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRControl – rozhraní](iclrcontrol-interface.md)
- [ICLRDebugManager – rozhraní](iclrdebugmanager-interface.md)
- [EndConnection – metoda](iclrdebugmanager-endconnection-method.md)
- [SetConnectionTasks – metoda](iclrdebugmanager-setconnectiontasks-method.md)
- [IHostControl – rozhraní](ihostcontrol-interface.md)
