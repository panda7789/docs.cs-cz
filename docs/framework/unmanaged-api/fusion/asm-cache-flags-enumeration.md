---
title: ASM_CACHE_FLAGS – výčet
ms.date: 03/30/2017
api_name:
- ASM_CACHE_FLAGS
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- ASM_CACHE_FLAGS
helpviewer_keywords:
- ASM_CACHE_FLAGS enumeration [.NET Framework fusion]
ms.assetid: 82e9a7da-321b-48b8-b239-52eaffda6be8
topic_type:
- apiref
ms.openlocfilehash: 85ac976daec8fd76ee21012a30611235609f4b34
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109495"
---
# <a name="asm_cache_flags-enumeration"></a>ASM_CACHE_FLAGS – výčet
Určuje zdroj sestavení, který je reprezentován [IAssemblyCacheItem](iassemblycacheitem-interface.md) v globální mezipaměti sestavení (GAC).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    ASM_CACHE_ZAP       = 0x01,  
    ASM_CACHE_GAC       = 0x02,  
    ASM_CACHE_DOWNLOAD  = 0x04,  
    ASM_CACHE_ROOT      = 0x08,  
    ASM_CACHE_ROOT_EX   = 0x80  
} ASM_CACHE_FLAGS;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`ASM_CACHE_ZAP`|Vytvoří výčet mezipaměti předkompilovaných sestavení pomocí nástroje Ngen. exe.|  
|`ASM_CACHE_GAC`|Vytvoří výčet globální mezipaměti sestavení (GAC).|  
|`ASM_CACHE_DOWNLOAD`|Vytvoří výčet sestavení, která byla stažena na vyžádání nebo která byla Stínově zkopírována.|  
|`ASM_CACHE_ROOT`|Označuje, že funkce [GetCachePath –](getcachepath-function.md) by měla vracet cestu k globální mezipaměti sestavení (Common Language Runtime) verze 2,0. Smysluplný pouze v kontextu volání [GetCachePath –](getcachepath-function.md).|  
|`ASM_CACHE_ROOT_EX`|Označuje, že funkce [GetCachePath –](getcachepath-function.md) by měla vracet cestu k globální mezipaměti sestavení pro CLR verze 4. Smysluplný pouze v kontextu volání [GetCachePath –](getcachepath-function.md).|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Fusion. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [GetCachePath – funkce](getcachepath-function.md)
- [IAssemblyCacheItem – rozhraní](iassemblycacheitem-interface.md)
- [Výčty pro fúze](fusion-enumerations.md)
