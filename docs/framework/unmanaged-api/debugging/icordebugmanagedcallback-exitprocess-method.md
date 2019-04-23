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
ms.openlocfilehash: 51162bfb6f9763d2ab4ac1f86e0ccdc15b601271
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59159871"
---
# <a name="icordebugmanagedcallbackexitprocess-method"></a>ICorDebugManagedCallback::ExitProcess – metoda
Upozorní ladicího programu, že proces byl ukončen.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ExitProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pProcess`  
 [in] Ukazatel na objekt ICorDebugProcess, který představuje proces.  
  
## <a name="remarks"></a>Poznámky  
 Nejde pokračovat od `ExitProcess` událostí. Tato událost může aktivovat asynchronně s ostatními událostmi během procesu se zdá být zastaven. Tato situace může nastat, pokud se proces ukončí při zastavení, obvykle kvůli některé externí platnost.  
  
 Pokud common language runtime (CLR) je již odesílání spravované zpětné volání, tato událost bude odložena až do po vrátila tohoto zpětného volání.  
  
 `ExitProcess` Událostí je jediná událost výstupu/uvolnění, která je zaručeně získat volat pro vypnutí.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugManagedCallback – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
