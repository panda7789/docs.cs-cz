---
title: 'Postupy: Získávání informací o typu a členu ze sestavení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- obtaining assembly information
- assemblies [.NET Framework], obtaining information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 44fcded298f33a420a505900f618c1c67f4b9b6f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50180059"
---
# <a name="how-to-obtain-type-and-member-information-from-an-assembly"></a><span data-ttu-id="4827d-102">Postupy: Získávání informací o typu a členu ze sestavení</span><span class="sxs-lookup"><span data-stu-id="4827d-102">How to: Obtain Type and Member Information from an Assembly</span></span>
<span data-ttu-id="4827d-103"><xref:System.Reflection> Obor názvů obsahuje mnoho metod pro získání informací ze sestavení.</span><span class="sxs-lookup"><span data-stu-id="4827d-103">The <xref:System.Reflection> namespace contains many methods for obtaining information from an assembly.</span></span> <span data-ttu-id="4827d-104">Tato část ukazuje jednu z těchto metod.</span><span class="sxs-lookup"><span data-stu-id="4827d-104">This section demonstrates one of these methods.</span></span> <span data-ttu-id="4827d-105">Další informace najdete v tématu [Přehled reflexe](../../../docs/framework/reflection-and-codedom/reflection.md).</span><span class="sxs-lookup"><span data-stu-id="4827d-105">For additional information, see [Reflection Overview](../../../docs/framework/reflection-and-codedom/reflection.md).</span></span>  
  
 <span data-ttu-id="4827d-106">Následující příklad získá informace o typu a členu ze sestavení.</span><span class="sxs-lookup"><span data-stu-id="4827d-106">The following example obtains type and member information from an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4827d-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="4827d-107">Example</span></span>  
 [!code-cpp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.types.viewinfo/cpp/source6.cpp#8)]
 [!code-csharp[Conceptual.Types.ViewInfo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.viewinfo/cs/source6.cs#8)]
 [!code-vb[Conceptual.Types.ViewInfo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.viewinfo/vb/source6.vb#8)]  
  
## <a name="see-also"></a><span data-ttu-id="4827d-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="4827d-108">See Also</span></span>  
- [<span data-ttu-id="4827d-109">Programování pomocí domén aplikace</span><span class="sxs-lookup"><span data-stu-id="4827d-109">Programming with Application Domains</span></span>](./application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="4827d-110">Reflexe</span><span class="sxs-lookup"><span data-stu-id="4827d-110">Reflection</span></span>](../../../docs/framework/reflection-and-codedom/reflection.md)  
- [<span data-ttu-id="4827d-111">Používání domén aplikací</span><span class="sxs-lookup"><span data-stu-id="4827d-111">Using Application Domains</span></span>](../../../docs/framework/app-domains/use.md)
