---
title: ICorDebugMutableDataTarget::SetThreadContext – metoda
ms.date: 03/30/2017
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3826bacb935652a282eac359170d9b93518e5cd
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42931795"
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a>ICorDebugMutableDataTarget::SetThreadContext – metoda
Nastaví kontext (hodnot registru) pro vlákno.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwThreadID`  
 [in] Identifikátor vlákna operačního systému definovaný.  
  
 `contextSize`  
 [in] Velikost `pContext` vyrovnávací paměti k zapsání.  
  
 `pContext`  
 [in] Ukazatel na počet bajtů k zápisu.  
  
## <a name="remarks"></a>Poznámky  
 `SetThreadContext` Metoda aktualizuje aktuální kontext pro vlákno určené parametrem operačního systému definovaný `dwThreadID` argument. Formát záznamu o kontextu je určen podle platformy indikován [icordebugdatatarget::getplatform –](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) metody. Na Windows, jde [kontextu](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) struktury.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugMutableDataTarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
