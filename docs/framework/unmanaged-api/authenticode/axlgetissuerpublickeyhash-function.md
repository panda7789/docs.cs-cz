---
title: Funkce _AxlGetIssuerPublicKeyHash
ms.date: 03/30/2017
api_name:
- _AxlGetIssuerPublicKeyHash
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: fb626b41-b888-4625-84c3-2c02b5e3866f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: de55594db68e084009a095a083e065fbd0b8f0df
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741326"
---
# <a name="axlgetissuerpublickeyhash-function"></a>\_AxlGetIssuerPublicKeyHash – funkce
Načte hodnotu hash SHA-1 veřejný klíč přidružený privátní klíč, který se používá k podepsání zadaný certifikát.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT _AxlGetIssuerPublicKeyHash (  
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,  
    [out] LPWSTR                *ppwszPublicKeyHash  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pChainContext`  
 [in] Zprostředkovatel kryptografických služeb blob veřejného klíče. Zobrazit [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) struktury.  
  
 `ppwszPublicKeyHash`  
 [out] Ukazatel na WCHAR * pro příjem šestnáctkově zakódovaného token veřejného klíče.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK` Pokud je funkce úspěšná; v opačném případě `S_FALSE`.  
  
## <a name="see-also"></a>Viz také:

- [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
