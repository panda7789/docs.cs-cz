---
title: <paramref>– Průvodce programováním v C#
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: 4f3b521d24c8b4677a05b0b145cb36c31b2793f2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287308"
---
# <a name="paramref-c-programming-guide"></a><span data-ttu-id="2b5e6-102">\<paramref>(Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="2b5e6-102">\<paramref> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="2b5e6-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b5e6-103">Syntax</span></span>

```xml
<paramref name="name"/>
```

## <a name="parameters"></a><span data-ttu-id="2b5e6-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="2b5e6-104">Parameters</span></span>

- `name`

  <span data-ttu-id="2b5e6-105">Název parametru, na který se má odkazovat</span><span class="sxs-lookup"><span data-stu-id="2b5e6-105">The name of the parameter to refer to.</span></span> <span data-ttu-id="2b5e6-106">Název uzavřete do uvozovek ("").</span><span class="sxs-lookup"><span data-stu-id="2b5e6-106">Enclose the name in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="2b5e6-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2b5e6-107">Remarks</span></span>

<span data-ttu-id="2b5e6-108">`<paramref>`Značka poskytuje způsob, jak označit, že slovo v komentářích kódu, například v `<summary>` bloku nebo, `<remarks>` odkazuje na parametr.</span><span class="sxs-lookup"><span data-stu-id="2b5e6-108">The `<paramref>` tag gives you a way to indicate that a word in the code comments, for example in a `<summary>` or `<remarks>` block refers to a parameter.</span></span> <span data-ttu-id="2b5e6-109">Soubor XML lze zpracovat pro formátování tohoto slova nějakým způsobem, například tučným písmem nebo kurzívou.</span><span class="sxs-lookup"><span data-stu-id="2b5e6-109">The XML file can be processed to format this word in some distinct way, such as with a bold or italic font.</span></span>

<span data-ttu-id="2b5e6-110">Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="2b5e6-110">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="2b5e6-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="2b5e6-111">Example</span></span>

[!code-csharp[csProgGuideDocComments#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#7)]

## <a name="see-also"></a><span data-ttu-id="2b5e6-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="2b5e6-112">See also</span></span>

- [<span data-ttu-id="2b5e6-113">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="2b5e6-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2b5e6-114">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="2b5e6-114">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
