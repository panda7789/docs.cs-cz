---
title: CREATE_ASM_NAME_OBJ_FLAGS – výčet
ms.date: 03/30/2017
api_name:
- CREATE_ASM_NAME_OBJ_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- CREATE_ASM_NAME_OBJ_FLAGS
helpviewer_keywords:
- CREATE_ASM_NAME_OBJ_FLAGS enumeration [.NET Framework fusion]
ms.assetid: a5ed2fd0-c7d2-4603-aaca-5d0caad92675
topic_type:
- apiref
ms.openlocfilehash: ee856dbd398d0fa5e3eee7d9b2b2cfc7c7a57ecf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176588"
---
# <a name="create_asm_name_obj_flags-enumeration"></a>CREATE_ASM_NAME_OBJ_FLAGS – výčet
Určuje atributy objektu [IAssemblyName Interface,](iassemblyname-interface.md) když je vytvořen funkcí [CreateAssemblyNameObject.](createassemblynameobject-function.md)  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
  
    CANOF_PARSE_DISPLAY_NAME            = 0x1,  
    CANOF_SET_DEFAULT_VALUES            = 0x2,  
    CANOF_VERIFY_FRIEND_ASSEMBLYNAME    = 0x4,  
    CANOF_PARSE_FRIEND_DISPLAY_NAME     =
        CANOF_PARSE_DISPLAY_NAME | CANOF_VERIFY_FRIEND_ASSEMBLYNAME  
  
} CREATE_ASM_NAME_OBJ_FLAGS;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`CANOF_PARSE_DISPLAY_NAME`|Označuje, že předaný parametr je textová identita.|  
|`CANOF_SET_DEFAULT_VALUES`|Nastaví několik výchozích hodnot.|  
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|Ověří pravidlo sestavení přítele (pouze název a veřejný klíč). Tento člen je určen pouze pro interní použití.|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|Kombinace `CANOF_PARSE_DISPLAY_NAME` a `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` příznaky. Tento člen je určen pouze pro interní použití.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).  
  
 **Záhlaví:** Fusion.h  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [IAssemblyName – rozhraní](iassemblyname-interface.md)
- [CreateAssemblyNameObject – funkce](createassemblynameobject-function.md)
- [Výčty fúzí](fusion-enumerations.md)
