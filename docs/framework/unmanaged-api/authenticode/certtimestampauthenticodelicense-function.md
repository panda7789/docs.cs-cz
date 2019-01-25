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
ms.openlocfilehash: 9987640f988f2239a01d2dfdbcd6b1684579d8bc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54601504"
---
# <a name="certtimestampauthenticodelicense-function"></a>Funkce CertTimestampAuthenticodeLicense
Časová razítka na Authenticode XrML licence.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CertTimestampAuthenticodeLicense (  
    [in]  PCRYPT_DATA_BLOB   pSignedLicenseBlob,  
    [in]  LPCWSTR            pwszTimestampURI,  
    [out] PCRYPT_DATA_BLOB   pTimestampSignatureBlob  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pSignedLicenseBlob`  
 [in] Podepsané Authenticode XrML licenci, která má být opatřená časovým razítkem. Zobrazit [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) struktury.  
  
 `pwszTimestampURI`  
 [in] Identifikátor URI serveru časového razítka.  
  
 `pTimestampSignatureBlob`  
 [out] Ukazatel na CRYPT_DATA_BLOB přijímat časové razítko podpis s kódováním base64. Je odpovědností volajícího uvolnit `pTimestampSignatureBlob` -> `pbData` s `HepFree()` po použití. Zobrazit [CRYPTOAPI_BLOB](/windows/desktop/api/dpapi/ns-dpapi-_cryptoapi_blob) struktury.  
  
## <a name="remarks"></a>Poznámky  
 Podpis časového razítka je ve skutečnosti zprávu PKCS #7 SignedData jehož obsah je binární forma SignatureValue z podpisu licence. V podstatě slouží jako protipodpisu licence.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK` Pokud je funkce úspěšná. V opačném případě vrátí kód chyby.  
  
## <a name="see-also"></a>Viz také:
- [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
