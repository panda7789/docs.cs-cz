---
title: ICorDebugDataTarget::GetThreadContext – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.GetThreadContext Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::GetThreadContext
helpviewer_keywords:
- ICorDebugDataTarget::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: c8954268-1821-4b23-b665-dbb55f2af31b
topic_type:
- apiref
ms.openlocfilehash: 79708aa5a2abcb8d7465f82a8beb918484c193b9
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976548"
---
# <a name="icordebugdatatargetgetthreadcontext-method"></a>ICorDebugDataTarget::GetThreadContext – metoda
Vrátí aktuální kontext vlákna pro zadané vlákno.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetThreadContext(  
       [in] DWORD dwThreadID,  
       [in] ULONG32 contextFlags,  
       [in] ULONG32 contextSize,  
       [out, size_is(contextSize)] BYTE * pContext);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwThreadID`  
 pro Identifikátor vlákna, jehož kontext má být načten. Identifikátor je definován operačním systémem.  
  
 `contextFlags`  
 pro Bitová kombinace příznaků závislých na platformě, která označuje, které části kontextu by měly být čteny.  
  
 `contextSize`  
 pro Velikost `pContext`.  
  
 `pContext`  
 mimo Vyrovnávací paměť, kde bude uložen kontext vlákna.  
  
## <a name="remarks"></a>Poznámky  
 Na platformách systému `pContext` Windows musí být `CONTEXT` struktura (definovaná v souboru Winnt. h), která je vhodná pro typ počítače určený metodou [ICorDebugDataTarget:: GetPlatform](icordebugdatatarget-getplatform-method.md) . `contextFlags`musí mít stejné hodnoty jako `ContextFlags` pole `CONTEXT` struktury. `CONTEXT` Struktura je specifická pro procesor; Podrobnosti najdete v souboru WinNT. h.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugDataTarget – rozhraní](icordebugdatatarget-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
- [Ladění](index.md)
