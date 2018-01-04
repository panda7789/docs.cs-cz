---
title: "ICorDebugMutableDataTarget::ContinueStatusChanged – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 5a66d3f4-dd16-4d62-9dcc-0eab7041d894
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ba8fe9b0d4a09bdfe3d3e6459f16bf041dc396a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmutabledatatargetcontinuestatuschanged-method"></a>ICorDebugMutableDataTarget::ContinueStatusChanged – metoda
Změní stav pokračování události nezpracovaných ladění na zadané vlákno.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ContinueStatusChanged(  
   [in] DWORD dwThreadId,  
   [in] CORDB_CONTINUE_STATUS continueStatus);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwThreadId`  
 Identifikátor vlákno definované operačního systému.  
  
 `continueStatus`  
 A[COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)hodnotu, která představuje nový požadovaný stav pokračování.  
  
## <a name="remarks"></a>Poznámky  
 Ladicí program volání `ContinueStatusChanged` metoda při volání metody ICorDebug, vyžaduje aktuální událost ladění zpracovávat způsobem, který je potenciálně liší od způsobu, ve kterém se za normálních okolností by ošetřit. Například, pokud dojde k výjimce nezpracovaných a ladicí program požadavky operace, která by zrušit výjimku (například [icordebugilframe::setip –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) nebo `FuncEval`), toto rozhraní API slouží k vyžádání, že se výjimka zrušena.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugMutableDataTarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
