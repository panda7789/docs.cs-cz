---
title: CorOpenFlags – výčet
ms.date: 03/30/2017
api_name:
- CorOpenFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorOpenFlags
helpviewer_keywords:
- CorOpenFlags enumeration [.NET Framework metadata]
ms.assetid: e27a83b5-2698-4996-9032-1e0fed8b91ca
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 55934ef08b10764bb705d7c166621ec7cfcadd0a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59108511"
---
# <a name="coropenflags-enumeration"></a>CorOpenFlags – výčet
Obsahuje příznak hodnoty, které řídí chování metadata po otevření souborů manifestu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorOpenFlags  
{  
    ofRead              =   0x00000000,  
    ofWrite             =   0x00000001,  
    ofReadWriteMask     =   0x00000001,  
    ofCopyMemory        =   0x00000002,  
    ofCacheImage        =   0x00000004,  
    ofManifestMetadata  =   0x00000008,  
    ofReadOnly          =   0x00000010,  
    ofTakeOwnership     =   0x00000020,  
    ofCacheImage        =   0x00000004,  
    ofNoTypeLib         =   0x00000080,  
    ofNoTransform       =   0x00001000,  
    ofReserved1         =   0x00000100,  
    ofReserved2         =   0x00000200,  
    ofReserved          =   0xffffff40  
} CorOpenFlags;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`ofRead`|Označuje, že by soubor otevřen jen pro čtení.|  
|`ofWrite`|Označuje, že soubor by měl být otevřena pro zápis.<br /><br /> Pokud používáte `ofWrite` příznak při otevírání souboru .winmd, je třeba také předat `ofNoTransform` příznak.|  
|`ofReadWriteMask`|Maska pro čtení a zápis.|  
|`ofCopyMemory`|Označuje, že by soubor načíst do paměti. Metadata musí udržovat vlastní kopii.|  
|`ofCacheImage`|Zastaralé. Tento příznak se ignoruje.|  
|`ofManifestMetadata`|Zastaralé. Tento příznak se ignoruje.|  
|`ofReadOnly`|Označuje, že soubor musí být otevřen pro čtení a že volání `QueryInterface` pro [imetadataemit –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) nelze provést.|  
|`ofTakeOwnership`|Označuje, že byla přidělena paměť pomocí volání do [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) a bude uvolněna metadata.|  
|`ofNoTypeLib`|Zastaralé. Tento příznak se ignoruje.|  
|`ofNoTransform`|Označuje, že by mělo být zakázáno automatické transformace soubory .winmd. Jinými slovy by mělo být zakázáno projekce typu modulu Windows Runtime na typ rozhraní .NET Framework. Další informace najdete v tématu [Windows Runtime a CLR - pod pokličkou pomocí .NET a modulem Windows Runtime](https://msdn.microsoft.com/magazine/jj651569.aspx).|  
|`ofReserved1`|Vyhrazeno pro interní použití.|  
|`ofReserved2`|Vyhrazeno pro interní použití.|  
|`ofReserved`|Vyhrazeno pro interní použití.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
