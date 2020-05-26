---
title: IHostSyncManager::CreateMonitorEvent – metoda
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateMonitorEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateMonitorEvent
helpviewer_keywords:
- CreateMonitorEvent method [.NET Framework hosting]
- IHostSyncManager::CreateMonitorEvent method [.NET Framework hosting]
ms.assetid: 524c7fd3-9b5c-46e7-99ba-555fd2fe33f0
topic_type:
- apiref
ms.openlocfilehash: c0f7e1fd6bf4c9386300b11477df85e87899fc67
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83803325"
---
# <a name="ihostsyncmanagercreatemonitorevent-method"></a>IHostSyncManager::CreateMonitorEvent – metoda
Vytvoří monitorovaný objekt události automatického resetování.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateMonitorEvent (  
    [in]  SIZE_T cookie,  
    [out] IHostAutoEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `cookie`  
 pro Soubor cookie, který se má přidružit k objektu události.  
  
 `ppEvent`  
 mimo Ukazatel na adresu instance [IHostAutoEvent](ihostautoevent-interface.md) nebo hodnotu null, pokud objekt události nelze vytvořit.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|`CreateMonitorEvent`úspěšně vráceno.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
|E_OUTOFMEMORY|Pro vytvoření požadovaného objektu události není k dispozici dostatek paměti.|  
  
## <a name="remarks"></a>Poznámky  
 `CreateMonitorEvent`Vrátí `IHostAutoEvent` , že CLR používá při implementaci spravovaného <xref:System.Threading.Monitor?displayProperty=nameWithType> typu. Tato metoda zrcadlí `CreateEvent` funkci Win32 s hodnotou `false` zadanou pro `bManualReset` parametr.  
  
 Hostitel může pomocí souboru cookie určit, který úkol čeká na monitorování voláním metody [ICLRSyncManager:: GetMonitorOwner –](iclrsyncmanager-getmonitorowner-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRSyncManager – rozhraní](iclrsyncmanager-interface.md)
- [IHostAutoEvent – rozhraní](ihostautoevent-interface.md)
- [IHostSyncManager – rozhraní](ihostsyncmanager-interface.md)
- <xref:System.Threading.Monitor>
