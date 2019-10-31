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
ms.openlocfilehash: e23dfb86c2129a02a0ca95de8c89d8294e97ad81
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136840"
---
# <a name="createdebugginginterfacefromversion-function"></a>CreateDebuggingInterfaceFromVersion – funkce
Vytvoří objekt [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) na základě zadaných informací o verzi.  
  
 Tato funkce je zastaralá v .NET Framework 4. Místo toho chcete-li získat rozhraní pro modul CLR (Common Language Runtime) 2,0, použijte metodu [ICLRRuntimeInfo:: GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) a určete identifikátor třídy CLSID_CLRDebuggingLegacy a identifikátor rozhraní IID_ICorDebug. Chcete-li získat rozhraní pro CLR 4 nebo novější, zavolejte funkci [CLRCreateInstance –](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) a určete identifikátor třídy CLSID_CLRDebugging a identifikátor rozhraní IID_ICLRDebugging.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  int      iDebuggerVersion,   
    [in]  LPCWSTR  szDebuggeeVersion,   
    [out] IUnknown **ppCordb  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `iDebuggerVersion`  
 pro Verze `ICorDebug`, kterou očekává ladicí program. Platné hodnoty najdete ve výčtu [CorDebugInterfaceVersion –](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) .  
  
 `szDebuggeeVersion`  
 pro Verze společného jazykového modulu runtime přidružená k aplikaci nebo procesu, který se má ladit. Informace o načtení této hodnoty naleznete v metodě [GetVersionFromProcess –](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) nebo [GetRequestedRuntimeVersion –](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md) .  
  
 `ppCordb`  
 mimo Umístění, které přijímá ukazatel na objekt `ICorDebug`.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrací standardní chybové kódy modelu COM, jak jsou definovány v souboru WinError. h, kromě následujících hodnot.  
  
|Návratový kód|Popis|  
|-----------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|E_INVALIDARG|`szDebuggeeVersion` nebo `ppCordb` je null nebo je řetězec verze nesprávný.|  
  
## <a name="remarks"></a>Poznámky  
 Parametr `szDebuggeeVersion` se mapuje na odpovídající verzi MSCorDbi. dll.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Zastaralé funkce pro hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
