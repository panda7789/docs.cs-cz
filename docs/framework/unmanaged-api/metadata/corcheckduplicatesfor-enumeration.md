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
ms.openlocfilehash: 6b551743227dc1c6069796038782a515e6dbe8c4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443785"
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
  
|Člen|Popis|  
|------------|-----------------|  
|`MDDupAll`|Zkontroluje všechny tokeny metadat pro duplicity.|  
|`MDDupENC`|Nepoužívá se.|  
|`MDNoDupChecks`|Nekontrolujte tokeny metadat pro duplicity.|  
|`MDDupTypeDef`|Kontrolovat duplicity tokenů `mdTypeDef`.|  
|`MDDupInterfaceImpl`|Kontrolovat duplicity tokenů `mdInterfaceImpl`.|  
|`MDDupMethodDef`|Kontrolovat duplicity tokenů `mdMethodDef`.|  
|`MDDupTypeRef`|Kontrolovat duplicity tokenů `mdTypeRef`.|  
|`MDDupMemberRef`|Kontrolovat duplicity tokenů `mdMemberRef`.|  
|`MDDupCustomAttribute`|Kontrolovat duplicity tokenů `mdCustomAttribute`.|  
|`MDDupParamDef`|Kontrolovat duplicity tokenů `mdParamDef`.|  
|`MDDupPermission`|Kontrolovat duplicity tokenů `mdPermission`.|  
|`MDDupProperty`|Kontrolovat duplicity tokenů `mdProperty`.|  
|`MDDupEvent`|Kontrolovat duplicity tokenů `mdEvent`.|  
|`MDDupFieldDef`|Kontrolovat duplicity tokenů `mdFieldDef`.|  
|`MDDupSignature`|Kontrolovat duplicity tokenů `mdSignature`.|  
|`MDDupModuleRef`|Kontrolovat duplicity tokenů `mdModuleRef`.|  
|`MDDupTypeSpec`|Kontrolovat duplicity tokenů `mdTypeSpec`.|  
|`MDDupImplMap`|Kontrolovat duplicity tokenů `mdImplMap`.|  
|`MDDupAssemblyRef`|Kontrolovat duplicity tokenů `mdAssemblyRef`.|  
|`MDDupFile`|Kontrolovat duplicity tokenů `mdFile`.|  
|`MDDupExportedType`|Kontrolovat duplicity tokenů `mdExportedType`.|  
|`MDDupManifestResource`|Kontrolovat duplicity tokenů `mdManifestResource`.|  
|`MDDupGenericParam`|Kontrolovat duplicity tokenů `mdGenericParam`.|  
|`MDDupMethodSpec`|Kontrolovat duplicity tokenů `mdMethodSpec`.|  
|`MDDupGenericParamConstraint`|Kontrolovat duplicity tokenů `mdGenericParamConstraint`.|  
|`MDDupAssembly`|Kontrolovat duplicity tokenů `mdAssembly`.|  
|`MDDupDefault`|Zkontroluje duplicity `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`a `mdMethodSpec`ch tokenů.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorHdr. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
