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
ms.openlocfilehash: 5c7211fc2523b70313a1e4d4d9d2da0dcecd1d32
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009428"
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
  
|Člen|Description|  
|------------|-----------------|  
|`usMajorVersion`|Hlavní číslo verze odkazovaného sestavení. Tato hodnota nemůže být nulová. Pokud jsou nastaveny všechny bity `usMajorVersion` , není hlavní verze určena.|  
|`usMinorVersion`|Číslo dílčí verze odkazovaného sestavení Tato hodnota nemůže být nulová. Pokud jsou nastaveny všechny bity `usMinorVersion` , není podverze určena.|  
|`usBuildNumber`|Číslo sestavení odkazovaného sestavení Tato hodnota nemůže být nulová. Pokud jsou nastaveny všechny bity `usBuildNumber` , číslo sestavení není zadáno.|  
|`usRevisionNumber`|Číslo revize odkazovaného sestavení Tato hodnota nemůže být nulová. Pokud jsou nastaveny všechny bity `usRevisionNumber` , číslo revize není zadáno.|  
|`szLocale`|Seznam názvů národních prostředí, které odpovídají specifikaci RFC1766, oddělený středníky a určením národních prostředí podporovaných odkazovaným sestavením. Hodnota null označuje nezávislost národního prostředí. **Poznámka:**  Ve .NET Framework verze 1,0 nemůžete zadat více než jedno národní prostředí.|  
|`cbLocale`|Velikost v různých znacích `szLocale` .|  
|`rdwProcessor`|Pole identifikátorů, jak je definováno v souboru Winnt. h pro typy procesorů, které jsou podporovány odkazovaným sestavením. Hodnota NULL označuje nezávislost procesoru.|  
|`ulProcessor`|Délka `rdwProcessor` pole.|  
|`rOS`|Pole instancí [OSINFO –](osinfo-structure.md) určujících operační systémy, které jsou podporovány odkazovaným sestavením. Hodnota NULL označuje nezávislost operačního systému.|  
|`ulOS`|Délka `rOS` pole.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Struktury pro metadata](metadata-structures.md)
- [IMetaDataAssemblyEmit – rozhraní](imetadataassemblyemit-interface.md)
- [OSINFO – struktura](osinfo-structure.md)
