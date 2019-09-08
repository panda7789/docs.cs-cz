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
ms.openlocfilehash: e0bcabb32d50b236d42a555c073b50ba3a234dde
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796484"
---
# <a name="identity_attribute-structure"></a>IDENTITY_ATTRIBUTE – struktura
Obsahuje informace o atributech metadat instance [IDefinitionIdentity –](idefinitionidentity-interface.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`pszNamespace`|Ukazatel na řetězec znaků zakončený hodnotou null, který obsahuje obor názvů, ve kterém je atribut.|  
|`pszName`|Ukazatel na řetězec znaků zakončený hodnotou null, který obsahuje název atributu.|  
|`pszValue`|Ukazatel na řetězec znaků zakončený hodnotou null, který obsahuje hodnotu atributu.|  
  
## <a name="remarks"></a>Poznámky  
 `IDENTITY_ATTRIBUTE` Struktura obsahuje tři ukazatele na řetězce znaků zakončených hodnotou null. Tyto tři řetězce popisují jeden atribut.  
  
 Instance `IDENTITY_ATTRIBUTE` struktury je přidružená k instanci struktury [IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md) . Struktura obsahuje skutečné řetězce a odpovídající `IDENTITY_ATTRIBUTE_BLOB` struktura obsahuje seznam posunů ke `IDENTITY_ATTRIBUTE` třem řetězcům uvedeným ve struktuře. `IDENTITY_ATTRIBUTE`  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** Izolace. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IDefinitionIdentity – rozhraní](idefinitionidentity-interface.md)
- [IDENTITY_ATTRIBUTE_BLOB – struktura](identity-attribute-blob-structure.md)
- [Struktury pro fúze](fusion-structures.md)
