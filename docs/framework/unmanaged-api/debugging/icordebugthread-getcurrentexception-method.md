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
ms.openlocfilehash: 3a4da6f958407c0b704ffb7372a77b7f022fc824
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379772"
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
  
 Výjimky mohou být vnořené (například pokud je vyvolána výjimka ve filtru nebo ve vyhodnocení funkce), takže v jednom vlákně může existovat několik zbývajících výjimek. `GetCurrentException`Vrátí aktuální výjimku.  
  
 Objekt výjimky a typ se mohou změnit po celou dobu životnosti výjimky. Například po vyjímka typu x může modul CLR (Common Language Runtime) mít nedostatek paměti a propagovat jej na výjimku mimo paměť.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
