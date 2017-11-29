---
title: "ASSEMBLYMETADATA – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ASSEMBLYMETADATA
api_location: mscoree.dll
api_type: COM
f1_keywords: ASSEMBLYMETADATA
helpviewer_keywords: ASSEMBLYMETADATA structure [.NET Framework metadata]
ms.assetid: 1af98e57-9145-4d35-bb78-77d1da7c91a5
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5652907abc17868414c554cb5c87b0856d2c5a0c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="assemblymetadata-structure"></a>ASSEMBLYMETADATA – struktura
Obsahuje informace o odkazované sestavení, včetně jeho verzi a jeho úrovně podpory pro národní prostředí, procesory a operační systémy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct {  
    USHORT  usMajorVersion;  
    USHORT  usMinorVersion;  
    USHORT  usBuildNumber;  
    USHORT  usRevisionNumber;  
    LPWSTR  szLocale;  
    ULONG   cbLocale;  
    DWORD*  rdwProcessor[];  
    ULONG   ulProcessor  
    OSINFO* rOS[];  
    ULONG   ulOS;  
} ASSEMBLYMETADATA;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`usMajorVersion`|Hlavní číslo verze odkazované sestavení. Tato hodnota nemůže být nula. Pokud všechny bity `usMajorVersion` jsou nastavené, není zadán hlavní verzi.|  
|`usMinorVersion`|Číslo podverze odkazované sestavení. Tato hodnota nemůže být nula. Pokud všechny bity `usMinorVersion` jsou nastavené na podverzi není zadán.|  
|`usBuildNumber`|Číslo sestavení odkazované sestavení. Tato hodnota nemůže být nula. Pokud všechny bity `usBuildNumber` jsou nastavené, číslo sestavení není zadán.|  
|`usRevisionNumber`|Číslo revize odkazované sestavení. Tato hodnota nemůže být nula. Pokud všechny bity `usRevisionNumber` jsou nastavené, číslo revize není zadán.|  
|`szLocale`|Seznam názvů národní prostředí podle specifikace RFC1766, oddělené středníky, zadání národní prostředí nepodporuje odkazované sestavení. Hodnota null určuje nezávislost národního prostředí. **Poznámka:** v rozhraní .NET Framework verze 1.0 nelze zadat více než jeden národního prostředí.|  
|`cbLocale`|Velikost v široké znaky `szLocale`.|  
|`rdwProcessor`|Pole identifikátory, jak jsou definovány v souboru Winnt.h, pro typy procesoru, které jsou podporovány odkazované sestavení. Hodnota NULL určuje nezávislost procesoru.|  
|`ulProcessor`|Délka `rdwProcessor` pole.|  
|`rOS`|Pole [osinfo –](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md) instance zadání operační systémy, které jsou podporovány odkazované sestavení. Hodnota NULL znamená nezávislost operačního systému.|  
|`ulOS`|Délka `rOS` pole.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** používat jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Struktury metadat](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)  
 [Imetadataassemblyemit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)  
 [Osinfo – struktura](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md)
