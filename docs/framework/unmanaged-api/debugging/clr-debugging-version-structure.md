---
title: CLR_DEBUGGING_VERSION – struktura
ms.date: 03/30/2017
api_name:
- CLR_DEBUGGING_VERSION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLR_DEBUGGING_VERSION
helpviewer_keywords:
- CLR_DEBUGGING_VERSION structure [.NET Framework debugging]
ms.assetid: 4d821186-3ddf-405a-ac44-d79438a9f7f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4be232ab557d582f3521b8775108c004b5a3dd78
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="clrdebuggingversion-structure"></a>CLR_DEBUGGING_VERSION – struktura
Definuje verze produktu common language runtime (CLR) pro účely ladění.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Typedef struct _CLR_DEBUGGING_VERSION  
{  
WORD wStructVersion;  
WORD wMajor;   
WORD wMinor;  
WORD wBuild;  
WORD wRevision;  
}  CLR_DEBUGGING_VERSION;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`wStructVersion`|Číslo verze struktura|  
|`wMajor`|Hlavní číslo verze.|  
|`wMinor`|Vedlejší číslo verze.|  
|`wBuild`|Číslo sestavení.|  
|`wRevision`|Číslo revize.|  
  
## <a name="remarks"></a>Poznámky  
 `CLR_DEBUGGING_VERSION` Struktura je stejný jako cor_version – struktura, ale je `CLR_DEBUGGING_VERSION` struktura zajišťuje na další struktura pole verze (`wStructVersion`). V tomto poli musí být v současné době nastavit na nulu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Struktury pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
