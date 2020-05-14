---
title: ICorDebugTypeEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugTypeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugTypeEnum::Next
helpviewer_keywords:
- ICorDebugTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugTypeEnum interface [.NET Framework debugging]
ms.assetid: d0fdeba3-c195-4ece-8caf-79b1f40025d2
topic_type:
- apiref
ms.openlocfilehash: 83adea3d659eea6d4af9ae364aad18df67e69c03
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396625"
---
# <a name="icordebugtypeenumnext-method"></a>ICorDebugTypeEnum::Next – metoda
Získá počet instancí "ICorDebugType" určených `celt` od výčtu počínaje aktuální pozicí.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugType *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `celt`  
 pro Počet instancí, `ICorDebugType` které mají být načteny.  
  
 `values`  
 mimo Pole ukazatelů, z nichž každý odkazuje na `ICorDebugType` objekt.  
  
 `pceltFetched`  
 mimo Ukazatel na počet `ICorDebugType` skutečně vrácených instancí. Tato hodnota může být null `celt` , pokud je jedna.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také
