---
title: Hledání deklarací v sadě deklarací
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- claims [WCF], finding in a claimset
- claims [WCF]
ms.assetid: a76ce107-aeb3-47d0-bfa9-134c53664e20
ms.openlocfilehash: 42e6ee682220913f872da337eb41f6c290082988
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59137121"
---
# <a name="finding-claims-in-a-claimset"></a><span data-ttu-id="db122-102">Hledání deklarací v sadě deklarací</span><span class="sxs-lookup"><span data-stu-id="db122-102">Finding Claims in a ClaimSet</span></span>
<span data-ttu-id="db122-103">Zkoumání obsahu <xref:System.IdentityModel.Claims.ClaimSet> pro konkrétní typy deklarací, které je běžné úlohy při použití ověřování na základě deklarací identity.</span><span class="sxs-lookup"><span data-stu-id="db122-103">Examining the content of a <xref:System.IdentityModel.Claims.ClaimSet> for particular types of claims is a common task when using claim-based authorization.</span></span> <span data-ttu-id="db122-104">K prozkoumání <xref:System.IdentityModel.Claims.ClaimSet> přítomnosti konkrétních deklarací identit, použijte <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="db122-104">To examine a <xref:System.IdentityModel.Claims.ClaimSet> for the presence of particular claims, use the <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> method.</span></span> <span data-ttu-id="db122-105">Tato metoda poskytuje lepší výkon než iterace přímo přes <xref:System.IdentityModel.Claims.ClaimSet>.</span><span class="sxs-lookup"><span data-stu-id="db122-105">This method provides better performance than iterating directly over the <xref:System.IdentityModel.Claims.ClaimSet>.</span></span> <span data-ttu-id="db122-106">Následující příklad ukazuje použití těchto.</span><span class="sxs-lookup"><span data-stu-id="db122-106">The following example demonstrates this usage.</span></span> <span data-ttu-id="db122-107">Všimněte si, že `claimType` a `claimRight` může být parametry `null`.</span><span class="sxs-lookup"><span data-stu-id="db122-107">Note that the `claimType` and `claimRight` parameters can be `null`.</span></span> <span data-ttu-id="db122-108">Parametry v takovém případě bude odpovídat všechny typy deklarací identity a deklarací identity práva.</span><span class="sxs-lookup"><span data-stu-id="db122-108">In that case, the parameters will match all claim types and claim rights.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db122-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="db122-109">Example</span></span>  
 [!code-csharp[c_FindClaimsPerf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_findclaimsperf/cs/c_findclaimsperf.cs#2)]
 [!code-vb[c_FindClaimsPerf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_findclaimsperf/vb/c_findclaimsperf.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="db122-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="db122-110">See also</span></span>

- [<span data-ttu-id="db122-111">Správa deklarací identity a autorizace pomocí modelu identit</span><span class="sxs-lookup"><span data-stu-id="db122-111">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
