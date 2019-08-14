---
title: ICorProfilerInfo9::GetILToNativeMapping3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetILToNativeMapping3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 46ceef43806fda9956797935c5eeec61f865dc6e
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973684"
---
# <a name="icorprofilerinfo9getiltonativemapping3-method"></a>ICorProfilerInfo9:: GetILToNativeMapping3 – metoda
  
 Vzhledem k počáteční adrese nativního kódu vrací nativní informace mapování IL pro tuto verzi zpracovaných kompilátorem JIT kódu.   
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetILToNativeMapping3( [in]  UINT_PTR pNativeCodeStartAddress,
                               [in]  ULONG32 cMap,
                               [out] ULONG32 *pcMap,
                               [out] COR_DEBUG_IL_TO_NATIVE_MAP map[]);
```  
  
#### <a name="parameters"></a>Parametry  
 `pNativeCodeStartAddress` \
 pro Ukazatel na začátek nativní funkce.

 `cMap` \
 pro Maximální velikost `map` pole. 

 `pcMap` \
 mimo Celkový počet dostupných struktur COR_DEBUG_IL_TO_NATIVE_MAP.

 `map` \
 mimo Pole struktur [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) , z nichž každý Určuje posun. Poté, co `map` `COR_DEBUG_IL_TO_NATIVE_MAP` metoda vrátí, bude obsahovat některé nebo všechny struktury. `GetILToNativeMapping3`

## <a name="remarks"></a>Poznámky  
 Pokud je povolená vrstvená kompilace, může mít metoda více než jeden tělo nativního kódu. [ICorProfilerInfo9:: GetNativeCodeStartAddresses](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-getnativecodestartaddresses-method.md) vrátí počáteční adresy pro všechny tělo nativního kódu.

## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [podporované operační systémy .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).  
  
 **Hlaviček** CorProf.idl, CorProf.h  
  
 **Knihovna** CorGuids.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)] 
  
## <a name="see-also"></a>Viz také:
- [Rozhraní ICorProfilerInfo9](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md)

