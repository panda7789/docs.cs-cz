---
title: "Omezení rizik: X509CertificateClaimSet.FindClaims – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d1b10d5c746839f504eab258664b2a60d12244f7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a>Omezení rizik: X509CertificateClaimSet.FindClaims – metoda
Počínaje aplikací cílených [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> metoda se pokusí přiřadit `claimType` argument všechny záznamy DNS v jeho poli SAN.  
  
## <a name="impact"></a>Dopad  
 Tato změna ovlivní pouze aplikace, které cílové verze rozhraní .NET Framework od verze [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].  
  
 Pro aplikace, které cílí na předchozích verzích rozhraní .NET Framework <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> metoda se pokusí o porovnání `claimType` argument pouze poslední položky DNS.  
  
## <a name="mitigation"></a>Zmírnění  
 Pokud se tato změna není žádoucí, aplikace, která cílové verze rozhraní .NET Framework, počínaje [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] můžete vyjádření výslovného nesouhlasu se přidáním následující nastavení konfigurace na [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) oddílu aplikace konfigurační soubor:  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />   
</runtime>  
```  
  
 Kromě toho aplikace, které cílí na předchozích verzích rozhraní .NET Framework, ale běží v rámci [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] a novější verze můžete vyjádřit výslovný souhlas pro toto chování přidáním následující nastavení konfigurace na [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)oddílu konfiguračního souboru aplikace:  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />   
</runtime>  
```  
  
## <a name="see-also"></a>Viz také  
 [Odlišnosti ve změnách cílení](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
