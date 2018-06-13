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
ms.openlocfilehash: 7ca22d701277e71e509e6b291eb59a0223a0250c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488595"
---
# <a name="finding-claims-in-a-claimset"></a><span data-ttu-id="e7085-102">Hledání deklarací v sadě deklarací</span><span class="sxs-lookup"><span data-stu-id="e7085-102">Finding Claims in a ClaimSet</span></span>
<span data-ttu-id="e7085-103">Zkoumání obsahu <xref:System.IdentityModel.Claims.ClaimSet> pro konkrétní typy deklarací identity je běžné úlohy při použití ověřování na základě deklarace.</span><span class="sxs-lookup"><span data-stu-id="e7085-103">Examining the content of a <xref:System.IdentityModel.Claims.ClaimSet> for particular types of claims is a common task when using claim-based authorization.</span></span> <span data-ttu-id="e7085-104">K prozkoumání <xref:System.IdentityModel.Claims.ClaimSet> přítomnost konkrétních deklarací identit, použijte <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="e7085-104">To examine a <xref:System.IdentityModel.Claims.ClaimSet> for the presence of particular claims, use the <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> method.</span></span> <span data-ttu-id="e7085-105">Tato metoda poskytuje lepší výkon než iterování přímo přes <xref:System.IdentityModel.Claims.ClaimSet>.</span><span class="sxs-lookup"><span data-stu-id="e7085-105">This method provides better performance than iterating directly over the <xref:System.IdentityModel.Claims.ClaimSet>.</span></span> <span data-ttu-id="e7085-106">Následující příklad ukazuje toto použití.</span><span class="sxs-lookup"><span data-stu-id="e7085-106">The following example demonstrates this usage.</span></span> <span data-ttu-id="e7085-107">Všimněte si, že `claimType` a `claimRight` může být parametry `null`.</span><span class="sxs-lookup"><span data-stu-id="e7085-107">Note that the `claimType` and `claimRight` parameters can be `null`.</span></span> <span data-ttu-id="e7085-108">V takovém případě bude parametry odpovídají všechny typy deklarací identity a deklarací identity práva.</span><span class="sxs-lookup"><span data-stu-id="e7085-108">In that case, the parameters will match all claim types and claim rights.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7085-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="e7085-109">Example</span></span>  
 [!code-csharp[c_FindClaimsPerf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_findclaimsperf/cs/c_findclaimsperf.cs#2)]
 [!code-vb[c_FindClaimsPerf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_findclaimsperf/vb/c_findclaimsperf.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="e7085-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="e7085-110">See Also</span></span>  
 [<span data-ttu-id="e7085-111">Správa deklarací identity a autorizace pomocí modelu identit</span><span class="sxs-lookup"><span data-stu-id="e7085-111">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
