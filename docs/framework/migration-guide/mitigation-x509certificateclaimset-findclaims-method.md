---
title: 'Zmírnění: X509CertificateClaimSet.FindClaims Metoda'
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
ms.openlocfilehash: f94a5f685a5aa94332bf2e15e5d5eb0def02d7ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400139"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a>Zmírnění: X509CertificateClaimSet.FindClaims Metoda
Počínaje aplikacemi, které cílí na rozhraní .NET Framework 4.6.1, se <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> metoda pokusí porovnat `claimType` argument se všemi položkami DNS v poli SAN.  
  
## <a name="impact"></a>Dopad  
 Tato změna se týká pouze aplikací, které cílí na verze rozhraní .NET Framework počínaje rozhraním .NET Framework 4.6.1.  
  
 U aplikací, které cílí na předchozí <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> verze rozhraní .NET `claimType` Framework, se metoda pokusí porovnat argument pouze s poslední položkou DNS.  
  
## <a name="mitigation"></a>Omezení rizik  
 Pokud je tato změna nežádoucí, aplikace, které cílí na verze rozhraní .NET Framework počínaje rozhraním .NET Framework 4.6.1, se z ní mohou odhlásit přidáním následujícího nastavení konfigurace do [ \<](../configure-apps/file-schema/runtime/runtime-element.md) části konfigurace>runtime aplikace:  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />
</runtime>  
```  
  
 Kromě toho se aplikace, které cílí na předchozí verze rozhraní .NET Framework, ale jsou spuštěny v rámci rozhraní .NET Framework [ \<](../configure-apps/file-schema/runtime/runtime-element.md) 4.6.1 a novějších verzí, mohou přihlásit k tomuto chování přidáním následujícího nastavení konfigurace do části konfigurace konfiguračního souboru aplikace>běhu:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />
</runtime>  
```  
  
## <a name="see-also"></a>Viz také

- [Kompatibilita aplikací](application-compatibility.md)
