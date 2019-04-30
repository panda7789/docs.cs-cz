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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1b2535441da173ee13653c68f25039fd1431261a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948951"
---
# <a name="axlpublickeyblobtopublickeytoken-function"></a>Funkce _AxlPublicKeyBlobToPublicKeyToken
Vypočítá silným názvem token veřejného klíče z CSP publickeyblob – formátu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT _AxlPublicKeyBlobToPublicKeyToken (  
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,  
    [out] LPWSTR                 *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pCspPublicKeyBlob`  
 [in] Zprostředkovatel kryptografických služeb blob veřejného klíče.  
  
 `ppwszPublicKeyHash`  
 [out] Ukazatel na WCHAR * pro příjem hexadecimální zakódovaná hodnota hash veřejného klíče.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK` Pokud je funkce úspěšná; v opačném případě `S_FALSE`.  
  
## <a name="see-also"></a>Viz také:

- [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
