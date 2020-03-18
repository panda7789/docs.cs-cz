---
title: <typeparamref>- Průvodce programováním jazyka C#
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: 266eadad322fd3c4167c7a911cb57ef1e1333012
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789662"
---
# <a name="typeparamref-c-programming-guide"></a><span data-ttu-id="2ffbc-102">\<typeparamref> (průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="2ffbc-102">\<typeparamref> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="2ffbc-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ffbc-103">Syntax</span></span>

```xml
<typeparamref name="name"/>
```

## <a name="parameters"></a><span data-ttu-id="2ffbc-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="2ffbc-104">Parameters</span></span>

- `name`

  <span data-ttu-id="2ffbc-105">Název parametru typu.</span><span class="sxs-lookup"><span data-stu-id="2ffbc-105">The name of the type parameter.</span></span> <span data-ttu-id="2ffbc-106">Název uzavřete do uvozovek (" ").</span><span class="sxs-lookup"><span data-stu-id="2ffbc-106">Enclose the name in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="2ffbc-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2ffbc-107">Remarks</span></span>

<span data-ttu-id="2ffbc-108">Další informace o parametrech typu v obecných typech a metodách naleznete v [tématu Generics](../generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="2ffbc-108">For more information on type parameters in generic types and methods, see [Generics](../generics/index.md).</span></span>

<span data-ttu-id="2ffbc-109">Pomocí této značky můžete spotřebitelům souboru dokumentace umožnit formátovat slovo nějakým odlišným způsobem, například kurzívou.</span><span class="sxs-lookup"><span data-stu-id="2ffbc-109">Use this tag to enable consumers of the documentation file to format the word in some distinct way, for example in italics.</span></span>

<span data-ttu-id="2ffbc-110">Kompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentů komentáře do souboru.</span><span class="sxs-lookup"><span data-stu-id="2ffbc-110">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="2ffbc-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="2ffbc-111">Example</span></span>

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a><span data-ttu-id="2ffbc-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="2ffbc-112">See also</span></span>

- [<span data-ttu-id="2ffbc-113">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="2ffbc-113">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="2ffbc-114">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="2ffbc-114">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
