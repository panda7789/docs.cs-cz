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
ms.openlocfilehash: 6f231c4f9782518e30cbaa89c6b085c72aafcc92
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33445442"
---
# <a name="coropenflags-enumeration"></a>CorOpenFlags – výčet
Obsahuje příznak hodnoty, které řídí chování metadat při otevírání souborů manifestu.  
  
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
|`ofRead`|Označuje, že soubor musí být otevřen jen pro čtení.|  
|`ofWrite`|Označuje, že soubor musí být otevřen pro zápis.<br /><br /> Pokud používáte `ofWrite` příznak při otevření souboru .winmd, by také předáte `ofNoTransform` příznak.|  
|`ofReadWriteMask`|Maska pro čtení a zápis.|  
|`ofCopyMemory`|Označuje, že byste si měli přečíst soubor do paměti. Metadata musí udržovat svůj vlastní kopie.|  
|`ofCacheImage`|Zastaralé. Tento příznak se ignoruje.|  
|`ofManifestMetadata`|Zastaralé. Tento příznak se ignoruje.|  
|`ofReadOnly`|Označuje, že soubor musí být otevřen pro čtení a že volání `QueryInterface` pro [imetadataemit –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) nelze provést.|  
|`ofTakeOwnership`|Označuje, že je paměť byl přidělen s použitím volání [CoTaskMemAlloc](http://msdn.microsoft.com/library/c4cb588d-9482-4f90-a92e-75b604540d5c) a využívalo metadata.|  
|`ofNoTypeLib`|Zastaralé. Tento příznak se ignoruje.|  
|`ofNoTransform`|Označuje, že by mělo být zakázáno automatické transformace .winmd souborů. Jinými slovy by mělo být zakázáno projekce typu na typ rozhraní .NET Framework prostředí Windows Runtime. Další informace najdete v tématu [pod kapotou s .NET a prostředí Windows Runtime](http://msdn.microsoft.com/magazine/jj651569.aspx).|  
|`ofReserved1`|Vyhrazeno pro interní použití.|  
|`ofReserved2`|Vyhrazeno pro interní použití.|  
|`ofReserved`|Vyhrazeno pro interní použití.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
