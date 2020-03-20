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
ms.openlocfilehash: adc8ea16f0ab2bf383f8a63c49ba7d61c6bac113
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176445"
---
# <a name="createdebugginginterfacefromversion-function"></a>CreateDebuggingInterfaceFromVersion – funkce
Vytvoří objekt [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) na základě informací o zadané verzi.  
  
 Tato funkce je v rozhraní .NET Framework 4 zastaralá. Místo toho chcete získat rozhraní pro modul CLR (CLR) 2.0, použijte metodu [ICLRRuntimeInfo::GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) a zadejte identifikátor třídy CLSID_CLRDebuggingLegacy a identifikátor rozhraní IID_ICorDebug. Chcete-li získat rozhraní pro CLR 4 nebo novější, zavolejte funkci [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) a zadejte identifikátor třídy CLSID_CLRDebugging a identifikátor rozhraní IID_ICLRDebugging.  
  
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
 [v] Verze, `ICorDebug` která je očekávána ladicí program. Viz [CorDebugInterfaceVersion](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md) výčet platné hodnoty.  
  
 `szDebuggeeVersion`  
 [v] Verze za běhu běžného jazyka přidružená k aplikaci nebo procesu, který má být laděn. Informace o načtení této hodnoty naleznete v metodě [GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md) nebo [GetRequestedRuntimeVersion.](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)  
  
 `ppCordb`  
 [out] Umístění, které přijímá ukazatel `ICorDebug` na objekt.  
  
## <a name="return-value"></a>Návratová hodnota  
 Tato metoda vrátí standardní kódy chyb COM, jak jsou definovány v souboru WinError.h kromě následujících hodnot.  
  
|Návratový kód|Popis|  
|-----------------|-----------------|  
|S_OK|Metoda byla úspěšně dokončena.|  
|E_invalidarg|`szDebuggeeVersion`nebo `ppCordb` je null nebo je řetězec verze nesprávný.|  
  
## <a name="remarks"></a>Poznámky  
 Parametr `szDebuggeeVersion` se mapuje na odpovídající verzi souboru MSCorDbi.dll.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** Soubor MSCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Zastaralé funkce hostování CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
