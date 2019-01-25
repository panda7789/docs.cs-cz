---
title: Authenticode (referenční dokumentace nespravovaného rozhraní API)
ms.date: 03/30/2017
ms.assetid: 7e8cc303-6e77-4116-aa8b-7ea297a3a467
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ee0aca905c488bc3d285d69e431e79740bf8b7b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54623761"
---
# <a name="authenticode-unmanaged-api-reference"></a>Authenticode (referenční dokumentace nespravovaného rozhraní API)
Podporuje modul vytváření a ověřování Authenticode XrML licence.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Funkce _AxlGetIssuerPublicKeyHash](../../../../docs/framework/unmanaged-api/authenticode/axlgetissuerpublickeyhash-function.md)  
 Načte hodnotu hash SHA-1 veřejný klíč přidružený privátní klíč, který se používá k podepsání zadaný certifikát.  
  
 [Funkce _AxlPublicKeyBlobToPublicKeyToken](../../../../docs/framework/unmanaged-api/authenticode/axlpublickeyblobtopublickeytoken-function.md)  
 Vypočítá silným názvem token veřejného klíče z CSP publickeyblob – formátu.  
  
 [Funkce _AxlRSAKeyValueToPublicKeyToken](../../../../docs/framework/unmanaged-api/authenticode/axlrsakeyvaluetopublickeytoken-function.md)  
 Převede operace modulo a Exponent token veřejného klíče silného názvu.  
  
 [Funkce CertFreeAuthenticodeSignerInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodesignerinfo-function.md)  
 Uvolní prostředky přidělené struktura AXL_AUTHENTICODE_SIGNER_INFO.  
  
 [Funkce CertFreeAuthenticodeTimestamperInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodetimestamperinfo-function.md)  
 Uvolní prostředky přidělené struktura AXL_AUTHENTICODE_TIMESTAMPER_INFO.  
  
 [Funkce CertTimestampAuthenticodeLicense](../../../../docs/framework/unmanaged-api/authenticode/certtimestampauthenticodelicense-function.md)  
 Označit časovou značkou licenci Authenticode XrML vytvořené CertCreateAuthenticodeLicense.  
  
 [Funkce CertVerifyAuthenticodeLicense](../../../../docs/framework/unmanaged-api/authenticode/certverifyauthenticodelicense-function.md)  
 Ověří platnost licence k Authenticode XrML.  
  
 [Struktura AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md)  
 Definuje informace o podpisu Authenticode.  
  
 [Struktura AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md)  
 Definuje informace o čase stamper Authenticode.  
  
## <a name="see-also"></a>Viz také:
- [Referenční informace o nespravovaném rozhraní API](../../../../docs/framework/unmanaged-api/index.md)
