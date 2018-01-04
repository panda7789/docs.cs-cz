---
title: "OSINFO – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: OSINFO
api_location: mscoree.dll
api_type: COM
f1_keywords: OSINFO
helpviewer_keywords: OSINFO structure [.NET Framework metadata]
ms.assetid: fac7b480-7adb-4450-a5e9-690fed81ffae
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dd30fe7904fa6c0685dd9c39931cc545e4e30583
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="osinfo-structure"></a>OSINFO – struktura
Obsahuje podrobné informace o operačním systému pro modul nebo sestavení.  
  
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
|`dwOSPlatformId`|Jedna z hodnot identifikátoru definovaných funkcí platformy Microsoft Windows `GetVersionEx`. Podporovány jsou následující hodnoty:<br /><br /> -VER_PLATFORM_WIN32s, nebo 0x0000, zadejte systému Windows 3.1.<br />-VER_PLATFORM_WIN32_WINDOWS, nebo 0x0001, a zadejte systému Windows 95, Windows 98 nebo operační systémy jejich následníky.<br />-VER_PLATFORM_WIN32_NT, nebo 0x0010, určete systému Windows NT nebo operační systémy jeho následníky.|  
|`dwOSMajorVersion`|Hlavní verze operačního systému, nebo hodnota NULL označíte, všechny verze.|  
|`dwOSMinorVersion`|Podverze operačního systému, nebo hodnota NULL označíte, všechny verze.|  
  
## <a name="remarks"></a>Poznámky  
 `OSINFO`je založena na `OSVERSIONINFOEX` struktury tedy použité ve volání funkce platformy Microsoft Windows `GetVersionEx`. Tato struktura je pomocí assemblymetadata – struktura slouží k určení jeho podporu operačního systému.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Struktury pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
