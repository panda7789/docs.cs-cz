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
ms.openlocfilehash: a82ce9709e008e092c5f31372a89bf9a16e1f88b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767024"
---
# <a name="corcheckduplicatesfor-enumeration"></a>CorCheckDuplicatesFor – výčet
Určuje tokeny metadat, které budou zkontrolovat duplicitu.  
  
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
|`MDDupAll`|Zkontrolujte všechny tokeny metadat pro duplicitní položky.|  
|`MDDupENC`|Nepoužívá se.|  
|`MDNoDupChecks`|Nezaškrtávejte políčko tokeny metadat pro duplicitní položky.|  
|`MDDupTypeDef`|Zkontrolovat duplikáty `mdTypeDef` tokeny.|  
|`MDDupInterfaceImpl`|Zkontrolovat duplikáty `mdInterfaceImpl` tokeny.|  
|`MDDupMethodDef`|Zkontrolovat duplikáty `mdMethodDef` tokeny.|  
|`MDDupTypeRef`|Zkontrolovat duplikáty `mdTypeRef` tokeny.|  
|`MDDupMemberRef`|Zkontrolovat duplikáty `mdMemberRef` tokeny.|  
|`MDDupCustomAttribute`|Zkontrolovat duplikáty `mdCustomAttribute` tokeny.|  
|`MDDupParamDef`|Zkontrolovat duplikáty `mdParamDef` tokeny.|  
|`MDDupPermission`|Zkontrolovat duplikáty `mdPermission` tokeny.|  
|`MDDupProperty`|Zkontrolovat duplikáty `mdProperty` tokeny.|  
|`MDDupEvent`|Zkontrolovat duplikáty `mdEvent` tokeny.|  
|`MDDupFieldDef`|Zkontrolovat duplikáty `mdFieldDef` tokeny.|  
|`MDDupSignature`|Zkontrolovat duplikáty `mdSignature` tokeny.|  
|`MDDupModuleRef`|Zkontrolovat duplikáty `mdModuleRef` tokeny.|  
|`MDDupTypeSpec`|Zkontrolovat duplikáty `mdTypeSpec` tokeny.|  
|`MDDupImplMap`|Zkontrolovat duplikáty `mdImplMap` tokeny.|  
|`MDDupAssemblyRef`|Zkontrolovat duplikáty `mdAssemblyRef` tokeny.|  
|`MDDupFile`|Zkontrolovat duplikáty `mdFile` tokeny.|  
|`MDDupExportedType`|Zkontrolovat duplikáty `mdExportedType` tokeny.|  
|`MDDupManifestResource`|Zkontrolovat duplikáty `mdManifestResource` tokeny.|  
|`MDDupGenericParam`|Zkontrolovat duplikáty `mdGenericParam` tokeny.|  
|`MDDupMethodSpec`|Zkontrolovat duplikáty `mdMethodSpec` tokeny.|  
|`MDDupGenericParamConstraint`|Zkontrolovat duplikáty `mdGenericParamConstraint` tokeny.|  
|`MDDupAssembly`|Zkontrolovat duplikáty `mdAssembly` tokeny.|  
|`MDDupDefault`|Zkontrolovat duplikáty `mdMemberRef`, `mdTypeRef`, `mdSignature`, `mdTypeSpec`, a `mdMethodSpec` tokeny.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
