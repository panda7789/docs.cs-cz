---
title: Funkce _AxlGetIssuerPublicKeyHash
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
- _AxlGetIssuerPublicKeyHash
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: fb626b41-b888-4625-84c3-2c02b5e3866f
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fee2b3e0e74ec13009a9b02d226c6a99b0e2f34b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="axlgetissuerpublickeyhash-function"></a>Funkce _AxlGetIssuerPublicKeyHash
Načte hodnotu hash SHA-1 veřejný klíč přidružený privátní klíč, který se používá k podepisování zadaný certifikát.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT _AxlGetIssuerPublicKeyHash (  
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,  
    [out] LPWSTR                *ppwszPublicKeyHash  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pChainContext`  
 [v] Zprostředkovatel kryptografických služeb veřejného klíče objektu blob. Najdete v článku [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) struktury.  
  
 `ppwszPublicKeyHash`  
 [out] Ukazatel na WCHAR * přijímat kódováním šestnáctkově token veřejného klíče.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`Pokud funkci úspěšně. v opačném případě `S_FALSE`.  
  
## <a name="see-also"></a>Viz také  
 [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
