---
title: <remarks> - Průvodce programováním jazyka C#
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: e37dac9cb9fed1df6ca027f09f2c95dbbc8ea66d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793376"
---
# <a name="remarks-c-programming-guide"></a><span data-ttu-id="b3ab0-102">\<poznámky> (průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b3ab0-102">\<remarks> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="b3ab0-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b3ab0-103">Syntax</span></span>

```xml
<remarks>description</remarks>
```

## <a name="parameters"></a><span data-ttu-id="b3ab0-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="b3ab0-104">Parameters</span></span>

- `Description`

  <span data-ttu-id="b3ab0-105">Popis člena.</span><span class="sxs-lookup"><span data-stu-id="b3ab0-105">A description of the member.</span></span>

## <a name="remarks"></a><span data-ttu-id="b3ab0-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b3ab0-106">Remarks</span></span>

<span data-ttu-id="b3ab0-107">Poznámka \<> značka se používá k přidání informací o typu, doplnění informací určených [ \<souhrnem>](./summary.md).</span><span class="sxs-lookup"><span data-stu-id="b3ab0-107">The \<remarks> tag is used to add information about a type, supplementing the information specified with [\<summary>](./summary.md).</span></span> <span data-ttu-id="b3ab0-108">Tyto informace se zobrazí v okně Prohlížeč objektů.</span><span class="sxs-lookup"><span data-stu-id="b3ab0-108">This information is displayed in the Object Browser window.</span></span>

<span data-ttu-id="b3ab0-109">Kompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentů komentáře do souboru.</span><span class="sxs-lookup"><span data-stu-id="b3ab0-109">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="b3ab0-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="b3ab0-110">Example</span></span>

[!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]

## <a name="see-also"></a><span data-ttu-id="b3ab0-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="b3ab0-111">See also</span></span>

- [<span data-ttu-id="b3ab0-112">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b3ab0-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b3ab0-113">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="b3ab0-113">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
