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
ms.openlocfilehash: ad582fc2fd1bd1d2fc9d5a0d483fdb3a51309a10
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436502"
---
# <a name="coropenflags-enumeration"></a>CorOpenFlags – výčet
Obsahuje hodnoty příznaků, které řídí chování metadat při otevírání souborů manifestu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
|`ofRead`|Označuje, že by měl být soubor otevřen pouze pro čtení.|  
|`ofWrite`|Označuje, že by měl být soubor otevřen pro zápis.<br /><br /> Pokud při otevírání souboru winmd používáte příznak `ofWrite`, měli byste také předat příznak `ofNoTransform`.|  
|`ofReadWriteMask`|Maska pro čtení a zápis.|  
|`ofCopyMemory`|Indikuje, že by měl být soubor čten do paměti. Metadata by měla uchovávat svou vlastní kopii.|  
|`ofCacheImage`|Zastaralé. Tento příznak se ignoruje.|  
|`ofManifestMetadata`|Zastaralé. Tento příznak se ignoruje.|  
|`ofReadOnly`|Označuje, že by měl být soubor otevřen pro čtení a že volání `QueryInterface` pro [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) nelze vytvořit.|  
|`ofTakeOwnership`|Indikuje, že paměť byla přidělena pomocí volání [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) a bude uvolněna metadaty.|  
|`ofNoTypeLib`|Zastaralé. Tento příznak se ignoruje.|  
|`ofNoTransform`|Určuje, že automatické transformace souborů. winmd by měly být zakázané. Jinými slovy, je třeba zakázat projekci prostředí Windows Runtime typu pro .NET Framework typ. Další informace naleznete v tématu [prostředí Windows Runtime a CLR – pod digestoří s .NET a prostředí Windows Runtime](https://docs.microsoft.com/archive/msdn-magazine/2012/windows-8-special-issue/windows-runtime-and-the-clr-underneath-the-hood-with-net-and-the-windows-runtime).|  
|`ofReserved1`|Vyhrazeno pro interní použití.|  
|`ofReserved2`|Vyhrazeno pro interní použití.|  
|`ofReserved`|Vyhrazeno pro interní použití.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorHdr. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
