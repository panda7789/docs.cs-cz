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
ms.openlocfilehash: a11b7d5939c4c20504b1ff3dfb4613f85bca0db4
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007972"
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
  
|Člen|Description|  
|------------|-----------------|  
|`m_linkType`|Typ, který se má propojit v nativním kódu. Tato hodnota je jednou z hodnot [CorNativeLinkType –](cornativelinktype-enumeration.md) .|  
|`m_flags`|Příznaky používané linkerem při propojování nativního kódu. Tato hodnota je jednou z hodnot [CorNativeLinkFlags –](cornativelinkflags-enumeration.md) .|  
|`m_entryPoint`|Token metadat MemberRef, který představuje vstupní bod. Formát je `lib:entrypoint`.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Struktury pro metadata](metadata-structures.md)
- [CorNativeLinkType – výčet](cornativelinktype-enumeration.md)
- [CorNativeLinkFlags – výčet](cornativelinkflags-enumeration.md)
