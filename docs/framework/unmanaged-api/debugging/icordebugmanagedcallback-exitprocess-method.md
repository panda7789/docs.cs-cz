---
title: ICorDebugManagedCallback::ExitProcess – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitProcess
helpviewer_keywords:
- ExitProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::ExitProcess method [.NET Framework debugging]
ms.assetid: 63a7d47a-0d54-4e29-9767-9f09feaa38b7
topic_type:
- apiref
ms.openlocfilehash: 4380b8a3803e164aab7318821a9dbde32ecc3a0b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781745"
---
# <a name="icordebugmanagedcallbackexitprocess-method"></a>ICorDebugManagedCallback::ExitProcess – metoda
Oznamuje ladicímu programu, že došlo k ukončení procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ExitProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pProcess`  
 pro Ukazatel na objekt ICorDebugProcess, který představuje proces.  
  
## <a name="remarks"></a>Poznámky  
 Nemůžete pokračovat z `ExitProcess` události. Tato událost může být vyvolána asynchronně s ostatními událostmi, pokud se zdá, že se proces zastaví. Tato situace může nastat, pokud se proces ukončí během zastavení, obvykle kvůli nějakému externímu vynutitmu.  
  
 Pokud již modul CLR (Common Language Runtime) odesílá spravované zpětné volání, bude tato událost zpožděna až po vrácení zpětného volání.  
  
 Událost `ExitProcess` je jediná událost ukončení/uvolnění, která zaručuje, že se má volat při vypnutí.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugManagedCallback – rozhraní](icordebugmanagedcallback-interface.md)
