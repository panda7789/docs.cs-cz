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
ms.openlocfilehash: 1954da20d382630f965582fcc01bbaf72665720a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595450"
---
# <a name="finding-claims-in-a-claimset"></a><span data-ttu-id="6988e-102">Hledání deklarací v sadě deklarací</span><span class="sxs-lookup"><span data-stu-id="6988e-102">Finding Claims in a ClaimSet</span></span>
<span data-ttu-id="6988e-103">Zkoumání obsahu <xref:System.IdentityModel.Claims.ClaimSet> pro konkrétní typy deklarací identity je běžný úkol při použití autorizace založené na deklaracích.</span><span class="sxs-lookup"><span data-stu-id="6988e-103">Examining the content of a <xref:System.IdentityModel.Claims.ClaimSet> for particular types of claims is a common task when using claim-based authorization.</span></span> <span data-ttu-id="6988e-104"><xref:System.IdentityModel.Claims.ClaimSet>Pro zjištění přítomnosti konkrétních deklarací použijte <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="6988e-104">To examine a <xref:System.IdentityModel.Claims.ClaimSet> for the presence of particular claims, use the <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> method.</span></span> <span data-ttu-id="6988e-105">Tato metoda poskytuje lepší výkon než iterace přímo přes <xref:System.IdentityModel.Claims.ClaimSet> .</span><span class="sxs-lookup"><span data-stu-id="6988e-105">This method provides better performance than iterating directly over the <xref:System.IdentityModel.Claims.ClaimSet>.</span></span> <span data-ttu-id="6988e-106">Následující příklad demonstruje toto použití.</span><span class="sxs-lookup"><span data-stu-id="6988e-106">The following example demonstrates this usage.</span></span> <span data-ttu-id="6988e-107">Všimněte si, `claimType` že `claimRight` parametry a můžou být `null` .</span><span class="sxs-lookup"><span data-stu-id="6988e-107">Note that the `claimType` and `claimRight` parameters can be `null`.</span></span> <span data-ttu-id="6988e-108">V takovém případě budou parametry odpovídat všem typům deklarací identity a nárokům na deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="6988e-108">In that case, the parameters will match all claim types and claim rights.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6988e-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="6988e-109">Example</span></span>  
 [!code-csharp[c_FindClaimsPerf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_findclaimsperf/cs/c_findclaimsperf.cs#2)]
 [!code-vb[c_FindClaimsPerf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_findclaimsperf/vb/c_findclaimsperf.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="6988e-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="6988e-110">See also</span></span>

- [<span data-ttu-id="6988e-111">Správa deklarací a autorizace s modelem identity</span><span class="sxs-lookup"><span data-stu-id="6988e-111">Managing Claims and Authorization with the Identity Model</span></span>](managing-claims-and-authorization-with-the-identity-model.md)
