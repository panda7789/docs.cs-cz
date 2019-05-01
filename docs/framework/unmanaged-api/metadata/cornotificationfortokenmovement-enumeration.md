---
title: CorNotificationForTokenMovement – výčet
ms.date: 03/30/2017
api_name:
- CorNotificationForTokenMovement
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNotificationForTokenMovement
helpviewer_keywords:
- CorNotificationForTokenMovement enumeration [.NET Framework metadata]
ms.assetid: 1edd1670-976a-4fc8-bef7-7c41e60ad989
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 15c5e8b34f2748868611bd7dc47ef73c491b1338
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62045432"
---
# <a name="cornotificationfortokenmovement-enumeration"></a>CorNotificationForTokenMovement – výčet
Určuje oznámení, které se odešlou do metadat rozhraní API klienta, když dojde k tokenu přemapování.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum CorNotificationForTokenMovement {  
  
    MDNotifyDefault             = 0x0000000f,  
    MDNotifyAll                 = 0xffffffff,  
    MDNotifyNone                = 0x00000000,  
    MDNotifyMethodDef           = 0x00000001,  
    MDNotifyMemberRef           = 0x00000002,  
    MDNotifyFieldDef            = 0x00000004,  
    MDNotifyTypeRef             = 0x00000008,  
  
    MDNotifyTypeDef             = 0x00000010,  
    MDNotifyParamDef            = 0x00000020,  
    MDNotifyInterfaceImpl       = 0x00000040,  
    MDNotifyProperty            = 0x00000080,  
    MDNotifyEvent               = 0x00000100,  
    MDNotifySignature           = 0x00000200,  
    MDNotifyTypeSpec            = 0x00000400,  
    MDNotifyCustomAttribute     = 0x00000800,  
    MDNotifySecurityValue       = 0x00001000,  
    MDNotifyPermission          = 0x00002000,  
    MDNotifyModuleRef           = 0x00004000,  
  
    MDNotifyNameSpace           = 0x00008000,  
  
    MDNotifyAssemblyRef         = 0x01000000,  
    MDNotifyFile                = 0x02000000,  
    MDNotifyExportedType        = 0x04000000,  
    MDNotifyResource            = 0x08000000  
  
} CorNotificationForTokenMovement;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`MDNotifyDefault`|Upozornit při `mdTypeRef`, `mdMethodDef`, `mdMemberRef`, nebo `mdFieldDef` přesunout tokeny.|  
|`MDNotifyAll`|Upozorněte při přesunu žádný token.|  
|`MDNotifyNone`|Upozorňován přesunout tokeny.|  
|`MDNotifyMethodDef`|Upozornit při `mdMethodDef` přesune token.|  
|`MDNotifyMemberRef`|Upozornit při `mdMemberRef` přesune token.|  
|`MDNotifyFieldDef`|Upozornit při `mdFieldDef` přesune token.|  
|`MDNotifyTypeRef`|Upozornit při `mdTypeRef` přesune token.|  
|`MDNotifyTypeDef`|Upozornit při `mdTypeDef` přesune token.|  
|`MDNotifyParamDef`|Upozornit při `mdParamDef` přesune token.|  
|`MDNotifyInterfaceImpl`|Upozornit při `mdInterfaceImpl` přesune token.|  
|`MDNotifyProperty`|Upozornit při `mdProperty` přesune token.|  
|`MDNotifyEvent`|Upozornit při `mdEvent` přesune token.|  
|`MDNotifySignature`|Upozornit při `mdSignature` přesune token.|  
|`MDNotifyTypeSpec`|Upozornit při `mdTypeSpec` přesune token.|  
|`MDNotifyCustomAttribute`|Upozornit při `mdCustomAttribute` přesune token.|  
|`MDNotifySecurityValue`|Upozornit při `mdSecurityValue` přesune token.|  
|`MDNotifyPermission`|Upozornit při `mdPermission` přesune token.|  
|`MDNotifyModuleRef`|Upozornit při `mdModuleRef` přesune token.|  
|`MDNotifyNameSpace`|Upozornit při `mdNameSpace` přesune token.|  
|`MDNotifyAssemblyRef`|Upozornit při `mdAssemblyRef` přesune token.|  
|`MDNotifyFile`|Upozornit při `mdFile` přesune token.|  
|`MDNotifyExportedType`|Upozornit při `mdExportedType` přesune token.|  
|`MDNotifyResource`|Upozornit při `mdManifestResource` přesune token.|  
  
## <a name="remarks"></a>Poznámky  
 Token může být znovu namapována (přesunuté,) během metadat sloučení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
