---
title: AssemblyRefFlags – výčet
ms.date: 03/30/2017
api_name:
- AssemblyRefFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyRefFlags
helpviewer_keywords:
- AssemblyRefFlags enumeration [.NET Framework metadata]
ms.assetid: decd4f46-f3b2-466f-9501-e74f2b86b846
topic_type:
- apiref
ms.openlocfilehash: 23d293a87112c62cb2127b435faeca258a7de226
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444220"
---
# <a name="assemblyrefflags-enumeration"></a>AssemblyRefFlags – výčet
Contains values that describe features of an assembly reference.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    arfFullOriginator = 0x0001  
} AssemblyRefFlags;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`arfFullOriginator`|Specifies that the assembly reference contains full, unhashed information about the publisher of the assembly.|  
  
## <a name="requirements"></a>Požadavky  
 **Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** Cor.h  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [DefineAssemblyRef – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-defineassemblyref-method.md)
