---
title: <typeparamref>– C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: f01df27b920dcf3011a51015c771d2da3b442c4c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69587427"
---
# <a name="typeparamref-c-programming-guide"></a><span data-ttu-id="910c1-102">\<typeparamref > (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="910c1-102">\<typeparamref> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="910c1-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="910c1-103">Syntax</span></span>  
  
```xml  
<typeparamref name="name"/>  
```  
  
## <a name="parameters"></a><span data-ttu-id="910c1-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="910c1-104">Parameters</span></span>  
 `name`  
 <span data-ttu-id="910c1-105">Název parametru typu.</span><span class="sxs-lookup"><span data-stu-id="910c1-105">The name of the type parameter.</span></span> <span data-ttu-id="910c1-106">Název uzavřete do uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="910c1-106">Enclose the name in double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="910c1-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="910c1-107">Remarks</span></span>  
 <span data-ttu-id="910c1-108">Další informace o parametrech typu v obecných typech a metodách naleznete [](../generics/index.md)v tématu generické typy.</span><span class="sxs-lookup"><span data-stu-id="910c1-108">For more information on type parameters in generic types and methods, see [Generics](../generics/index.md).</span></span>  
  
 <span data-ttu-id="910c1-109">Pomocí této značky můžete uživatelům souboru dokumentace povolit formátování určitého slova nějakým způsobem, například kurzívou.</span><span class="sxs-lookup"><span data-stu-id="910c1-109">Use this tag to enable consumers of the documentation file to format the word in some distinct way, for example in italics.</span></span>  
  
 <span data-ttu-id="910c1-110">Zkompilujte pomocí [/doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte dokumentační komentáře do souboru.</span><span class="sxs-lookup"><span data-stu-id="910c1-110">Compile with [/doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="910c1-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="910c1-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]  
  
## <a name="see-also"></a><span data-ttu-id="910c1-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="910c1-112">See also</span></span>

- [<span data-ttu-id="910c1-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="910c1-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="910c1-114">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="910c1-114">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
