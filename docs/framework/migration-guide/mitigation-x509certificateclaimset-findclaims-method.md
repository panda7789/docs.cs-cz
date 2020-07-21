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
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a><span data-ttu-id="69c5e-103">Zmírnění: metoda X509CertificateClaimSet. FindClaims</span><span class="sxs-lookup"><span data-stu-id="69c5e-103">Mitigation: X509CertificateClaimSet.FindClaims Method</span></span>

<span data-ttu-id="69c5e-104">Počínaje aplikacemi, které cílí na .NET Framework 4.6.1, se <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> Metoda pokusí porovnat `claimType` argument se všemi položkami DNS v poli sítě SAN.</span><span class="sxs-lookup"><span data-stu-id="69c5e-104">Starting with apps that target .NET Framework 4.6.1, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method will attempt to match the `claimType` argument with all the DNS entries in its SAN field.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="69c5e-105">Dopad</span><span class="sxs-lookup"><span data-stu-id="69c5e-105">Impact</span></span>  
 <span data-ttu-id="69c5e-106">Tato změna ovlivní pouze aplikace, které cílí na verze .NET Framework počínaje .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="69c5e-106">This change only affects apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>  
  
 <span data-ttu-id="69c5e-107">U aplikací, které cílí na předchozí verze .NET Framework, se <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> Metoda pokusí porovnat `claimType` argument pouze s poslední položkou DNS.</span><span class="sxs-lookup"><span data-stu-id="69c5e-107">For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method attempts to match the `claimType` argument only with the last  DNS entry.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="69c5e-108">Omezení rizik</span><span class="sxs-lookup"><span data-stu-id="69c5e-108">Mitigation</span></span>  
 <span data-ttu-id="69c5e-109">Pokud je tato změna nežádoucí, aplikace, které cílí na verze .NET Framework počínaje .NET Framework 4.6.1, si ji můžou odhlásit přidáním následujícího nastavení konfigurace do [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) oddílu konfiguračního souboru aplikace:</span><span class="sxs-lookup"><span data-stu-id="69c5e-109">If this change is undesirable, apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1 can opt out of it by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />
</runtime>  
```  
  
 <span data-ttu-id="69c5e-110">Kromě toho aplikace, které cílí na předchozí verze .NET Framework, ale běží v .NET Framework 4.6.1 a novějších verzích se můžou k tomuto chování vyjádřit přidáním následujícího nastavení konfigurace do [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) části konfiguračního souboru aplikace:</span><span class="sxs-lookup"><span data-stu-id="69c5e-110">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="69c5e-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="69c5e-111">See also</span></span>

- [<span data-ttu-id="69c5e-112">Kompatibilita aplikací</span><span class="sxs-lookup"><span data-stu-id="69c5e-112">Application compatibility</span></span>](application-compatibility.md)
