---
title: Funkce CertVerifyAuthenticodeLicense
ms.date: 03/30/2017
api_name:
- CertVerifyAuthenticodeLicense
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 00118de7-33c6-41c4-8e1f-5d5e35e0da83
ms.openlocfilehash: 7cd25a24533b04dc45ee734f9e9639391311405a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099732"
---
# <a name="certverifyauthenticodelicense-function"></a>Funkce CertVerifyAuthenticodeLicense
Ověřuje platnost licence na technologii Authenticode pro technologii Authenticode.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CertVerifyAuthenticodeLicense (  
    [in]   PCRYPT_DATA_BLOB                   pLicenseBlob,  
    [in]   OPTIONAL DWORD                     dwFlags,  
    [out]  PAXL_AUTHENTICODE_SIGNER_INFO      pSignerInfo,  
    [out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pLicenseBlob`  
 pro Licence Authenticode pro technologii Authenticode, která se má ověřit.  
  
 Podívejte se na strukturu [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) .  
  
 `dwFlags`  
 pro Volitelné. Kombinace následujících hodnot:  
  
- AXL_REVOCATION_NO_CHECK  
  
- AXL_REVOCATION_CHECK_END_CERT_ONLY  
  
- AXL_REVOCATION_CHECK_ENTIRE_CHAIN  
  
- AXL_URL_CACHE_ONLY_RETRIEVAL  
  
- AXL_LIFETIME_SIGNING  
  
- AXL_TRUST_MICROSOFT_ROOT_ONLY  
  
 `pSignerInfo`  
 mimo Pro získání informací o podepisující osobě. Pokud licence není podepsaná, `dwError` je nastavená na TRUST_E_NOSIGNATURE. Je zodpovědností volajícího uvolnit prostředky pomocí funkce [CertFreeAuthenticodeSignerInfo](certfreeauthenticodesignerinfo-function.md) po použití.  
  
 Viz [Struktura AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md).  
  
 `pTimestamperInfo`  
 mimo Pro získání informací o časovém razítku, pokud je k dispozici. Pokud licence nebyla označena časovým razítkem, `dwError` je nastavená na TRUST_E_NOSIGNATURE. Je zodpovědností volajícího uvolnit prostředky pomocí funkce [CertFreeAuthenticodeTimestamperInfo](certfreeauthenticodetimestamperinfo-function.md) po použití.  
  
 Viz [Struktura AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md).  
  
## <a name="return-value"></a>Návratová hodnota  
 Pokud je úspěšná, vrátí `S_OK`. V opačném případě vrátí kód chyby.  
  
## <a name="see-also"></a>Viz také:

- [Authenticode](index.md)
- [GetHashFromHandle – metoda](../hosting/iclrstrongname-gethashfromhandle-method.md)
- [ICLRStrongName – rozhraní](../hosting/iclrstrongname-interface.md)
