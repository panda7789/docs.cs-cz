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
ms.openlocfilehash: ce6f5993b9c1aeb63e121b3567ee468cea1c9318
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007517"
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
  
|Člen|Description|  
|------------|-----------------|  
|`MDRefToDefDefault`|Určuje, že se odkazy na typy a odkazy členů mají převést na definice. Toto je výchozí hodnota ( `MDTypeRefToDef` &#124; `MDMemberRefToDef` ).|  
|`MDRefToDefAll`|Určuje, že všechny odkazované položky by měly být převedeny na definice.|  
|`MDRefToDefNone`|Určuje, že žádné odkazované položky by měly být převedeny na definice.|  
|`MDTypeRefToDef`|Určuje, že se mají převést pouze odkazy typu na definice typu.|  
|`MDMemberRefToDef`|Určuje, že by měly být převedeny pouze odkazy členů na definice. To znamená, že odkazy členů by měly být převedeny na buď definice metod, nebo definice polí.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorHdr. h  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Výčty pro metadata](metadata-enumerations.md)
