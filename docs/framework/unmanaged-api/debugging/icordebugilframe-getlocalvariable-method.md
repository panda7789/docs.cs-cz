---
title: ICorDebugILFrame::GetLocalVariable – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetLocalVariable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetLocalVariable
helpviewer_keywords:
- ICorDebugILFrame::GetLocalVariable method [.NET Framework debugging]
- GetLocalVariable method [.NET Framework debugging]
ms.assetid: c8706356-d50b-4f87-a40c-39c3b7f4fd38
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3424646337c3f90f15d991f3f669a296bf11d8ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413004"
---
# <a name="icordebugilframegetlocalvariable-method"></a>ICorDebugILFrame::GetLocalVariable – metoda
Získá hodnotu zadaného místní proměnné v rámci zásobníku tento Microsoft (MSIL intermediate language).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetLocalVariable (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwIndex`  
 [v] Index místní proměnné v rámci této MSIL zásobníku.  
  
 `ppValue`  
 [out] Ukazatel na adresu ICorDebugValue objekt, který reprezentuje načtené hodnoty.  
  
## <a name="remarks"></a>Poznámky  
 `GetLocalVariable` Metodu lze použít rámce zásobníku MSIL nebo v rámci kompilované v běhu (JIT).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
