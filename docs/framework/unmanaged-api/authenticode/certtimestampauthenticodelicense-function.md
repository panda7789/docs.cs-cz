---
title: Funkce CertTimestampAuthenticodeLicense
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CertTimestampAuthenticodeLicense
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: d468325a-21c5-43ce-8567-84e342b22308
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 53241a459f561bdfd8fc5cb077cb8384f1d906b9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
 `S_OK`Pokud funkci se zdaří. Jinak vrátí kód chyby.  
  
## <a name="see-also"></a>Viz také  
 [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
