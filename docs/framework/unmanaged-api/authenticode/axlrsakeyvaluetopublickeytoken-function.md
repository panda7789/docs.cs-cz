---
title: _AxlRSAKeyValueToPublicKeyToken – funkce
ms.date: 03/30/2017
api_name:
- _AxlRSAKeyValueToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: d60f19fe-7bec-47ba-b60e-ba9ce66abf8c
ms.openlocfilehash: 1f53df33a65d3f75b7574eda3507e370c2e086ac
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099821"
---
# <a name="_axlrsakeyvaluetopublickeytoken-function"></a>\_funkce AxlRSAKeyValueToPublicKeyToken

Převede zbytek a exponent na token veřejného klíče silného názvu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pModulusBlob`  
 pro Objekt BLOB v kódování Base64 (z prvku \<modul >).  Podívejte se na strukturu [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .  
  
 `pExponentBlob`  
 pro Objekt BLOB exponentem kódovaný ve formátu Base64 (z > elementu \<exponent). Podívejte se na strukturu [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .  
  
 `ppwszPublicKeyToken`  
 mimo Ukazatel na WCHAR * pro příjem šestnáctkově zakódovaného tokenu veřejného klíče.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`, zda je funkce úspěšná. V opačném případě vrátí kód chyby.  
  
## <a name="see-also"></a>Viz také:

- [Authenticode](index.md)
