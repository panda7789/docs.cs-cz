---
title: RUNTIME_INFO_FLAGS – výčet
ms.date: 03/30/2017
api_name:
- RUNTIME_INFO_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- RUNTIME_INFO_FLAGS
helpviewer_keywords:
- RUNTIME_INFO_FLAGS enumeration [.NET Framework hosting]
ms.assetid: adba37be-f775-4cdb-8919-5746ce694f33
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9483cf8671b7d3ad5430081d93925af30b3d8368
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215682"
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
|`RUNTIME_INFO_DONT_RETURN_DIRECTORY`|Označuje, že informace o adresáři by neměl být zahrnuty.|  
|`RUNTIME_INFO_DONT_RETURN_VERSION`|Označuje, že by neměl být zahrnuty informace o verzi.|  
|`RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG`|Určuje, že dialogové okno chyby by neměl být zobrazeny nebude úspěšná.|  
|`RUNTIME_INFO_IGNORE_ERROR_MODE`|Označuje, že efekty volání [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242) funkce s příznakem SEM_FAILCRITICALERRORS by měla být potlačena. To znamená dialogové okno instalace, které mají být zobrazeny po selhání, místo potlačeny.|  
|`RUNTIME_INFO_REQUEST_AMD64`|Označuje žádost o informace o AMD-64kompatibilní verzi modulu runtime.|  
|`RUNTIME_INFO_REQUEST_IA64`|Označuje žádost o informace o IA-64kompatibilní verzi modulu runtime.|  
|`RUNTIME_INFO_REQUEST_X86`|Označuje žádost o informace o x86 kompatibilní verzi modulu runtime.|  
|`RUNTIME_INFO_UPGRADE_VERSION`|Označuje, že informace o upgradu verze by měly být zahrnuty.|  
  
## <a name="remarks"></a>Poznámky  
 Následující příznaky Architektura platformy může být zadaný jenom jeden po druhém a nelze kombinovat:  
  
-   RUNTIME_INFO_REQUEST_IA64  
  
-   RUNTIME_INFO_REQUEST_AMD64  
  
-   RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MSCorEE.h  
  
 **Knihovna:** MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
