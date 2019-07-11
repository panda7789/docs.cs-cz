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
ms.openlocfilehash: 658b88349bedcbcefd0b97226c7bd1fa34f656c7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781911"
---
# <a name="corprffunctionargumentinfo-structure"></a>COR_PRF_FUNCTION_ARGUMENT_INFO – struktura
Představuje argumenty funkce, v pořadí zleva doprava.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_INFO {  
    ULONG numRanges;  
    ULONG totalArgumentSize;  
    COR_PRF_FUNCTION_ARGUMENT_RANGE ranges[1];  
} COR_PRF_FUNCTION_ARGUMENT_INFO;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`numRanges`|Počet bloků argumentů. To znamená, že tato hodnota je počet [cor_prf_function_argument_range –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-range-structure.md) struktur v `ranges` pole.|  
|`totalArgumentSize`|Celková velikost všech argumentů. Jinými slovy tato hodnota je součet délek argumentů.|  
|`ranges`|Pole `COR_PRF_FUNCTION_ARGUMENT_RANGE` struktury, z nichž každý představuje jeden blok argumentů funkce.|  
  
## <a name="remarks"></a>Poznámky  
 Funkce může mít velký počet argumentů. Tyto argumenty nemusí uložena souvisle v paměti. Můžete mít blok tři argumenty na jednom místě, blok dva argumenty na jiném místě a posledního bloku s jedním argumentem na jiném místě. Všechny tyto argumenty jsou pro stejnou funkci. právě jsou uloženy na různých místech.  
  
 `COR_PRF_FUNCTION_ARGUMENT_INFO` Struktura představuje všechny argumenty jedné funkce. Pole se používá k odkazování všechny bloky argumentů funkce. Ano, pro jednu funkci, máte jediný `COR_PRF_FUNCTION_ARGUMENT_INFO` strukturu, která odkazuje na více `COR_PRF_FUNCTION_ARGUMENT_RANGE` struktury, každý z nich odkazuje na jeden nebo více argumentů funkce.  
  
 Argumenty, které jsou uloženy v registrech, jsou přesahovat do paměti k vytvoření struktury.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
