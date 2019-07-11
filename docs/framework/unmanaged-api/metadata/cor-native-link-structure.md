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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ae518e5a736a78a261dc3821d53d93afee95a271
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779998"
---
# <a name="cornativelink-structure"></a>COR_NATIVE_LINK – struktura
Obsahuje informace, které slouží k propojení nativního kódu.  
  
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
|`m_linkType`|Typ propojení v nativním kódu. Tato hodnota je jedním z [cornativelinktype –](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md) hodnoty.|  
|`m_flags`|Příznaky použité linkerem při propojování nativního kódu. Tato hodnota je jedním z [cornativelinkflags –](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md) hodnoty.|  
|`m_entryPoint`|Token MemberRef metadata, která představuje vstupní bod. Formát je `lib:entrypoint`.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [CorNativeLinkType – výčet](../../../../docs/framework/unmanaged-api/metadata/cornativelinktype-enumeration.md)
- [CorNativeLinkFlags – výčet](../../../../docs/framework/unmanaged-api/metadata/cornativelinkflags-enumeration.md)
