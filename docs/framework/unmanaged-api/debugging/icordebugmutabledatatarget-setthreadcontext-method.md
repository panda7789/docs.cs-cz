---
title: 'ICorDebugMutableDataTarget:: SetThreadContext – – metoda'
ms.date: 03/30/2017
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
ms.openlocfilehash: 2c9e508c7a4059fee4e1cce6eb28e6de7b2fff6d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132708"
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a>ICorDebugMutableDataTarget:: SetThreadContext – – metoda
Nastaví kontext (hodnoty registru) pro vlákno.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwThreadID`  
 pro Identifikátor vlákna definovaného operačním systémem.  
  
 `contextSize`  
 pro Velikost vyrovnávací paměti pro `pContext`, která se má zapsat.  
  
 `pContext`  
 pro Ukazatel na bajty, které mají být zapsány.  
  
## <a name="remarks"></a>Poznámky  
 Metoda `SetThreadContext` aktualizuje aktuální kontext pro vlákno určené `dwThreadID` argumentem definovaným operačním systémem. Formát záznamu kontextu je určen platformou určenou metodou [ICorDebugDataTarget:: GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) . Ve Windows je to [kontextová](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) struktura.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugMutableDataTarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
