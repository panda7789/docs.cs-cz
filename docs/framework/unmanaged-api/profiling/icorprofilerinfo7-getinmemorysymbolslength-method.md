---
title: ICorProfilerInfo7::GetInMemorySymbolsLength – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.GetInMemorySymbolsLength
api_location:
- mscorwks.dll
- icorprof.idl
api_type:
- COM
ms.assetid: d62c4a4c-8a62-45aa-8f01-a8387cf36159
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5e662270fc8db3fb85e058e8d4f3346f58f79bb8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33457958"
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a>ICorProfilerInfo7::GetInMemorySymbolsLength – metoda
[Podporované v rozhraní .NET Framework 4.6.1 a novějších verzích]  
  
 Vrátí délku datového proudu symbolu v paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetInMemorySymbolsLength(  
        [in] ModuleID moduleId,  
        [out] DWORD* pCountSymbolBytes  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `moduleId`  
 [v] Identifikátor modul, který obsahuje datový proud v paměti.  
  
 pCountSymbolBytes  
 [out] Ukazatel na `DWORD` hodnotu, která po návratu metody obsahuje délka datového proudu v bajtech.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí metoda `S_OK` Pokud délka datového proudu paměti můžete určit, i když je nula (0).  
  
 Vrátí metoda `CORPROF_E_MODULE_IS_DYNAMIC` Pokud metoda byla vytvořena pomocí <xref:System.Reflection.Emit?displayProperty=nameWithType>.  
  
## <a name="remarks"></a>Poznámky  
 Pokud má modul symboly v paměti, délka datového proudu je umístěn v `pCountSymbolBytes`. Pokud modul nemá symboly v paměti `*pCountSymbolBytes = 0`.  
  
> [!NOTE]
>  Aktuální implementace Reflection.Emit nepodporuje. Pokud modul byl vytvořen pomocí Reflection.Emit, vrátí metoda `CORPROF_E_MODULE_IS_DYNAMIC`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerInfo7 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)
