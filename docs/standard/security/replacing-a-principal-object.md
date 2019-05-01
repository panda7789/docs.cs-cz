---
title: Nahrazení objektu zabezpečení
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- principal objects, replacing
- security [.NET Framework], replacing principal objects
- security [.NET Framework], principals
ms.assetid: c323687e-b196-487b-beba-f38f9b3f961b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5f33be207dd6166b16a04844f3d92b6e017d1c7a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018785"
---
# <a name="replacing-a-principal-object"></a><span data-ttu-id="d9c6c-102">Nahrazení objektu zabezpečení</span><span class="sxs-lookup"><span data-stu-id="d9c6c-102">Replacing a Principal Object</span></span>
<span data-ttu-id="d9c6c-103">Aplikace, které poskytují služby ověřování musí být schopen nahradit **hlavní** objektu (<xref:System.Security.Principal.IPrincipal>) pro dané vlákno.</span><span class="sxs-lookup"><span data-stu-id="d9c6c-103">Applications that provide authentication services must be able to replace the **Principal** object (<xref:System.Security.Principal.IPrincipal>) for a given thread.</span></span> <span data-ttu-id="d9c6c-104">Kromě toho musí systém zabezpečení pomáhají chránit možnost nahradit **instančního objektu** objekty, protože speciálně připojený, nesprávné **instančního objektu** ohrožuje zabezpečení vaší aplikace pomocí nárokování role nebo naléhavém identity.</span><span class="sxs-lookup"><span data-stu-id="d9c6c-104">Furthermore, the security system must help protect the ability to replace **Principal** objects because a maliciously attached, incorrect **Principal** compromises the security of your application by claiming an untrue identity or role.</span></span> <span data-ttu-id="d9c6c-105">Proto se aplikace, které vyžadují možnost nahradit **hlavní** objekty musí mít udělena <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> objektu pro kontrolu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="d9c6c-105">Therefore, applications that require the ability to replace **Principal** objects must be granted the <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> object for principal control.</span></span> <span data-ttu-id="d9c6c-106">(Všimněte si, že toto oprávnění se nevyžaduje k provádění kontrol zabezpečení na základě rolí nebo vytváření **hlavní** objekty.)</span><span class="sxs-lookup"><span data-stu-id="d9c6c-106">(Note that this permission is not required for performing role-based security checks or for creating **Principal** objects.)</span></span>  
  
 <span data-ttu-id="d9c6c-107">Aktuální **hlavní** objektu lze nahradit pomocí provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="d9c6c-107">The current **Principal** object can be replaced by performing the following tasks:</span></span>  
  
1. <span data-ttu-id="d9c6c-108">Vytvořit náhradu **hlavní** objektů a související **Identity** objektu.</span><span class="sxs-lookup"><span data-stu-id="d9c6c-108">Create the replacement **Principal** object and associated **Identity** object.</span></span>  
  
2. <span data-ttu-id="d9c6c-109">Připojit nový **hlavní** objekt kontextu volání.</span><span class="sxs-lookup"><span data-stu-id="d9c6c-109">Attach the new **Principal** object to the call context.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9c6c-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="d9c6c-110">Example</span></span>  
 <span data-ttu-id="d9c6c-111">Následující příklad ukazuje, jak vytvořit objekt obecný instančního objektu a nastavte hlavní vlákno.</span><span class="sxs-lookup"><span data-stu-id="d9c6c-111">The following example shows how to create a generic principal object and use it to set the principal of a thread.</span></span>  
  
 [!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
 [!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d9c6c-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d9c6c-112">See also</span></span>

- <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>
- [<span data-ttu-id="d9c6c-113">Objekty zabezpečení a identity</span><span class="sxs-lookup"><span data-stu-id="d9c6c-113">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)
