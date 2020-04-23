---
title: 'Zmírnění: X509CertificateClaimSet.FindClaims Metoda'
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
ms.openlocfilehash: 0b306960c4f11bb6f54aecaeb13297e7725e16a8
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102642"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a><span data-ttu-id="3a358-102">Zmírnění: X509CertificateClaimSet.FindClaims Metoda</span><span class="sxs-lookup"><span data-stu-id="3a358-102">Mitigation: X509CertificateClaimSet.FindClaims Method</span></span>

<span data-ttu-id="3a358-103">Počínaje aplikacemi, které cílí na rozhraní <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> .NET Framework 4.6.1, se metoda pokusí porovnat `claimType` argument se všemi položkami DNS v poli SAN.</span><span class="sxs-lookup"><span data-stu-id="3a358-103">Starting with apps that target .NET Framework 4.6.1, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method will attempt to match the `claimType` argument with all the DNS entries in its SAN field.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="3a358-104">Dopad</span><span class="sxs-lookup"><span data-stu-id="3a358-104">Impact</span></span>  
 <span data-ttu-id="3a358-105">Tato změna se týká pouze aplikací, které cílí na verze rozhraní .NET Framework počínaje rozhraním .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="3a358-105">This change only affects apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>  
  
 <span data-ttu-id="3a358-106">U aplikací, které cílí na předchozí <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> verze rozhraní .NET `claimType` Framework, se metoda pokusí porovnat argument pouze s poslední položkou DNS.</span><span class="sxs-lookup"><span data-stu-id="3a358-106">For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method attempts to match the `claimType` argument only with the last  DNS entry.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="3a358-107">Omezení rizik</span><span class="sxs-lookup"><span data-stu-id="3a358-107">Mitigation</span></span>  
 <span data-ttu-id="3a358-108">Pokud je tato změna nežádoucí, aplikace, které cílí na verze rozhraní .NET Framework počínaje rozhraním .NET Framework 4.6.1, se z ní mohou odhlásit přidáním následujícího nastavení konfigurace do [ \<](../configure-apps/file-schema/runtime/runtime-element.md) části konfigurace>runtime aplikace:</span><span class="sxs-lookup"><span data-stu-id="3a358-108">If this change is undesirable, apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1 can opt out of it by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />
</runtime>  
```  
  
 <span data-ttu-id="3a358-109">Kromě toho se aplikace, které cílí na předchozí verze rozhraní .NET Framework, ale jsou spuštěny v rámci rozhraní .NET Framework [ \<](../configure-apps/file-schema/runtime/runtime-element.md) 4.6.1 a novějších verzí, mohou přihlásit k tomuto chování přidáním následujícího nastavení konfigurace do části konfigurace konfiguračního souboru aplikace>běhu:</span><span class="sxs-lookup"><span data-stu-id="3a358-109">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3a358-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="3a358-110">See also</span></span>

- [<span data-ttu-id="3a358-111">Kompatibilita aplikací</span><span class="sxs-lookup"><span data-stu-id="3a358-111">Application compatibility</span></span>](application-compatibility.md)
