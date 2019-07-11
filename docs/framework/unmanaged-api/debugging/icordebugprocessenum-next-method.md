---
title: ICorDebugProcessEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcessEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcessEnum::Next
helpviewer_keywords:
- Next method, ICorDebugProcessEnum interface [.NET Framework debugging]
- ICorDebugProcessEnum::Next method [.NET Framework debugging]
ms.assetid: 4ac7077c-8d88-49c4-b360-b3af0c541c63
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 59efdb76c000a78007ec0321202793ed0dd50cfb
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768285"
---
# <a name="icordebugprocessenumnext-method"></a>ICorDebugProcessEnum::Next – metoda
Získá zadaný počet instancí ICorDebugProcess z výčtu od aktuální pozice.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugProcess *processes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `celt`  
 [in] Počet `ICorDebugProcess` instancí, který se má načíst.  
  
 `processes`  
 [out] Pole ukazatelů, každý z nich odkazuje na `ICorDebugProcess` objekt, který reprezentuje proces.  
  
 `pceltFetched`  
 [out] Ukazatel na počet `ICorDebugProcess` skutečně vrácených instancí. Tato hodnota může mít hodnotu null Pokud `celt` je jedna.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
