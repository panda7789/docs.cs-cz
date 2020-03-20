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
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a><span data-ttu-id="938c6-102">Zmírnění: X509CertificateClaimSet.FindClaims Metoda</span><span class="sxs-lookup"><span data-stu-id="938c6-102">Mitigation: X509CertificateClaimSet.FindClaims Method</span></span>
<span data-ttu-id="938c6-103">Počínaje aplikacemi, které cílí na rozhraní .NET Framework 4.6.1, se <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> metoda pokusí porovnat `claimType` argument se všemi položkami DNS v poli SAN.</span><span class="sxs-lookup"><span data-stu-id="938c6-103">Starting with apps that target the .NET Framework 4.6.1,  the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method will attempt to match the `claimType` argument with all the DNS entries in its SAN field.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="938c6-104">Dopad</span><span class="sxs-lookup"><span data-stu-id="938c6-104">Impact</span></span>  
 <span data-ttu-id="938c6-105">Tato změna se týká pouze aplikací, které cílí na verze rozhraní .NET Framework počínaje rozhraním .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="938c6-105">This change only affects apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>  
  
 <span data-ttu-id="938c6-106">U aplikací, které cílí na předchozí <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> verze rozhraní .NET `claimType` Framework, se metoda pokusí porovnat argument pouze s poslední položkou DNS.</span><span class="sxs-lookup"><span data-stu-id="938c6-106">For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method attempts to match the `claimType` argument only with the last  DNS entry.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="938c6-107">Omezení rizik</span><span class="sxs-lookup"><span data-stu-id="938c6-107">Mitigation</span></span>  
 <span data-ttu-id="938c6-108">Pokud je tato změna nežádoucí, aplikace, které cílí na verze rozhraní .NET Framework počínaje rozhraním .NET Framework 4.6.1, se z ní mohou odhlásit přidáním následujícího nastavení konfigurace do [ \<](../configure-apps/file-schema/runtime/runtime-element.md) části konfigurace>runtime aplikace:</span><span class="sxs-lookup"><span data-stu-id="938c6-108">If this change is undesirable, apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1 can opt out of it by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />
</runtime>  
```  
  
 <span data-ttu-id="938c6-109">Kromě toho se aplikace, které cílí na předchozí verze rozhraní .NET Framework, ale jsou spuštěny v rámci rozhraní .NET Framework [ \<](../configure-apps/file-schema/runtime/runtime-element.md) 4.6.1 a novějších verzí, mohou přihlásit k tomuto chování přidáním následujícího nastavení konfigurace do části konfigurace konfiguračního souboru aplikace>běhu:</span><span class="sxs-lookup"><span data-stu-id="938c6-109">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="938c6-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="938c6-110">See also</span></span>

- [<span data-ttu-id="938c6-111">Kompatibilita aplikací</span><span class="sxs-lookup"><span data-stu-id="938c6-111">Application compatibility</span></span>](application-compatibility.md)
