---
title: CorRegFlags – výčet
ms.date: 03/30/2017
api_name:
- CorRegFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRegFlags
helpviewer_keywords:
- CorRegFlags enumeration [.NET Framework metadata]
ms.assetid: 8d3080ee-39fe-4c57-8950-51323632d045
topic_type:
- apiref
ms.openlocfilehash: 79a9e4513a98a29edc11cc76c599f03c9c3a72b4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450109"
---
# <a name="corregflags-enumeration"></a>CorRegFlags – výčet
Provides flag values used for registration when installing a module or composite image.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum   
{  
    regNoCopy  = 0x00000001,  
    regConfig  = 0x00000002,  
    regHasRefs = 0x00000004  
} CorRegFlags;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`regNoCopy`|Specifies that files should not be copied into the destination.|  
|`regConfig`|Specifies that the module or composite is a configuration.|  
|`regHasRefs`|Specifies that the module or composite has class references.|  
  
## <a name="requirements"></a>Požadavky  
 **Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** Cor.h  
  
 **Library:** Included as a resource in MsCorEE.dll  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
