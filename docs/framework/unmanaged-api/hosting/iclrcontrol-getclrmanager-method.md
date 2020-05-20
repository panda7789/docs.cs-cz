---
title: ICLRControl::GetCLRManager – metoda
ms.date: 03/30/2017
api_name:
- ICLRControl.GetCLRManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl::GetCLRManager
helpviewer_keywords:
- GetCLRManager method [.NET Framework hosting]
- ICLRControl::GetCLRManager method [.NET Framework hosting]
ms.assetid: 8a11bfa4-cbb0-4082-82b5-f9fba66c93f5
topic_type:
- apiref
ms.openlocfilehash: 04cb45cd021532b6cb3d74a195cbd62e1ab8d31d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615849"
---
# <a name="iclrcontrolgetclrmanager-method"></a>ICLRControl::GetCLRManager – metoda
Získá ukazatel rozhraní na instanci kteréhokoli typu správce, který může hostitel použít ke konfiguraci modulu CLR (Common Language Runtime).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCLRManager (  
    [in]  REFIID  riid,  
    [out] void  **ppObject  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `riid`  
 pro `IID`Typ správce, který se má vrátit. `IID`Podporovány jsou následující hodnoty.  
  
- IID_ICLRDebugManager: Určuje, zda `ppObject` bude [ICLRDebugManager](iclrdebugmanager-interface.md)typu.  
  
- IID_ICLRErrorReportingManager: Určuje, zda `ppObject` bude [ICLRErrorReportingManager](iclrerrorreportingmanager-interface.md)typu.  
  
- IID_ICLRGCManager: Určuje, zda `ppObject` bude [ICLRGCManager](iclrgcmanager-interface.md)typu.  
  
- IID_ICLRHostProtectionManager: Určuje, zda `ppObject` bude [ICLRHostProtectionManager](iclrhostprotectionmanager-interface.md)typu.  
  
- IID_ICLROnEventManager: Určuje, zda `ppObject` bude [ICLROnEventManager](iclroneventmanager-interface.md)typu.  
  
- IID_ICLRPolicyManager: Určuje, zda `ppObject` bude [ICLRPolicyManager](iclrpolicymanager-interface.md)typu.  
  
- IID_ICLRTaskManager: Určuje, zda `ppObject` bude [ICLRTaskManager](iclrtaskmanager-interface.md)typu.  
  
 `ppObject`  
 mimo Ukazatel rozhraní na požadovaného správce nebo hodnotu null, pokud byl požadován neplatný typ správce.  
  
## <a name="return-value"></a>Návratová hodnota  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|Metoda byla úspěšně vrácena.|  
|HOST_E_CLRNOTAVAILABLE|Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.|  
|HOST_E_TIMEOUT|Vypršel časový limit volání.|  
|HOST_E_NOT_OWNER|Volající nevlastní zámek.|  
|HOST_E_ABANDONED|Událost byla zrušena při čekání na blokované vlákno nebo vlákna.|  
|E_FAIL|Došlo k neznámé chybě závažnosti. Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu možné použít. Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.|  
|E_NOINTERFACE|Typ rozhraní není podporován.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICLRControl – rozhraní](iclrcontrol-interface.md)
- [IHostControl – rozhraní](ihostcontrol-interface.md)
