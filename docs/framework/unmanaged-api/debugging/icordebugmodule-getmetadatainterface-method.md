---
title: "ICorDebugModule::GetMetaDataInterface – metoda"
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
- ICorDebugModule.GetMetaDataInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetMetaDataInterface
helpviewer_keywords:
- ICorDebugModule::GetMetaDatainterface method [.NET Framework debugging]
- GetMetaDatainterface method [.NET Framework debugging]
ms.assetid: 30d906f2-cf35-4fa9-9d4c-0c31b58c9f3a
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d374b83155ccc8511c6e3217a8a49819d81a7d48
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodulegetmetadatainterface-method"></a>ICorDebugModule::GetMetaDataInterface – metoda
Získá objekt rozhraní metadat, který můžete použít k prozkoumání metadata pro modul.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetMetaDataInterface (  
    [in] REFIID      riid,  
    [out] IUnknown **ppObj  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `riid`  
 [v] ID odkazu, který určuje rozhraní metadat.  
  
 `ppObj`  
 [out] Ukazatel na adresu `T:IUnknown` objekt, který je jedním z [rozhraní metadat](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).  
  
## <a name="remarks"></a>Poznámky  
 Ladicí program můžete použít `GetMetaDataInterface` metoda vytvořit kopii původní metadata pro modul, který musí to, aby bylo možné upravit tento modul. Ladicí program volání `GetMetaDataInterface` získat [imetadataemit –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md) rozhraní objektu pro modul, pak zavolá [imetadataemit::savetomemory –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-savetomemory-method.md) pro uložení kopie metadat modulu do paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Metadata](../../../../docs/framework/unmanaged-api/metadata/index.md)
