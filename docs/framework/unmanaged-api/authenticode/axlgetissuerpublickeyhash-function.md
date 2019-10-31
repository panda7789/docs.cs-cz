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
ms.openlocfilehash: 6d5ad995b55a3cde6363b297df6b8faf72689468
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132492"
---
# <a name="_axlgetissuerpublickeyhash-function"></a>\_funkce AxlGetIssuerPublicKeyHash
Načte hodnotu hash SHA-1 veřejného klíče přidruženého k privátnímu klíči, který se používá k podepsání zadaného certifikátu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT _AxlGetIssuerPublicKeyHash (  
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,  
    [out] LPWSTR                *ppwszPublicKeyHash  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pChainContext`  
 pro Objekt blob veřejného klíče CSP Podívejte se na strukturu [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .  
  
 `ppwszPublicKeyHash`  
 mimo Ukazatel na WCHAR * pro příjem šestnáctkově zakódovaného tokenu veřejného klíče.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`, zda je funkce úspěšná; jinak `S_FALSE`.  
  
## <a name="see-also"></a>Viz také:

- [Authenticode](index.md)
