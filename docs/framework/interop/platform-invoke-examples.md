---
title: "Příklady vyvolání platformy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1a4533aa1cef5d400fff0c8d3169b0b1edc22eab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="platform-invoke-examples"></a><span data-ttu-id="a2770-102">Příklady vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="a2770-102">Platform Invoke Examples</span></span>
<span data-ttu-id="a2770-103">Následující příklady ukazují, jak definovat a volání **MessageBox** funkce v User32.dll, předávání jednoduchý řetězec jako argument.</span><span class="sxs-lookup"><span data-stu-id="a2770-103">The following examples demonstrate how to define and call the **MessageBox** function in User32.dll, passing a simple string as an argument.</span></span> <span data-ttu-id="a2770-104">V příkladech <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> je nastaveno na **automaticky** umožníte cílové platformy určit Šířka znaku a zařazování pro řetězce.</span><span class="sxs-lookup"><span data-stu-id="a2770-104">In the examples, the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field is set to **Auto** to let the target platform determine the character width and string marshaling.</span></span>  
  
 [!code-cpp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cpp/Example.cpp#1)] 
 [!code-csharp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cs/Example1.cs#1)] 
 [!code-vb[Conceptual.Interop.PInvoke#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Interop.PInvoke/vb/Example1.vb#1)]  
  
 <span data-ttu-id="a2770-105">Další příklady najdete v tématu [zařazování dat s vyvolání platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="a2770-105">For additional examples, see [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2770-106">Viz také</span><span class="sxs-lookup"><span data-stu-id="a2770-106">See Also</span></span>  
 <xref:System.Runtime.InteropServices.DllImportAttribute>  
 [<span data-ttu-id="a2770-107">Vytváření prototypů ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="a2770-107">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [<span data-ttu-id="a2770-108">Určení znakové sady</span><span class="sxs-lookup"><span data-stu-id="a2770-108">Specifying a Character Set</span></span>](../../../docs/framework/interop/specifying-a-character-set.md)
