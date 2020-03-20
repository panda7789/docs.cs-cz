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
ms.openlocfilehash: 04dc12ab4d7d178ebf1575a3260f9f4981972782
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176185"
---
# <a name="corcheckduplicatesfor-enumeration"></a>CorCheckDuplicatesFor – výčet
Určuje tokeny metadat, které budou zkontrolovány na duplikáty.  
  
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
|`MDDupAll`|Zkontrolujte, zda všechny tokeny metadat neobsahují duplicity.|  
|`MDDupENC`|Nepoužívá se.|  
|`MDNoDupChecks`|Nekontrolujte tokeny metadat pro duplicity.|  
|`MDDupTypeDef`|Zkontrolujte duplicity `mdTypeDef` tokenů.|  
|`MDDupInterfaceImpl`|Zkontrolujte duplicity `mdInterfaceImpl` tokenů.|  
|`MDDupMethodDef`|Zkontrolujte duplicity `mdMethodDef` tokenů.|  
|`MDDupTypeRef`|Zkontrolujte duplicity `mdTypeRef` tokenů.|  
|`MDDupMemberRef`|Zkontrolujte duplicity `mdMemberRef` tokenů.|  
|`MDDupCustomAttribute`|Zkontrolujte duplicity `mdCustomAttribute` tokenů.|  
|`MDDupParamDef`|Zkontrolujte duplicity `mdParamDef` tokenů.|  
|`MDDupPermission`|Zkontrolujte duplicity `mdPermission` tokenů.|  
|`MDDupProperty`|Zkontrolujte duplicity `mdProperty` tokenů.|  
|`MDDupEvent`|Zkontrolujte duplicity `mdEvent` tokenů.|  
|`MDDupFieldDef`|Zkontrolujte duplicity `mdFieldDef` tokenů.|  
|`MDDupSignature`|Zkontrolujte duplicity `mdSignature` tokenů.|  
|`MDDupModuleRef`|Zkontrolujte duplicity `mdModuleRef` tokenů.|  
|`MDDupTypeSpec`|Zkontrolujte duplicity `mdTypeSpec` tokenů.|  
|`MDDupImplMap`|Zkontrolujte duplicity `mdImplMap` tokenů.|  
|`MDDupAssemblyRef`|Zkontrolujte duplicity `mdAssemblyRef` tokenů.|  
|`MDDupFile`|Zkontrolujte duplicity `mdFile` tokenů.|  
|`MDDupExportedType`|Zkontrolujte duplicity `mdExportedType` tokenů.|  
|`MDDupManifestResource`|Zkontrolujte duplicity `mdManifestResource` tokenů.|  
|`MDDupGenericParam`|Zkontrolujte duplicity `mdGenericParam` tokenů.|  
|`MDDupMethodSpec`|Zkontrolujte duplicity `mdMethodSpec` tokenů.|  
|`MDDupGenericParamConstraint`|Zkontrolujte duplicity `mdGenericParamConstraint` tokenů.|  
|`MDDupAssembly`|Zkontrolujte duplicity `mdAssembly` tokenů.|  
|`MDDupDefault`|Zkontrolujte duplicity `mdMemberRef` `mdTypeRef`, `mdSignature` `mdTypeSpec`, `mdMethodSpec` , a tokeny.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
