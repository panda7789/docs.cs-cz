---
title: ICorDebugRemote::CreateProcessEx – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugRemote.CreateProcessEx
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::CreateProcessEx
helpviewer_keywords:
- CreateProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
- ICorDebugRemote::CreateProcessEx method [.NET Framework debugging]
ms.assetid: 41af93c7-e448-4251-8d4d-413d38c635f2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d05384af8201fae8cf81650d38c99a5c44e6bd16
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744772"
---
# <a name="icordebugremotecreateprocessex-method"></a>ICorDebugRemote::CreateProcessEx – metoda
Spustí nějaký proces ve vzdáleném počítači v ladicím programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateProcessEx (  
    [in]  ICorDebugRemoteTarget*      pRemoteTarget,  
    [in]  LPCWSTR                     lpApplicationName,  
    [in]  LPWSTR                      lpCommandLine,  
    [in]  LPSECURITY_ATTRIBUTES       lpProcessAttributes,  
    [in]  LPSECURITY_ATTRIBUTES       lpThreadAttributes,  
    [in]  BOOL                        bInheritHandles,  
    [in]  DWORD                       dwCreationFlags,  
    [in]  PVOID                       lpEnvironment,  
    [in]  LPCWSTR                     lpCurrentDirectory,  
    [in]  LPSTARTUPINFOW              lpStartupInfo,  
    [in]  LPPROCESS_INFORMATION       lpProcessInformation,  
    [in]  CorDebugCreateProcessFlags  debuggingFlags,  
    [out] ICorDebugProcess**          ppProcess  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pRemoteTarget`  
 [in] Ukazatel [icordebugremotetarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md). Slouží k určení vzdáleného počítače, na kterém se spustí proces.  
  
 `lpApplicationName`  
 [in] Ukazatel na řetězec zakončený hodnotou null, který určuje modulu je spuštěn proces provést. Modul provádí v kontextu zabezpečení volajícího procesu.  
  
 `lpCommandLine`  
 [in] Ukazatel na řetězec zakončený hodnotou null, který určuje příkazový řádek, který se spustí proces spuštěný.  
  
 `lpProcessAttributes`  
 [in] Nepoužitý pro vzdálené ladění.  
  
 `lpThreadAttributes`  
 [in] Nepoužitý pro vzdálené ladění.  
  
 `bInheritHandles`  
 [in] Nepoužitý pro vzdálené ladění.  
  
 `dwCreationFlags`  
 [in] Nepoužitý pro vzdálené ladění.  
  
 `lpEnvironment`  
 [in] Ukazatele na blok prostředí nového procesu.  
  
 `lpCurrentDirectory`  
 [in] Ukazatel na řetězec zakončený hodnotou null, který určuje úplnou cestu k adresáři aktuální proces. Pokud má parametr hodnotu null, nový proces bude mít stejný aktuální jednotku a adresář jako volající proces.  
  
 `lpStartupInfo`  
 [in] Nepoužitý pro vzdálené ladění.  
  
 `lpProcessInformation`  
 [in] Nepoužitý pro vzdálené ladění.  
  
 `debuggingFlags`  
 [in] Nepoužitý pro vzdálené ladění.  
  
 `ppProcess`  
 [out] Ukazatel na adresu "Icordebugprocess – rozhraní" objekt, který představuje proces.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 Byl úspěšně spuštěn proces na vzdáleném počítači a vrácené "icordebugprocess – rozhraní" pro ladění.  
  
 E_FAIL (nebo jiné E_ návratové kódy)  
 Nelze spustit proces na vzdáleném počítači a vrátit "Icordebugprocess – rozhraní" pro ladění.  
  
## <a name="remarks"></a>Poznámky  
 Ladění ve smíšeném režimu není v Silverlightu podporovaný.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** 4.5, 4, 3.5 SP1  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugRemote – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)
- [ICorDebug – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
