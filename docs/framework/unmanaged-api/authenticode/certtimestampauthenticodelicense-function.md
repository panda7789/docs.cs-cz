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
ms.openlocfilehash: b110adac8c1ae68a3918a9e0fdf3f3eb4d017f0f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406205"
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
 [v] Podepsaný licence Authenticode XrML být časovým razítkem. Najdete v článku [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) struktury.  
  
 `pwszTimestampURI`  
 [v] Identifikátor URI serveru časového razítka.  
  
 `pTimestampSignatureBlob`  
 [out] Ukazatel na CRYPT_DATA_BLOB přijímat časové razítko podpis kódováním base64. Je zodpovědností volajícího k bezplatným `pTimestampSignatureBlob` -> `pbData` s `HepFree()` po použití. Najdete v článku [CRYPTOAPI_BLOB](http://msdn.microsoft.com/library/windows/desktop/aa380238.aspx) struktury.  
  
## <a name="remarks"></a>Poznámky  
 Podpis časové razítko je ve skutečnosti PKCS #7 SignedData zpráva, jejíž obsah je binární formu SignatureValue z podpisu s licencí. V podstatě to funguje jako kontrolní podpis licence.  
  
## <a name="return-value"></a>Návratová hodnota  
 `S_OK` Pokud funkci se zdaří. Jinak vrátí kód chyby.  
  
## <a name="see-also"></a>Viz také  
 [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
