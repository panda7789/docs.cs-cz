---
title: ICorDebugManagedCallback::LoadClass – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadClass
helpviewer_keywords:
- ICorDebugManagedCallback::LoadClass method [.NET Framework debugging]
- LoadClass method [.NET Framework debugging]
ms.assetid: e58dac7b-85c3-41ca-b9aa-3a7fc9ae6680
topic_type:
- apiref
ms.openlocfilehash: 5d35ab4610ffa04d15dd2404fdf8010308bcb42a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212725"
---
# <a name="icordebugmanagedcallbackloadclass-method"></a>ICorDebugManagedCallback::LoadClass – metoda
Oznamuje ladicímu programu, že byla načtena třída.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pAppDomain`  
 pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace, do které byla třída načtena.  
  
 `c`  
 pro Ukazatel na objekt ICorDebugClass, který představuje třídu.  
  
## <a name="remarks"></a>Poznámky  
 Toto zpětné volání nastane pouze v případě, že bylo povoleno načítání tříd pro modul, který obsahuje třídu. Načítání tříd je vždy povoleno pro dynamické moduly.  
  
 `LoadClass`Zpětné volání poskytuje vhodný čas ke svázání zarážek s nově vygenerovanými třídami v dynamických modulech.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [UnloadClass – metoda](icordebugmanagedcallback-unloadclass-method.md)
- [ICorDebugManagedCallback – rozhraní](icordebugmanagedcallback-interface.md)
