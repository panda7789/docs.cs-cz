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
ms.openlocfilehash: da830aaaced179fed642340c33e7b7c37b350aa3
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006555"
---
# <a name="runtime_info_flags-enumeration"></a>RUNTIME_INFO_FLAGS – výčet
Obsahuje hodnoty, které určují, jaké informace o modulu CLR (Common Language Runtime) by měly být vráceny.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
  
|Člen|Description|  
|------------|-----------------|  
|`RUNTIME_INFO_DONT_RETURN_DIRECTORY`|Označuje, že by neměly být zahrnuty informace o adresáři.|  
|`RUNTIME_INFO_DONT_RETURN_VERSION`|Určuje, že by neměly být zahrnuty informace o verzi.|  
|`RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG`|Označuje, že při selhání by se nemělo zobrazovat dialogové okno s chybou.|  
|`RUNTIME_INFO_IGNORE_ERROR_MODE`|Označuje, že účinky volání funkce [SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) s příznakem SEM_FAILCRITICALERRORS by měly být přepsány. To znamená, že při selhání by se mělo zobrazit dialogové okno instalace, místo aby se potlačilo.|  
|`RUNTIME_INFO_REQUEST_AMD64`|Označuje požadavek na informace o verzi modulu runtime kompatibilní s technologií AMD-64.|  
|`RUNTIME_INFO_REQUEST_IA64`|Označuje požadavek na informace o verzi modulu runtime kompatibilního s rozhraním IA-64.|  
|`RUNTIME_INFO_REQUEST_X86`|Označuje požadavek na informace o verzi modulu runtime kompatibilní s platformou x86.|  
|`RUNTIME_INFO_UPGRADE_VERSION`|Označuje, že by měly být zahrnuté informace o upgradu verze.|  
  
## <a name="remarks"></a>Poznámky  
 Následující příznaky architektury platformy lze zadat pouze jednou a nelze je kombinovat:  
  
- RUNTIME_INFO_REQUEST_IA64  
  
- RUNTIME_INFO_REQUEST_AMD64  
  
- RUNTIME_INFO_REQUEST_X86  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** MSCorEE. h  
  
 **Knihovna:** MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Výčty hostování](hosting-enumerations.md)
