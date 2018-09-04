---
title: '&lt;paramref&gt; (C# Programming Guide)'
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: 0e837a3acdd6316446327453af4508f501a9437b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43518348"
---
# <a name="ltparamrefgt-c-programming-guide"></a><span data-ttu-id="17974-102">&lt;paramref&gt; (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="17974-102">&lt;paramref&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="17974-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17974-103">Syntax</span></span>  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="17974-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="17974-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="17974-105">Název parametru jako reference.</span><span class="sxs-lookup"><span data-stu-id="17974-105">The name of the parameter to refer to.</span></span> <span data-ttu-id="17974-106">Název uzavřete do dvojitých uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="17974-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17974-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="17974-107">Remarks</span></span>  
 <span data-ttu-id="17974-108">\<Paramref > značky poskytuje způsob, jak určit, že slovo v kódu komentáře, například v \<summary > nebo \<Poznámky > bloku odkazuje na parametr.</span><span class="sxs-lookup"><span data-stu-id="17974-108">The \<paramref> tag gives you a way to indicate that a word in the code comments, for example in a \<summary> or \<remarks> block refers to a parameter.</span></span> <span data-ttu-id="17974-109">Soubor XML mohou být zpracovány do naformátuje toto slovo distinct způsobem, jako tučný nebo kurzívu písma.</span><span class="sxs-lookup"><span data-stu-id="17974-109">The XML file can be processed to format this word in some distinct way, such as with a bold or italic font.</span></span>  
  
 <span data-ttu-id="17974-110">Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="17974-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17974-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="17974-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#7](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/paramref_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="17974-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="17974-112">See Also</span></span>

- [<span data-ttu-id="17974-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="17974-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="17974-114">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="17974-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
