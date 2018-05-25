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
ms.openlocfilehash: 330d8ff784218483caf153b5c14f8a30df2d2452
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="platform-invoke-examples"></a><span data-ttu-id="0b97a-102">Příklady vyvolání platformy</span><span class="sxs-lookup"><span data-stu-id="0b97a-102">Platform Invoke Examples</span></span>
<span data-ttu-id="0b97a-103">Následující příklady ukazují, jak definovat a volání **MessageBox** funkce v User32.dll, předávání jednoduchý řetězec jako argument.</span><span class="sxs-lookup"><span data-stu-id="0b97a-103">The following examples demonstrate how to define and call the **MessageBox** function in User32.dll, passing a simple string as an argument.</span></span> <span data-ttu-id="0b97a-104">V příkladech <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> je nastaveno na **automaticky** umožníte cílové platformy určit Šířka znaku a zařazování pro řetězce.</span><span class="sxs-lookup"><span data-stu-id="0b97a-104">In the examples, the <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet?displayProperty=nameWithType> field is set to **Auto** to let the target platform determine the character width and string marshaling.</span></span>  
  
 [!code-cpp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/cpp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cpp/Example.cpp#1)] 
 [!code-csharp[Conceptual.Interop.PInvoke#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.Interop.PInvoke/cs/Example1.cs#1)] 
 [!code-vb[Conceptual.Interop.PInvoke#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.Interop.PInvoke/vb/Example1.vb#1)]  
  
 <span data-ttu-id="0b97a-105">Další příklady najdete v tématu [zařazování dat s vyvolání platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="0b97a-105">For additional examples, see [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b97a-106">Viz také</span><span class="sxs-lookup"><span data-stu-id="0b97a-106">See Also</span></span>  
 <xref:System.Runtime.InteropServices.DllImportAttribute>  
 [<span data-ttu-id="0b97a-107">Vytváření prototypů ve spravovaném kódu</span><span class="sxs-lookup"><span data-stu-id="0b97a-107">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [<span data-ttu-id="0b97a-108">Určení znakové sady</span><span class="sxs-lookup"><span data-stu-id="0b97a-108">Specifying a Character Set</span></span>](../../../docs/framework/interop/specifying-a-character-set.md)
