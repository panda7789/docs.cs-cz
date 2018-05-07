---
title: ICorDebugManagedCallback::ExitProcess – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitProcess
helpviewer_keywords:
- ExitProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::ExitProcess method [.NET Framework debugging]
ms.assetid: 63a7d47a-0d54-4e29-9767-9f09feaa38b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 42330296defe90980dd431ce39765a549057b82a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmanagedcallbackexitprocess-method"></a>ICorDebugManagedCallback::ExitProcess – metoda
Upozorní ladicího programu, proces byl ukončen.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ExitProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pProcess`  
 [v] Ukazatel na ICorDebugProcess objekt, který představuje proces.  
  
## <a name="remarks"></a>Poznámky  
 Nelze pokračovat od `ExitProcess` událostí. Tato událost může aktivovat asynchronně s ostatními událostmi během procesu se zobrazí zastavení. Tato situace může nastat, pokud se proces ukončí při zastavená, obvykle kvůli některé externí force.  
  
 Pokud modul CLR (CLR) je již odeslání spravované zpětné volání, tato událost bude opožděno až po vrátila že zpětné volání.  
  
 `ExitProcess` Událostí je pouze ukončení a vyřadit událost, který zaručeně zavolána na vypnutí.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugManagedCallback – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
