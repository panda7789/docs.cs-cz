---
title: 'Omezení rizik: X509CertificateClaimSet.FindClaims Method'
ms.date: 03/30/2017
ms.assetid: ee356e3b-f932-48f5-875a-5e42340bee63
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f7fb1eb0c502584caac11ca3dde6e7e646b29cfe
ms.sourcegitcommit: 26f4a7697c32978f6a328c89dc4ea87034065989
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/28/2019
ms.locfileid: "66251094"
---
# <a name="mitigation-x509certificateclaimsetfindclaims-method"></a><span data-ttu-id="d3548-102">Omezení rizik: X509CertificateClaimSet.FindClaims Method</span><span class="sxs-lookup"><span data-stu-id="d3548-102">Mitigation: X509CertificateClaimSet.FindClaims Method</span></span>
<span data-ttu-id="d3548-103">Počínaje aplikací určených pro rozhraní .NET Framework 4.6.1, <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> metoda se pokusí přiřadit `claimType` argument u všech položek DNS v jeho poli SAN.</span><span class="sxs-lookup"><span data-stu-id="d3548-103">Starting with apps that target the .NET Framework 4.6.1,  the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method will attempt to match the `claimType` argument with all the DNS entries in its SAN field.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="d3548-104">Dopad</span><span class="sxs-lookup"><span data-stu-id="d3548-104">Impact</span></span>  
 <span data-ttu-id="d3548-105">Tato změna ovlivní pouze aplikace, které cílové verze rozhraní .NET Framework počínaje .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="d3548-105">This change only affects apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1.</span></span>  
  
 <span data-ttu-id="d3548-106">Pro aplikace, které cílí na předchozí verze rozhraní .NET Framework <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> metoda se pokusí porovnat `claimType` argument pouze s poslední položky DNS.</span><span class="sxs-lookup"><span data-stu-id="d3548-106">For apps that target previous versions of the .NET Framework, the <xref:System.IdentityModel.Claims.X509CertificateClaimSet.FindClaims%2A?displayProperty=nameWithType> method attempts to match the `claimType` argument only with the last  DNS entry.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="d3548-107">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="d3548-107">Mitigation</span></span>  
 <span data-ttu-id="d3548-108">Pokud tuto změnu nežádoucí, aplikací s cílovou verzí rozhraní .NET Framework počínaje .NET Framework 4.6.1 můžete zrušit jej tak, že přidáte následující konfigurační nastavení [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) část konfigurační soubor aplikace:</span><span class="sxs-lookup"><span data-stu-id="d3548-108">If this change is undesirable, apps that target versions of the .NET Framework starting with the .NET Framework 4.6.1 can opt out of it by adding the following configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
   <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=true" />   
</runtime>  
```  
  
 <span data-ttu-id="d3548-109">Kromě toho, které cílí na předchozí verze rozhraní .NET Framework, ale jsou spuštěny v rozhraní .NET Framework 4.6.1 a novějších verzích můžete přejít k toto chování tak, že přidáte následující konfigurační nastavení [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) oddílu konfiguračního souboru aplikace:</span><span class="sxs-lookup"><span data-stu-id="d3548-109">In addition, apps that target previous versions of the .NET Framework but are running under the .NET Framework 4.6.1 and later versions can opt in to this behavior by adding the following configuration setting to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of the app’s configuration file:</span></span>  
  
```xml  
<runtime>  
    <AppContextSwitchOverrides value="Switch.System.IdentityModel.DisableMultipleDNSEntriesInSANCertificate=false" />   
</runtime>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d3548-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d3548-110">See also</span></span>

- [<span data-ttu-id="d3548-111">Odlišnosti ve změnách cílení</span><span class="sxs-lookup"><span data-stu-id="d3548-111">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
