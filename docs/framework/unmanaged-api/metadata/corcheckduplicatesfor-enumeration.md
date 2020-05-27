---
title: CorCheckDuplicatesFor – výčet
ms.date: 03/30/2017
api_name:
- CorCheckDuplicatesFor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCheckDuplicatesFor
helpviewer_keywords:
- CorCheckDuplicatesFor enumeration [.NET Framework metadata]
ms.assetid: d8ec8d3c-70f7-4cc6-9957-68068fd8f49c
topic_type:
- apiref
ms.openlocfilehash: 2985c419b25b8bf76df8fee0f0f37ba9ebee3df7
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007895"
---
# <a name="corcheckduplicatesfor-enumeration"></a>CorCheckDuplicatesFor – výčet
Určuje tokeny metadat, u kterých budou kontrolovány duplicity.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorCheckDuplicatesFor {  
  
    MDDupAll                    = 0xffffffff,  
    MDDupENC                    = MDDupAll,  
    MDNoDupChecks               = 0x00000000,  
    MDDupTypeDef                = 0x00000001,  
    MDDupInterfaceImpl          = 0x00000002,  
    MDDupMethodDef              = 0x00000004,  
    MDDupTypeRef                = 0x00000008,  
    MDDupMemberRef              = 0x00000010,  
    MDDupCustomAttribute        = 0x00000020,  
    MDDupParamDef               = 0x00000040,  
    MDDupPermission             = 0x00000080,  
    MDDupProperty               = 0x00000100,  
    MDDupEvent                  = 0x00000200,  
    MDDupFieldDef               = 0x00000400,  
    MDDupSignature              = 0x00000800,  
    MDDupModuleRef              = 0x00001000,  
    MDDupTypeSpec               = 0x00002000,  
    MDDupImplMap                = 0x00004000,  
    MDDupAssemblyRef            = 0x00008000,  
    MDDupFile                   = 0x00010000,  
    MDDupExportedType           = 0x00020000,  
    MDDupManifestResource       = 0x00040000,  
    MDDupGenericParam           = 0x00080000,  
    MDDupMethodSpec             = 0x00100000,  
    MDDupGenericParamConstraint = 0x00200000,  
  
    MDDupAssembly               = 0x10000000,  
  
    MDDupDefault =
        MDNoDupChecks | MDDupTypeRef | MDDupMemberRef |
        MDDupSignature | MDDupTypeSpec | MDDupMethodSpec  
  
} CorCheckDuplicatesFor;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Description|  
|------------|-----------------|  
|`MDDupAll`|Zkontroluje všechny tokeny metadat pro duplicity.|  
|`MDDupENC`|Nepoužívá se.|  
|`MDNoDupChecks`|Nekontrolujte tokeny metadat pro duplicity.|  
|`MDDupTypeDef`|Zkontroluje duplicity `mdTypeDef` tokenů.|  
|`MDDupInterfaceImpl`|Zkontroluje duplicity `mdInterfaceImpl` tokenů.|  
|`MDDupMethodDef`|Zkontroluje duplicity `mdMethodDef` tokenů.|  
|`MDDupTypeRef`|Zkontroluje duplicity `mdTypeRef` tokenů.|  
|`MDDupMemberRef`|Zkontroluje duplicity `mdMemberRef` tokenů.|  
|`MDDupCustomAttribute`|Zkontroluje duplicity `mdCustomAttribute` tokenů.|  
|`MDDupParamDef`|Zkontroluje duplicity `mdParamDef` tokenů.|  
|`MDDupPermission`|Zkontroluje duplicity `mdPermission` tokenů.|  
|`MDDupProperty`|Zkontroluje duplicity `mdProperty` tokenů.|  
|`MDDupEvent`|Zkontroluje duplicity `mdEvent` tokenů.|  
|`MDDupFieldDef`|Zkontroluje duplicity `mdFieldDef` tokenů.|  
|`MDDupSignature`|Zkontroluje duplicity `mdSignature` tokenů.|  
|`MDDupModuleRef`|Zkontroluje duplicity `mdModuleRef` tokenů.|  
|`MDDupTypeSpec`|Zkontroluje duplicity `mdTypeSpec` tokenů.|  
|`MDDupImplMap`|Zkontroluje duplicity `mdImplMap` tokenů.|  
|`MDDupAssemblyRef`|Zkontroluje duplicity `mdAssemblyRef` tokenů.|  
|`MDDupFile`|Zkontroluje duplicity `mdFile` tokenů.|  
|`MDDupExportedType`|Zkontroluje duplicity `mdExportedType` tokenů.|  
|`MDDupManifestResource`|Zkontroluje duplicity `mdManifestResource` tokenů.|  
|`MDDupGenericParam`|Zkontroluje duplicity `mdGenericParam` tokenů.|  
|`MDDupMethodSpec`|Zkontroluje duplicity `mdMethodSpec` tokenů.|  
|`MDDupGenericParamConstraint`|Zkontroluje duplicity `mdGenericParamConstraint` tokenů.|  
|`MDDupAssembly`|Zkontroluje duplicity `mdAssembly` tokenů.|  
|`MDDupDefault`|Kontrolovat duplicity `mdMemberRef` `mdTypeRef` tokenů,,, `mdSignature` `mdTypeSpec` a `mdMethodSpec` .|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorHdr. h  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Výčty pro metadata](metadata-enumerations.md)
