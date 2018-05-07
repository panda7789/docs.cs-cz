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
ms.openlocfilehash: 06bdc3605d981acad68a97901627f361da4061c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugremotecreateprocessex-method"></a>ICorDebugRemote::CreateProcessEx – metoda
Spustí proces ve vzdáleném počítači v rámci ladicího programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `pRemoteTarget`  
 [v] Ukazatel na [ICorDebugRemoteTarget rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md). Použít k určení vzdáleného počítače, na kterém se spustí proces.  
  
 `lpApplicationName`  
 [v] Ukazatel na řetězec ukončené hodnotou null, který určuje modulu provést spuštěného procesem. V modulu se spouštějí v kontextu zabezpečení volajícího procesu.  
  
 `lpCommandLine`  
 [v] Ukazatel na řetězec ukončené hodnotou null, který určuje příkazový řádek, který má být proveden spuštěného procesem.  
  
 `lpProcessAttributes`  
 [v] Nepoužívá se pro vzdálené ladění.  
  
 `lpThreadAttributes`  
 [v] Nepoužívá se pro vzdálené ladění.  
  
 `bInheritHandles`  
 [v] Nepoužívá se pro vzdálené ladění.  
  
 `dwCreationFlags`  
 [v] Nepoužívá se pro vzdálené ladění.  
  
 `lpEnvironment`  
 [v] Ukazatel na blok prostředí pro nový proces.  
  
 `lpCurrentDirectory`  
 [v] Ukazatel na řetězec ukončené hodnotou null, který určuje úplnou cestu k aktuálnímu adresáři pro proces. Pokud tento parametr hodnotu null, nový proces bude mít stejný aktuální jednotku a adresář jako volající proces.  
  
 `lpStartupInfo`  
 [v] Nepoužívá se pro vzdálené ladění.  
  
 `lpProcessInformation`  
 [v] Nepoužívá se pro vzdálené ladění.  
  
 `debuggingFlags`  
 [v] Nepoužívá se pro vzdálené ladění.  
  
 `ppProcess`  
 [out] Ukazatel na adresu "ICorDebugProcess rozhraní" objekt, který představuje proces.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 Úspěšně spustit proces na vzdáleném počítači a vrácený "ICorDebugProcess rozhraní" pro ladění.  
  
 E_FAIL (nebo ostatní návratové kódy E_)  
 Nelze spustit proces ve vzdáleném počítači a vrátí "ICorDebugProcess rozhraní" pro ladění.  
  
## <a name="remarks"></a>Poznámky  
 Ladění ve smíšeném režimu není podporována v programu Silverlight.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** 4.5, 4, 3.5 SP1  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugRemote – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 [ICorDebug – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
