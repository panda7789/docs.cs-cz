---
title: CorRefToDefCheck – výčet
ms.date: 03/30/2017
api_name:
- CorRefToDefCheck
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRefToDefCheck
helpviewer_keywords:
- CorRefToDefCheck enumeration [.NET Framework metadata]
ms.assetid: f9a80f1a-55af-4459-b095-8441aae16119
topic_type:
- apiref
ms.openlocfilehash: e6c3c9b842bd823e8975661964480fd801779b2d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450131"
---
# <a name="correftodefcheck-enumeration"></a>CorRefToDefCheck – výčet
Specifies flags to control which referenced items are converted to their definitions in order to optimize the code.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorRefToDefCheck {  
    MDRefToDefDefault           = 0x00000003,  
    MDRefToDefAll               = 0xffffffff,  
    MDRefToDefNone              = 0x00000000,  
    MDTypeRefToDef              = 0x00000001,  
    MDMemberRefToDef            = 0x00000002  
} CorRefToDefCheck;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`MDRefToDefDefault`|Specifies that type references and member references should be converted to definitions. This is the default value (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).|  
|`MDRefToDefAll`|Specifies that all referenced items should be converted to definitions.|  
|`MDRefToDefNone`|Specifies that no referenced items should be converted to definitions.|  
|`MDTypeRefToDef`|Specifies that only type references should be converted to type definitions.|  
|`MDMemberRefToDef`|Specifies that only member references should be converted to definitions. That is, member references should be converted to either method definitions or field definitions.|  
  
## <a name="requirements"></a>Požadavky  
 **Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorHdr.h  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
