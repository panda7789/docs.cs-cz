---
title: ICorDebugManagedCallback::EditAndContinueRemap – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.EditAndContinueRemap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::EditAndContinueRemap
helpviewer_keywords:
- EditAndContinueRemap method [.NET Framework debugging]
- ICorDebugManagedCallback::EditAndContinueRemap method [.NET Framework debugging]
ms.assetid: 24a8fcce-317e-48ff-aefc-d86123ada935
topic_type:
- apiref
ms.openlocfilehash: 78b87b5c566b0d760a205757430123665fb2fcd3
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213709"
---
# <a name="icordebugmanagedcallbackeditandcontinueremap-method"></a>ICorDebugManagedCallback::EditAndContinueRemap – metoda
Tato metoda je zastaralá. Oznamuje ladicímu programu, že byla do integrovaného vývojového prostředí (IDE) odeslána událost přemapování.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EditAndContinueRemap (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread *pThread,  
    [in] ICorDebugFunction *pFunction,  
    [in] BOOL fAccurate  
);  
```  
  
## <a name="remarks"></a>Poznámky  
 `EditAndContinueRemap`Metoda je volána, když došlo k pokusu o spuštění kódu ve staré verzi aktualizované funkce. Modul CLR (Common Language Runtime) volá `EditAndContinueRemap` metodu pro odeslání události přemapování na rozhraní IDE.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugManagedCallback – rozhraní](icordebugmanagedcallback-interface.md)
