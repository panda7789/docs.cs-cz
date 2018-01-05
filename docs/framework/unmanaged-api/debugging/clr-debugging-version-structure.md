---
title: "CLR_DEBUGGING_VERSION – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CLR_DEBUGGING_VERSION
api_location: mscordbi.dll
api_type: COM
f1_keywords: CLR_DEBUGGING_VERSION
helpviewer_keywords: CLR_DEBUGGING_VERSION structure [.NET Framework debugging]
ms.assetid: 4d821186-3ddf-405a-ac44-d79438a9f7f3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 092024f3f4e6fc1bc923ae2a299c5d9c21f1b1b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Struktury pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
