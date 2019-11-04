---
title: 'Zmírnění: metoda X509CertificateClaimSet. FindClaims'
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
ms.openlocfilehash: e75b1cae599b153012b8525a0e1e36ed116e695f
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457756"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a>Zmírnění: metoda X509CertificateClaimSet. FindClaims
Počínaje aplikacemi, které cílí na .NET Framework 4.6.1, se metoda <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> pokusí spárovat argument `claimType` se všemi položkami DNS v poli SAN.  
  
## <a name="impact"></a>Dopad  
 Tato změna ovlivní pouze aplikace, které cílí na verze .NET Framework počínaje .NET Framework 4.6.1.  
  
 U aplikací, které cílí na předchozí verze .NET Framework, se metoda <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> pokusí spárovat argument `claimType` jenom s poslední položkou DNS.  
  
## <a name="mitigation"></a>Zmírnění  
 Pokud je tato změna nežádoucí, aplikace, které cílí na verze .NET Framework počínaje .NET Framework 4.6.1, se můžou odhlásit přidáním následujícího nastavení konfigurace do části [> modulu runtime\<](../configure-apps/file-schema/runtime/runtime-element.md) konfiguračního souboru aplikace:  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />   
</runtime>  
```  
  
 Kromě toho aplikace, které cílí na předchozí verze .NET Framework, ale běží v .NET Framework 4.6.1 a novějších verzích se můžou k tomuto chování vyjádřit přidáním následujícího nastavení konfigurace do části [> modulu runtime\<](../configure-apps/file-schema/runtime/runtime-element.md) konfigurační soubor aplikace:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />   
</runtime>  
```  
  
## <a name="see-also"></a>Viz také:

- [Kompatibilita aplikací](application-compatibility.md)
