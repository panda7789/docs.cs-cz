---
title: 'Zmírnění: metoda X509CertificateClaimSet. FindClaims'
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
ms.openlocfilehash: 5591ecebeb924f84cc0efdaf78f40f9d835d2d02
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126089"
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

- [Odlišnosti ve změnách cílení](retargeting-changes-in-the-net-framework-4-6-1.md)
