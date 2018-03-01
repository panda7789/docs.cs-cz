---
title: "CorTokenType – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorTokenType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorTokenType
helpviewer_keywords:
- CorTokenType enumeration [.NET Framework metadata]
ms.assetid: 93c9a369-225f-4eff-9b78-3fbee4902cf1
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ae9164753e919b80e635582b15da5263194e215f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="cortokentype-enumeration"></a>CorTokenType – výčet
Určuje typ tokenu metadat.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorTokenType {  
  
    mdtModule                       = 0x00000000,  
    mdtTypeRef                      = 0x01000000,  
    mdtTypeDef                      = 0x02000000,  
    mdtFieldDef                     = 0x04000000,  
    mdtMethodDef                    = 0x06000000,  
    mdtParamDef                     = 0x08000000,  
    mdtInterfaceImpl                = 0x09000000,  
    mdtMemberRef                    = 0x0a000000,  
    mdtCustomAttribute              = 0x0c000000,  
    mdtPermission                   = 0x0e000000,  
    mdtSignature                    = 0x11000000,  
    mdtEvent                        = 0x14000000,  
    mdtProperty                     = 0x17000000,  
    mdtModuleRef                    = 0x1a000000,  
    mdtTypeSpec                     = 0x1b000000,  
    mdtAssembly                     = 0x20000000,  
    mdtAssemblyRef                  = 0x23000000,  
    mdtFile                         = 0x26000000,  
    mdtExportedType                 = 0x27000000,  
    mdtManifestResource             = 0x28000000,  
    mdtGenericParam                 = 0x2a000000,  
    mdtMethodSpec                   = 0x2b000000,  
    mdtGenericParamConstraint       = 0x2c000000,  
    mdtString                       = 0x70000000,  
    mdtName                         = 0x71000000,  
    mdtBaseType                     = 0x72000000  
  
} CorTokenType;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`mdtModule`|`mdModule` Tokenu.|  
|`mdtTypeRef`|`mdTypeRef` Tokenu.|  
|`mdtTypeDef`|`mdTypeDef` Tokenu.|  
|`mdtFieldDef`|`mdFieldDef` Tokenu.|  
|`mdtMethodDef`|`mdMethodDef` Tokenu.|  
|`mdtParamDef`|`mdParamDef` Tokenu.|  
|`mdtInterfaceImpl`|`mdInterfaceImpl` Tokenu.|  
|`mdtMemberRef`|`mdMemberRef` Tokenu.|  
|`mdtCustomAttribute`|`mdCustomAttribute` Tokenu.|  
|`mdtPermission`|`mdPermission` Tokenu.|  
|`mdtSignature`|`mdSignature` Tokenu.|  
|`mdtEvent`|`mdEvent` Tokenu.|  
|`mdtProperty`|`mdProperty` Tokenu.|  
|`mdtModuleRef`|`mdModuleRef` Tokenu.|  
|`mdtTypeSpec`|`mdTypeSpec` Tokenu.|  
|`mdtAssembly`|`mdAssembly` Tokenu.|  
|`mdtAssemblyRef`|`mdAssemblyRef` Tokenu.|  
|`mdtFile`|`mdFile` Tokenu.|  
|`mdtExportedType`|`mdExportedType` Tokenu.|  
|`mdtManifestResource`|`mdManifestResource` Tokenu.|  
|`mdtGenericParam`|`mdGenericParam` Tokenu.|  
|`mdtMethodSpec`|`mdMethodSpec` Tokenu.|  
|`mdtGenericParamConstraint`|`mdGenericParamConstraint` Tokenu.|  
|`mdtString`|`mdString` Tokenu.|  
|`mdtName`|`mdName` Tokenu.|  
|`mdtBaseType`|Nepoužívá se.|  
  
## <a name="remarks"></a>Poznámky  
 Každá hodnota se rovná hodnotě horní byte v odpovídající tokenu metadat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
