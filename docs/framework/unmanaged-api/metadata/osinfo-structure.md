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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0aba49fb4a60b2e471c541a8d8531a1cbc8627f9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775197"
---
# <a name="osinfo-structure"></a>OSINFO – struktura
Obsahuje podrobnosti o operačním systému pro sestavení nebo modulu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct {  
    DWORD   dwOSPlatformId;  
    DWORD   dwOSMajorVersion;   
    DWORD   dwOSMinorVersion;   
} OSINFO;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`dwOSPlatformId`|Jedna z hodnot identifikátoru definovaných funkcí platformy Microsoft Windows `GetVersionEx`. Podporovány jsou následující hodnoty:<br /><br /> -VER_PLATFORM_WIN32s, nebo 0x0000, chcete-li určit instalační služba systému Windows 3.1.<br />-VER_PLATFORM_WIN32_WINDOWS, nebo 0x0001, zadejte operační systémy Windows 95, Windows 98 nebo který z nich.<br />-VER_PLATFORM_WIN32_NT, nebo změnu 0x0010, Windows NT nebo operační systémy, který z něj.|  
|`dwOSMajorVersion`|Hlavní verze operačního systému, nebo hodnota NULL označuje všechny verze.|  
|`dwOSMinorVersion`|Podverze operačního systému, nebo hodnota NULL označuje všechny verze.|  
  
## <a name="remarks"></a>Poznámky  
 `OSINFO` vychází `OSVERSIONINFOEX` struktury, který je použité ve volání funkce platformy Microsoft Windows `GetVersionEx`. Tato struktura používá assemblymetadata – struktura označující jeho podporu operačního systému.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
