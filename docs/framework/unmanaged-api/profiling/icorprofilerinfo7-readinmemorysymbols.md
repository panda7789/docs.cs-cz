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
ms.openlocfilehash: 6732457220d795bbf8ae54277ef9f5c07cf96359
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495356"
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
 mimo Ukazatel na vyrovnávací paměť, do které budou kopírována data. Velikost vyrovnávací paměti by měla být `countSymbolBytes` místo k dispozici.  
  
 `countSymbolBytes`  
 pro Počet bajtů, které mají být zkopírovány.  
  
 `pCountSymbolBytesRead`  
 mimo Když metoda vrátí, obsahuje skutečný počet přečtených bajtů.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`, pokud bylo přečteno nenulový počet bajtů.  
  
 `CORPROF_E_MODULE_IS_DYNAMIC`, pokud byl modul vytvořen pomocí <xref:System.Reflection.Emit> .  
  
## <a name="remarks"></a>Poznámky  
 `ReadInMemorySymbols`Metoda se pokusí přečíst `countSymbolBytes` data začínající na posunu v `symbolsReadOffset` datovém proudu v paměti. Data se zkopírují do `pSymbolBytes` , což by mělo být `countSymbolBytes` dostupné místo.     `pCountSymbolsBytesRead`obsahuje skutečný počet přečtených bajtů, který může být menší, než `countSymbolBytes` je dosaženo konce datového proudu.  
  
> [!NOTE]
> Aktuální implementace nepodporuje reflexe. Emit. Pokud byl modul vytvořen pomocí reflexe. Emit, vrátí metoda `CORPROF_E_MODULE_IS_DYNAMIC` .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo7 – rozhraní](icorprofilerinfo7-interface.md)
