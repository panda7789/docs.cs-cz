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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6c2bb6f0324c461f59bd98a70333b176e79a16a6
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039595"
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
 mimo Ukazatel na CRYPT_DATA_BLOB pro příjem signatury časového razítka kódovaného ve formátu base64. Je zodpovědností volajícího, `pTimestampSignatureBlob` aby `HepFree()` po použití zadarmo ->. `pbData` Podívejte se na strukturu [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .  
  
## <a name="remarks"></a>Poznámky  
 Podpisem časového razítka je ve skutečnosti zpráva typu PKCS #7 SignedData, jejíž obsah je binární forma SignatureValue z podpisu licence. V podstatě to funguje jako počítadlo signatury licence.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK`Pokud je funkce úspěšná. V opačném případě vrátí kód chyby.  
  
## <a name="see-also"></a>Viz také:

- [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
