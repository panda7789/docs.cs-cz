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
ms.openlocfilehash: d03c22c455f0e44ce32d4593d9eee50ceef94a22
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443956"
---
# <a name="cor_native_link-structure"></a>COR_NATIVE_LINK – struktura
Contains information that is used to link native code.  
  
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
|`m_linkType`|The type to be linked in native code. This value is one of the [CorNativeLinkType](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) values.|  
|`m_flags`|Flags used by the linker when linking native code. This value is one of the [CorNativeLinkFlags](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) values.|  
|`m_entryPoint`|The MemberRef metadata token that represents the entry point. The format is `lib:entrypoint`.|  
  
## <a name="requirements"></a>Požadavky  
 **Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** Cor.h  
  
 **Library:** Used as a resource in MsCorEE.dll  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [CorNativeLinkType – výčet](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)
- [CorNativeLinkFlags – výčet](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)
