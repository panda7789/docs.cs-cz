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
ms.openlocfilehash: 04ae3c4dd663351eaf1a58646e24e8ae95aeb9ad
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378283"
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
 pro Velikost pole v bajtech `context` .  
  
 `context`  
 [in, out] Pole bajtů, které tvoří `CONTEXT` strukturu Win32 pro aktuální platformu.  
  
## <a name="remarks"></a>Poznámky  
 Ladicí program by měl zavolat tuto funkci namísto funkce Win32 `GetThreadContext` , protože vlákno může být ve stavu "napadeno", kde byl jeho kontext dočasně změněn. Vrácená data jsou `CONTEXT` strukturou Win32 pro aktuální platformu.  
  
 Pro jiné než koncové snímky by klienti měli ověřit, které Registry jsou platné, pomocí [ICorDebugRegisterSet:: GetRegistersAvailable –](icordebugregisterset-getregistersavailable-method.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugRegisterSet – rozhraní](icordebugregisterset-interface.md)
- [ICorDebugRegisterSet2 – rozhraní](icordebugregisterset2-interface.md)
