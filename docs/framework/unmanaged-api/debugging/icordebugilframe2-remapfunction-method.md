---
title: ICorDebugILFrame2::RemapFunction – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2.RemapFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2::RemapFunction
helpviewer_keywords:
- ICorDebugILFrame2::RemapFunction method [.NET Framework debugging]
- RemapFunction method [.NET Framework debugging]
ms.assetid: dd639ba0-f77b-426d-9ff6-f92706840348
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 75004f646c01897ef3e3016b073220ad33a0d925
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967582"
---
# <a name="icordebugilframe2remapfunction-method"></a>ICorDebugILFrame2::RemapFunction – metoda
Přemapuje upravenou funkci zadáním nového posunu jazyka MSIL (Microsoft Intermediate Language).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RemapFunction (  
    [in] ULONG32      newILOffset  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `newILOffset`  
 pro Nový posun MSIL rámce zásobníku, na kterém by měl být umístěn ukazatel na instrukci. Tato hodnota musí být bod sekvence.  
  
 Je zodpovědností volajícího, aby zajistila platnost této hodnoty. Například posun jazyka MSIL není platný, pokud je mimo hranice funkce.  
  
## <a name="remarks"></a>Poznámky  
 Když je upravena funkce rámce, ladicí program může zavolat `RemapFunction` metodu pro prohození v nejnovější verzi funkce rámce, aby ji bylo možné spustit. Spuštění kódu bude zahájeno v daném posunu MSIL.  
  
> [!NOTE]
> Volání `RemapFunction`, podobně jako volání [ICorDebugILFrame:: SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md), okamžitě zruší platnost všech ladicích rozhraní, která souvisí s generováním trasování zásobníku pro vlákno. Mezi tato rozhraní patří [ICorDebugChain](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md), ICorDebugILFrame, ICorDebugInternalFrame a ICorDebugNativeFrame.  
  
 `RemapFunction` Metodu lze volat pouze v kontextu aktuálního rámce a pouze v jednom z následujících případů:  
  
- Po přijetí zpětného volání [ICorDebugManagedCallback2:: FunctionRemapOpportunity –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md) , které ještě nepokračovalo.  
  
- Při provádění kódu je zastaveno z důvodu události [ICorDebugManagedCallback:: EditAndContinueRemap –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md) pro tento rámec.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlaviček** CorDebug. idl, CorDebug. h  
  
 **Knihovna** CorGuids.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
