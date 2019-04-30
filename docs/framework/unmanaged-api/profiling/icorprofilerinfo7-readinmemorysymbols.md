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
ms.openlocfilehash: 662863ec69e464dafe893552f1d81755313acc75
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61786212"
---
# <a name="icorprofilerinfo7readinmemorysymbols"></a>ICorProfilerInfo7::ReadInMemorySymbols
[Podporované v [!INCLUDE[net_v461](../../../../includes/net-v461-md.md)] a novější verze]  
  
 Přečte bajtů ze symbolů v paměti datového proudu.  
  
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
  
## <a name="parameters"></a>Parametry  
 `moduleId`  
 [in] Identifikátor modulu, který obsahuje datový proud v paměti.  
  
 `symbolsReadOffset`  
 [in] Posun v rámci datového proudu v paměti od kterého začne číst bajty.  
  
 `pSymbolBytes`  
 [out] Ukazatel do vyrovnávací paměti, do které se kopírují data. Vyrovnávací paměť by měl mít `countSymbolBytes` volného místa.  
  
 `countSymbolBytes`  
 [in] Počet bajtů, které mají kopírovat.  
  
 `pCountSymbolBytesRead`  
 [out] Po návratu metody obsahuje skutečný počet přečtených bajtů.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`, pokud byla přečtena nenulové počet bajtů.  
  
 `CORPROF_E_MODULE_IS_DYNAMIC`, pokud modul byl vytvořen pomocí <xref:System.Reflection.Emit>.  
  
## <a name="remarks"></a>Poznámky  
 `ReadInMemorySymbols` Metoda se pokusí přečíst `countSymbolBytes` dat začínající na posunu `symbolsReadOffset` v rámci datového proudu v paměti. Data zkopírována do `pSymbolBytes`, která má mít `countSymbolBytes` volného místa.     `pCountSymbolsBytesRead` obsahuje skutečný počet bajtů, přečtěte si, které mohou být menší než `countSymbolBytes` Pokud je dosaženo konce datového proudu.  
  
> [!NOTE]
>  Aktuální implementace nepodporuje Reflection.Emit. Pokud modul byl vytvořen pomocí třídy Reflection.Emit, metoda vrátí `CORPROF_E_MODULE_IS_DYNAMIC`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo7 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
