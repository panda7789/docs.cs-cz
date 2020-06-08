---
title: IHostTask::Join – metoda
ms.date: 03/30/2017
api_name:
- IHostTask.Join
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::Join
helpviewer_keywords:
- IHostTask::Join method [.NET Framework hosting]
- Join method, IHostTask interface [.NET Framework hosting]
ms.assetid: 2cffcc52-19e0-4ced-a440-fc7375078ac9
topic_type:
- apiref
ms.openlocfilehash: 20919bd9889408821cf57817082e3c7d5cebc240
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503911"
---
# <a name="ihosttaskjoin-method"></a>IHostTask::Join – metoda
Blokuje volající úlohu, dokud se nedokončí úkol, který je reprezentován aktuální instancí [IHostTask](ihosttask-interface.md) , zadaný časový interval uplyne nebo [IHostTask:: Alert](ihosttask-alert-method.md) je volána.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Join (  
    [in] DWORD milliseconds,  
    [in] DWORD option  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `milliseconds`  
 pro Časový interval (v milisekundách), po který se má čekat na ukončení úlohy. Pokud tento interval uplyne před ukončením úlohy, volající úkol odblokuje.  
  
 `option`  
 pro Jedna z hodnot [WAIT_OPTION](wait-option-enumeration.md) . Hodnota WAIT_ALERTABLE instruuje hostitele, že má probudit úlohu, pokud `Alert` je volána před `milliseconds` uplynutím doby.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|`Join`úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena, zatímco na ní bylo zastaveno blokované vlákno nebo vlákno, nebo aktuální `IHostTask` instance není přidružena k úloze.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRTask – rozhraní](iclrtask-interface.md)
- [ICLRTaskManager – rozhraní](iclrtaskmanager-interface.md)
- [IHostTask – rozhraní](ihosttask-interface.md)
- [IHostTaskManager – rozhraní](ihosttaskmanager-interface.md)
- [WAIT_OPTION – výčet](wait-option-enumeration.md)
