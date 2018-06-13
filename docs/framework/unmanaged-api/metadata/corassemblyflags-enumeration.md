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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9d6ec37bbd8750c27a41b5f18180c7726cdcd483
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33442828"
---
# <a name="corassemblyflags-enumeration"></a>CorAssemblyFlags – výčet
Obsahuje hodnoty, které popisují metadata použít sestavení kompilace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|`afPublicKey`|Označuje, že odkaz na sestavení obsahuje veřejný klíč, úplné a bez otisku.|  
|`afPA_None`|Označuje, že neurčené na architektuře procesoru.|  
|`afPA_MSIL`|Označuje, že je na architektuře procesoru neutrální (PE32).|  
|`afPA_x86`|Označuje, že je na architektuře procesoru x86 (PE32).|  
|`afPA_IA64`|Označuje, že je na architektuře procesoru pro procesory Itanium (PE32 +).|  
|`afPA_AMD64`|Označuje, že je na architektuře procesoru AMD X64 (PE32 +).|  
|`afPA_ARM`|Označuje, že je na architektuře procesoru ARM (PE32).|  
|`afPA_NoPlatform`|Označuje, že je sestavení referenční sestavení při; To znamená platí pro všechny architektura však nelze spustit na jakékoli architektuře. Proto příznak je stejný jako `afPA_Mask`.|  
|`afPA_Specified`|Označuje, že příznaky architektura procesoru by mělo být předáno `AssemblyRef` záznamu.|  
|`afPA_Mask`|Maska, která popisuje architekturu procesoru.|  
|`afPA_FullMask`|Určuje, že je zahrnuté popis architekturu procesoru.|  
|`afPA_Shift`|Určuje počet posunutí v příznaky architektura procesoru do a z indexu.|  
|`afEnableJITcompileTracking`|Určuje odpovídající hodnotu z <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> z <xref:System.Diagnostics.DebuggableAttribute>.|  
|`afDisableJITcompileOptimizer`|Určuje odpovídající hodnotu z <xref:System.Diagnostics.DebuggableAttribute.DebuggingModes> z <xref:System.Diagnostics.DebuggableAttribute>.|  
|`afRetargetable`|Označuje, že sestavení může být v době běhu změnit cíl na necílené sestavení z jiného vydavatele.|  
|`afContentType_Mask`|Maska, která popisuje typ obsahu.|  
|`afContentType_Default`|Určuje výchozí typ obsahu.|  
|`afContentType_WindowsRuntime`|Určuje, [!INCLUDE[wrt](../../../../includes/wrt-md.md)] typ obsahu.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
