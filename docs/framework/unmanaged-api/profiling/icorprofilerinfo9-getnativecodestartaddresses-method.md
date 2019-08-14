---
title: ICorProfilerInfo9::GetNativeCodeStartAddresses
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetNativeCodeStartAddresses
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: f5c7f11a322e4cf3ed38608e0f380dd632bc8fb6
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973690"
---
# <a name="icorprofilerinfo9getnativecodestartaddresses-method"></a>ICorProfilerInfo9:: GetNativeCodeStartAddresses – metoda
  
 S ohledem na functionId a rejitId vytvoří výčet počáteční adresy kódu pro všechny zpracovaných kompilátorem JIT verze tohoto kódu, který aktuálně existuje.   
  
## <a name="syntax"></a>Syntaxe  
  
```cpp
HRESULT GetNativeCodeStartAddresses( [in]  FunctionID functionID,
                                     [in]  ReJITID reJitId,
                                     [in]  ULONG32 cCodeStartAddresses,
                                     [out] ULONG32 *pcCodeStartAddresses,
                                     [out] UINT_PTR codeStartAddresses[]);
```  
  
#### <a name="parameters"></a>Parametry  
 `functionId`  
 pro Mělo by se vrátit ID funkce, jejíž počáteční adresy nativního kódu by měly být vráceny.  
  
 `reJitId`  
 pro Identita funkce Rekompilované JIT. 
  
 `cCodeStartAddresses` \
 pro Maximální velikost `codeStartAddresses` pole.

 `pcCodeStartAddresses` \
 mimo Počet dostupných adres.

 `codeStartAddresses` \
 mimo Pole `UINT_PTR`, z nichž každá z nich je počáteční adresou pro nativní tělo zadané funkce. 

## <a name="remarks"></a>Poznámky  
 Pokud je povolená vrstvená kompilace, funkce může mít více než jeden tělo nativního kódu. 

## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [podporované operační systémy .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).  
  
 **Hlaviček** CorProf.idl, CorProf.h  
  
 **Knihovna** CorGuids.lib  
  
 **Verze rozhraní .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)] 
  
## <a name="see-also"></a>Viz také:
- [Rozhraní ICorProfilerInfo9](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md)

