---
title: IMethodMalloc::Alloc – metoda
ms.date: 03/30/2017
api_name:
- IMethodMalloc.Alloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc::Alloc
helpviewer_keywords:
- IMethodMalloc::Alloc method [.NET Framework profiling]
- Alloc method, IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8653bd4c-2290-43d2-a3e1-cbbd50033f4f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6d73fe16720248d541bac64a432bb6f35d6873b6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="imethodmallocalloc-method"></a>IMethodMalloc::Alloc – metoda
Pokusí se přidělit zadanou velikost paměti pro nový tělo funkce (MSIL intermediate language) společnosti Microsoft.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
PVOID Alloc (  
    [in] ULONG   cb  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cb`  
 [v] Počet bajtů k přidělení pro tělo metoda.  
  
## <a name="remarks"></a>Poznámky  
 Přidělenou paměť bude zahájena v adresu větší než bázové adresy modul, který je přidružen toto přidělení. Jinými slovy každý allocator se vytvoří pro konkrétního modulu a pokusí se přidělit paměť na kladné posunu z jeho základní adresu. Pokud `Alloc` nepodaří přidělit požadovaný počet bajtů na adresu větší než základní adresu modulu, vrátí E_OUTOFMEMORY, bez ohledu na skutečné množství paměti místa.  
  
 `Alloc` Metoda má být použita ve spojení s [icorprofilerinfo::setilfunctionbody –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) metoda.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** WindSee [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [IMethodMalloc – rozhraní](../../../../docs/framework/unmanaged-api/profiling/imethodmalloc-interface.md)
