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
ms.openlocfilehash: b92885d2a6514839a864d6a345dd8af8b07b90c1
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489810"
---
# <a name="icordebugilframe2remapfunction-method"></a>ICorDebugILFrame2::RemapFunction – metoda
Změní funkce se upravila tak, že zadáte nové posun Microsoft intermediate language (MSIL)  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT RemapFunction (  
    [in] ULONG32      newILOffset  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `newILOffset`  
 [in] Rámec zásobníku bylo jakou by měl být umístěn ukazatel na instrukci nové posun jazyka MSIL. Tato hodnota musí být bodu sekvence.  
  
 Je odpovědností volajícího cílem zajistit platnost této hodnoty. Například posun MSIL není platný, pokud je mimo rozsah funkce.  
  
## <a name="remarks"></a>Poznámky  
 Při funkce rámec byl upraven, můžete volat ladicí program `RemapFunction` metoda do odkládacího souboru v nejnovější verzi funkce rámce, proto mohou být provedeny. Spuštění kódu se začne daným posunem jazyka MSIL.  
  
> [!NOTE]
>  Volání `RemapFunction`, třeba volání [icordebugilframe::setip –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md), okamžitě skončí platnost všech ladění rozhraní, které se vztahují k vygenerování trasování zásobníku pro vlákno. Tato rozhraní zahrnují [icordebugchain –](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md), ICorDebugILFrame icordebuginternalframe – a icordebugnativeframe –.  
  
 `RemapFunction` Metodu lze volat pouze v kontextu aktuálního rámce a pouze v jednom z následujících případech:  
  
-   Po přijetí [icordebugmanagedcallback2::functionremapopportunity –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-functionremapopportunity-method.md) zpětné volání, které nebylo dosud pokračování.  
  
-   Když je z důvodu zastaví provádění kódu [icordebugmanagedcallback::editandcontinueremap –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-editandcontinueremap-method.md) události pro tento rámec.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
