---
title: ICorProfilerInfo7::ReadInMemorySymbols
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.ReadInMemorySymbols
api_location:
- CorProf.idl
- CorProf.h
- CorGuids.lib
api_type:
- COM
ms.assetid: 1745a0b9-8332-4777-a670-b549bff3b901
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95b463b23c230d620d746e48da49d75238ef2cb7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955373"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a>ICorProfilerInfo7::ReadInMemorySymbols
[Podporováno v .NET Framework 4.6.1 a novějších verzích]  
  
 Načte bajty z datového proudu symbolů v paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `moduleId`  
 pro Identifikátor modulu, který obsahuje datový proud v paměti.  
  
 `symbolsReadOffset`  
 pro Posun v rámci proudu v paměti, ve kterém se mají začít číst bajty.  
  
 `pSymbolBytes`  
 mimo Ukazatel na vyrovnávací paměť, do které budou kopírována data. Velikost vyrovnávací paměti by `countSymbolBytes` měla být místo k dispozici.  
  
 `countSymbolBytes`  
 pro Počet bajtů, které mají být zkopírovány.  
  
 `pCountSymbolBytesRead`  
 mimo Když metoda vrátí, obsahuje skutečný počet přečtených bajtů.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`, pokud bylo přečteno nenulový počet bajtů.  
  
 `CORPROF_E_MODULE_IS_DYNAMIC`, pokud byl modul vytvořen pomocí <xref:System.Reflection.Emit>.  
  
## <a name="remarks"></a>Poznámky  
 Metoda `ReadInMemorySymbols` se pokusí přečíst `countSymbolBytes` data začínající na posunu `symbolsReadOffset` v datovém proudu v paměti. Data se zkopírují do `pSymbolBytes`, což by mělo být `countSymbolBytes` dostupné místo.     `pCountSymbolsBytesRead`obsahuje skutečný počet přečtených bajtů, který může být menší, než `countSymbolBytes` je dosaženo konce datového proudu.  
  
> [!NOTE]
> Aktuální implementace nepodporuje reflexe. Emit. Pokud byl modul vytvořen pomocí reflexe. Emit, vrátí `CORPROF_E_MODULE_IS_DYNAMIC`metoda.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlaviček** CorProf.idl, CorProf.h  
  
 **Knihovna** CorGuids.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo7 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
