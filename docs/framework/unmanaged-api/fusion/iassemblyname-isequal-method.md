---
title: "IAssemblyName::IsEqual – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAssemblyName.IsEqual
api_location: fusion.dll
api_type: COM
f1_keywords: IAssemblyName::IsEqual
helpviewer_keywords:
- IsEqual method [.NET Framework fusion]
- IAssemblyName::IsEqual method [.NET Framework fusion]
ms.assetid: 6dfc220f-d0d4-45b3-bfce-5829f817766f
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 51a4fbe005a8e270b9fe6767ae5173bd027a191b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iassemblynameisequal-method"></a>IAssemblyName::IsEqual – metoda
Určuje, zda je zadané [iassemblyname –](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) objekt rovná to `IAssemblyName`, podle příznaky zadaný porovnání.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT IsEqual (  
    [in] IAssemblyName  *pName,  
    [in] DWORD          dwCmpFlags  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pName`  
 [v] `IAssemblyName` Objekt, do které chcete porovnat `IAssemblyName`.  
  
 `dwCmpFlags`  
 [v] Bitovou kombinaci [ASM_CMP_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cmp-flags-enumeration.md) hodnoty, které ovlivňují porovnání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Fusion.h  
  
 **NET Framework verze:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Iassemblyname – rozhraní](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [Výčty fúzí](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
