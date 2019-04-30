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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aebc6dfe4830e6477cda8fd279b8ef2a8040895c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61914534"
---
# <a name="createasmnameobjflags-enumeration"></a>CREATE_ASM_NAME_OBJ_FLAGS – výčet
Určuje atributy [iassemblyname – rozhraní](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) objektu při jejím vytváření pomocí [createassemblynameobject –](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md) funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|`CANOF_PARSE_DISPLAY_NAME`|Označuje, že je parametr předaný textovou identitu.|  
|`CANOF_SET_DEFAULT_VALUES`|Nastaví několik výchozích hodnot.|  
|`CANOF_VERIFY_FRIEND_ASSEMBLYNAME`|Ověří pravidla sestavení typu friend (pouze název a veřejný klíč). Tento člen je jen pro interní použití.|  
|`CANOF_PARSE_FRIEND_DISPLAY_NAME`|Kombinace `CANOF_PARSE_DISPLAY_NAME` a `CANOF_VERIFY_FRIEND_ASSEMBLYNAME` příznaky. Tento člen je jen pro interní použití.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Fusion.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [IAssemblyName – rozhraní](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)
- [CreateAssemblyNameObject – funkce](../../../../docs/framework/unmanaged-api/fusion/createassemblynameobject-function.md)
- [Výčty pro fúze](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
