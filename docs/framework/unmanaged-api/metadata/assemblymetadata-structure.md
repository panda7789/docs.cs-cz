---
title: ASSEMBLYMETADATA – struktura
ms.date: 03/30/2017
api_name:
- ASSEMBLYMETADATA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ASSEMBLYMETADATA
helpviewer_keywords:
- ASSEMBLYMETADATA structure [.NET Framework metadata]
ms.assetid: 1af98e57-9145-4d35-bb78-77d1da7c91a5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8f0a9b9c149c86b4d9121275aa858dfdc0cdbac7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59195160"
---
# <a name="assemblymetadata-structure"></a>ASSEMBLYMETADATA – struktura
Obsahuje informace o odkazovaném sestavení, včetně jeho verze a jeho úroveň podpory pro národní prostředí, procesory a operační systémy.  
  
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
|`usMajorVersion`|Číslo hlavní verze odkazovaného sestavení. Tato hodnota nemůže být nula. Pokud všechny bity `usMajorVersion` je nastaveno, hlavní verze není zadán.|  
|`usMinorVersion`|Číslo podverze odkazovaného sestavení. Tato hodnota nemůže být nula. Pokud všechny bity `usMinorVersion` je nastaveno, vedlejší verze není zadán.|  
|`usBuildNumber`|Číslo sestavení odkazovaného sestavení. Tato hodnota nemůže být nula. Pokud všechny bity `usBuildNumber` je nastaveno, není určeno číslo sestavení.|  
|`usRevisionNumber`|Číslo revize odkazovaného sestavení. Tato hodnota nemůže být nula. Pokud všechny bity `usRevisionNumber` je nastaveno, není určeno číslo revize.|  
|`szLocale`|Seznam názvů národních prostředí, který odpovídá specifikaci RFC1766 oddělené středníkem, určení národních prostředí podporovaných odkazovaných sestavení. Hodnota null znamená nezávislost národní prostředí. **Poznámka:**  V rozhraní .NET Framework verze 1.0 nelze zadat více než jedno prostředí.|  
|`cbLocale`|Velikost v širokých znaků `szLocale`.|  
|`rdwProcessor`|Pole identifikátory, jak jsou definovány v souboru Winnt.h, pro typy procesorů, které jsou podporovány odkazovaném sestavení. Hodnota NULL znamená nezávislost procesoru.|  
|`ulProcessor`|Délka `rdwProcessor` pole.|  
|`rOS`|Pole [osinfo –](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md) instance zadání operační systémy, které jsou podporovány odkazovaném sestavení. Hodnota NULL znamená nezávislost operačního systému.|  
|`ulOS`|Délka `rOS` pole.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury metadat](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [OSINFO – struktura](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md)
