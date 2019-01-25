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
ms.openlocfilehash: 06c9119a2b842a0efcd4af752ba72dbfda03bf13
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54653854"
---
# <a name="stackoverflowtype-enumeration"></a>StackOverflowType – výčet
Obsahuje hodnoty, které označují základní příčiny událost přetečení zásobníku.  
  
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
|`SO_ClrEngine`|Prováděcí modul způsobila přetečení zásobníku.|  
|`SO_Managed`|Spravovaný kód způsobila přetečení zásobníku.|  
|`SO_Other`|Nespravovaný kód způsobila přetečení zásobníku.|  
  
## <a name="remarks"></a>Poznámky  
 Tyto informace se předává k hostiteli volání [iactiononclrevent::ONEVENT –](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [Výčty pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
