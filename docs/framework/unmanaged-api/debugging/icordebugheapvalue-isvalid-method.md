---
title: ICorDebugHeapValue::IsValid – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue.IsValid
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue::IsValid
helpviewer_keywords:
- IsValid method [.NET Framework debugging]
- ICorDebugHeapValue::IsValid method [.NET Framework debugging]
ms.assetid: 68e20e62-203d-46d8-bb91-8d3c61cfacc3
topic_type:
- apiref
ms.openlocfilehash: 7edf0065fa7eb39dada167a682f2b634a438f1f3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138401"
---
# <a name="icordebugheapvalueisvalid-method"></a>ICorDebugHeapValue::IsValid – metoda
Získá hodnotu, která označuje, zda je objekt reprezentovaný tímto ICorDebugHeapValue platný.  
  
 Tato metoda je zastaralá ve verzi .NET Framework 2,0.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsValid (  
    [out] BOOL    *pbValid  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pbValid`  
 mimo Ukazatel na logickou hodnotu, která označuje, zda je tato hodnota na haldě platná.  
  
## <a name="remarks"></a>Poznámky  
 Hodnota je neplatná, pokud byla uvolněna systémem uvolňování paměti.  
  
 Tato metoda je zastaralá. V .NET Framework 2,0 jsou všechny hodnoty platné, dokud je volána metoda [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) , v níž je čas zrušení platnosti hodnot.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
