---
title: BucketParameters – struktura
ms.date: 03/30/2017
api_name:
- BucketParameters
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- BucketParameters
helpviewer_keywords:
- BucketParameters structure [.NET Framework hosting]
ms.assetid: 9432487e-f276-45d6-9a13-9a68024dbd46
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0b5e4db8e385baefe3067755bbdc4555c5887ab6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="bucketparameters-structure"></a>BucketParameters – struktura
Ukládá název typu události a parametry pro aktuální výjimka, ke které je přidruženo k události.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct _BucketParameters {  
    BOOL  fInited;                    
    WCHAR pszEventTypeName[255];      
    WCHAR pszParams[10][255];         
} BucketParameters;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`fInited`|`true`, pokud je platná; zbytek tato struktura v opačném `false`.|  
|`pszEventTypeName`|Název typu události.|  
|`pszParams`|Pole řetězců, z nichž každý určuje parametr pro aktuální výjimky přidružený k události.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.idl  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Struktury pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
