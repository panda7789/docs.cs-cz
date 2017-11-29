---
title: "ICorDebugThread::GetCurrentException – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.GetCurrentException
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::GetCurrentException
helpviewer_keywords:
- ICorDebugThread::GetCurrentException method [.NET Framework debugging]
- GetCurrentException method [.NET Framework debugging]
ms.assetid: 331ed465-a195-4359-8584-b82c6098b29b
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fb48e99aa719e564bd23842efcaeda071441023b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
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
  
 Výjimky mohou být vnořené (například pokud ve filtru nebo do vyhodnocení funkce je vyvolána výjimka), takže může být několik nezpracovaných výjimek na jedno vlákno. `GetCurrentException`Vrátí aktuální výjimku.  
  
 Objekt výjimky a typ mohou změnit po celou dobu životnosti výjimky. Například po je vyvolána výjimka typu x, modul CLR (CLR) může mít nedostatek paměti a povyšte ho na výjimku z důvodu nedostatku paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
