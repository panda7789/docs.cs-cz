---
title: ICorDebugStepper::SetInterceptMask – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetInterceptMask
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetInterceptMask
helpviewer_keywords:
- SetInterceptMask method [.NET Framework debugging]
- ICorDebugStepper::SetInterceptMask method [.NET Framework debugging]
ms.assetid: 6245e2ae-5cc2-43ff-8cc1-71953d12113a
topic_type:
- apiref
ms.openlocfilehash: e88fa543eca39c14962f0dbbe8053829713401c8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137580"
---
# <a name="icordebugsteppersetinterceptmask-method"></a>ICorDebugStepper::SetInterceptMask – metoda
Nastaví hodnotu, která určuje typy kódu, na které se má vzstep.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetInterceptMask (  
    [in] CorDebugIntercept    mask  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `mask`  
 pro Kombinace hodnot výčtu CorDebugIntercept –, která určuje typy kódu.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je nastaven bit pro zachytávací modul, stepper se dokončí při zjištění daného typu zachycení kódu. Pokud je bit vymazán, kód zachycení se přeskočí.  
  
 Metoda `SetInterceptMask` může mít nepředvídatelné interakce s [ICorDebugStepper:: SetUnmappedStopMask –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) (z pohledu uživatele). Například pokud jedinou viditelnou část (která je neinterní) obsažená v inicializačním kódu třídy chybí informace o mapování a STOP_NO_MAPPING_INFO není nastaven (viz metoda [ICorDebugStepper:: SetUnmappedStopMask –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) a CorDebugUnmappedStop – výčet), stepper bude Krokovat s inicializací třídy. Ve výchozím nastavení se použije jenom hodnota INTERCEPT_NONE výčtu `CorDebugIntercept`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
