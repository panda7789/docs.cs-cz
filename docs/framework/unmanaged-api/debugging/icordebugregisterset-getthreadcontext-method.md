---
title: ICorDebugRegisterSet::GetThreadContext – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetThreadContext
helpviewer_keywords:
- GetThreadContext method, ICorDebugRegisterSet interface [.NET Framework debugging]
- ICorDebugRegisterSet::GetThreadContext method [.NET Framework debugging]
ms.assetid: 0f63400b-dc1c-48d6-b51a-75c3f7f28e03
topic_type:
- apiref
ms.openlocfilehash: db4f9bc6277015055cbcdb509628f2862a71dbc4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127156"
---
# <a name="icordebugregistersetgetthreadcontext-method"></a>ICorDebugRegisterSet::GetThreadContext – metoda
Získá kontext aktuálního vlákna.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetThreadContext(  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize),  
        size_is(contextSize)] BYTE context[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `contextSize`  
 pro Velikost pole `context` v bajtech  
  
 `context`  
 [in, out] Pole bajtů, které tvoří strukturu `CONTEXT` Win32 pro aktuální platformu.  
  
## <a name="remarks"></a>Poznámky  
 Ladicí program by měl zavolat tuto funkci namísto funkce Win32 `GetThreadContext`, protože vlákno může být ve stavu "napadeno", kde byl jeho kontext dočasně změněn. Vrácená data jsou strukturou `CONTEXT` Win32 pro aktuální platformu.  
  
 Pro jiné než koncové snímky by klienti měli ověřit, které Registry jsou platné, pomocí [ICorDebugRegisterSet:: GetRegistersAvailable –](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-getregistersavailable-method.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugRegisterSet – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
- [ICorDebugRegisterSet2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)
