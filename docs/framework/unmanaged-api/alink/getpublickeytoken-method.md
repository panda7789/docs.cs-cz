---
title: GetPublicKeyToken – metoda
ms.date: 03/30/2017
api_name:
- IALink2.GetPublicKeyToken
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetPublicKeyToken
helpviewer_keywords:
- GetPublicKeyToken method
ms.assetid: 4a16374c-94b0-47b0-9fed-88c2b0cdccd4
topic_type:
- apiref
ms.openlocfilehash: 2e7ed4e1529104db30b0b06665f74342d9ca9a01
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447239"
---
# <a name="getpublickeytoken-method"></a>GetPublicKeyToken – metoda
Načte token veřejného klíče pro daný soubor klíče nebo kontejneru klíčů.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetPublicKeyToken(  
    LPCWSTR pszKeyFile,  
    LPCWSTR pszKeyContainer,  
    void* pvPublicKeyToken,  
    DWORD* pcbPublicKeyToken  
) PURE;  
```  
  
## <a name="parameters"></a>Parametry  
 `pszKeyFile`  
 Název souboru klíče  
  
 `pszKeyContainer`  
 Název kontejneru klíčů.  
  
 `pvPublicKeyToken`  
 Adresa, kam se má uložit klíč tokenu  
  
 `pcbPublicKeyToken`  
 Určuje velikost vyrovnávací paměti v bajtech vyznačených `pvPublicKeyToken`. Při návratu obsahuje skutečný počet použitých bajtů.  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK, pokud je metoda úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 Vyžaduje ALink. h.  
  
## <a name="see-also"></a>Viz také:

- [IALink2 – rozhraní](ialink2-interface.md)
- [IALink – rozhraní](ialink-interface.md)
- [Rozhraní API ALink](index.md)
