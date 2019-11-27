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
ms.openlocfilehash: 411fad0accb59431f776c5bd66e8bd3027ddd907
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450155"
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
  
|Člen|Popis|  
|------------|-----------------|  
|`MDNotifyDefault`|Upozorní, když se přesunou `mdTypeRef`, `mdMethodDef`, `mdMemberRef`nebo tokeny `mdFieldDef`.|  
|`MDNotifyAll`|Upozorní, když se libovolný token přesune.|  
|`MDNotifyNone`|Neupozorňovat při přesunu tokenů|  
|`MDNotifyMethodDef`|Upozorní, když se přesune token `mdMethodDef`.|  
|`MDNotifyMemberRef`|Upozorní, když se přesune token `mdMemberRef`.|  
|`MDNotifyFieldDef`|Upozorní, když se přesune token `mdFieldDef`.|  
|`MDNotifyTypeRef`|Upozorní, když se přesune token `mdTypeRef`.|  
|`MDNotifyTypeDef`|Upozorní, když se přesune token `mdTypeDef`.|  
|`MDNotifyParamDef`|Upozorní, když se přesune token `mdParamDef`.|  
|`MDNotifyInterfaceImpl`|Upozorní, když se přesune token `mdInterfaceImpl`.|  
|`MDNotifyProperty`|Upozorní, když se přesune token `mdProperty`.|  
|`MDNotifyEvent`|Upozorní, když se přesune token `mdEvent`.|  
|`MDNotifySignature`|Upozorní, když se přesune token `mdSignature`.|  
|`MDNotifyTypeSpec`|Upozorní, když se přesune token `mdTypeSpec`.|  
|`MDNotifyCustomAttribute`|Upozorní, když se přesune token `mdCustomAttribute`.|  
|`MDNotifySecurityValue`|Upozorní, když se přesune token `mdSecurityValue`.|  
|`MDNotifyPermission`|Upozorní, když se přesune token `mdPermission`.|  
|`MDNotifyModuleRef`|Upozorní, když se přesune token `mdModuleRef`.|  
|`MDNotifyNameSpace`|Upozorní, když se přesune token `mdNameSpace`.|  
|`MDNotifyAssemblyRef`|Upozorní, když se přesune token `mdAssemblyRef`.|  
|`MDNotifyFile`|Upozorní, když se přesune token `mdFile`.|  
|`MDNotifyExportedType`|Upozorní, když se přesune token `mdExportedType`.|  
|`MDNotifyResource`|Upozorní, když se přesune token `mdManifestResource`.|  
  
## <a name="remarks"></a>Poznámky  
 Token se dá při sloučení metadat znovu namapovat (tj., to je přesunutý).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorHdr. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
