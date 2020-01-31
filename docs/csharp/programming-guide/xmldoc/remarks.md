---
title: <remarks> – C# Průvodce programováním
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: e37dac9cb9fed1df6ca027f09f2c95dbbc8ea66d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793376"
---
# <a name="remarks-c-programming-guide"></a><span data-ttu-id="d1eaa-102">\<poznámky > (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="d1eaa-102">\<remarks> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="d1eaa-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1eaa-103">Syntax</span></span>

```xml
<remarks>description</remarks>
```

## <a name="parameters"></a><span data-ttu-id="d1eaa-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="d1eaa-104">Parameters</span></span>

- `Description`

  <span data-ttu-id="d1eaa-105">Popis člena</span><span class="sxs-lookup"><span data-stu-id="d1eaa-105">A description of the member.</span></span>

## <a name="remarks"></a><span data-ttu-id="d1eaa-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d1eaa-106">Remarks</span></span>

<span data-ttu-id="d1eaa-107">Značka \<poznámky > se používá k přidání informací o typu, doplňování informací zadaných s [\<souhrn >](./summary.md).</span><span class="sxs-lookup"><span data-stu-id="d1eaa-107">The \<remarks> tag is used to add information about a type, supplementing the information specified with [\<summary>](./summary.md).</span></span> <span data-ttu-id="d1eaa-108">Tyto informace se zobrazí v okně Prohlížeč objektů.</span><span class="sxs-lookup"><span data-stu-id="d1eaa-108">This information is displayed in the Object Browser window.</span></span>

<span data-ttu-id="d1eaa-109">Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="d1eaa-109">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="d1eaa-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="d1eaa-110">Example</span></span>

[!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]

## <a name="see-also"></a><span data-ttu-id="d1eaa-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d1eaa-111">See also</span></span>

- [<span data-ttu-id="d1eaa-112">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="d1eaa-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d1eaa-113">Doporučené značky pro dokumentační komentáře</span><span class="sxs-lookup"><span data-stu-id="d1eaa-113">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
