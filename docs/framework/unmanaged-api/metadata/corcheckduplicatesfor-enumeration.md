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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9cdb1570b682088e92ff7c7a78d84259d02d8512
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="corcheckduplicatesfor-enumeration"></a>CorCheckDuplicatesFor – výčet
Určuje metadata tokeny, které budou sloužit k duplicitní položky.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|`MDDupAll`|Zkontrolujte všechny tokeny metadat pro duplicitní položky.|  
|`MDDupENC`|Nepoužívá se.|  
|`MDNoDupChecks`|Neprovádět kontrolu tokenů metadat pro duplicitní položky.|  
|`MDDupTypeDef`|Zkontrolujte duplikáty `mdTypeDef` tokeny.|  
|`MDDupInterfaceImpl`|Zkontrolujte duplikáty `mdInterfaceImpl` tokeny.|  
|`MDDupMethodDef`|Zkontrolujte duplikáty `mdMethodDef` tokeny.|  
|`MDDupTypeRef`|Zkontrolujte duplikáty `mdTypeRef` tokeny.|  
|`MDDupMemberRef`|Zkontrolujte duplikáty `mdMemberRef` tokeny.|  
|`MDDupCustomAttribute`|Zkontrolujte duplikáty `mdCustomAttribute` tokeny.|  
|`MDDupParamDef`|Zkontrolujte duplikáty `mdParamDef` tokeny.|  
|`MDDupPermission`|Zkontrolujte duplikáty `mdPermission` tokeny.|  
|`MDDupProperty`|Zkontrolujte duplikáty `mdProperty` tokeny.|  
|`MDDupEvent`|Zkontrolujte duplikáty `mdEvent` tokeny.|  
|`MDDupFieldDef`|Zkontrolujte duplikáty `mdFieldDef` tokeny.|  
|`MDDupSignature`|Zkontrolujte duplikáty `mdSignature` tokeny.|  
|`MDDupModuleRef`|Zkontrolujte duplikáty `mdModuleRef` tokeny.|  
|`MDDupTypeSpec`|Zkontrolujte duplikáty `mdTypeSpec` tokeny.|  
|`MDDupImplMap`|Zkontrolujte duplikáty `mdImplMap` tokeny.|  
|`MDDupAssemblyRef`|Zkontrolujte duplikáty `mdAssemblyRef` tokeny.|  
|`MDDupFile`|Zkontrolujte duplikáty `mdFile` tokeny.|  
|`MDDupExportedType`|Zkontrolujte duplikáty `mdExportedType` tokeny.|  
|`MDDupManifestResource`|Zkontrolujte duplikáty `mdManifestResource` tokeny.|  
|`MDDupGenericParam`|Zkontrolujte duplikáty `mdGenericParam` tokeny.|  
|`MDDupMethodSpec`|Zkontrolujte duplikáty `mdMethodSpec` tokeny.|  
|`MDDupGenericParamConstraint`|Zkontrolujte duplikáty `mdGenericParamConstraint` tokeny.|  
|`MDDupAssembly`|Zkontrolujte duplikáty `mdAssembly` tokeny.|  
|`MDDupDefault`|Zkontrolujte duplikáty `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, a `mdMethodSpec` tokeny.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
