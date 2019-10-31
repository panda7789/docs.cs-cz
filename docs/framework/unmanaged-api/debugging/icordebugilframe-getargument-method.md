---
title: ICorDebugILFrame::GetArgument – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetArgument
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetArgument
helpviewer_keywords:
- GetArgument method [.NET Framework debugging]
- ICorDebugILFrame::GetArgument method [.NET Framework debugging]
ms.assetid: 4e2fd423-f643-4c27-ba5f-41b5ebc3b416
topic_type:
- apiref
ms.openlocfilehash: 01c7cb2e4359a477c26f995602dbf29668e567c0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131011"
---
# <a name="icordebugilframegetargument-method"></a>ICorDebugILFrame::GetArgument – metoda
Získá hodnotu zadaného argumentu v rámci tohoto rámce zásobníku jazyka MSIL (Microsoft Intermediate Language).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetArgument (  
    [in] DWORD                  dwIndex,  
    [out] ICorDebugValue        **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwIndex`  
 pro Index argumentu v tomto snímku zásobníku MSIL.  
  
 `ppValue`  
 mimo Ukazatel na adresu objektu ICorDebugValue, který představuje načtenou hodnotu.  
  
## <a name="remarks"></a>Poznámky  
 Metodu `GetArgument` lze použít buď v rámci rámce zásobníku MSIL, nebo v kompilovaném snímku JIT (just-in-time).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
