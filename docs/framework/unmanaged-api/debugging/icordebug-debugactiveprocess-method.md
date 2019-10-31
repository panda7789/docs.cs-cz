---
title: ICorDebug::DebugActiveProcess – metoda
ms.date: 03/30/2017
api_name:
- ICorDebug.DebugActiveProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::DebugActiveProcess
helpviewer_keywords:
- DebugActiveProcess method [.NET Framework debugging]
- ICorDebug::DebugActiveProcess method [.NET Framework debugging]
ms.assetid: fdab0ade-7f56-4fa2-b3ef-f7a1d2852bba
topic_type:
- apiref
ms.openlocfilehash: 5b988b110100cd159b8e262573df409847d635c6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134128"
---
# <a name="icordebugdebugactiveprocess-method"></a>ICorDebug::DebugActiveProcess – metoda
Připojí ladicí program k existujícímu procesu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DebugActiveProcess (  
    [in]  DWORD               id,  
    [in]  BOOL                win32Attach,  
    [out] ICorDebugProcess    **ppProcess  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `id`  
 pro ID procesu, ke kterému má být připojen ladicí program.  
  
 `win32Attach`  
 pro Logická hodnota, která je nastavena na `true`, pokud se má ladicí program chovat jako ladicí program Win32 pro proces a odeslání nespravovaných zpětných volání; v opačném případě `false`.  
  
 `ppProcess`  
 mimo Ukazatel na adresu objektu "ICorDebugProcess", který představuje proces, ke kterému byl připojen ladicí program.  
  
## <a name="remarks"></a>Poznámky  
 Ladění spolupráce se nepodporuje na platformách, které nejsou založené na platformě IA-64 a platformě AMD64.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebug – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
