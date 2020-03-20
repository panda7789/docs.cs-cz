---
title: ICorDebugHeapEnum::Next – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugHeapEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapEnum::Next
helpviewer_keywords:
- ICorDebugHeapEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 2221fd06-9e27-4113-972e-2530db8c3594
topic_type:
- apiref
ms.openlocfilehash: f5af8e559b4fbfeb60530372185ca10104ade987
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178854"
---
# <a name="icordebugheapenumnext-method"></a>ICorDebugHeapEnum::Next – metoda
Získá zadaný počet [COR_HEAPOBJECT](cor-heapobject-structure.md) instancí, které obsahují informace o objektech na spravované haldy.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_HEAPOBJECT  objects[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parametry  
 celt  
 [v] Počet objektů, které mají být načteny.  
  
  – objekty  
 [out] Pole ukazatelů, z nichž každý odkazuje na [COR_HEAPOBJECT](cor-heapobject-structure.md) objekt, který poskytuje informace o objektu na spravované haldy.  
  
 pceltnačten  
 [out] Ukazatel na počet [objektů COR_HEAPOBJECT](cor-heapobject-structure.md) skutečně `objects`vrácených v . Tato hodnota `null` může `celt` být, pokud je 1.  
  
## <a name="remarks"></a>Poznámky  
 Toto `COR_HEAPOBJECT.type` pole je identifikátorem vnořeného rozhraní COM s počítaného odkazem. Tento odkaz musí být uvolněn `ICorDebugHeapEnum::Next`volajícím .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugHeapEnum – rozhraní](icordebugheapenum-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
