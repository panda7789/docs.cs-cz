---
title: CorMethodSemanticsAttr – výčet
ms.date: 03/30/2017
api_name:
- CorMethodSemanticsAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodSemanticsAttr
helpviewer_keywords:
- CorMethodSemanticsAttr enumeration [.NET Framework metadata]
ms.assetid: ca2af325-eb9d-4a91-90e4-267e45b98611
topic_type:
- apiref
ms.openlocfilehash: bab215a8221696a0e43e228278085fcef52a40e9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442820"
---
# <a name="cormethodsemanticsattr-enumeration"></a>CorMethodSemanticsAttr – výčet
Contains values that describe the relationship between a method and an associated property or event.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorMethodSemanticsAttr {  
  
    msSetter    =   0x0001,  
    msGetter    =   0x0002,  
    msOther     =   0x0004,  
    msAddOn     =   0x0008,  
    msRemoveOn  =   0x0010,  
    msFire      =   0x0020,  
  
} CorMethodSemanticsAttr;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`msSetter`|Specifies that the method is a `set` accessor for a property.|  
|`msGetter`|Specifies that the method is a `get` accessor for a property.|  
|`msOther`|Specifies that the method has a relationship to a property or an event other than those defined here.|  
|`msAddOn`|Specifies that the method adds handler methods for an event.|  
|`msRemoveOn`|Specifies that the method removes handler methods for an event.|  
|`msFire`|Specifies that the method raises an event.|  
  
## <a name="requirements"></a>Požadavky  
 **Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorHdr.h  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
