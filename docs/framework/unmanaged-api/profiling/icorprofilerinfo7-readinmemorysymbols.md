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
ms.openlocfilehash: 9874c8e567a89fd3977be360666c86406f2cd395
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a>ICorProfilerInfo7::ReadInMemorySymbols
[V podporované [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] a novější verze]  
  
 Čte bajtů z datového proudu symbolu v paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ReadInMemorySymbols(  
        [in] ModuleID moduleId,  
        [in] DWORD symbolsReadOffset,  
        [out] BYTE* pSymbolBytes,  
        [in] DWORD countSymbolBytes,  
        [out] DWORD* pCountSymbolBytesRead  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `moduleId`  
 [v] Identifikátor modul, který obsahuje datový proud v paměti.  
  
 `symbolsReadOffset`  
 [v] Posun v rámci datového proudu v paměti, pro kterou chcete spustit čtení bajtů.  
  
 `pSymbolBytes`  
 [out] Ukazatel do vyrovnávací paměti, ke kterému se zkopírují data. Vyrovnávací paměti by měl mít `countSymbolBytes` množství dostupného místa.  
  
 `countSymbolBytes`  
 [v] Počet bajtů ke kopírování.  
  
 `pCountSymbolBytesRead`  
 [out] Po návratu metody obsahuje skutečný počet přečtených bajtů.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`, pokud byla přečtena nenulový počet bajtů.  
  
 `CORPROF_E_MODULE_IS_DYNAMIC`, pokud modul byl vytvořen pomocí <xref:System.Reflection.Emit>.  
  
## <a name="remarks"></a>Poznámky  
 `ReadInMemorySymbols` Metoda se pokusí přečíst `countSymbolBytes` začínající na posunu dat `symbolsReadOffset` v rámci datového proudu v paměti. Data budou zkopírována do `pSymbolBytes`, který by měl být `countSymbolBytes` množství dostupného místa.     `pCountSymbolsBytesRead` obsahuje skutečný počet bajtů přečtených, což může být menší než `countSymbolBytes` Pokud dosažen konec datového proudu.  
  
> [!NOTE]
>  Aktuální implementace Reflection.Emit nepodporuje. Pokud modul byl vytvořen pomocí Reflection.Emit, vrátí metoda `CORPROF_E_MODULE_IS_DYNAMIC`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerInfo7 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
