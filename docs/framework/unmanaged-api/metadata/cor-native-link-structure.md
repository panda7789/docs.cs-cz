---
title: COR_NATIVE_LINK – struktura
ms.date: 03/30/2017
api_name:
- COR_NATIVE_LINK
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_NATIVE_LINK
helpviewer_keywords:
- COR_NATIVE_LINK structure [.NET Framework metadata]
ms.assetid: 6ef78d3c-1c69-4141-b687-dcb065b7a74d
topic_type:
- apiref
ms.openlocfilehash: 812b70a594b5aa933f52d36f32d96d712267ecf4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177962"
---
# <a name="cor_native_link-structure"></a>COR_NATIVE_LINK – struktura
Obsahuje informace, které se používají k propojení nativního kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`m_linkType`|Typ, který má být propojen v nativním kódu. Tato hodnota je jednou z hodnot [CorNativeLinkType.](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)|  
|`m_flags`|Příznaky používané propojovacím programem při propojování nativního kódu. Tato hodnota je jednou z hodnot [CorNativeLinkFlags.](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)|  
|`m_entryPoint`|Token metadat MemberRef, který představuje vstupní bod. Formát je `lib:entrypoint`.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Struktury pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [CorNativeLinkType – výčet](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)
- [CorNativeLinkFlags – výčet](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)
