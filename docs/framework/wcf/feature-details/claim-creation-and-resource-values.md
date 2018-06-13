---
title: Vytvoření nároku a hodnoty prostředků
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], creation and resource values
ms.assetid: 30431f76-cbe7-4bad-bad7-8e43e23a82d4
ms.openlocfilehash: cfa697023ca9d4c0b6f43c90c382816993dccc5d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488049"
---
# <a name="claim-creation-and-resource-values"></a><span data-ttu-id="10b9c-102">Vytvoření nároku a hodnoty prostředků</span><span class="sxs-lookup"><span data-stu-id="10b9c-102">Claim Creation and Resource Values</span></span>
<span data-ttu-id="10b9c-103"><xref:System.IdentityModel.Claims.Claim> Třída poskytuje několik metod, vytváření instancí předdefinované typy deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="10b9c-103">The <xref:System.IdentityModel.Claims.Claim> class provides several methods for creating instances of built-in claims types.</span></span> <span data-ttu-id="10b9c-104">Z těchto metod následující provést žádné sémantického nebo formátu kontrola na zadaný prostředek:</span><span class="sxs-lookup"><span data-stu-id="10b9c-104">Of these methods, the following perform no semantic or format checking on the supplied resource:</span></span>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateDnsClaim%2A>  
  
-   <span data-ttu-id="10b9c-105"><xref:System.IdentityModel.Claims.Claim.CreateHashClaim%2A> (nekontroluje délku nebo obsah pole bajtů)</span><span class="sxs-lookup"><span data-stu-id="10b9c-105"><xref:System.IdentityModel.Claims.Claim.CreateHashClaim%2A> (does not check the length or content of the byte array)</span></span>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateNameClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateSpnClaim%2A>  
  
-   <span data-ttu-id="10b9c-106"><xref:System.IdentityModel.Claims.Claim.CreateThumbprintClaim%2A> (nekontroluje délku nebo obsah pole bajtů)</span><span class="sxs-lookup"><span data-stu-id="10b9c-106"><xref:System.IdentityModel.Claims.Claim.CreateThumbprintClaim%2A> (does not check the length or content of the byte array)</span></span>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateUpnClaim%2A>  
  
 <span data-ttu-id="10b9c-107">Potřeba dát pozor při volání metody výše aby prostředek, který předané hodnoty jsou ve správném formátu nebo obsahují správný druh informací (nebo obě).</span><span class="sxs-lookup"><span data-stu-id="10b9c-107">Care should be taken when calling the above methods to ensure that the resource values passed in are of the correct format or contain the correct kind of information (or both).</span></span>  
  
 <span data-ttu-id="10b9c-108">Tyto metody přijímají konkrétní typy:</span><span class="sxs-lookup"><span data-stu-id="10b9c-108">The following methods take specific types:</span></span>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateDenyOnlyWindowsSidClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateMailAddressClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateRsaClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateUriClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateWindowsSidClaim%2A>  
  
-   <xref:System.IdentityModel.Claims.Claim.CreateX500DistinguishedNameClaim%2A>  
  
## <a name="see-also"></a><span data-ttu-id="10b9c-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="10b9c-109">See Also</span></span>  
 <xref:System.IdentityModel.Claims.Claim>  
 <xref:System.IdentityModel.Claims.ClaimSet>  
 [<span data-ttu-id="10b9c-110">Správa deklarací identity a autorizace pomocí modelu identit</span><span class="sxs-lookup"><span data-stu-id="10b9c-110">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
