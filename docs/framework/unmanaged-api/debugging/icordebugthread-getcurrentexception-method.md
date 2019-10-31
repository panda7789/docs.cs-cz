---
title: ICorDebugThread::GetCurrentException – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetCurrentException
helpviewer_keywords:
- ICorDebugThread::GetCurrentException method [.NET Framework debugging]
- GetCurrentException method [.NET Framework debugging]
ms.assetid: 331ed465-a195-4359-8584-b82c6098b29b
topic_type:
- apiref
ms.openlocfilehash: 8082b2a3654f1605f18f3b68f54464dc83c8e60a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133493"
---
# <a name="icordebugthreadgetcurrentexception-method"></a>ICorDebugThread::GetCurrentException – metoda
Získá ukazatel rozhraní na objekt ICorDebugValue, který představuje výjimku, která je aktuálně vyvolána spravovaným kódem.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCurrentException (  
    [out] ICorDebugValue **ppExceptionObject  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppExceptionObject`  
 mimo Ukazatel na adresu `ICorDebugValue` objektu, který představuje výjimku, která je aktuálně vyvolána spravovaným kódem.  
  
## <a name="remarks"></a>Poznámky  
 Objekt výjimky bude existovat od okamžiku, kdy je výjimka vyvolána až do konce `catch` bloku. Vyhodnocení funkce, která je prováděna metodami ICorDebugEval, vyčistí objekt výjimky při instalaci a obnoví ho při dokončení.  
  
 Výjimky mohou být vnořené (například pokud je vyvolána výjimka ve filtru nebo ve vyhodnocení funkce), takže v jednom vlákně může existovat několik zbývajících výjimek. `GetCurrentException` vrátí aktuální výjimku.  
  
 Objekt výjimky a typ se mohou změnit po celou dobu životnosti výjimky. Například po vyjímka typu x může modul CLR (Common Language Runtime) mít nedostatek paměti a propagovat jej na výjimku mimo paměť.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
