---
title: "RUNTIME_INFO_FLAGS – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: RUNTIME_INFO_FLAGS
api_location: mscoree.dll
api_type: COM
f1_keywords: RUNTIME_INFO_FLAGS
helpviewer_keywords: RUNTIME_INFO_FLAGS enumeration [.NET Framework hosting]
ms.assetid: adba37be-f775-4cdb-8919-5746ce694f33
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d050972857ba652ae0b40727260f681c383208b0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="runtimeinfoflags-enumeration"></a>RUNTIME_INFO_FLAGS – výčet
Obsahuje hodnoty, které označují, jaké informace o common language runtime (CLR) má být vrácen.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
  
    RUNTIME_INFO_UPGRADE_VERSION             = 0x01,  
    RUNTIME_INFO_REQUEST_IA64                = 0x02,  
    RUNTIME_INFO_REQUEST_AMD64               = 0x04,  
    RUNTIME_INFO_REQUEST_X86                 = 0x08,  
    RUNTIME_INFO_DONT_RETURN_DIRECTORY       = 0x10,  
    RUNTIME_INFO_DONT_RETURN_VERSION         = 0x20,  
    RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG      = 0x40,  
    RUNTIME_INFO_IGNORE_ERROR_MODE           = 0x1000  
  
} RUNTIME_INFO_FLAGS;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`RUNTIME_INFO_DONT_RETURN_DIRECTORY`|Označuje, že informací v adresáři nesmí být zahrnuty.|  
|`RUNTIME_INFO_DONT_RETURN_VERSION`|Označuje, že informace o verzi, neměl by zahrnovat.|  
|`RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG`|Označuje, že by neměla zobrazit dialogové okno chyby při selhání.|  
|`RUNTIME_INFO_IGNORE_ERROR_MODE`|Určuje, že důsledky volání [SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkId=255242) funkce s příznakem SEM_FAILCRITICALERRORS by měla být potlačena. To znamená dialogové okno instalace se mají při selhání, místo potlačeny.|  
|`RUNTIME_INFO_REQUEST_AMD64`|Určuje žádost o informace o AMD-64-compatible verzi modulu runtime.|  
|`RUNTIME_INFO_REQUEST_IA64`|Určuje žádost o informace o IA-64-compatible verzi modulu runtime.|  
|`RUNTIME_INFO_REQUEST_X86`|Určuje žádost o informace o x86 kompatibilní verzi modulu runtime.|  
|`RUNTIME_INFO_UPGRADE_VERSION`|Označuje, že informace o upgradu verze by měly být zahrnuty.|  
  
## <a name="remarks"></a>Poznámky  
 Následující příznaky Architektura platformy může být zadaná jenom jedna najednou a nelze jej kombinovat:  
  
-   RUNTIME_INFO_REQUEST_IA64  
  
-   RUNTIME_INFO_REQUEST_AMD64  
  
-   RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
