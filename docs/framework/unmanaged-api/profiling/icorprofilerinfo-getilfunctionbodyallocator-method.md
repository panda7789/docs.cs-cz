---
title: ICorProfilerInfo::GetILFunctionBodyAllocator – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILFunctionBodyAllocator
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILFunctionBodyAllocator
helpviewer_keywords:
- GetILFunctionBodyAllocator method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBodyAllocator method [.NET Framework profiling]
ms.assetid: 5da1bf3d-dddf-4892-b266-578ee54d570b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2cd66a895f99d62e8deaa45afab12d963aee2901
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59109119"
---
# <a name="icorprofilerinfogetilfunctionbodyallocator-method"></a>ICorProfilerInfo::GetILFunctionBodyAllocator – metoda
Získá rozhraní, které představuje způsob, jak přidělit paměť pro záměnu těla metody v kódu Microsoft intermediate language (MSIL).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetILFunctionBodyAllocator(  
    [in]  ModuleID      moduleId,  
    [out] IMethodMalloc **ppMalloc);  
```  
  
## <a name="parameters"></a>Parametry  
 `moduleId`  
 [in] ID modulu, ve kterém se nachází metodu.  
  
 `ppMalloc`  
 [out] Ukazatel [imethodmalloc –](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md) rozhraní, které poskytuje metodu pro přidělení paměti.  
  
## <a name="remarks"></a>Poznámky  
 Tělo metody v kódu jazyka MSIL musí být umístěn jako relativní virtuální adresu (RVA), relativní k načteného modulu, což znamená, že následuje modul v rámci 4 GB. Aby bylo snazší pro nástroj vyměnit tělo metody, `GetILFunctionBodyAllocator` metoda zajišťuje, že paměť je přidělena v tomto rozsahu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
