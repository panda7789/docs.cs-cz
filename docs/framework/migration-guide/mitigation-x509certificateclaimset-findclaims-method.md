---
title: Zmírnění X509CertificateClaimSet.FindClaims Method
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ffc03e6c88a2aabb967587d8b1ee7d0b784b4e7d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70778936"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a><span data-ttu-id="af2e0-102">Zmírnění X509CertificateClaimSet.FindClaims Method</span><span class="sxs-lookup"><span data-stu-id="af2e0-102">Mitigation: X509CertificateClaimSet.FindClaims Method</span></span>
<span data-ttu-id="af2e0-103">Počínaje aplikacemi, které cílí na .NET Framework 4.6.1, <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> se metoda pokusí `claimType` porovnat argument se všemi položkami DNS v poli sítě SAN.</span><span class="sxs-lookup"><span data-stu-id="af2e0-103">Starting with apps that target the .NET Framework 4.6.1,  the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method will attempt to match the `claimType` argument with all the DNS entries in its SAN field.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="af2e0-104">Dopad</span><span class="sxs-lookup"><span data-stu-id="af2e0-104">Impact</span></span>  
 <span data-ttu-id="af2e0-105">Tato změna ovlivní pouze aplikace, které cílí na verze .NET Framework počínaje .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="af2e0-105">This change only affects apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>  
  
 <span data-ttu-id="af2e0-106">U aplikací, které cílí na předchozí verze .NET Framework, se <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> metoda pokusí `claimType` porovnat argument pouze s poslední položkou DNS.</span><span class="sxs-lookup"><span data-stu-id="af2e0-106">For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method attempts to match the `claimType` argument only with the last  DNS entry.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="af2e0-107">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="af2e0-107">Mitigation</span></span>  
 <span data-ttu-id="af2e0-108">Pokud je tato změna nežádoucí, aplikace, které cílí na verze .NET Framework počínaje .NET Framework 4.6.1, se můžou odhlásit přidáním následujícího nastavení konfigurace do [ \<oddílu běhového >](../configure-apps/file-schema/runtime/runtime-element.md) konfiguračního souboru aplikace. :</span><span class="sxs-lookup"><span data-stu-id="af2e0-108">If this change is undesirable, apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1 can opt out of it by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />   
</runtime>  
```  
  
 <span data-ttu-id="af2e0-109">Kromě toho aplikace, které cílí na předchozí verze .NET Framework, ale běží v .NET Framework 4.6.1 a novějších verzích se můžou k tomuto chování vyjádřit přidáním následujícího nastavení konfigurace do [ \<části modulu runtime >](../configure-apps/file-schema/runtime/runtime-element.md) konfigurační soubor aplikace:</span><span class="sxs-lookup"><span data-stu-id="af2e0-109">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />   
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="af2e0-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="af2e0-110">See also</span></span>

- [<span data-ttu-id="af2e0-111">Odlišnosti ve změnách cílení</span><span class="sxs-lookup"><span data-stu-id="af2e0-111">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6-1.md)
