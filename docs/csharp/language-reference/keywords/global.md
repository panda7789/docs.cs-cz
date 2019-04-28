---
title: globální kontextové klíčové slovo - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- global
- global_CSharpKeyword
helpviewer_keywords:
- global keyword [C#]
ms.assetid: 8932c16a-6959-42c2-86e7-2c4221ab788b
ms.openlocfilehash: b9273feb38b14dce61facc0f59b0890c431b9a7a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61661506"
---
# <a name="global-c-reference"></a><span data-ttu-id="68637-102">global (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="68637-102">global (C# Reference)</span></span>

<span data-ttu-id="68637-103">`global` Kontextové klíčové slovo, pokud jde o před [:: operator](../operators/namespace-alias-qualifer.md), odkazuje na globální obor názvů, což je výchozí obor názvů pro libovolném programu C# a v opačném případě nepojmenovaný.</span><span class="sxs-lookup"><span data-stu-id="68637-103">The `global` contextual keyword, when it comes before the [:: operator](../operators/namespace-alias-qualifer.md), refers to the global namespace, which is the default namespace for any C# program and is otherwise unnamed.</span></span> <span data-ttu-id="68637-104">Další informace najdete v tématu [jak: Použití aliasu globálního Namespace](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md).</span><span class="sxs-lookup"><span data-stu-id="68637-104">For more information, see [How to: Use the Global Namespace Alias](../../programming-guide/namespaces/how-to-use-the-global-namespace-alias.md).</span></span>

## <a name="example"></a><span data-ttu-id="68637-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="68637-105">Example</span></span>

<span data-ttu-id="68637-106">Následující příklad ukazuje způsob použití `global` kontextové klíčové slovo určit, že třída `TestApp` je definována v globálním oboru názvů:</span><span class="sxs-lookup"><span data-stu-id="68637-106">The following example shows how to use the `global` contextual keyword to specify that the class `TestApp` is defined in the global namespace:</span></span>

[!code-csharp[csrefKeywordsContextual#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#13)]

## <a name="see-also"></a><span data-ttu-id="68637-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="68637-107">See also</span></span>

- [<span data-ttu-id="68637-108">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="68637-108">Namespaces</span></span>](../../programming-guide/namespaces/index.md)