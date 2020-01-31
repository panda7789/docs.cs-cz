---
title: ICorDebugHeapSegmentEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum::Next
helpviewer_keywords:
- ICorDebugHeapSegmentEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 51625fd0-7399-49c7-b22b-5dfb05451fe6
topic_type:
- apiref
ms.openlocfilehash: 89ce4eafa46be3e9ba7cdb06884034a521e43bca
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777536"
---
# <a name="icordebugheapsegmentenumnext-method"></a>ICorDebugHeapSegmentEnum::Next – metoda
Získá zadaný počet instancí [COR_HEAPOBJECT](cor-heapobject-structure.md) , které obsahují informace o oblastech paměti spravované haldy.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],   
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametry  
 celt  
 pro Počet segmentů, které mají být načteny.  
  
 segmenty  
 mimo Pole ukazatelů, z nichž každý odkazuje na objekt [COR_HEAPOBJECT](cor-heapobject-structure.md) , který poskytuje informace o oblasti paměti ve spravované haldě.  
  
 pceltFetched  
 mimo Ukazatel na počet objektů [COR_HEAPOBJECT](cor-heapobject-structure.md) ve skutečnosti vrácených v `segments`. Tato hodnota může být `null`, pokud `celt` 1.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugHeapSegmentEnum – rozhraní](icordebugheapsegmentenum-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
