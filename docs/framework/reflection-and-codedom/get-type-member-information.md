---
title: 'Postupy: Získání informací o typech a členech pomocí reflexe'
description: Naučte se, jak získat informace o typu a členu pomocí reflexe pomocí oboru názvů System. Reflection.
ms.date: 09/03/2019
helpviewer_keywords:
- reflection, obtaining member information
- types [.NET Framework], obtaining member information from
ms.assetid: 348ae651-ccda-4f13-8eda-19e8337e9438
dev_langs:
- cpp
- csharp
- vb
ms.openlocfilehash: fa7af39c0addb328944a03236c26982301caf722
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865317"
---
# <a name="how-to-get-type-and-member-information-by-using-reflection"></a><span data-ttu-id="b1f3f-103">Postupy: Získání informací o typech a členech pomocí reflexe</span><span class="sxs-lookup"><span data-stu-id="b1f3f-103">How to: Get type and member information by using reflection</span></span>
<span data-ttu-id="b1f3f-104"><xref:System.Reflection>Obor názvů obsahuje mnoho metod získání informací o typech a jejich členech.</span><span class="sxs-lookup"><span data-stu-id="b1f3f-104">The <xref:System.Reflection> namespace contains many methods for obtaining information about types and their members.</span></span> <span data-ttu-id="b1f3f-105">Tento článek ukazuje jednu z těchto metod, <xref:System.Type.GetMembers%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="b1f3f-105">This article demonstrates one of these methods, <xref:System.Type.GetMembers%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b1f3f-106">Další informace najdete v tématu [Přehled reflexe](reflection.md).</span><span class="sxs-lookup"><span data-stu-id="b1f3f-106">For additional information, see [Reflection overview](reflection.md).</span></span>
  
## <a name="example"></a><span data-ttu-id="b1f3f-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="b1f3f-107">Example</span></span>

<span data-ttu-id="b1f3f-108">Následující příklad získá informace o typu a členu pomocí reflexe:</span><span class="sxs-lookup"><span data-stu-id="b1f3f-108">The following example obtains type and member information by using reflection:</span></span>

[!code-cpp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cpp)]
[!code-csharp[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.cs)]
[!code-vb[Get type members](../../../samples/snippets/standard/reflection/memberinfo/gettypemembers.vb)]

## <a name="see-also"></a><span data-ttu-id="b1f3f-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="b1f3f-109">See also</span></span>

- [<span data-ttu-id="b1f3f-110">Program s aplikačními doménami</span><span class="sxs-lookup"><span data-stu-id="b1f3f-110">Program with application domains</span></span>](../app-domains/application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="b1f3f-111">Reflexe</span><span class="sxs-lookup"><span data-stu-id="b1f3f-111">Reflection</span></span>](reflection.md)
- [<span data-ttu-id="b1f3f-112">Použití aplikačních domén</span><span class="sxs-lookup"><span data-stu-id="b1f3f-112">Use application domains</span></span>](../app-domains/use.md)
