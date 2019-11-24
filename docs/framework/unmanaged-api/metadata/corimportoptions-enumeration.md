---
title: CorImportOptions – výčet
ms.date: 03/30/2017
api_name:
- CorImportOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorImportOptions
helpviewer_keywords:
- CorImportOptions enumeration [.NET Framework metadata]
ms.assetid: 4e5d03cb-97c9-4ff4-8dbd-17d94ee374d3
topic_type:
- apiref
ms.openlocfilehash: 44d1776e2902988353ef4fd58aca20e56203b9da
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442844"
---
# <a name="corimportoptions-enumeration"></a>CorImportOptions – výčet
Contains flag values that control the behavior during importation of an assembly outside the current scope.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorImportOptions {  
  
    MDImportOptionDefault                = 0x00000000,  
    MDImportOptionAll                    = 0xFFFFFFFF,  
    MDImportOptionAllTypeDefs            = 0x00000001,  
    MDImportOptionAllMethodDefs          = 0x00000002,  
    MDImportOptionAllFieldDefs           = 0x00000004,  
    MDImportOptionAllProperties          = 0x00000008,  
    MDImportOptionAllEvents              = 0x00000010,  
    MDImportOptionAllCustomAttributes    = 0x00000020,  
    MDImportOptionAllExportedTypes       = 0x00000040  
  
} CorImportOptions;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`MDImportOptionDefault`|Indicates the default behavior, which is to skip deleted records.|  
|`MDImportOptionAll`|Indicates that all metadata should be enumerated.|  
|`MDImportOptionAllTypeDefs`|Indicates that all TypeDefs, including deleted ones, should be enumerated.|  
|`MDImportOptionAllMethodDefs`|Indicates that all MethodDefs, including deleted ones, should be enumerated.|  
|`MDImportOptionAllFieldDefs`|Indicates that all FieldDefs, including deleted ones, should be enumerated.|  
|`MDImportOptionAllProperties`|Indicates that all PropertyDefs, including deleted ones, should be enumerated.|  
|`MDImportOptionAllEvents`|Indicates that all EventDefs, including deleted ones, should be enumerated.|  
|`MDImportOptionAllCustomAttributes`|Indicates that all custom attributes, including deleted ones, should be enumerated.|  
|`MDImportOptionAllExportedTypes`|Indicates that all exported types, including deleted ones, should be enumerated.|  
  
## <a name="requirements"></a>Požadavky  
 **Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorHdr.h  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
