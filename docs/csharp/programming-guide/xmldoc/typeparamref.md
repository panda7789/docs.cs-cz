---
title: <typeparamref> - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: 834aff6e4673a306559daa1b9517e11538e90ad0
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55273345"
---
# <a name="typeparamref-c-programming-guide"></a><span data-ttu-id="261c5-102">\<typeparamref > (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="261c5-102">\<typeparamref> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="261c5-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="261c5-103">Syntax</span></span>  
  
```xml  
<typeparamref name="name"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="261c5-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="261c5-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="261c5-105">Název parametru typu.</span><span class="sxs-lookup"><span data-stu-id="261c5-105">The name of the type parameter.</span></span> <span data-ttu-id="261c5-106">Název uzavřete do dvojitých uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="261c5-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="261c5-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="261c5-107">Remarks</span></span>  
 <span data-ttu-id="261c5-108">Další informace o parametrech typu v obecné typy a metody, naleznete v tématu [obecných typů](../../../csharp/programming-guide/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="261c5-108">For more information on type parameters in generic types and methods, see [Generics](../../../csharp/programming-guide/generics/index.md).</span></span>  
  
 <span data-ttu-id="261c5-109">Použijte tuto značku k povolení příjemcům soubor dokumentace k formátování slovo nějakým způsobem distinct, například kurzívou.</span><span class="sxs-lookup"><span data-stu-id="261c5-109">Use this tag to enable consumers of the documentation file to format the word in some distinct way, for example in italics.</span></span>  
  
 <span data-ttu-id="261c5-110">Kompilovat s [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentačních komentářů do souboru.</span><span class="sxs-lookup"><span data-stu-id="261c5-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="261c5-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="261c5-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#13](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/typeparamref_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="261c5-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="261c5-112">See also</span></span>

- [<span data-ttu-id="261c5-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="261c5-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="261c5-114">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="261c5-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
