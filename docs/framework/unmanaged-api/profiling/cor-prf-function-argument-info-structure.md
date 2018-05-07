---
title: COR_PRF_FUNCTION_ARGUMENT_INFO – struktura
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION_ARGUMENT_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION_ARGUMENT_INFO
helpviewer_keywords:
- COR_PRF_FUNCTION_ARGUMENT_INFO structure [.NET Framework profiling]
ms.assetid: 07cf3bab-e193-4991-8205-3f41cf2d67b3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1fbc41ca1366b412c37d6af09e90e3f1b042ba21
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="corprffunctionargumentinfo-structure"></a>COR_PRF_FUNCTION_ARGUMENT_INFO – struktura
Představuje argumenty funkcí v pořadí zleva doprava.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_INFO {  
    ULONG numRanges;  
    ULONG totalArgumentSize;  
    COR_PRF_FUNCTION_ARGUMENT_RANGE ranges[1];  
} COR_PRF_FUNCTION_ARGUMENT_INFO;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`numRanges`|Počet bloků argumentů. Tato hodnota je počet [COR_PRF_FUNCTION_ARGUMENT_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) struktury v `ranges` pole.|  
|`totalArgumentSize`|Celková velikost všech argumentů. Jinými slovy tato hodnota je součtem argument délek.|  
|`ranges`|Pole `COR_PRF_FUNCTION_ARGUMENT_RANGE` struktury, z nichž každý představuje jeden blok argumenty funkce.|  
  
## <a name="remarks"></a>Poznámky  
 Funkce může mít mnoho argumentů. Tyto argumenty nemusí být souvisle uložené v paměti. Můžete mít blok tři argumenty na jednom místě, blok dva argumenty na jiném místě a poslední blok jeden argument na jiné místo. Jsou všechny tyto argumenty pro stejnou funkci; právě byly uloženy do různých místech.  
  
 `COR_PRF_FUNCTION_ARGUMENT_INFO` Struktura představuje všechny argumenty jedné funkce. Chcete-li všechny bloky argumenty funkce používá pole. Ano, pro jednu funkci, máte jediný `COR_PRF_FUNCTION_ARGUMENT_INFO` strukturu, která odkazuje na více `COR_PRF_FUNCTION_ARGUMENT_RANGE` struktury, každý z nich odkazuje na jeden nebo více argumenty funkce.  
  
 Argumenty, které jsou uložené v registrech jsou uniknout do paměti k vytvoření struktury.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Struktury pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
