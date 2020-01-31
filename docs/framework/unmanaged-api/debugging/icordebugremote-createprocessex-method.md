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
ms.openlocfilehash: cfec84483d387630623f77c176c668171303dd0f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791979"
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
 pro Ukazatel na [rozhraní ICorDebugRemoteTarget](icordebugremotetarget-interface.md). Slouží k určení vzdáleného počítače, na kterém se proces spustí.  
  
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

- [ICorDebugRemote – rozhraní](icordebugremote-interface.md)
- [ICorDebug – rozhraní](icordebug-interface.md)

- [Rozhraní pro ladění](debugging-interfaces.md)
