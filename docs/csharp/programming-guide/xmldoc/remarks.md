---
title: <remarks> – Průvodce programováním v C#
description: Další informace o XML <remarks> Inteligentní. Tato značka slouží k přidání informací o typu, doplňování informací zadaných s <summary>.
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: d38905d100e24158e7a1412f6be9f01a7ced2382
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381499"
---
# <a name="remarks-c-programming-guide"></a><span data-ttu-id="c5227-106">\<remarks>(Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="c5227-106">\<remarks> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="c5227-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5227-107">Syntax</span></span>

```xml
<remarks>description</remarks>
```

## <a name="parameters"></a><span data-ttu-id="c5227-108">Parametry</span><span class="sxs-lookup"><span data-stu-id="c5227-108">Parameters</span></span>

- `Description`

  <span data-ttu-id="c5227-109">Popis člena</span><span class="sxs-lookup"><span data-stu-id="c5227-109">A description of the member.</span></span>

## <a name="remarks"></a><span data-ttu-id="c5227-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c5227-110">Remarks</span></span>

<span data-ttu-id="c5227-111">`<remarks>`Značka slouží k přidání informací o typu a doplňování informací zadaných s [\<summary>](./summary.md) .</span><span class="sxs-lookup"><span data-stu-id="c5227-111">The `<remarks>` tag is used to add information about a type, supplementing the information specified with [\<summary>](./summary.md).</span></span> <span data-ttu-id="c5227-112">Tyto informace se zobrazí v okně Prohlížeč objektů.</span><span class="sxs-lookup"><span data-stu-id="c5227-112">This information is displayed in the Object Browser window.</span></span>

<span data-ttu-id="c5227-113">Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="c5227-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="c5227-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="c5227-114">Example</span></span>

[!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]

## <a name="see-also"></a><span data-ttu-id="c5227-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c5227-115">See also</span></span>

- [<span data-ttu-id="c5227-116">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="c5227-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c5227-117">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="c5227-117">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
