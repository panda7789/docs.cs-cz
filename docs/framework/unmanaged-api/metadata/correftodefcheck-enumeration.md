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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5caf432b5de7cb0c8ff0e6f53b3e79a64ecf802e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="correftodefcheck-enumeration"></a>CorRefToDefCheck – výčet
Určuje příznaky tak, aby řízení odkazované položek, které jsou převedeny na jejich definice k optimalizaci kód.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|`MDRefToDefDefault`|Určuje, že odkazy na typ a odkazy na členy mají být převedeny na definice. Toto je výchozí hodnota (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).|  
|`MDRefToDefAll`|Určuje, zda všechny odkazované položky mají být převedeny na definice.|  
|`MDRefToDefNone`|Určuje, že žádné odkazované položky mají být převedeny na definice.|  
|`MDTypeRefToDef`|Určuje, že pouze odkazy na typ měli převést na typ definice.|  
|`MDMemberRefToDef`|Určuje, že mají být převedeny pouze člen odkazy na definice. To znamená odkazy na členy, které mají být převedeny na metoda definice nebo definice polí.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
