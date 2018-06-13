---
title: AssemblyFlags – výčet
ms.date: 03/30/2017
api_name:
- AssemblyFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyFlags
helpviewer_keywords:
- AssemblyFlags enumeration [.NET Framework metadata]
ms.assetid: 40f9bd9e-16ec-447e-81b0-168c875e9866
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2fc6d08e960b0ba82c76945a318ec723546f71b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444903"
---
# <a name="assemblyflags-enumeration"></a>AssemblyFlags – výčet
Obsahuje hodnoty, které popisují funkce běhové sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    afImplicitExportedTypes = 0x0001,  
    afImplicitResources = 0x0002,  
    afNonSideBySideAppDomain = 0x0010,  
    afNonSideBySideProcess = 0x0020,  
    afNonSideBySideMachine = 0x0030  
} AssemblyFlags;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`afImplicitExportedTypes`|Určuje, že jsou definice exportovaný typu implicitní v souborech, které tvoří sestavení. V rozhraní .NET Framework verze 1.0 a 1.1 Tato hodnota je vždy předpokládá, že pokud chcete nastavit.|  
|`afImplicitResources`|Určuje, že jsou definice prostředků implicitní v souborech, které tvoří sestavení. V rozhraní .NET Framework 1.0 a 1.1 Tato hodnota je vždy předpokládá, že pokud chcete nastavit.|  
|`afNonSideBySideAppDomain`|Určuje, že sestavení nelze provést s jinými verzemi, pokud běží ve stejné doméně aplikace.|  
|`afNonSideBySideProcess`|Určuje, že sestavení nelze provést s jinými verzemi spuštěné ve stejném procesu.|  
|`afNonSideBySideMachine`|Určuje, že sestavení nelze provést s jinými verzemi, pokud jsou spuštěné na stejném počítači.|  
  
## <a name="remarks"></a>Poznámky  
 Hodnoty mezi 0x0010 a 0x0070, včetně, se používají k popisu funkce kompatibility vedle sebe odkazované sestavení. Pokud nejsou nastavené žádné z těchto hodnot, sestavení se považuje za kompatibilní vedle sebe.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MsCorEE.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
 [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
