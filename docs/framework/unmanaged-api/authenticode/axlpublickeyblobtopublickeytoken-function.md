---
title: Funkce _AxlPublicKeyBlobToPublicKeyToken
ms.date: 03/30/2017
api_name:
- _AxlPublicKeyBlobToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 2d92a746-d68c-4f53-a16e-727f071a2d80
ms.openlocfilehash: 33b8f47813a3bf43bd69741c9febb150fa3a92e3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099897"
---
# <a name="_axlpublickeyblobtopublickeytoken-function"></a>\_funkce AxlPublicKeyBlobToPublicKeyToken
Vypočítá token veřejného klíče se silným názvem z formátu PublicKeyBlob – CSP.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT _AxlPublicKeyBlobToPublicKeyToken (  
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,  
    [out] LPWSTR                 *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pCspPublicKeyBlob`  
 pro Objekt blob veřejného klíče CSP  
  
 `ppwszPublicKeyHash`  
 mimo Ukazatel na WCHAR * pro příjem šestnáctkově zakódované hodnoty hash veřejného klíče.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`, zda je funkce úspěšná; jinak `S_FALSE`.  
  
## <a name="see-also"></a>Viz také:

- [Authenticode](index.md)
