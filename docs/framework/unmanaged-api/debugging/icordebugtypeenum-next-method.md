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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf70d8665d3984c379da9d9058cd97315def7b76
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54677677"
---
# <a name="icordebugtypeenumnext-method"></a>ICorDebugTypeEnum::Next – metoda
Získá počet instancí "ICorDebugType" určené `celt` z výčtu od aktuální pozice.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Next (  
    [in]  ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugType *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celt`  
 [in] Počet `ICorDebugType` instancí, který se má načíst.  
  
 `values`  
 [out] Pole ukazatelů, každý z nich odkazuje na `ICorDebugType` objektu.  
  
 `pceltFetched`  
 [out] Ukazatel na počet `ICorDebugType` skutečně vrácených instancí. Tato hodnota může mít hodnotu null Pokud `celt` je jedna.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

