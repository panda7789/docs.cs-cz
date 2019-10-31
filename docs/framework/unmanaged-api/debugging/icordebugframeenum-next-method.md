---
title: ICorDebugFrameEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFrameEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrameEnum::Next
helpviewer_keywords:
- ICorDebugFrameEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugFrameEnum interface [.NET Framework debugging]
ms.assetid: 0bc96acb-6179-4328-a447-cda562ce9e98
topic_type:
- apiref
ms.openlocfilehash: ff74a9849b74b8a8e6b8c03f1fc4e7c7eee1ec14
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124061"
---
# <a name="icordebugframeenumnext-method"></a>ICorDebugFrameEnum::Next – metoda
Získá zadaný počet instancí ICorDebugFrame od aktuální pozice.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugFrame *frames[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `celt`  
 pro Počet instancí `ICorDebugFrame`, které mají být načteny.  
  
 `frames`  
 mimo Pole ukazatelů, z nichž každý odkazuje na objekt `ICorDebugFrame`.  
  
 `pceltFetched`  
 mimo Ukazatel na počet skutečně vrácených instancí `ICorDebugFrame`. Tato hodnota může být null, pokud `celt` je jedna.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
