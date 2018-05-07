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
ms.openlocfilehash: 96ab659e6ab6cc9601c0e9a1ab511da92905c242
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="cornotificationfortokenmovement-enumeration"></a>CorNotificationForTokenMovement – výčet
Určuje oznámení, které se budou odesílat do metadat rozhraní API klienta, když dojde k tokenu přemapování.  
  
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
|`MDNotifyDefault`|Upozornit, když `mdTypeRef`, `mdMethodDef`, `mdMemberRef`, nebo `mdFieldDef` přesunutí tokeny.|  
|`MDNotifyAll`|Upozorněte, když přesune všechny token.|  
|`MDNotifyNone`|Není-li zprávu přesunout tokeny.|  
|`MDNotifyMethodDef`|Upozornit, když `mdMethodDef` token přesune.|  
|`MDNotifyMemberRef`|Upozornit, když `mdMemberRef` token přesune.|  
|`MDNotifyFieldDef`|Upozornit, když `mdFieldDef` token přesune.|  
|`MDNotifyTypeRef`|Upozornit, když `mdTypeRef` token přesune.|  
|`MDNotifyTypeDef`|Upozornit, když `mdTypeDef` token přesune.|  
|`MDNotifyParamDef`|Upozornit, když `mdParamDef` token přesune.|  
|`MDNotifyInterfaceImpl`|Upozornit, když `mdInterfaceImpl` token přesune.|  
|`MDNotifyProperty`|Upozornit, když `mdProperty` token přesune.|  
|`MDNotifyEvent`|Upozornit, když `mdEvent` token přesune.|  
|`MDNotifySignature`|Upozornit, když `mdSignature` token přesune.|  
|`MDNotifyTypeSpec`|Upozornit, když `mdTypeSpec` token přesune.|  
|`MDNotifyCustomAttribute`|Upozornit, když `mdCustomAttribute` token přesune.|  
|`MDNotifySecurityValue`|Upozornit, když `mdSecurityValue` token přesune.|  
|`MDNotifyPermission`|Upozornit, když `mdPermission` token přesune.|  
|`MDNotifyModuleRef`|Upozornit, když `mdModuleRef` token přesune.|  
|`MDNotifyNameSpace`|Upozornit, když `mdNameSpace` token přesune.|  
|`MDNotifyAssemblyRef`|Upozornit, když `mdAssemblyRef` token přesune.|  
|`MDNotifyFile`|Upozornit, když `mdFile` token přesune.|  
|`MDNotifyExportedType`|Upozornit, když `mdExportedType` token přesune.|  
|`MDNotifyResource`|Upozornit, když `mdManifestResource` token přesune.|  
  
## <a name="remarks"></a>Poznámky  
 Token může být znovu namapovaný (která je, přesunuta) během metadat sloučení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
