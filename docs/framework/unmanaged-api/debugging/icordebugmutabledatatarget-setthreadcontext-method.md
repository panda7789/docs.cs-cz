---
title: 'ICorDebugMutableDataTarget:: SetThreadContext – – metoda'
ms.date: 03/30/2017
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
ms.openlocfilehash: a6df6bf030ad339f5d02b95cd191b30db60aa167
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210147"
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
 pro Velikost `pContext` vyrovnávací paměti, která má být zapsána.  
  
 `pContext`  
 pro Ukazatel na bajty, které mají být zapsány.  
  
## <a name="remarks"></a>Poznámky  
 `SetThreadContext`Metoda aktualizuje aktuální kontext pro vlákno určené argumentem definovaným operačním systémem `dwThreadID` . Formát záznamu kontextu je určen platformou určenou metodou [ICorDebugDataTarget:: GetPlatform](icordebugdatatarget-getplatform-method.md) . Ve Windows je to [kontextová](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) struktura.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugMutableDataTarget – rozhraní](icordebugmutabledatatarget-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
