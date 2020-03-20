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
ms.openlocfilehash: 048fe687e4d979576896f5310bddc855b40bb695
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175223"
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
  
|Člen|Popis|  
|------------|-----------------|  
|`dwOSPlatformId`|Jedna z hodnot identifikátorů definovaných `GetVersionEx`funkcí platformy Microsoft Windows . Podporovány jsou následující hodnoty:<br /><br /> - VER_PLATFORM_WIN32s, nebo 0x0000, určit Microsoft Windows 3.1.<br />- VER_PLATFORM_WIN32_WINDOWS nebo 0x0001, chcete-li zadat windows 95, Windows 98 nebo operační systémy pocházející z nich.<br />- VER_PLATFORM_WIN32_NT nebo 0x0002, chcete-li zadat systém Windows NT nebo operační systémy pocházející z něj.|  
|`dwOSMajorVersion`|Hlavní verze operačního systému nebo hodnota NULL označující libovolnou verzi.|  
|`dwOSMinorVersion`|Dílčí verze operačního systému nebo hodnota NULL označující libovolnou verzi.|  
  
## <a name="remarks"></a>Poznámky  
 `OSINFO`Je založen `OSVERSIONINFOEX` na struktuře, která se používá `GetVersionEx`při volání funkce platformy Microsoft Windows . Tato struktura se používá assemblymetadata struktury k označení jeho podporu operačního systému.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Kor.h.  
  
 **Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Struktury pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
