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
ms.openlocfilehash: 8b7edf1cc642228c4a79c855b51727264f31741c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107983"
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
 Struktura `IDENTITY_ATTRIBUTE` obsahuje tři ukazatele na řetězce znaků zakončených hodnotou null. Tyto tři řetězce popisují jeden atribut.  
  
 Instance struktury `IDENTITY_ATTRIBUTE` je přidružená k instanci struktury [IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md) . Struktura `IDENTITY_ATTRIBUTE` obsahuje skutečné řetězce a odpovídající `IDENTITY_ATTRIBUTE_BLOB` struktura vypisuje posuny k třem řetězcům uvedeným ve struktuře `IDENTITY_ATTRIBUTE`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Izolace. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IDefinitionIdentity – rozhraní](idefinitionidentity-interface.md)
- [IDENTITY_ATTRIBUTE_BLOB – struktura](identity-attribute-blob-structure.md)
- [Struktury pro fúze](fusion-structures.md)
