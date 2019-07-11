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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 37b644227a6085352bed682f0ddd7c3455b54895
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760700"
---
# <a name="icordebugsteppersetinterceptmask-method"></a>ICorDebugStepper::SetInterceptMask – metoda
Nastaví hodnotu, která určuje typy kódu, které jsou vkročili.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetInterceptMask (  
    [in] CorDebugIntercept    mask  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `mask`  
 [in] Kombinace hodnot cordebugintercept – výčet, který určuje typy kódu.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je nastaven bit pro zachycování, krokovače dokončí, když dochází k danému typu zachycení kódu. Pokud bit vymazán, prověřuje zachycovací kódu se přeskočí.  
  
 `SetInterceptMask` Metoda může mít nepředvídatelné interakce s [icordebugstepper::setunmappedstopmask –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) (od uživatele pohledu). Například pokud viditelné jenom (to znamená, – vnitřní) část inicializační kód třídy chybí informace o mapování a není nastaven STOP_NO_MAPPING_INFO (naleznete v tématu [icordebugstepper::setunmappedstopmask –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) metoda a Cordebugunmappedstop – výčet) krokovače přesune se krokování přes inicializace třídy. Ve výchozím nastavení pouze INTERCEPT_NONE hodnotu `CorDebugIntercept` se použije výčet.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
