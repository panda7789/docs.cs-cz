---
title: ICorDebugModule::IsDynamic – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.IsDynamic
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::IsDynamic
helpviewer_keywords:
- IsDynamic method [.NET Framework debugging]
- ICorDebugModule::IsDynamic method [.NET Framework debugging]
ms.assetid: 5eefe716-5025-4a4c-970c-c823cdc7bb87
topic_type:
- apiref
ms.openlocfilehash: 5774b40178ce0d7c2ef5d063a37b9011fc2630df
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127953"
---
# <a name="icordebugmoduleisdynamic-method"></a>ICorDebugModule::IsDynamic – metoda
Načte hodnotu, která označuje, jestli je tento modul dynamický.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsDynamic(  
    [out] BOOL *pDynamic  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pDynamic`  
 [out] `true`, pokud je tento modul dynamický; v opačném případě `false`.  
  
## <a name="remarks"></a>Poznámky  
 Dynamický modul může přidat nové třídy a odstranit existující třídy i poté, co byl modul načten. Zpětná volání [ICorDebugManagedCallback:: LoadClass –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md) a [ICorDebugManagedCallback:: UnloadClass –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md) informují ladicí program, když byla třída přidána nebo odstraněna.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
