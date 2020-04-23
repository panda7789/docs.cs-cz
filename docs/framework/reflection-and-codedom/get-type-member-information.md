---
title: 'Postupy: načtení informací o typu a členu pomocí reflexe'
ms.date: 09/03/2019
helpviewer_keywords:
- reflection, obtaining member information
- types [.NET Framework], obtaining member information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
dev_langs:
- cpp
- csharp
- vb
ms.openlocfilehash: 9ffc173bbd0ed12eedea0c191f6d39baf181793a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130206"
---
# <a name="how-to-get-type-and-member-information-by-using-reflection"></a><span data-ttu-id="3ce4c-102">Postupy: načtení informací o typu a členu pomocí reflexe</span><span class="sxs-lookup"><span data-stu-id="3ce4c-102">How to: Get type and member information by using reflection</span></span>
<span data-ttu-id="3ce4c-103"><xref:System.Reflection> Obor názvů obsahuje mnoho metod získání informací o typech a jejich členech.</span><span class="sxs-lookup"><span data-stu-id="3ce4c-103">The <xref:System.Reflection> namespace contains many methods for obtaining information about types and their members.</span></span> <span data-ttu-id="3ce4c-104">Tento článek ukazuje jednu z těchto metod, <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3ce4c-104">This article demonstrates one of these methods, <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3ce4c-105">Další informace najdete v tématu [Přehled reflexe](reflection.md).</span><span class="sxs-lookup"><span data-stu-id="3ce4c-105">For additional information, see [Reflection overview](reflection.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="3ce4c-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="3ce4c-106">Example</span></span>

<span data-ttu-id="3ce4c-107">Následující příklad získá informace o typu a členu pomocí reflexe:</span><span class="sxs-lookup"><span data-stu-id="3ce4c-107">The following example obtains type and member information by using reflection:</span></span>

[!code-cpp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cpp)]
[!code-csharp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cs)]
[!code-vb[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.vb)]

## <a name="see-also"></a><span data-ttu-id="3ce4c-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="3ce4c-108">See also</span></span>

- [<span data-ttu-id="3ce4c-109">Program s aplikačními doménami</span><span class="sxs-lookup"><span data-stu-id="3ce4c-109">Program with application domains</span></span>](../app-domains/application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="3ce4c-110">Reflexe</span><span class="sxs-lookup"><span data-stu-id="3ce4c-110">Reflection</span></span>](reflection.md)
- [<span data-ttu-id="3ce4c-111">Použití aplikačních domén</span><span class="sxs-lookup"><span data-stu-id="3ce4c-111">Use application domains</span></span>](../app-domains/use.md)
