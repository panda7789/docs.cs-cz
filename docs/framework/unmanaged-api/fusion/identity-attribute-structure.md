---
title: IDENTITY_ATTRIBUTE – struktura
ms.date: 03/30/2017
api_name:
- IDENTITY_ATTRIBUTE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDENTITY_ATTRIBUTE
helpviewer_keywords:
- IDENTITY_ATTRIBUTE structure [.NET Framework fusion]
ms.assetid: 1ee7c434-9681-4fa8-badd-652cb1a9742b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb970d31fb5158adc7dbcbb7cc0175cc91c83c8c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107338"
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
|`pszNamespace`|Ukazatel na řetězec znaků zakončené znakem null, který obsahuje obor názvů příslušný atribut nachází v.|  
|`pszName`|Ukazatel na řetězec znaků zakončené znakem null, který obsahuje název atributu.|  
|`pszValue`|Ukazatel na řetězec znaků zakončené znakem null, který obsahuje hodnotu atributu.|  
  
## <a name="remarks"></a>Poznámky  
 `IDENTITY_ATTRIBUTE` Struktura obsahuje tři ukazatele na řetězce znaků zakončených znakem null. Tyto tři řetězce popisu jeden atribut.  
  
 Instance `IDENTITY_ATTRIBUTE` struktura je přidružený k instanci [identity_attribute_blob –](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md) struktury. `IDENTITY_ATTRIBUTE` Struktura obsahuje skutečné řetězce a odpovídající `IDENTITY_ATTRIBUTE_BLOB` struktura obsahuje seznam posunutí pro tři řetězce, uvedené v `IDENTITY_ATTRIBUTE` struktury.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Isolation.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IDefinitionIdentity – rozhraní](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)
- [IDENTITY_ATTRIBUTE_BLOB – struktura](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md)
- [Struktury fúzí](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
