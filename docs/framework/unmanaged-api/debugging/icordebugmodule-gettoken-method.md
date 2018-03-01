---
title: "ICorDebugModule::GetToken – metoda"
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
- ICorDebugModule.GetToken
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetToken
helpviewer_keywords:
- ICorDebugModule::GetToken method [.NET Framework debugging]
- GetToken method, ICorDebugModule interface [.NET Framework debugging]
ms.assetid: f759f87a-18ae-4c1a-8300-29b803432d0a
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 651612b07a69f0cbcc9c818fe7627bf496f6d68e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodulegettoken-method"></a>ICorDebugModule::GetToken – metoda
Získá token pro položku tabulky pro tento modul.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetToken(  
    [out] mdModule *pToken  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pToken`  
 [out] Ukazatel `mdModule` token, který odkazuje na metadata modulu.  
  
## <a name="remarks"></a>Poznámky  
 Token se dá předat do [imetadataimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), [imetadataimport2 –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md), a [imetadataassemblyimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) rozhraní import metadat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Metadata](../../../../docs/framework/unmanaged-api/metadata/index.md)
