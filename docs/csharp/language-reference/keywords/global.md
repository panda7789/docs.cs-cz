---
title: globální kontextové klíčové slovo (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- global
- global_CSharpKeyword
helpviewer_keywords:
- global keyword [C#]
ms.assetid: 8932c16a-6959-42c2-86e7-2c4221ab788b
ms.openlocfilehash: 79e0184f58ffc6232038abdd3d9f852147d5732c
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404285"
---
# <a name="global-c-reference"></a><span data-ttu-id="e4217-102">global (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="e4217-102">global (C# Reference)</span></span>

<span data-ttu-id="e4217-103">`global` Kontextové klíčové slovo, pokud jde o před [:: operator](../operators/namespace-alias-qualifer.md), odkazuje na globální obor názvů, což je výchozí obor názvů pro libovolném programu C# a v opačném případě nepojmenovaný.</span><span class="sxs-lookup"><span data-stu-id="e4217-103">The `global` contextual keyword, when it comes before the [:: operator](../operators/namespace-alias-qualifer.md), refers to the global namespace, which is the default namespace for any C# program and is otherwise unnamed.</span></span> <span data-ttu-id="e4217-104">Další informace najdete v tématu [postupy: použití aliasu globálního Namespace](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md).</span><span class="sxs-lookup"><span data-stu-id="e4217-104">For more information, see [How to: Use the Global Namespace Alias](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md).</span></span>

## <a name="example"></a><span data-ttu-id="e4217-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="e4217-105">Example</span></span>

<span data-ttu-id="e4217-106">Následující příklad ukazuje způsob použití `global` kontextové klíčové slovo určit, že třída `TestApp` je definována v globálním oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="e4217-106">The following example shows how to use the `global` contextual keyword to specify that the class `TestApp` is defined in the global namespace:</span></span>

[!code-csharp[csrefKeywordsContextual#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#13)]

## <a name="see-also"></a><span data-ttu-id="e4217-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e4217-107">See also</span></span>

[<span data-ttu-id="e4217-108">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="e4217-108">Namespaces</span></span>](../../programming-guide/namespaces/index.md)