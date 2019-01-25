---
title: 'Omezení rizik: X509CertificateClaimSet.FindClaims Method'
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ccc24cd494866c087860144f1720988ccfc2dfa8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54536435"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a>Omezení rizik: X509CertificateClaimSet.FindClaims Method
Počínaje aplikací, které se zaměřují [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> metoda se pokusí přiřadit `claimType` argument u všech položek DNS v jeho poli SAN.  
  
## <a name="impact"></a>Dopad  
 Tato změna ovlivní pouze aplikace, které cílí rozhraní .NET Framework počínaje verzí [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].  
  
 Pro aplikace, které cílí na předchozí verze rozhraní .NET Framework <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> metoda se pokusí porovnat `claimType` argument pouze s poslední položky DNS.  
  
## <a name="mitigation"></a>Zmírnění  
 Pokud tuto změnu nežádoucí, aplikace, která cílit na rozhraní .NET Framework počínaje verzí [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] můžete vyjádřit výslovný nesouhlas ho tak, že přidáte následující konfigurační nastavení [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) část aplikace konfigurační soubor:  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />   
</runtime>  
```  
  
 Kromě toho, které cílí na předchozí verze rozhraní .NET Framework, ale jsou spuštěny [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] a novější verze můžete vyjádřit výslovný souhlas pro toto chování tak, že přidáte následující konfigurační nastavení pro [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)oddílu konfiguračního souboru aplikace:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />   
</runtime>  
```  
  
## <a name="see-also"></a>Viz také:
- [Odlišnosti ve změnách cílení](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
