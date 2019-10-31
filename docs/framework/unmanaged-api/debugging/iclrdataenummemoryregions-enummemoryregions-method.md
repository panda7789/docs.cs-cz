---
title: ICLRDataEnumMemoryRegions::EnumMemoryRegions – metoda
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegions.EnumMemoryRegions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions
helpviewer_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions method [.NET Framework debugging]
- EnumMemoryRegions method [.NET Framework debugging]
ms.assetid: 22d2e339-f174-40b5-a478-0b744501566f
topic_type:
- apiref
ms.openlocfilehash: 693ec07176f80711709cd9b85c6886bea8be74b2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122970"
---
# <a name="iclrdataenummemoryregionsenummemoryregions-method"></a>ICLRDataEnumMemoryRegions::EnumMemoryRegions – metoda
Vytvoří výčet zadaných oblastí paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnumMemoryRegions (  
    [in] ICLRDataEnumMemoryRegionsCallback  *callback,  
    [in] ULONG32                            miniDumpFlags,  
    [in] CLRDataEnumMemoryFlags             clrFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `callback`  
 pro Ukazatel na instanci [ICLRDataEnumMemoryRegionsCallback –](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) , která je volána touto metodou pro každou oblast paměti, která je vyčíslena pro oznamování ladicímu programu výsledku.  
  
 Výčet oblastí paměti pokračuje i v případě, že zpětné volání signalizuje selhání.  
  
 `miniDumpFlags`  
 pro Nepoužívá se.  
  
 `clrFlags`  
 pro Hodnota výčtu [CLRDataEnumMemoryFlags –](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md) , která určuje oblasti paměti, které mají být vyčísleny.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda používá zadanou instanci [ICLRDataEnumMemoryRegionsCallback –](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) k upozorňování volajícího výsledku.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** ClrData. idl, ClrData. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRDataEnumMemoryRegions – rozhraní](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-interface.md)
