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
ms.openlocfilehash: f7872f1904cfcab860bb25459aabd47e6dcf38ac
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a><span data-ttu-id="a6861-102">Omezení rizik: X509CertificateClaimSet.FindClaims – metoda</span><span class="sxs-lookup"><span data-stu-id="a6861-102">Mitigation: X509CertificateClaimSet.FindClaims Method</span></span>
<span data-ttu-id="a6861-103">Počínaje aplikací cílených [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> metoda se pokusí přiřadit `claimType` argument všechny záznamy DNS v jeho poli SAN.</span><span class="sxs-lookup"><span data-stu-id="a6861-103">Starting with apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)],  the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method will attempt to match the `claimType` argument with all the DNS entries in its SAN field.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="a6861-104">Dopad</span><span class="sxs-lookup"><span data-stu-id="a6861-104">Impact</span></span>  
 <span data-ttu-id="a6861-105">Tato změna ovlivní pouze aplikace, které cílové verze rozhraní .NET Framework od verze [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a6861-105">This change only affects apps that target versions of the .NET Framework starting with the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].</span></span>  
  
 <span data-ttu-id="a6861-106">Pro aplikace, které cílí na předchozích verzích rozhraní .NET Framework <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> metoda se pokusí o porovnání `claimType` argument pouze poslední položky DNS.</span><span class="sxs-lookup"><span data-stu-id="a6861-106">For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method attempts to match the `claimType` argument only with the last  DNS entry.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="a6861-107">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="a6861-107">Mitigation</span></span>  
 <span data-ttu-id="a6861-108">Pokud se tato změna není žádoucí, aplikace, která cílové verze rozhraní .NET Framework, počínaje [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] můžete vyjádření výslovného nesouhlasu se přidáním následující nastavení konfigurace na [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) oddílu aplikace konfigurační soubor:</span><span class="sxs-lookup"><span data-stu-id="a6861-108">If this change is undesirable, apps that target versions of the .NET Framework starting with the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] can opt out of it by adding the following configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />   
</runtime>  
```  
  
 <span data-ttu-id="a6861-109">Kromě toho aplikace, které cílí na předchozích verzích rozhraní .NET Framework, ale běží v rámci [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] a novější verze můžete vyjádřit výslovný souhlas pro toto chování přidáním následující nastavení konfigurace na [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)oddílu konfiguračního souboru aplikace:</span><span class="sxs-lookup"><span data-stu-id="a6861-109">In addition, apps that target previous versions of the .NET Framework but are running under the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and later versions can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />   
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a6861-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="a6861-110">See Also</span></span>  
 [<span data-ttu-id="a6861-111">Odlišnosti ve změnách cílení</span><span class="sxs-lookup"><span data-stu-id="a6861-111">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
