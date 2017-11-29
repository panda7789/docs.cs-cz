---
title: "IDENTITY_ATTRIBUTE – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDENTITY_ATTRIBUTE
api_location: fusion.dll
api_type: COM
f1_keywords: IDENTITY_ATTRIBUTE
helpviewer_keywords: IDENTITY_ATTRIBUTE structure [.NET Framework fusion]
ms.assetid: 1ee7c434-9681-4fa8-badd-652cb1a9742b
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3fc4d9f7a95a3283d87f036163592f43e87dd053
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="identityattribute-structure"></a>IDENTITY_ATTRIBUTE – struktura
Obsahuje informace o atributu metadata o [idefinitionidentity –](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instance.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`pszNamespace`|Ukazatel na řetězec znaků ukončené hodnotou null, která obsahuje obor názvů je atribut v.|  
|`pszName`|Ukazatel na řetězec znaků ukončené hodnotou null, který obsahuje název atributu.|  
|`pszValue`|Ukazatel na řetězec znaků ukončený hodnotou null, obsahující hodnotu atributu.|  
  
## <a name="remarks"></a>Poznámky  
 `IDENTITY_ATTRIBUTE` Struktura obsahuje tři ukazatele na řetězce ukončené hodnotou null znaků. Tyto tři řetězce popisují jeden atribut.  
  
 Instance `IDENTITY_ATTRIBUTE` struktura je přidružený instanci [identity_attribute_blob –](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md) struktura. `IDENTITY_ATTRIBUTE` Struktura obsahuje skutečné řetězce a odpovídající `IDENTITY_ATTRIBUTE_BLOB` struktura uvádí posunutí na tři řetězce uvedené v `IDENTITY_ATTRIBUTE` struktura.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Isolation.h  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Idefinitionidentity – rozhraní](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)  
 [Identity_attribute_blob – struktura](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md)  
 [Struktury fúzí](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
