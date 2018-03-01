---
title: Funkce _AxlPublicKeyBlobToPublicKeyToken
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
- _AxlPublicKeyBlobToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 2d92a746-d68c-4f53-a16e-727f071a2d80
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7c9dfd42d0908032ed9a652f6f4f5736ba775ce8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="axlpublickeyblobtopublickeytoken-function"></a>Funkce _AxlPublicKeyBlobToPublicKeyToken
Vypočítá silným názvem token veřejného klíče z formátu CSP PUBLICKEYBLOB.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT _AxlPublicKeyBlobToPublicKeyToken (  
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,  
    [out] LPWSTR                 *ppwszPublicKeyToken  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pCspPublicKeyBlob`  
 [v] Zprostředkovatel kryptografických služeb veřejného klíče objektu blob.  
  
 `ppwszPublicKeyHash`  
 [out] Ukazatel na WCHAR * přijímat kódováním šestnáctkově hodnota hash veřejného klíče.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`Pokud funkci úspěšně. v opačném případě `S_FALSE`.  
  
## <a name="see-also"></a>Viz také  
 [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
