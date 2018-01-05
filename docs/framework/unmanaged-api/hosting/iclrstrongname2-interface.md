---
title: "ICLRStrongName2 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRStrongName2
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRStrongName2
helpviewer_keywords: ICLRStrongName2 interface [.NET Framework hosting]
ms.assetid: 9f098a74-201e-4628-a468-8dee9ab99b4a
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d4e1274f675ae9289faa6c530d34cd61d033aa07
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrstrongname2-interface"></a>ICLRStrongName2 – rozhraní
Poskytuje možnost vytvořit silné názvy pomocí skupiny zabezpečení (SHA-256, SHA-384 a SHA-512) algoritmy Hash SHA-2.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[StrongNameGetPublicKeyEx – metoda](../../../../docs/framework/unmanaged-api/hosting/strongnamegetpublickeyex-method.md)|Získá veřejný klíč z páru veřejného a privátního klíče RSA a určuje algoritmus hash a algoritmus podpisu.|  
|[StrongNameSignatureVerificationEx2 – metoda](../../../../docs/framework/unmanaged-api/hosting/strongnamesignatureverificationex2-method.md)|Ověří podpis silně pojmenované sestavení a poskytuje mapování z klíče ECMA skutečné klíče.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** MetaHost.h  
  
 **Knihovna:** zahrnuty jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]
