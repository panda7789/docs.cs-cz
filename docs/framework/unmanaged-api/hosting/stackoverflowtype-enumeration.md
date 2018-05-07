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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e888b2359336c68ea6fdf52f798145fda12002e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="stackoverflowtype-enumeration"></a>StackOverflowType – výčet
Obsahuje hodnoty, které označují základní příčinu události přetečení zásobníku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`SO_ClrEngine`|Spouštěcí modul způsobila přetečení zásobníku.|  
|`SO_Managed`|Spravovaný kód způsobila přetečení zásobníku.|  
|`SO_Other`|Nespravovaný kód způsobila přetečení zásobníku.|  
  
## <a name="remarks"></a>Poznámky  
 Tato informace je předána na hostitele pomocí volání [iactiononclrevent::ONEVENT –](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) metoda.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
