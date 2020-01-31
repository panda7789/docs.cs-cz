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
ms.openlocfilehash: f2b2bbe8bcecf71f6d3016fb35dfbf5ba1353aea
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785629"
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
 pro Ukazatel na instanci [ICLRDataEnumMemoryRegionsCallback –](iclrdataenummemoryregionscallback-interface.md) , která je volána touto metodou pro každou oblast paměti, která je vyčíslena pro oznamování ladicímu programu výsledku.  
  
 Výčet oblastí paměti pokračuje i v případě, že zpětné volání signalizuje selhání.  
  
 `miniDumpFlags`  
 pro Nepoužívá se.  
  
 `clrFlags`  
 pro Hodnota výčtu [CLRDataEnumMemoryFlags –](clrdataenummemoryflags-enumeration.md) , která určuje oblasti paměti, které mají být vyčísleny.  
  
## <a name="remarks"></a>Poznámky  
 Tato metoda používá zadanou instanci [ICLRDataEnumMemoryRegionsCallback –](iclrdataenummemoryregionscallback-interface.md) k upozorňování volajícího výsledku.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** ClrData. idl, ClrData. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICLRDataEnumMemoryRegions – rozhraní](iclrdataenummemoryregions-interface.md)
