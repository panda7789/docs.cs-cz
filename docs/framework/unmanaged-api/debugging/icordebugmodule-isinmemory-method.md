---
title: ICorDebugModule::IsInMemory – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugModule.IsInMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::IsInMemory
helpviewer_keywords:
- IsInMemory method [.NET Framework debugging]
- ICorDebugModule::IsInMemory method [.NET Framework debugging]
ms.assetid: 89940711-98e7-4aa6-bffc-5e39e91e1b7d
topic_type:
- apiref
ms.openlocfilehash: c5fa55a84ed8907a5072f6099c3bf02cd6d78683
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213124"
---
# <a name="icordebugmoduleisinmemory-method"></a>ICorDebugModule::IsInMemory – metoda
Načte hodnotu, která označuje, jestli tento modul existuje jenom v paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsInMemory(  
    [out] BOOL *pInMemory  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pInMemory`  
 [out] `true` Pokud tento modul existuje pouze v paměti; v opačném případě `false` .  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR (Common Language Runtime) podporuje načítání modulů z nezpracovaných datových proudů bajtů. Tyto moduly se nazývají *moduly v paměti* a neexistují na disku.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také
