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
ms.openlocfilehash: 9792abb4ee38a45aae59eaf79f1f0499539bd2ae
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791766"
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
  
 Metoda `SetInterceptMask` může mít nepředvídatelné interakce s [ICorDebugStepper:: SetUnmappedStopMask –](icordebugstepper-setunmappedstopmask-method.md) (z pohledu uživatele). Například pokud jedinou viditelnou část (která je neinterní) obsažená v inicializačním kódu třídy chybí informace o mapování a STOP_NO_MAPPING_INFO není nastavena (viz metoda [ICorDebugStepper:: SetUnmappedStopMask –](icordebugstepper-setunmappedstopmask-method.md) a výčet CorDebugUnmappedStop –), stepper bude Krokovat s inicializací třídy. Ve výchozím nastavení se použije jenom hodnota INTERCEPT_NONE výčtu `CorDebugIntercept`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
