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
Určuje příznaky pro řízení, které odkazované položky jsou převedeny na jejich definice za účelem optimalizace kódu.  
  
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
|`MDRefToDefDefault`|Určuje, že se odkazy na typy a odkazy členů mají převést na definice. Toto je výchozí hodnota (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).|  
|`MDRefToDefAll`|Určuje, že všechny odkazované položky by měly být převedeny na definice.|  
|`MDRefToDefNone`|Určuje, že žádné odkazované položky by měly být převedeny na definice.|  
|`MDTypeRefToDef`|Určuje, že se mají převést pouze odkazy typu na definice typu.|  
|`MDMemberRefToDef`|Určuje, že by měly být převedeny pouze odkazy členů na definice. To znamená, že odkazy členů by měly být převedeny na buď definice metod, nebo definice polí.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorHdr. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
