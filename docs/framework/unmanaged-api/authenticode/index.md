---
title: Authenticode (referenční dokumentace nespravovaného rozhraní API)
ms.date: 03/30/2017
ms.assetid: 7e8cc303-6e77-4116-aa8b-7ea297a3a467
ms.openlocfilehash: 1b8b2222950c75f7f9d2ec2704f722087645cd7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73132455"
---
# <a name="authenticode-unmanaged-api-reference"></a>Authenticode (referenční dokumentace nespravovaného rozhraní API)
Podporuje modul pro vytváření a ověřování licencí Authenticode XrML.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Funkce _AxlGetIssuerPublicKeyHash](axlgetissuerpublickeyhash-function.md)  
 Načte hašiš SHA-1 veřejného klíče přidruženého k soukromému klíči, který se používá k podepsání zadaného certifikátu.  
  
 [Funkce _AxlPublicKeyBlobToPublicKeyToken](axlpublickeyblobtopublickeytoken-function.md)  
 Vypočítá token veřejného klíče silného názvu z formátu CSP PUBLICKEYBLOB.  
  
 [Funkce _AxlRSAKeyValueToPublicKeyToken](axlrsakeyvaluetopublickeytoken-function.md)  
 Převede modul a exponent na token veřejného klíče silného názvu.  
  
 [Funkce CertFreeAuthenticodeSignerInfo](certfreeauthenticodesignerinfo-function.md)  
 Uvolní prostředky přidělené pro AXL_AUTHENTICODE_SIGNER_INFO strukturu.  
  
 [Funkce CertFreeAuthenticodeTimestamperInfo](certfreeauthenticodetimestamperinfo-function.md)  
 Uvolní prostředky přidělené pro AXL_AUTHENTICODE_TIMESTAMPER_INFO strukturu.  
  
 [Funkce CertTimestampAuthenticodeLicense](certtimestampauthenticodelicense-function.md)  
 Časová razítka licence Authenticode XrML vytvořená společností CertCreateAuthenticodeLicense.  
  
 [Funkce CertVerifyAuthenticodeLicense](certverifyauthenticodelicense-function.md)  
 Ověří platnost licence Authenticode XrML.  
  
 [Struktura AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md)  
 Definuje informace o autorovi podpisu Authenticode.  
  
 [Struktura AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md)  
 Definuje informace o časovém razítku Authenticode.  
  
## <a name="see-also"></a>Viz také

- [Nespravované rozhraní API](../index.md)
