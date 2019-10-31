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
ms.openlocfilehash: 9e1a5ba65da09c90f33e5e8108c3bd91f3aee4a1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131284"
---
# <a name="icordebugremotecreateprocessex-method"></a>ICorDebugRemote::CreateProcessEx – metoda
Spustí proces na vzdáleném počítači v rámci ladicího programu.  
  
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
 pro Ukazatel na [rozhraní ICorDebugRemoteTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md). Slouží k určení vzdáleného počítače, na kterém se proces spustí.  
  
 `lpApplicationName`  
 pro Ukazatel na řetězec zakončený hodnotou null, který určuje modul, který má být spuštěn spuštěným procesem. Modul je spuštěn v kontextu zabezpečení volajícího procesu.  
  
 `lpCommandLine`  
 pro Ukazatel na řetězec zakončený hodnotou null, který určuje příkazový řádek, který má být spuštěn spuštěným procesem.  
  
 `lpProcessAttributes`  
 pro Nevyužité pro vzdálené ladění.  
  
 `lpThreadAttributes`  
 pro Nevyužité pro vzdálené ladění.  
  
 `bInheritHandles`  
 pro Nevyužité pro vzdálené ladění.  
  
 `dwCreationFlags`  
 pro Nevyužité pro vzdálené ladění.  
  
 `lpEnvironment`  
 pro Ukazatel na blok prostředí pro nový proces.  
  
 `lpCurrentDirectory`  
 pro Ukazatel na řetězec zakončený hodnotou null, který určuje úplnou cestu k aktuálnímu adresáři pro daný proces. Pokud má tento parametr hodnotu null, nový proces bude mít stejnou aktuální jednotku a adresář jako volající proces.  
  
 `lpStartupInfo`  
 pro Nevyužité pro vzdálené ladění.  
  
 `lpProcessInformation`  
 pro Nevyužité pro vzdálené ladění.  
  
 `debuggingFlags`  
 pro Nevyužité pro vzdálené ladění.  
  
 `ppProcess`  
 mimo Ukazatel na adresu objektu rozhraní ICorDebugProcess, který představuje proces.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 Proces byl úspěšně spuštěn na vzdáleném počítači a pro ladění vrátil rozhraní ICorDebugProcess.  
  
 E_FAIL (nebo jiné návratové kódy E_)  
 Nepovedlo se spustit proces na vzdáleném počítači a vrátit rozhraní ICorDebugProcess pro ladění.  
  
## <a name="remarks"></a>Poznámky  
 Ladění ve smíšeném režimu není v Silverlightu podporované.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** 4,5, 4, 3,5 SP1  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugRemote – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)
- [ICorDebug – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
