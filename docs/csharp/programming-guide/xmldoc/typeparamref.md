---
title: '&lt;typeparamref&gt; - C# Průvodce programováním pro službu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: cfee16ad1cdc1e019a4133259c1603f5a0a09ac8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54536552"
---
# <a name="lttypeparamrefgt-c-programming-guide"></a><span data-ttu-id="e09c6-102">&lt;typeparamref&gt; (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="e09c6-102">&lt;typeparamref&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="e09c6-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e09c6-103">Syntax</span></span>  
  
```xml  
<typeparamref name="name"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e09c6-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="e09c6-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="e09c6-105">Název parametru typu.</span><span class="sxs-lookup"><span data-stu-id="e09c6-105">The name of the type parameter.</span></span> <span data-ttu-id="e09c6-106">Název uzavřete do dvojitých uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="e09c6-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e09c6-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e09c6-107">Remarks</span></span>  
 <span data-ttu-id="e09c6-108">Další informace o parametrech typu v obecné typy a metody, naleznete v tématu [obecných typů](../../../csharp/programming-guide/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="e09c6-108">For more information on type parameters in generic types and methods, see [Generics](../../../csharp/programming-guide/generics/index.md).</span></span>  
  
 <span data-ttu-id="e09c6-109">Použijte tuto značku k povolení příjemcům soubor dokumentace k formátování slovo nějakým způsobem distinct, například kurzívou.</span><span class="sxs-lookup"><span data-stu-id="e09c6-109">Use this tag to enable consumers of the documentation file to format the word in some distinct way, for example in italics.</span></span>  
  
 <span data-ttu-id="e09c6-110">Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="e09c6-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e09c6-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="e09c6-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#13](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/typeparamref_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="e09c6-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e09c6-112">See also</span></span>

- [<span data-ttu-id="e09c6-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e09c6-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="e09c6-114">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="e09c6-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
