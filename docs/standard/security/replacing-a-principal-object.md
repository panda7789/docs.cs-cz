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
ms.openlocfilehash: 056bd0bbafe0e7dc84d8d0c532ff844370c59230
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291211"
---
# <a name="replacing-a-principal-object"></a><span data-ttu-id="cbdda-102">Nahrazení objektu zabezpečení</span><span class="sxs-lookup"><span data-stu-id="cbdda-102">Replacing a Principal Object</span></span>
<span data-ttu-id="cbdda-103">Aplikace, které poskytují služby ověřování, musí být schopné nahradit objekt **zabezpečení** ( <xref:System.Security.Principal.IPrincipal> ) pro dané vlákno.</span><span class="sxs-lookup"><span data-stu-id="cbdda-103">Applications that provide authentication services must be able to replace the **Principal** object (<xref:System.Security.Principal.IPrincipal>) for a given thread.</span></span> <span data-ttu-id="cbdda-104">Kromě toho systém zabezpečení musí pomoct chránit možnost nahradit **Hlavní** objekty, protože neoprávněně připojená, nesprávná **jistina** ohrožuje zabezpečení vaší aplikace tím, že nárokuje neplatnou identitu nebo roli.</span><span class="sxs-lookup"><span data-stu-id="cbdda-104">Furthermore, the security system must help protect the ability to replace **Principal** objects because a maliciously attached, incorrect **Principal** compromises the security of your application by claiming an untrue identity or role.</span></span> <span data-ttu-id="cbdda-105">Proto musí být aplikace, které vyžadují možnost nahradit **Hlavní** objekty, uděleny <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> objektu pro hlavní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="cbdda-105">Therefore, applications that require the ability to replace **Principal** objects must be granted the <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> object for principal control.</span></span> <span data-ttu-id="cbdda-106">(Upozorňujeme, že toto oprávnění není vyžadováno pro provádění kontrol zabezpečení na základě rolí nebo pro vytváření objektů **zabezpečení** .)</span><span class="sxs-lookup"><span data-stu-id="cbdda-106">(Note that this permission is not required for performing role-based security checks or for creating **Principal** objects.)</span></span>  
  
 <span data-ttu-id="cbdda-107">Aktuální objekt **zabezpečení** může být nahrazen prováděním následujících úloh:</span><span class="sxs-lookup"><span data-stu-id="cbdda-107">The current **Principal** object can be replaced by performing the following tasks:</span></span>  
  
1. <span data-ttu-id="cbdda-108">Vytvořte náhradní objekt **zabezpečení** a přidružený objekt **identity** .</span><span class="sxs-lookup"><span data-stu-id="cbdda-108">Create the replacement **Principal** object and associated **Identity** object.</span></span>  
  
2. <span data-ttu-id="cbdda-109">Připojte nový objekt **zabezpečení** k kontextu volání.</span><span class="sxs-lookup"><span data-stu-id="cbdda-109">Attach the new **Principal** object to the call context.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbdda-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="cbdda-110">Example</span></span>  
 <span data-ttu-id="cbdda-111">Následující příklad ukazuje, jak vytvořit obecný objekt zabezpečení a použít ho k nastavení objektu zabezpečení vlákna.</span><span class="sxs-lookup"><span data-stu-id="cbdda-111">The following example shows how to create a generic principal object and use it to set the principal of a thread.</span></span>  
  
 [!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
 [!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="cbdda-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="cbdda-112">See also</span></span>

- <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>
- [<span data-ttu-id="cbdda-113">Objekty zabezpečení a identity</span><span class="sxs-lookup"><span data-stu-id="cbdda-113">Principal and Identity Objects</span></span>](principal-and-identity-objects.md)
