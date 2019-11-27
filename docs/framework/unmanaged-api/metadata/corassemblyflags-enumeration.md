---
title: CorAssemblyFlags – výčet
ms.date: 03/30/2017
api_name:
- CorAssemblyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorAssemblyFlags
helpviewer_keywords:
- CorAssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: bb8db3b6-d81d-49fc-b74c-dbc908a9eab9
topic_type:
- apiref
ms.openlocfilehash: fda890cee5f513ea8cf7e82e710f5451a860c49f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443906"
---
# <a name="corassemblyflags-enumeration"></a>CorAssemblyFlags – výčet
Obsahuje hodnoty, které popisují metadata použitá pro kompilaci sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorAssemblyFlags {  
  
    afPublicKey             =   0x0001,  
    afPA_None               =   0x0000,  
    afPA_MSIL               =   0x0010,  
    afPA_x86                =   0x0020,  
    afPA_IA64               =   0x0030,  
    afPA_AMD64              =   0x0040,  
    afPA_ARM                =   0x0050,  
    afPA_NoPlatform         =   0x0070,  
    afPA_Specified          =   0x0080,  
    afPA_Mask               =   0x0070,  
    afPA_FullMask           =   0x00F0,  
    afPA_Shift              =   0x0004,  
  
    afEnableJITcompileTracking  =   0x8000,  
    afDisableJITcompileOptimizer=   0x4000,  
  
    afRetargetable          =   0x0100,  
    afContentType_Default        =   0x0000,  
    afContentType_WindowsRuntime =   0x0200,  
    afContentType_Mask           =   0x0E00,  
  
} CorAssemblyFlags;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`afPublicKey`|Označuje, že odkaz na sestavení obsahuje úplný, nehashový veřejný klíč.|  
|`afPA_None`|Označuje, že není určena architektura procesoru.|  
|`afPA_MSIL`|Označuje, že architektura procesoru je neutrální (PE32).|  
|`afPA_x86`|Označuje, že architektura procesoru je x86 (PE32).|  
|`afPA_IA64`|Indikuje, že architektura procesoru je Itanium (PE32 +).|  
|`afPA_AMD64`|Označuje, že architektura procesoru je AMD x64 (PE32 +).|  
|`afPA_ARM`|Indikuje, že architektura procesoru je ARM (PE32).|  
|`afPA_NoPlatform`|Indikuje, že sestavení je referenční sestavení; To znamená, že se vztahuje na všechny architektury, ale nelze je spustit v žádné architektuře. Proto příznak je stejný jako `afPA_Mask`.|  
|`afPA_Specified`|Indikuje, že by se měly rozšířit příznaky architektury procesoru na záznam `AssemblyRef`.|  
|`afPA_Mask`|Maska, která popisuje architekturu procesoru.|  
|`afPA_FullMask`|Určuje, že je zahrnutý popis architektury procesoru.|  
|`afPA_Shift`|Označuje počet posunutí v příznacích architektury procesoru na a z indexu.|  
|`afEnableJITcompileTracking`|Určuje odpovídající hodnotu z <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> <xref:System.Diagnostics.DebuggableAttribute>.|  
|`afDisableJITcompileOptimizer`|Určuje odpovídající hodnotu z <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> <xref:System.Diagnostics.DebuggableAttribute>.|  
|`afRetargetable`|Označuje, že sestavení může být v době běhu znovu cíleno na sestavení z jiného vydavatele.|  
|`afContentType_Mask`|Maska, která popisuje typ obsahu.|  
|`afContentType_Default`|Označuje výchozí typ obsahu.|  
|`afContentType_WindowsRuntime`|Určuje typ obsahu prostředí Windows Runtime.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorHdr. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
