---
title: Funkce _AxlRSAKeyValueToPublicKeyToken
ms.date: 03/30/2017
api_name:
- _AxlRSAKeyValueToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: d60f19fe-7bec-47ba-b60e-ba9ce66abf8c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a340af9ba196dbcd8618afdd83bcf7e56124bf7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54529905"
---
# <a name="axlrsakeyvaluetopublickeytoken-function"></a>\_AxlRSAKeyValueToPublicKeyToken – funkce

Převede operace modulo a Exponent token veřejného klíče silného názvu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
### <a name="parameters"></a>Parametry  
 `pModulusBlob`  
 [in] Tento objekt blob s kódováním base64 numerického zbytku (z \<numerického zbytku > element).  Zobrazit [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) struktury.  
  
 `pExponentBlob`  
 [in] Exponent blob s kódováním base64 (z \<Exponent > element). Zobrazit [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) struktury.  
  
 `ppwszPublicKeyToken`  
 [out] Ukazatel na WCHAR * pro příjem šestnáctkově zakódovaného token veřejného klíče.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK` Pokud je funkce úspěšná. V opačném případě vrátí kód chyby.  
  
## <a name="see-also"></a>Viz také:
- [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
