---
title: <paramref>- Průvodce programováním jazyka C#
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: 12df257271369dc7f0a5c066b712a8d8e6c38761
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793405"
---
# <a name="paramref-c-programming-guide"></a><span data-ttu-id="06e8d-102">\<paramref> (průvodce programováním Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="06e8d-102">\<paramref> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="06e8d-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06e8d-103">Syntax</span></span>

```xml
<paramref name="name"/>
```

## <a name="parameters"></a><span data-ttu-id="06e8d-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="06e8d-104">Parameters</span></span>

- `name`

  <span data-ttu-id="06e8d-105">Název parametru, na který se má odkazovat.</span><span class="sxs-lookup"><span data-stu-id="06e8d-105">The name of the parameter to refer to.</span></span> <span data-ttu-id="06e8d-106">Název uzavřete do uvozovek (" ").</span><span class="sxs-lookup"><span data-stu-id="06e8d-106">Enclose the name in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="06e8d-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="06e8d-107">Remarks</span></span>

<span data-ttu-id="06e8d-108">Značka \<paramref> vám dává způsob, jak označit, že slovo \<v komentářích kódu, například v souhrnné> nebo \<poznámky> bloku odkazuje na parametr.</span><span class="sxs-lookup"><span data-stu-id="06e8d-108">The \<paramref> tag gives you a way to indicate that a word in the code comments, for example in a \<summary> or \<remarks> block refers to a parameter.</span></span> <span data-ttu-id="06e8d-109">Soubor XML lze zpracovat pro formátování tohoto slova nějakým odlišným způsobem, například tučným písmem nebo kurzívou.</span><span class="sxs-lookup"><span data-stu-id="06e8d-109">The XML file can be processed to format this word in some distinct way, such as with a bold or italic font.</span></span>

<span data-ttu-id="06e8d-110">Kompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentů komentáře do souboru.</span><span class="sxs-lookup"><span data-stu-id="06e8d-110">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="06e8d-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="06e8d-111">Example</span></span>

[!code-csharp[csProgGuideDocComments#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#7)]

## <a name="see-also"></a><span data-ttu-id="06e8d-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="06e8d-112">See also</span></span>

- [<span data-ttu-id="06e8d-113">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="06e8d-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="06e8d-114">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="06e8d-114">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
