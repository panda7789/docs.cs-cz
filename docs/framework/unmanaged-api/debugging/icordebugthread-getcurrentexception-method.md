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
ms.openlocfilehash: 82686fdd14783257987ec5bf9a24db7d87049d42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421743"
---
# <a name="icordebugthreadgetcurrentexception-method"></a>ICorDebugThread::GetCurrentException – metoda
Získá ukazatele rozhraní ICorDebugValue objektu, která představuje výjimku, která je aktuálně hlášeny ve spravovaném kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetCurrentException (  
    [out] ICorDebugValue **ppExceptionObject  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppExceptionObject`  
 [out] Ukazatel na adresu `ICorDebugValue` objekt, který představuje výjimku, která je aktuálně hlášeny ve spravovaném kódu.  
  
## <a name="remarks"></a>Poznámky  
 Objekt výjimky bude existovat od času se výjimka až do konce `catch` bloku. Vyhodnocení funkce, která se provádí pomocí metody ICorDebugEval, bude vymažte objekt výjimky na instalační program a obnovte ji po dokončení.  
  
 Výjimky mohou být vnořené (například pokud ve filtru nebo do vyhodnocení funkce je vyvolána výjimka), takže může být několik nezpracovaných výjimek na jedno vlákno. `GetCurrentException` Vrátí aktuální výjimku.  
  
 Objekt výjimky a typ mohou změnit po celou dobu životnosti výjimky. Například po je vyvolána výjimka typu x, modul CLR (CLR) může mít nedostatek paměti a povyšte ho na výjimku z důvodu nedostatku paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
