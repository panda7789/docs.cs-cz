---
title: Příklady vyvolání platformy
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 37a864083fa7cfbea16614a94454571f31deed3a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59136705"
---
# <a name="platform-invoke-examples"></a><span data-ttu-id="1ca68-102">Příklady vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="1ca68-102">Platform Invoke Examples</span></span>
<span data-ttu-id="1ca68-103">Následující příklady ukazují, jak definovat a volat **MessageBox** funkce v User32.dll předáním jako argument jednoduchým řetězcem.</span><span class="sxs-lookup"><span data-stu-id="1ca68-103">The following examples demonstrate how to define and call the **MessageBox** function in User32.dll, passing a simple string as an argument.</span></span> <span data-ttu-id="1ca68-104">V příkladech <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> je nastaveno na **automaticky** chcete, aby cílová platforma určit Šířka znaku a zařazování pro řetězce.</span><span class="sxs-lookup"><span data-stu-id="1ca68-104">In the examples, the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field is set to **Auto** to let the target platform determine the character width and string marshaling.</span></span>  
  
 [!code-cpp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cpp/Example.cpp#1)] 
 [!code-csharp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cs/Example1.cs#1)] 
 [!code-vb[Conceptual.Interop.PInvoke#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Interop.PInvoke/vb/Example1.vb#1)]  
  
 <span data-ttu-id="1ca68-105">Další příklady najdete v tématu [zařazování dat pomocí vyvolání platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="1ca68-105">For additional examples, see [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ca68-106">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1ca68-106">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="1ca68-107">Vytváření prototypů ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="1ca68-107">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
- [<span data-ttu-id="1ca68-108">Určení sady znaků</span><span class="sxs-lookup"><span data-stu-id="1ca68-108">Specifying a Character Set</span></span>](../../../docs/framework/interop/specifying-a-character-set.md)
