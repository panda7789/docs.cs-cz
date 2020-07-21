---
title: 'Zmírnění: metoda X509CertificateClaimSet. FindClaims'
description: Přečtěte si, jak se změnila metoda X509CertificateClaimSet. FindClaims u aplikací, které cílí na .NET Framework 4.6.1.
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
ms.openlocfilehash: 304d8fb5adc27b33f2410faaaf8662e0ff9be66d
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475317"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a>Zmírnění: metoda X509CertificateClaimSet. FindClaims

Počínaje aplikacemi, které cílí na .NET Framework 4.6.1, se <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> Metoda pokusí porovnat `claimType` argument se všemi položkami DNS v poli sítě SAN.  
  
## <a name="impact"></a>Dopad  
 Tato změna ovlivní pouze aplikace, které cílí na verze .NET Framework počínaje .NET Framework 4.6.1.  
  
 U aplikací, které cílí na předchozí verze .NET Framework, se <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> Metoda pokusí porovnat `claimType` argument pouze s poslední položkou DNS.  
  
## <a name="mitigation"></a>Omezení rizik  
 Pokud je tato změna nežádoucí, aplikace, které cílí na verze .NET Framework počínaje .NET Framework 4.6.1, si ji můžou odhlásit přidáním následujícího nastavení konfigurace do [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) oddílu konfiguračního souboru aplikace:  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />
</runtime>  
```  
  
 Kromě toho aplikace, které cílí na předchozí verze .NET Framework, ale běží v .NET Framework 4.6.1 a novějších verzích se můžou k tomuto chování vyjádřit přidáním následujícího nastavení konfigurace do [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) části konfiguračního souboru aplikace:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />
</runtime>  
```  
  
## <a name="see-also"></a>Viz také

- [Kompatibilita aplikací](application-compatibility.md)
