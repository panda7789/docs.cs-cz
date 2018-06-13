---
title: COR_PRF_FUNCTION_ARGUMENT_RANGE – struktura
ms.date: 03/30/2017
api_name:
- COR_PRF_FUNCTION_ARGUMENT_RANGE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FUNCTION_ARGUMENT_RANGE
helpviewer_keywords:
- COR_PRF_FUNCTION_ARGUMENT_RANGE structure [.NET Framework profiling'
ms.assetid: 9f469eac-ac66-419b-8668-fe705bc1a51f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 92e3a0a930a4e4b91cac27cbed1b745dea4207a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450021"
---
# <a name="corprffunctionargumentrange-structure"></a>COR_PRF_FUNCTION_ARGUMENT_RANGE – struktura
Představuje blok argumenty funkce souvisle uložené v pořadí zleva doprava v paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct _COR_PRF_FUNCTION_ARGUMENT_RANGE {  
    UINT_PTR startAddress;  
    ULONG length;  
} COR_PRF_FUNCTION_ARGUMENT_RANGE;  
```  
  
## <a name="members"></a>Členové  
  
|Členové|Popis|  
|-------------|-----------------|  
|`startAddress`|Počáteční adresa bloku.|  
|`length`|Délka souvislý blok.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Struktury pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
