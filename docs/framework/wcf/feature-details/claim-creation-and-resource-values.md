---
title: Vytvoření nároku a hodnoty prostředků
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], creation and resource values
ms.assetid: 30431f76-cbe7-4bad-bad7-8e43e23a82d4
ms.openlocfilehash: bd9a8b7faf3cd7a648ff6b2a50ac68f21561497c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766906"
---
# <a name="claim-creation-and-resource-values"></a><span data-ttu-id="4ba88-102">Vytvoření nároku a hodnoty prostředků</span><span class="sxs-lookup"><span data-stu-id="4ba88-102">Claim Creation and Resource Values</span></span>
<span data-ttu-id="4ba88-103"><xref:System.IdentityModel.Claims.Claim> Třída poskytuje několik metod pro vytváření instancí vestavěné typy deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="4ba88-103">The <xref:System.IdentityModel.Claims.Claim> class provides several methods for creating instances of built-in claims types.</span></span> <span data-ttu-id="4ba88-104">Z těchto metod následující provést žádné sémantické nebo formátování kontrolujeme zadaného prostředku:</span><span class="sxs-lookup"><span data-stu-id="4ba88-104">Of these methods, the following perform no semantic or format checking on the supplied resource:</span></span>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateDnsClaim%2A>  
  
- <span data-ttu-id="4ba88-105"><xref:System.IdentityModel.Claims.Claim.CreateHashClaim%2A> (nekontroluje délku nebo obsahu objektu pole bajtů)</span><span class="sxs-lookup"><span data-stu-id="4ba88-105"><xref:System.IdentityModel.Claims.Claim.CreateHashClaim%2A> (does not check the length or content of the byte array)</span></span>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateNameClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateSpnClaim%2A>  
  
- <span data-ttu-id="4ba88-106"><xref:System.IdentityModel.Claims.Claim.CreateThumbprintClaim%2A> (nekontroluje délku nebo obsahu objektu pole bajtů)</span><span class="sxs-lookup"><span data-stu-id="4ba88-106"><xref:System.IdentityModel.Claims.Claim.CreateThumbprintClaim%2A> (does not check the length or content of the byte array)</span></span>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateUpnClaim%2A>  
  
 <span data-ttu-id="4ba88-107">By měl být věnovat pozornost při volání metody výše zajistit, že prostředek, který předané hodnoty jsou ve správném formátu nebo obsahují správný druh informací (nebo obojí).</span><span class="sxs-lookup"><span data-stu-id="4ba88-107">Care should be taken when calling the above methods to ensure that the resource values passed in are of the correct format or contain the correct kind of information (or both).</span></span>  
  
 <span data-ttu-id="4ba88-108">Následující metody provést určité typy:</span><span class="sxs-lookup"><span data-stu-id="4ba88-108">The following methods take specific types:</span></span>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateDenyOnlyWindowsSidClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateMailAddressClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateRsaClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateUriClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateWindowsSidClaim%2A>  
  
- <xref:System.IdentityModel.Claims.Claim.CreateX500DistinguishedNameClaim%2A>  
  
## <a name="see-also"></a><span data-ttu-id="4ba88-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4ba88-109">See also</span></span>

- <xref:System.IdentityModel.Claims.Claim>
- <xref:System.IdentityModel.Claims.ClaimSet>
- [<span data-ttu-id="4ba88-110">Správa deklarací identity a autorizace pomocí modelu identit</span><span class="sxs-lookup"><span data-stu-id="4ba88-110">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
