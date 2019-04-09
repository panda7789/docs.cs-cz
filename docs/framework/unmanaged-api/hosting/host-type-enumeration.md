---
title: HOST_TYPE – výčet
ms.date: 03/30/2017
api_name:
- HOST_TYPE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- HOST_TYPE
helpviewer_keywords:
- HOST_TYPE enumeration [.NET Framework hosting]
ms.assetid: 51f848be-84c5-4036-9839-c762c576bbf5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dfb1cff3e95c5ff86d22913745b7d14982766b48
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59175224"
---
# <a name="hosttype-enumeration"></a>HOST_TYPE – výčet
Obsahuje hodnoty, které určují typ hostitele, který spouští aplikaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    HOST_TYPE_DEFAULT     = 0x0,  
    HOST_TYPE_APPLAUNCH   = 0x1,  
    HOST_TYPE_CORFLAG     = 0x2  
} HOST_TYPE;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`HOST_TYPE_APPLAUNCH`|Spuštění aplikace z AppLaunch.exe.<br /><br /> Používejte tuto hodnotu pro částečně důvěryhodné aplikace.|  
|`HOST_TYPE_CORFLAG`|Spusťte aplikaci přímo. To znamená spusťte aplikaci z vlastního souboru .exe.<br /><br /> Používejte tuto hodnotu pro plně důvěryhodné aplikace.|  
|`HOST_TYPE_DEFAULT`|Stejné jako HOST_TYPE_APPLAUNCH.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
