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
ms.openlocfilehash: 3d4e44eefaf99a40b9c4f1c45e7dd81192f8b607
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904270"
---
# <a name="icordebugheapsegmentenumnext-method"></a>ICorDebugHeapSegmentEnum::Next – metoda
Získá zadaný počet instancí [COR_SEGMENT](cor-segment-structure.md) , které obsahují informace o oblastech paměti spravované haldy.  
  
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
 mimo Pole ukazatelů, z nichž každý odkazuje na objekt [COR_SEGMENT](cor-segment-structure.md) , který poskytuje informace o oblasti paměti ve spravované haldě.  
  
 pceltFetched  
 mimo Ukazatel na počet skutečně vrácených objektů [COR_SEGMENT](cor-segment-structure.md) `segments` . Tato hodnota může být `null` `celt` , pokud je 1.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugHeapSegmentEnum – rozhraní](icordebugheapsegmentenum-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
