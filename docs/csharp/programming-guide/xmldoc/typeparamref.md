---
title: Průvodce C# programováním <typeparamref>
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: 3e96d55d7cf60b2a9085cf065ef3b8193b173c5d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711672"
---
# <a name="typeparamref-c-programming-guide"></a><span data-ttu-id="9f289-102">\<typeparamref > (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="9f289-102">\<typeparamref> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="9f289-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f289-103">Syntax</span></span>  
  
```xml  
<typeparamref name="name"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f289-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="9f289-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="9f289-105">Název parametru typu.</span><span class="sxs-lookup"><span data-stu-id="9f289-105">The name of the type parameter.</span></span> <span data-ttu-id="9f289-106">Název uzavřete do uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="9f289-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9f289-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9f289-107">Remarks</span></span>  
 <span data-ttu-id="9f289-108">Další informace o parametrech typu v obecných typech a metodách naleznete v tématu [generické](../generics/index.md)typy.</span><span class="sxs-lookup"><span data-stu-id="9f289-108">For more information on type parameters in generic types and methods, see [Generics](../generics/index.md).</span></span>  
  
 <span data-ttu-id="9f289-109">Pomocí této značky můžete uživatelům souboru dokumentace povolit formátování určitého slova nějakým způsobem, například kurzívou.</span><span class="sxs-lookup"><span data-stu-id="9f289-109">Use this tag to enable consumers of the documentation file to format the word in some distinct way, for example in italics.</span></span>  
  
 <span data-ttu-id="9f289-110">Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="9f289-110">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f289-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="9f289-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]  
  
## <a name="see-also"></a><span data-ttu-id="9f289-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9f289-112">See also</span></span>

- [<span data-ttu-id="9f289-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="9f289-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9f289-114">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="9f289-114">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
