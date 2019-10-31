---
title: Funkce CertTimestampAuthenticodeLicense
ms.date: 03/30/2017
api_name:
- CertTimestampAuthenticodeLicense
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: d468325a-21c5-43ce-8567-84e342b22308
ms.openlocfilehash: 3c5e803c874e1254510f75189846d7cb12cb1ee2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132477"
---
# <a name="certtimestampauthenticodelicense-function"></a>Funkce CertTimestampAuthenticodeLicense
Časová razítka licence XrML technologie Authenticode.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CertTimestampAuthenticodeLicense (  
    [in]  PCRYPT_DATA_BLOB   pSignedLicenseBlob,  
    [in]  LPCWSTR            pwszTimestampURI,  
    [out] PCRYPT_DATA_BLOB   pTimestampSignatureBlob  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pSignedLicenseBlob`  
 pro Podepsaná licence technologie Authenticode pro technologii Authenticode, která bude označená časovým razítkem Podívejte se na strukturu [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .  
  
 `pwszTimestampURI`  
 pro Identifikátor URI serveru časového razítka.  
  
 `pTimestampSignatureBlob`  
 mimo Ukazatel na CRYPT_DATA_BLOB pro příjem signatury časového razítka kódovaného ve formátu base64. Je zodpovědností volajícího uvolnit `pTimestampSignatureBlob`->`pbData` se `HepFree()` po použití. Podívejte se na strukturu [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .  
  
## <a name="remarks"></a>Poznámky  
 Podpisem časového razítka je ve skutečnosti zpráva typu PKCS #7 SignedData, jejíž obsah je binární forma SignatureValue z podpisu licence. V podstatě to funguje jako počítadlo signatury licence.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`, zda je funkce úspěšná. V opačném případě vrátí kód chyby.  
  
## <a name="see-also"></a>Viz také:

- [Authenticode](index.md)
