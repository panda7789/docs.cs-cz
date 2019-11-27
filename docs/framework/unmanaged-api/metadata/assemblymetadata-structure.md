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
ms.openlocfilehash: 24ec1f7d553a59425f7eb02af8e91010d940eb07
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444265"
---
# <a name="assemblymetadata-structure"></a>ASSEMBLYMETADATA – struktura
Obsahuje informace o odkazovaném sestavení, včetně jeho verze a jeho úrovně podpory pro národní prostředí, procesory a operační systémy.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
|`usMajorVersion`|Hlavní číslo verze odkazovaného sestavení. Tato hodnota nemůže být nulová. Pokud jsou nastaveny všechny bity `usMajorVersion`, není určena hlavní verze.|  
|`usMinorVersion`|Číslo dílčí verze odkazovaného sestavení Tato hodnota nemůže být nulová. Pokud jsou nastaveny všechny bity `usMinorVersion`, není určena vedlejší verze.|  
|`usBuildNumber`|Číslo sestavení odkazovaného sestavení Tato hodnota nemůže být nulová. Pokud jsou nastaveny všechny bity `usBuildNumber`, číslo sestavení není zadáno.|  
|`usRevisionNumber`|Číslo revize odkazovaného sestavení Tato hodnota nemůže být nulová. Pokud jsou nastaveny všechny bity `usRevisionNumber`, číslo revize není zadáno.|  
|`szLocale`|Seznam názvů národních prostředí, které odpovídají specifikaci RFC1766, oddělený středníky a určením národních prostředí podporovaných odkazovaným sestavením. Hodnota null označuje nezávislost národního prostředí. **Poznámka:**  Ve .NET Framework verze 1,0 nemůžete zadat více než jedno národní prostředí.|  
|`cbLocale`|Velikost v různých znacích `szLocale`.|  
|`rdwProcessor`|Pole identifikátorů, jak je definováno v souboru Winnt. h pro typy procesorů, které jsou podporovány odkazovaným sestavením. Hodnota NULL označuje nezávislost procesoru.|  
|`ulProcessor`|Délka pole `rdwProcessor`.|  
|`rOS`|Pole instancí [OSINFO –](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md) určujících operační systémy, které jsou podporovány odkazovaným sestavením. Hodnota NULL označuje nezávislost operačního systému.|  
|`ulOS`|Délka pole `rOS`.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-structures.md)
- [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
- [OSINFO – struktura](../../../../docs/framework/unmanaged-api/metadata/osinfo-structure.md)
