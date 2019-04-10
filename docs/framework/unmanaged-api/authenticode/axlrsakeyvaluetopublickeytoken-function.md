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
ms.openlocfilehash: 49476a4417e5431842f8e2ba0371c53c5c9f03e9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207822"
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
  
## <a name="parameters"></a>Parametry  
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
