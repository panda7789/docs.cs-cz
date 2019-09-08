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
ms.openlocfilehash: 4b101a912eb58ed14f81d847ea2fd6ce9f22c065
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787090"
---
# <a name="_axlgetissuerpublickeyhash-function"></a>\_AxlGetIssuerPublicKeyHash – funkce
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
 `S_OK`Pokud je funkce úspěšná; v `S_FALSE`opačném případě.  
  
## <a name="see-also"></a>Viz také:

- [Authenticode](index.md)
