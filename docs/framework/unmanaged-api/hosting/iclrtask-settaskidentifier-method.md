---
title: ICLRTask::SetTaskIdentifier – metoda
ms.date: 03/30/2017
api_name:
- ICLRTask.SetTaskIdentifier
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask::SetTaskIdentifier
helpviewer_keywords:
- SetTaskIdentifier method [.NET Framework hosting]
- ICLRTask::SetTaskIdentifier method [.NET Framework hosting]
ms.assetid: bdb7f047-1e90-40fc-9e3b-d44a16509073
topic_type:
- apiref
ms.openlocfilehash: e1b93356fd40aacdec2e764946e3e3b12d0bd306
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762939"
---
# <a name="iclrtasksettaskidentifier-method"></a>ICLRTask::SetTaskIdentifier – metoda
Instruuje modul CLR (Common Language Runtime), aby přidružil zadanou hodnotu identifikátoru k úloze reprezentované aktuální instancí [ICLRTask](iclrtask-interface.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetTaskIdentifier (  
    [in] DWORD Asked  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `Asked`  
 pro Jedinečný identifikátor pro modul CLR (Common Language Runtime), který se má přidružit k úloze reprezentované aktuální `ICLRTask` instancí.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`SetTaskIdentifier`úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Poznámky  
 Hostitel může přidružit identifikátor k úloze, aby bylo možné integrovat modul CLR a hostitele v ladicím prostředí. Identifikátor nemá pro CLR žádný význam. CLR je předá aplikaci ladicího programu. Ladicí program může tento identifikátor použít k přidružení zásobníku volání CLR k zásobníku volání hostitele a při zobrazení v uživatelském rozhraní ladicího programu povolit sjednocení příslušných trasovacích informací.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRTask – rozhraní](iclrtask-interface.md)
- [ICLRTaskManager – rozhraní](iclrtaskmanager-interface.md)
- [IHostTask – rozhraní](ihosttask-interface.md)
- [IHostTaskManager – rozhraní](ihosttaskmanager-interface.md)
