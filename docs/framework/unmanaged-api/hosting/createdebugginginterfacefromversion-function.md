---
title: CreateDebuggingInterfaceFromVersion – funkce
ms.date: 03/30/2017
api_name:
- CreateDebuggingInterfaceFromVersion
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function [.NET Framework hosting]
ms.assetid: a746a849-463c-44f5-a2f0-9e812ed8bcc3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bfba74137bab6dfe90626b5600193494df795d77
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54695579"
---
# <a name="createdebugginginterfacefromversion-function"></a>CreateDebuggingInterfaceFromVersion – funkce
Vytvoří [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) objektu na základě zadané verze informací.  
  
 Tato funkce je zastaralé v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]. Místo toho rozhraní pro modul common language runtime (CLR) 2.0, použijte [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) metodu a zadejte identifikátor třídy CLSID_CLRDebuggingLegacy a IID_ICorDebug identifikátoru rozhraní. K získání rozhraní pro modul CLR 4 nebo novější, zavolejte [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) fungovat a zadejte identifikátor třídy CLSID_CLRDebugging a IID_ICLRDebugging identifikátoru rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,   
    [in]  LPCWSTR  szDebuggeeVersion,   
    [out] IUnknown **ppCordb  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `iDebuggerVersion`  
 [in] Verze `ICorDebug` to je očekáváno ladicím programem. Zobrazit [cordebuginterfaceversion –](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) platné hodnoty výčtu.  
  
 `szDebuggeeVersion`  
 [in] Verze společného běhového jazykového přidružené aplikace nebo proces, který chcete ladit. Zobrazit [getversionfromprocess –](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) nebo [getrequestedruntimeversion –](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) metoda informace o načtení tuto hodnotu.  
  
 `ppCordb`  
 [out] Umístění, které přijímá ukazatel `ICorDebug` objektu.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací standardní kódy chyb modelu COM, jak jsou definovány v souboru WinError.h kromě následujících hodnot.  
  
|Návratový kód|Popis|  
|-----------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|E_INVALIDARG|`szDebuggeeVersion` nebo `ppCordb` má hodnotu null nebo verze řetězce je nesprávný.|  
  
## <a name="remarks"></a>Poznámky  
 `szDebuggeeVersion` Parametr mapují na odpovídající verzi knihovna MSCorDbi.dll.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [Zastaralé funkce pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
