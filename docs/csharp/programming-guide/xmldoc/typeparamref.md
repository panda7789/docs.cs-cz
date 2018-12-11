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
ms.openlocfilehash: bbe9bed5a32e463424b98f4066e95374401931e2
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243917"
---
# <a name="lttypeparamrefgt-c-programming-guide"></a><span data-ttu-id="4752b-102">&lt;typeparamref&gt; (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="4752b-102">&lt;typeparamref&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="4752b-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4752b-103">Syntax</span></span>  
  
```xml  
<typeparamref name="name"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4752b-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="4752b-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="4752b-105">Název parametru typu.</span><span class="sxs-lookup"><span data-stu-id="4752b-105">The name of the type parameter.</span></span> <span data-ttu-id="4752b-106">Název uzavřete do dvojitých uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="4752b-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4752b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4752b-107">Remarks</span></span>  
 <span data-ttu-id="4752b-108">Další informace o parametrech typu v obecné typy a metody, naleznete v tématu [obecných typů](../../../csharp/programming-guide/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="4752b-108">For more information on type parameters in generic types and methods, see [Generics](../../../csharp/programming-guide/generics/index.md).</span></span>  
  
 <span data-ttu-id="4752b-109">Použijte tuto značku k povolení příjemcům soubor dokumentace k formátování slovo nějakým způsobem distinct, například kurzívou.</span><span class="sxs-lookup"><span data-stu-id="4752b-109">Use this tag to enable consumers of the documentation file to format the word in some distinct way, for example in italics.</span></span>  
  
 <span data-ttu-id="4752b-110">Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="4752b-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4752b-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="4752b-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#13](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/typeparamref_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="4752b-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="4752b-112">See Also</span></span>

- [<span data-ttu-id="4752b-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="4752b-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="4752b-114">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="4752b-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
