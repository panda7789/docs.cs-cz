---
title: ICorDebugModule::GetFunctionFromToken – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetFunctionFromToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetFunctionFromToken
helpviewer_keywords:
- GetFunctionFromToken method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetFunctionFromToken method [.NET Framework debugging]
ms.assetid: 6fe12194-4ef7-43c1-9570-ade35ccf127a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: acffd24ae9d5aad5f48058eec036f912ee016289
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmodulegetfunctionfromtoken-method"></a>ICorDebugModule::GetFunctionFromToken – metoda
Získá funkce, která je zadána token metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetFunctionFromToken(  
    [in] mdMethodDef methodDef,  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `methodDef`  
 [v] A `mdMethodDef` metadata token, který odkazuje na funkci metadata.  
  
 `ppFunction`  
 [out] Ukazatel na adresu objekt rozhraní ICorDebugFunction, který představuje funkci.  
  
## <a name="remarks"></a>Poznámky  
 `GetFunctionFromToken` Metoda vrátí CORDBG_E_FUNCTION_NOT_IL HRESULT, pokud je předaná hodnota `methodDef` neodkazuje na metodu (MSIL intermediate language) společnosti Microsoft.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
