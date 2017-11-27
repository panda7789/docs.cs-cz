---
title: "ICorDebugMutableDataTarget::SetThreadContext – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8c43ef5405ed582cc55af69d7f41887c0615965f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a>ICorDebugMutableDataTarget::SetThreadContext – metoda
Nastaví kontext (hodnot registru) vlákna.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwThreadID`  
 [v] Identifikátor vlákno definované operačního systému.  
  
 `contextSize`  
 [v] Velikost `pContext` vyrovnávací paměť k zapsání.  
  
 `pContext`  
 [v] Ukazatel na bajtů, které mají být zapsána.  
  
## <a name="remarks"></a>Poznámky  
 `SetThreadContext` Metoda aktualizuje aktuální kontext pro vlákno určeného operačního systému definovaná `dwThreadID` argument. Formát kontextu záznamu je určen podle platformy indikován [icordebugdatatarget::getplatform –](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) metoda. V systému Windows, [kontextu](http://msdn.microsoft.com/library/windows/desktop/ms679284.aspx) struktura.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugMutableDataTarget rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 [Ladění v rozhraní](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
