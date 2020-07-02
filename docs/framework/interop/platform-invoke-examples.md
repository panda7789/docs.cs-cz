---
title: Příklady vyvolání platformy
description: Podívejte se na příklad vyvolání platformy, který ukazuje, jak definovat a volat funkci MessageBox v User32.dll.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [.NET Framework], platform invoke
- unmanaged functions
- COM interop, platform invoke
- platform invoke, examples
- interoperation with unmanaged code, platform invoke
- DLL functions
ms.assetid: 15926806-f0b7-487e-93a6-4e9367ec689f
ms.openlocfilehash: 97b0720b8954bc24a4058e6a03c32d32bd9e3180
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620804"
---
# <a name="platform-invoke-examples"></a><span data-ttu-id="23cc9-103">Příklady vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="23cc9-103">Platform Invoke Examples</span></span>
<span data-ttu-id="23cc9-104">Následující příklady ukazují, jak definovat a volat funkci **MessageBox** v User32.dll, předejte jednoduchý řetězec jako argument.</span><span class="sxs-lookup"><span data-stu-id="23cc9-104">The following examples demonstrate how to define and call the **MessageBox** function in User32.dll, passing a simple string as an argument.</span></span> <span data-ttu-id="23cc9-105">V příkladech <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> je pole nastaveno na hodnotu **automaticky** , aby cílová platforma mohla určit šířku znaku a zařazování řetězců.</span><span class="sxs-lookup"><span data-stu-id="23cc9-105">In the examples, the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field is set to **Auto** to let the target platform determine the character width and string marshaling.</span></span>  
  
 [!code-cpp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cpp/Example.cpp#1)]
 [!code-csharp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cs/Example1.cs#1)]
 [!code-vb[Conceptual.Interop.PInvoke#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Interop.PInvoke/vb/Example1.vb#1)]  
  
 <span data-ttu-id="23cc9-106">Další příklady naleznete v tématu [zařazování dat s voláním platformy](marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="23cc9-106">For additional examples, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23cc9-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="23cc9-107">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="23cc9-108">Vytváření prototypů ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="23cc9-108">Creating Prototypes in Managed Code</span></span>](creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="23cc9-109">Určení sady znaků</span><span class="sxs-lookup"><span data-stu-id="23cc9-109">Specifying a Character Set</span></span>](specifying-a-character-set.md)
