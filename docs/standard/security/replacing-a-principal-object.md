---
title: "Nahrazení objektu zabezpečení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- principal objects, replacing
- security [.NET Framework], replacing principal objects
- security [.NET Framework], principals
ms.assetid: c323687e-b196-487b-beba-f38f9b3f961b
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c53064ae12889df09b5259fbb7c8159cfdcd07aa
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="replacing-a-principal-object"></a><span data-ttu-id="a9a68-102">Nahrazení objektu zabezpečení</span><span class="sxs-lookup"><span data-stu-id="a9a68-102">Replacing a Principal Object</span></span>
<span data-ttu-id="a9a68-103">Aplikace, které poskytují služby ověřování musí být schopen nahradit **hlavní** objektu (<xref:System.Security.Principal.IPrincipal>) pro dané vlákno.</span><span class="sxs-lookup"><span data-stu-id="a9a68-103">Applications that provide authentication services must be able to replace the **Principal** object (<xref:System.Security.Principal.IPrincipal>) for a given thread.</span></span> <span data-ttu-id="a9a68-104">Kromě toho musí systém zabezpečení pomáhat chránit schopnost nahradit **hlavní** objekty, protože speciálně připojený, nesprávný **hlavní** ohrožuje zabezpečení vaší aplikace nárokování role nebo PRAVDA identity.</span><span class="sxs-lookup"><span data-stu-id="a9a68-104">Furthermore, the security system must help protect the ability to replace **Principal** objects because a maliciously attached, incorrect **Principal** compromises the security of your application by claiming an untrue identity or role.</span></span> <span data-ttu-id="a9a68-105">Proto aplikace, vyžadovat schopnost nahradit **hlavní** objekty musí mít udělen <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> objektu pro kontrolu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="a9a68-105">Therefore, applications that require the ability to replace **Principal** objects must be granted the <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType> object for principal control.</span></span> <span data-ttu-id="a9a68-106">(Všimněte si, že toto oprávnění není požadováno k provádění kontrol na základě rolí zabezpečení nebo vytváření **hlavní** objekty.)</span><span class="sxs-lookup"><span data-stu-id="a9a68-106">(Note that this permission is not required for performing role-based security checks or for creating **Principal** objects.)</span></span>  
  
 <span data-ttu-id="a9a68-107">Aktuální **hlavní** objekt lze nahradit provedením následujících úloh:</span><span class="sxs-lookup"><span data-stu-id="a9a68-107">The current **Principal** object can be replaced by performing the following tasks:</span></span>  
  
1.  <span data-ttu-id="a9a68-108">Vytvoření nahrazení **hlavní** objektu a související **Identity** objektu.</span><span class="sxs-lookup"><span data-stu-id="a9a68-108">Create the replacement **Principal** object and associated **Identity** object.</span></span>  
  
2.  <span data-ttu-id="a9a68-109">Připojit nové **hlavní** objekt, který má v kontextu.</span><span class="sxs-lookup"><span data-stu-id="a9a68-109">Attach the new **Principal** object to the call context.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9a68-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="a9a68-110">Example</span></span>  
 <span data-ttu-id="a9a68-111">Následující příklad ukazuje, jak vytvořit obecný objekt zabezpečení a použít ho nastavit objekt zabezpečení vlákna.</span><span class="sxs-lookup"><span data-stu-id="a9a68-111">The following example shows how to create a generic principal object and use it to set the principal of a thread.</span></span>  
  
 [!code-csharp[SetCurrentPrincipal#1](../../../samples/snippets/csharp/VS_Snippets_CLR/SetCurrentPrincipal/CS/program.cs#1)]
 [!code-vb[SetCurrentPrincipal#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/SetCurrentPrincipal/VB/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="a9a68-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="a9a68-112">See Also</span></span>  
 <xref:System.Security.Permissions.SecurityPermission?displayProperty=nameWithType>  
 [<span data-ttu-id="a9a68-113">Objekty zabezpečení a identity</span><span class="sxs-lookup"><span data-stu-id="a9a68-113">Principal and Identity Objects</span></span>](../../../docs/standard/security/principal-and-identity-objects.md)
