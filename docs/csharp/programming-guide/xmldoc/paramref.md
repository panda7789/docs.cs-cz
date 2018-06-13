---
title: '&lt;paramref&gt; (C# Průvodce programováním)'
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: 0b0d49b90e097e23d3878281f9accda14b057720
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33325130"
---
# <a name="ltparamrefgt-c-programming-guide"></a><span data-ttu-id="5a4bf-102">&lt;paramref&gt; (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="5a4bf-102">&lt;paramref&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="5a4bf-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5a4bf-103">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5a4bf-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="5a4bf-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="5a4bf-105">Název parametru, který bude odkazovat na.</span><span class="sxs-lookup"><span data-stu-id="5a4bf-105">The name of the parameter to refer to.</span></span> <span data-ttu-id="5a4bf-106">Uzavřete název do dvojitých uvozovek nahoře ("").</span><span class="sxs-lookup"><span data-stu-id="5a4bf-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a4bf-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5a4bf-107">Remarks</span></span>  
 <span data-ttu-id="5a4bf-108">\<Paramref > Značka poskytuje způsob, jak znamenat, že komentáře slovo v kódu, například v \<souhrnné > nebo \<Poznámky > bloku odkazuje na parametr.</span><span class="sxs-lookup"><span data-stu-id="5a4bf-108">The \<paramref> tag gives you a way to indicate that a word in the code comments, for example in a \<summary> or \<remarks> block refers to a parameter.</span></span> <span data-ttu-id="5a4bf-109">K formátování slovo nějakým způsobem distinct, například s tučné a kurzíva písma lze zpracovat soubor XML.</span><span class="sxs-lookup"><span data-stu-id="5a4bf-109">The XML file can be processed to format this word in some distinct way, such as with a bold or italic font.</span></span>  
  
 <span data-ttu-id="5a4bf-110">Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="5a4bf-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a4bf-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="5a4bf-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#7](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/paramref_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="5a4bf-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a4bf-112">See Also</span></span>  
 [<span data-ttu-id="5a4bf-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="5a4bf-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5a4bf-114">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="5a4bf-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
