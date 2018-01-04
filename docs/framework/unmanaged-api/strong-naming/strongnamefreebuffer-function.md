---
title: "StrongNameFreeBuffer – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameFreeBuffer
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: StrongNameFreeBuffer
helpviewer_keywords: StrongNameFreeBuffer function [.NET Framework strong naming]
ms.assetid: eda21ecf-4734-4f92-aaba-9f34884385db
topic_type: apiref
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f4f5bde035b0ab9df07bb0ab709a67ae1a4cff3f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamefreebuffer-function"></a>StrongNameFreeBuffer – funkce
Uvolní paměť, který byl přidělen s předchozí volání funkce silným názvem, jako [strongnamegetpublickey –](../../../../docs/framework/unmanaged-api/strong-naming/strongnamegetpublickey-function.md), [strongnametokenfrompublickey –](../../../../docs/framework/unmanaged-api/strong-naming/strongnametokenfrompublickey-function.md), nebo [strongnamesignaturegeneration – ](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturegeneration-function.md).  
  
 Tato funkce je zastaralá. Použití [iclrstrongname::strongnamefreebuffer –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) metoda místo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
VOID StrongNameFreeBuffer (   
   [in] BYTE   *pbMemory  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbMemory`  
 [v] Ukazatel na paměť uvolnit.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** StrongName.h  
  
 **Knihovna:** zahrnuty jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [StrongNameFreeBuffer – metoda](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)  
 [ICLRStrongName – rozhraní](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
