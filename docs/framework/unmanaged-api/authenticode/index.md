---
title: Authenticode (referenční dokumentace nespravovaného rozhraní API)
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 7e8cc303-6e77-4116-aa8b-7ea297a3a467
caps.latest.revision: 4
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0b790064ef64ab44f3798a62d5dbf004f0f0bba6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="authenticode-unmanaged-api-reference"></a>Authenticode (referenční dokumentace nespravovaného rozhraní API)
Podporuje modul vytvoření a ověření Authenticode XrML licence.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Funkce _AxlGetIssuerPublicKeyHash](../../../../docs/framework/unmanaged-api/authenticode/axlgetissuerpublickeyhash-function.md)  
 Načte hodnotu hash SHA-1 veřejný klíč přidružený privátní klíč, který se používá k podepisování zadaný certifikát.  
  
 [Funkce _AxlPublicKeyBlobToPublicKeyToken](../../../../docs/framework/unmanaged-api/authenticode/axlpublickeyblobtopublickeytoken-function.md)  
 Vypočítá silným názvem token veřejného klíče z formátu CSP PUBLICKEYBLOB.  
  
 [Funkce _AxlRSAKeyValueToPublicKeyToken](../../../../docs/framework/unmanaged-api/authenticode/axlrsakeyvaluetopublickeytoken-function.md)  
 Převede Exponent a Modulus silný název tokenu veřejného klíče.  
  
 [Funkce CertFreeAuthenticodeSignerInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodesignerinfo-function.md)  
 Uvolní prostředky přidělené pro struktura AXL_AUTHENTICODE_SIGNER_INFO.  
  
 [Funkce CertFreeAuthenticodeTimestamperInfo](../../../../docs/framework/unmanaged-api/authenticode/certfreeauthenticodetimestamperinfo-function.md)  
 Uvolní prostředky přidělené pro struktura AXL_AUTHENTICODE_TIMESTAMPER_INFO.  
  
 [Funkce CertTimestampAuthenticodeLicense](../../../../docs/framework/unmanaged-api/authenticode/certtimestampauthenticodelicense-function.md)  
 Časové značky licenci Authenticode XrML vytvořené CertCreateAuthenticodeLicense.  
  
 [Funkce CertVerifyAuthenticodeLicense](../../../../docs/framework/unmanaged-api/authenticode/certverifyauthenticodelicense-function.md)  
 Ověří platnost licence na Authenticode XrML.  
  
 [Struktura AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md)  
 Definuje informace podepisující osoba Authenticode.  
  
 [Struktura AXL_AUTHENTICODE_TIMESTAMPER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-timestamper-info-structure.md)  
 Definuje informace stamper čas Authenticode.  
  
## <a name="see-also"></a>Viz také  
 [Referenční informace o nespravovaném rozhraní API](../../../../docs/framework/unmanaged-api/index.md)
