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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c4baa4eb4da48b923ab0137ca25d9d819c94e33d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994029"
---
# <a name="icordebugthreadgetcurrentexception-method"></a>ICorDebugThread::GetCurrentException – metoda
Získá ukazatel rozhraní na ICorDebugValue objekt, který představuje výjimku, která je právě vyvolané spravovaného kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetCurrentException (  
    [out] ICorDebugValue **ppExceptionObject  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppExceptionObject`  
 [out] Ukazatel na adresu `ICorDebugValue` objekt, který představuje výjimku, která je aktuálně vyvolané ve spravovaném kódu.  
  
## <a name="remarks"></a>Poznámky  
 Objekt výjimky budou existovat od doby, kdy je vyvolána výjimka až do konce `catch` bloku. Vyhodnocení funkce, které se provádí pomocí metody ICorDebugEval, bude vymažte objekt výjimky, instalace a obnovení při dokončení.  
  
 Výjimky mohou být vnořené (například pokud je vyvolána výjimka ve filtru nebo vyhodnocení funkce), takže může být více nezpracovaných výjimek v jednom vlákně. `GetCurrentException` Vrátí aktuální výjimky.  
  
 Objekt výjimky a typ může změnit během životnosti výjimku. Například po je vyvolána výjimka typu x, common language runtime (CLR) může mít nedostatek paměti a povýšit na výjimku mimo z důvodu nedostatku paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
