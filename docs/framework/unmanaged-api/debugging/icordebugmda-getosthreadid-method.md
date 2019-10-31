---
title: ICorDebugMDA::GetOSThreadId – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetOSThreadId
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetOSThreadId
helpviewer_keywords:
- ICorDebugMDA::GetOSThreadId method [.NET Framework debugging]
- GetOSThreadId method [.NET Framework debugging]
ms.assetid: 7ca7c364-ade4-4219-b434-9f6ae2359be6
topic_type:
- apiref
ms.openlocfilehash: e9846234f8217b822860c2400a54a91a651a0a56
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129819"
---
# <a name="icordebugmdagetosthreadid-method"></a>ICorDebugMDA::GetOSThreadId – metoda
Načte identifikátor vlákna operačního systému (OS), na kterém je spuštěný pomocník spravovaného ladění (MDA) reprezentovaný [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetOSThreadId (  
    [out] DWORD    *pOsTid  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pOsTid`  
 mimo Ukazatel na identifikátor vlákna operačního systému.  
  
## <a name="remarks"></a>Poznámky  
 Vlákno OS se používá místo ICorDebugThread a umožňuje v situacích, ve kterých je spuštěný MDA, buď v nativním vlákně, nebo ve spravovaném vlákně, které ještě nezadalo spravovaný kód.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugMDA – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
