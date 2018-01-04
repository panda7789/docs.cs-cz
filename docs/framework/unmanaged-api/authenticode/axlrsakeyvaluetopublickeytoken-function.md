---
title: Funkce _AxlRSAKeyValueToPublicKeyToken
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: _AxlRSAKeyValueToPublicKeyToken
api_location: clr.dll
api_type: DLLExport
ms.assetid: d60f19fe-7bec-47ba-b60e-ba9ce66abf8c
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b1380f658d9c154d9ea41228cace5f9a3eed39b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="axlrsakeyvaluetopublickeytoken-function"></a>Funkce _AxlRSAKeyValueToPublicKeyToken
Převede Exponent a Modulus silný název tokenu veřejného klíče.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pModulusBlob`  
 [v] Objekt blob kódováním base64 numerického zbytku (z \<numerického zbytku > elementu).  Najdete v článku [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) struktury.  
  
 `pExponentBlob`  
 [v] Objekt blob Exponent kódováním base64 (z \<Exponent > elementu). Najdete v článku [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) struktury.  
  
 `ppwszPublicKeyToken`  
 [out] Ukazatel na WCHAR * přijímat kódováním šestnáctkově token veřejného klíče.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`Pokud funkci se zdaří. Jinak vrátí kód chyby.  
  
## <a name="see-also"></a>Viz také  
 [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
