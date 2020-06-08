---
title: OSINFO – struktura
ms.date: 03/30/2017
api_name:
- OSINFO
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- OSINFO
helpviewer_keywords:
- OSINFO structure [.NET Framework metadata]
ms.assetid: fac7b480-7adb-4450-a5e9-690fed81ffae
topic_type:
- apiref
ms.openlocfilehash: ab9d7eb6f5760b43fe805443bbe1ea4a95c72069
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501063"
---
# <a name="osinfo-structure"></a>OSINFO – struktura
Obsahuje podrobnosti o operačním systému pro sestavení nebo modul.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;
    DWORD   dwOSMinorVersion;
} OSINFO;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Description|  
|------------|-----------------|  
|`dwOSPlatformId`|Jedna z hodnot identifikátoru definovaná funkcí platformy Microsoft Windows `GetVersionEx` Podporovány jsou následující hodnoty:<br /><br /> -VER_PLATFORM_WIN32s nebo 0x0000, pokud chcete zadat Microsoft Windows 3,1.<br />-VER_PLATFORM_WIN32_WINDOWS nebo 0x0001, chcete-li určit systémy Windows 95, Windows 98 nebo operační systémy, které jsou z nich pořízené.<br />-VER_PLATFORM_WIN32_NT nebo 0x0002, chcete-li určit systémy Windows NT nebo operační systémy, které jsou z něj pořízené.|  
|`dwOSMajorVersion`|Hlavní verze operačního systému nebo hodnota NULL k označení libovolné verze.|  
|`dwOSMinorVersion`|Dílčí verze operačního systému nebo hodnota NULL k označení libovolné verze.|  
  
## <a name="remarks"></a>Poznámky  
 `OSINFO`vychází ze `OSVERSIONINFOEX` struktury používané při volání funkce platformy Microsoft Windows `GetVersionEx` . Tato struktura je používána strukturou AssemblyMetadata – k označení podpory operačního systému.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro metadata](metadata-structures.md)
- [IMetaDataAssemblyEmit – rozhraní](imetadataassemblyemit-interface.md)
