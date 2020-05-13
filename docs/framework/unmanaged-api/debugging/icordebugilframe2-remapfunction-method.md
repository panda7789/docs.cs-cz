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
ms.openlocfilehash: 43f585417ed52b92c23087c0f02fd188ee09ea7e
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210212"
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
> Volání `RemapFunction` , podobně jako volání [ICorDebugILFrame:: SetIP](icordebugilframe-setip-method.md), okamžitě zruší platnost všech ladicích rozhraní, která souvisí s generováním trasování zásobníku pro vlákno. Mezi tato rozhraní patří [ICorDebugChain](icordebugchain-interface.md), ICorDebugILFrame, ICorDebugInternalFrame a ICorDebugNativeFrame.  
  
 `RemapFunction`Metodu lze volat pouze v kontextu aktuálního rámce a pouze v jednom z následujících případů:  
  
- Po přijetí zpětného volání [ICorDebugManagedCallback2:: FunctionRemapOpportunity –](icordebugmanagedcallback2-functionremapopportunity-method.md) , které ještě nepokračovalo.  
  
- Při provádění kódu je zastaveno z důvodu události [ICorDebugManagedCallback:: EditAndContinueRemap –](icordebugmanagedcallback-editandcontinueremap-method.md) pro tento rámec.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
