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
ms.openlocfilehash: e8065a5492884a4b7f5d662737e4beddc6fca5b3
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007595"
---
# <a name="cornotificationfortokenmovement-enumeration"></a>CorNotificationForTokenMovement – výčet
Určuje oznámení, která se odešlou do klienta rozhraní API pro metadata, když dojde k přemapování tokenu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
  
|Člen|Description|  
|------------|-----------------|  
|`MDNotifyDefault`|Upozorní, `mdTypeRef` Když `mdMethodDef` se `mdMemberRef` `mdFieldDef` tokeny přesunou,, nebo.|  
|`MDNotifyAll`|Upozorní, když se libovolný token přesune.|  
|`MDNotifyNone`|Neupozorňovat při přesunu tokenů|  
|`MDNotifyMethodDef`|Upozorní, když se `mdMethodDef` token přesune.|  
|`MDNotifyMemberRef`|Upozorní, když se `mdMemberRef` token přesune.|  
|`MDNotifyFieldDef`|Upozorní, když se `mdFieldDef` token přesune.|  
|`MDNotifyTypeRef`|Upozorní, když se `mdTypeRef` token přesune.|  
|`MDNotifyTypeDef`|Upozorní, když se `mdTypeDef` token přesune.|  
|`MDNotifyParamDef`|Upozorní, když se `mdParamDef` token přesune.|  
|`MDNotifyInterfaceImpl`|Upozorní, když se `mdInterfaceImpl` token přesune.|  
|`MDNotifyProperty`|Upozorní, když se `mdProperty` token přesune.|  
|`MDNotifyEvent`|Upozorní, když se `mdEvent` token přesune.|  
|`MDNotifySignature`|Upozorní, když se `mdSignature` token přesune.|  
|`MDNotifyTypeSpec`|Upozorní, když se `mdTypeSpec` token přesune.|  
|`MDNotifyCustomAttribute`|Upozorní, když se `mdCustomAttribute` token přesune.|  
|`MDNotifySecurityValue`|Upozorní, když se `mdSecurityValue` token přesune.|  
|`MDNotifyPermission`|Upozorní, když se `mdPermission` token přesune.|  
|`MDNotifyModuleRef`|Upozorní, když se `mdModuleRef` token přesune.|  
|`MDNotifyNameSpace`|Upozorní, když se `mdNameSpace` token přesune.|  
|`MDNotifyAssemblyRef`|Upozorní, když se `mdAssemblyRef` token přesune.|  
|`MDNotifyFile`|Upozorní, když se `mdFile` token přesune.|  
|`MDNotifyExportedType`|Upozorní, když se `mdExportedType` token přesune.|  
|`MDNotifyResource`|Upozorní, když se `mdManifestResource` token přesune.|  
  
## <a name="remarks"></a>Poznámky  
 Token se dá při sloučení metadat znovu namapovat (tj., to je přesunutý).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorHdr. h  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Výčty pro metadata](metadata-enumerations.md)
