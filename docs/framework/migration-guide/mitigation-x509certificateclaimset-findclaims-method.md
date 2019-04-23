---
title: 'Omezení rizik: X509CertificateClaimSet.FindClaims Method'
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e3b3645d9fc00087e163b9200edb5fbcf0dbbd9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59217208"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a><span data-ttu-id="04910-102">Omezení rizik: X509CertificateClaimSet.FindClaims Method</span><span class="sxs-lookup"><span data-stu-id="04910-102">Mitigation: X509CertificateClaimSet.FindClaims Method</span></span>
<span data-ttu-id="04910-103">Počínaje aplikací, které se zaměřují [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> metoda se pokusí přiřadit `claimType` argument u všech položek DNS v jeho poli SAN.</span><span class="sxs-lookup"><span data-stu-id="04910-103">Starting with apps that target the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)],  the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method will attempt to match the `claimType` argument with all the DNS entries in its SAN field.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="04910-104">Dopad</span><span class="sxs-lookup"><span data-stu-id="04910-104">Impact</span></span>  
 <span data-ttu-id="04910-105">Tato změna ovlivní pouze aplikace, které cílí rozhraní .NET Framework počínaje verzí [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].</span><span class="sxs-lookup"><span data-stu-id="04910-105">This change only affects apps that target versions of the .NET Framework starting with the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].</span></span>  
  
 <span data-ttu-id="04910-106">Pro aplikace, které cílí na předchozí verze rozhraní .NET Framework <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> metoda se pokusí porovnat `claimType` argument pouze s poslední položky DNS.</span><span class="sxs-lookup"><span data-stu-id="04910-106">For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method attempts to match the `claimType` argument only with the last  DNS entry.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="04910-107">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="04910-107">Mitigation</span></span>  
 <span data-ttu-id="04910-108">Pokud tuto změnu nežádoucí, aplikace, která cílit na rozhraní .NET Framework počínaje verzí [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] můžete vyjádřit výslovný nesouhlas ho tak, že přidáte následující konfigurační nastavení [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) část aplikace konfigurační soubor:</span><span class="sxs-lookup"><span data-stu-id="04910-108">If this change is undesirable, apps that target versions of the .NET Framework starting with the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] can opt out of it by adding the following configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />   
</runtime>  
```  
  
 <span data-ttu-id="04910-109">Kromě toho, které cílí na předchozí verze rozhraní .NET Framework, ale jsou spuštěny [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] a novější verze můžete vyjádřit výslovný souhlas pro toto chování tak, že přidáte následující konfigurační nastavení pro [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)oddílu konfiguračního souboru aplikace:</span><span class="sxs-lookup"><span data-stu-id="04910-109">In addition, apps that target previous versions of the .NET Framework but are running under the [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] and later versions can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />   
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="04910-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="04910-110">See also</span></span>

- [<span data-ttu-id="04910-111">Odlišnosti ve změnách cílení</span><span class="sxs-lookup"><span data-stu-id="04910-111">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
