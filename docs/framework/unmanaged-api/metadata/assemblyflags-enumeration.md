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
ms.openlocfilehash: ffb5953c843a338b4548253457a0c3b1ca0c20f5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444297"
---
# <a name="assemblyflags-enumeration"></a>AssemblyFlags – výčet
Obsahuje hodnoty, které popisují funkce běhu sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
|`afImplicitExportedTypes`|Určuje, že exportované definice typu jsou implicitní v rámci souborů, které tvoří sestavení. V .NET Framework verzích 1,0 a 1,1 je tato hodnota vždycky nastavená.|  
|`afImplicitResources`|Určuje, že definice prostředků jsou implicitní v rámci souborů, které tvoří sestavení. V .NET Framework 1,0 a 1,1 je tato hodnota vždy nastavena jako nastavená.|  
|`afNonSideBySideAppDomain`|Určuje, že sestavení nemůže být spuštěno s jinými verzemi, pokud jsou spuštěny ve stejné doméně aplikace.|  
|`afNonSideBySideProcess`|Určuje, že sestavení nemůže být spuštěno s jinými verzemi, pokud jsou spuštěny ve stejném procesu.|  
|`afNonSideBySideMachine`|Určuje, že sestavení nemůže být spuštěno s jinými verzemi, pokud jsou spuštěny ve stejném počítači.|  
  
## <a name="remarks"></a>Poznámky  
 Hodnoty mezi 0x0010 a 0x0070, včetně, se používají k popisu souběžných funkcí kompatibility odkazovaného sestavení. Pokud žádná z těchto hodnot není nastavena, předpokládá se, že sestavení je souběžně kompatibilní.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** MsCorEE. h  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [IMetaDataAssemblyEmit – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
