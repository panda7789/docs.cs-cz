---
title: Authenticode (referenční dokumentace nespravovaného rozhraní API)
ms.date: 03/30/2017
ms.assetid: 7e8cc303-6e77-4116-aa8b-7ea297a3a467
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d2c0163d03a19a7bc00ae705fd633ef4f0880082
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70776554"
---
# <a name="authenticode-unmanaged-api-reference"></a>Authenticode (referenční dokumentace nespravovaného rozhraní API)
Podporuje modul pro vytváření a ověřování licencí Authenticode.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Funkce _AxlGetIssuerPublicKeyHash](axlgetissuerpublickeyhash-function.md)  
 Načte hodnotu hash SHA-1 veřejného klíče přidruženého k privátnímu klíči, který se používá k podepsání zadaného certifikátu.  
  
 [Funkce _AxlPublicKeyBlobToPublicKeyToken](axlpublickeyblobtopublickeytoken-function.md)  
 Vypočítá token veřejného klíče se silným názvem z formátu PublicKeyBlob – CSP.  
  
 [Funkce _AxlRSAKeyValueToPublicKeyToken](axlrsakeyvaluetopublickeytoken-function.md)  
 Převede zbytek a exponent na token veřejného klíče silného názvu.  
  
 [Funkce CertFreeAuthenticodeSignerInfo](certfreeauthenticodesignerinfo-function.md)  
 Uvolní prostředky přidělené pro strukturu AXL_AUTHENTICODE_SIGNER_INFO.  
  
 [Funkce CertFreeAuthenticodeTimestamperInfo](certfreeauthenticodetimestamperinfo-function.md)  
 Uvolní prostředky přidělené pro strukturu AXL_AUTHENTICODE_TIMESTAMPER_INFO.  
  
 [Funkce CertTimestampAuthenticodeLicense](certtimestampauthenticodelicense-function.md)  
 Tato časová razítka mají licenci na technologii Authenticode vytvořenou pomocí CertCreateAuthenticodeLicense.  
  
 [Funkce CertVerifyAuthenticodeLicense](certverifyauthenticodelicense-function.md)  
 Ověřuje platnost licence na technologii Authenticode pro technologii Authenticode.  
  
 [Struktura AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md)  
 Definuje přihlašovací údaje Authenticode.  
  
 [Struktura AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md)  
 Definuje informace o časovém razítku technologie Authenticode.  
  
## <a name="see-also"></a>Viz také:

- [Referenční informace o nespravovaném rozhraní API](../index.md)
