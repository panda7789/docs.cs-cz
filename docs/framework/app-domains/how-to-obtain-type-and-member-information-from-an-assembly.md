---
title: "Postupy: Získávání informací o typu a členu ze sestavení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- obtaining assembly information
- assemblies [.NET Framework], obtaining information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1c3112b7484e4d03eaacd218ff8e8ac34e77745b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-obtain-type-and-member-information-from-an-assembly"></a><span data-ttu-id="8d7a3-102">Postupy: Získávání informací o typu a členu ze sestavení</span><span class="sxs-lookup"><span data-stu-id="8d7a3-102">How to: Obtain Type and Member Information from an Assembly</span></span>
<span data-ttu-id="8d7a3-103"><xref:System.Reflection> Obor názvů obsahuje mnoho metody pro získání informací ze sestavení.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-103">The <xref:System.Reflection> namespace contains many methods for obtaining information from an assembly.</span></span> <span data-ttu-id="8d7a3-104">V této části ukážeme jednu z těchto metod.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-104">This section demonstrates one of these methods.</span></span> <span data-ttu-id="8d7a3-105">Další informace najdete v tématu [Přehled reflexe](../../../docs/framework/reflection-and-codedom/reflection.md).</span><span class="sxs-lookup"><span data-stu-id="8d7a3-105">For additional information, see [Reflection Overview](../../../docs/framework/reflection-and-codedom/reflection.md).</span></span>  
  
 <span data-ttu-id="8d7a3-106">Následující příklad získává informace typu a členu ze sestavení.</span><span class="sxs-lookup"><span data-stu-id="8d7a3-106">The following example obtains type and member information from an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d7a3-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="8d7a3-107">Example</span></span>  
 [!code-cpp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source6.cpp#8)]
 [!code-csharp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source6.cs#8)]
 [!code-vb[Conceptual.Types.ViewInfo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source6.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="8d7a3-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="8d7a3-108">See Also</span></span>  
 [<span data-ttu-id="8d7a3-109">Programování s doménami aplikací</span><span class="sxs-lookup"><span data-stu-id="8d7a3-109">Programming with Application Domains</span></span>](http://msdn.microsoft.com/library/bd36055b-56bd-43eb-b4d8-820c37172131)  
 [<span data-ttu-id="8d7a3-110">Reflexe</span><span class="sxs-lookup"><span data-stu-id="8d7a3-110">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
 [<span data-ttu-id="8d7a3-111">Používání domén aplikací</span><span class="sxs-lookup"><span data-stu-id="8d7a3-111">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
