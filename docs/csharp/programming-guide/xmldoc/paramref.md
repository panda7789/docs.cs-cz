---
title: <paramref>– Průvodce programováním v C#
description: Přečtěte si o <paramref> značce XML. Tato značka poskytuje způsob, jak označit, že slovo v kódu je parametr.
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: 133f43abfaf349806404d6d37fb472e3145c51b7
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381837"
---
# <a name="paramref-c-programming-guide"></a><span data-ttu-id="9a5db-104">\<paramref>(Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="9a5db-104">\<paramref> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="9a5db-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9a5db-105">Syntax</span></span>

```xml
<paramref name="name"/>
```

## <a name="parameters"></a><span data-ttu-id="9a5db-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="9a5db-106">Parameters</span></span>

- `name`

  <span data-ttu-id="9a5db-107">Název parametru, na který se má odkazovat</span><span class="sxs-lookup"><span data-stu-id="9a5db-107">The name of the parameter to refer to.</span></span> <span data-ttu-id="9a5db-108">Název uzavřete do uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="9a5db-108">Enclose the name in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="9a5db-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9a5db-109">Remarks</span></span>

<span data-ttu-id="9a5db-110">`<paramref>`Značka poskytuje způsob, jak označit, že slovo v komentářích kódu, například v `<summary>` bloku nebo, `<remarks>` odkazuje na parametr.</span><span class="sxs-lookup"><span data-stu-id="9a5db-110">The `<paramref>` tag gives you a way to indicate that a word in the code comments, for example in a `<summary>` or `<remarks>` block refers to a parameter.</span></span> <span data-ttu-id="9a5db-111">Soubor XML lze zpracovat pro formátování tohoto slova nějakým způsobem, například tučným písmem nebo kurzívou.</span><span class="sxs-lookup"><span data-stu-id="9a5db-111">The XML file can be processed to format this word in some distinct way, such as with a bold or italic font.</span></span>

<span data-ttu-id="9a5db-112">Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="9a5db-112">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="9a5db-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="9a5db-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#7)]

## <a name="see-also"></a><span data-ttu-id="9a5db-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9a5db-114">See also</span></span>

- [<span data-ttu-id="9a5db-115">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="9a5db-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9a5db-116">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="9a5db-116">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
