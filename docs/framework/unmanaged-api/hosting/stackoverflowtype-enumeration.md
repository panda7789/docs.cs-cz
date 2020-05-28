---
title: StackOverflowType – výčet
ms.date: 03/30/2017
api_name:
- StackOverflowType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StackOverflowType
helpviewer_keywords:
- StackOverflowType enumeration [.NET Framework hosting]
ms.assetid: dab648ad-972b-479c-b129-b4c1dcbd932e
topic_type:
- apiref
ms.openlocfilehash: f399d33dbe05cb5768aa45533ef30d28409e18e2
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006464"
---
# <a name="stackoverflowtype-enumeration"></a>StackOverflowType – výčet
Obsahuje hodnoty, které indikují základní příčinu události přetečení zásobníku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Description|  
|------------|-----------------|  
|`SO_ClrEngine`|Přetečení zásobníku bylo způsobené prováděcím modulem.|  
|`SO_Managed`|Přetečení zásobníku bylo způsobeno spravovaným kódem.|  
|`SO_Other`|Přetečení zásobníku bylo způsobeno nespravovaným kódem.|  
  
## <a name="remarks"></a>Poznámky  
 Tyto informace jsou předány hostiteli prostřednictvím volání metody [IActionOnCLREvent –::](iactiononclrevent-onevent-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Výčty hostování](hosting-enumerations.md)
