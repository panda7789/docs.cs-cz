---
title: <typeparamref>– Průvodce programováním v C#
description: Přečtěte si o <typeparamref> značce XML. Tato značka umožňuje uživatelům souboru dokumentace naformátovat nějaký text nějakým způsobem, například kurzívou.
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: a39e896f1242452c7bcc94faa1e7ef3086ae2149
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380719"
---
# <a name="typeparamref-c-programming-guide"></a><span data-ttu-id="86fd7-104">\<typeparamref>(Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="86fd7-104">\<typeparamref> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="86fd7-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86fd7-105">Syntax</span></span>

```xml
<typeparamref name="name"/>
```

## <a name="parameters"></a><span data-ttu-id="86fd7-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="86fd7-106">Parameters</span></span>

- `name`

  <span data-ttu-id="86fd7-107">Název parametru typu.</span><span class="sxs-lookup"><span data-stu-id="86fd7-107">The name of the type parameter.</span></span> <span data-ttu-id="86fd7-108">Název uzavřete do uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="86fd7-108">Enclose the name in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="86fd7-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="86fd7-109">Remarks</span></span>

<span data-ttu-id="86fd7-110">Další informace o parametrech typu v obecných typech a metodách naleznete v tématu [generické](../generics/index.md)typy.</span><span class="sxs-lookup"><span data-stu-id="86fd7-110">For more information on type parameters in generic types and methods, see [Generics](../generics/index.md).</span></span>

<span data-ttu-id="86fd7-111">Pomocí této značky můžete uživatelům souboru dokumentace povolit formátování určitého slova nějakým způsobem, například kurzívou.</span><span class="sxs-lookup"><span data-stu-id="86fd7-111">Use this tag to enable consumers of the documentation file to format the word in some distinct way, for example in italics.</span></span>

<span data-ttu-id="86fd7-112">Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="86fd7-112">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="86fd7-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="86fd7-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a><span data-ttu-id="86fd7-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="86fd7-114">See also</span></span>

- [<span data-ttu-id="86fd7-115">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="86fd7-115">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="86fd7-116">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="86fd7-116">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
