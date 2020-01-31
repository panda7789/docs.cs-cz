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
ms.openlocfilehash: c92ee580caed9f1fb87a31b676747769ad31a0e2
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867246"
---
# <a name="cor_prf_function_argument_info-structure"></a>COR_PRF_FUNCTION_ARGUMENT_INFO – struktura
Představuje argumenty funkce v pořadí zleva doprava.  
  
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
|`numRanges`|Počet bloků argumentů. To znamená, že tato hodnota je počet [COR_PRF_FUNCTION_ARGUMENT_RANGE](cor-prf-function-argument-range-structure.md) struktur v poli `ranges`.|  
|`totalArgumentSize`|Celková velikost všech argumentů. Jinými slovy je tato hodnota součtem délek argumentů.|  
|`ranges`|Pole struktur `COR_PRF_FUNCTION_ARGUMENT_RANGE`, z nichž každý představuje jeden blok argumentů funkce.|  
  
## <a name="remarks"></a>Poznámky  
 Funkce může mít mnoho argumentů. Tyto argumenty nemusí být uloženy souvisle v paměti. Můžete mít blok tří argumentů na jednom místě, blok dvou argumentů na jiném místě a konečný blok jednoho argumentu na jiném místě. Tyto argumenty jsou všechny pro stejnou funkci. jsou právě uloženy na různých místech.  
  
 Struktura `COR_PRF_FUNCTION_ARGUMENT_INFO` představuje všechny argumenty jediné funkce. Používá pole k odkazování na všechny bloky argumentů funkce. Pro jedinou funkci tedy máte jednu strukturu `COR_PRF_FUNCTION_ARGUMENT_INFO`, která odkazuje na více `COR_PRF_FUNCTION_ARGUMENT_RANGE` struktur, z nichž každý odkazuje na jeden nebo více argumentů funkce.  
  
 Argumenty, které jsou uloženy v registrech, jsou přerozděleny do paměti pro sestavení struktur.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro profilaci](profiling-structures.md)
