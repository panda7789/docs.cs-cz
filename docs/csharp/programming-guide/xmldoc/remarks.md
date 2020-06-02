---
title: <remarks> – Průvodce programováním v C#
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: 739027786e02e559d86f990bf614e261b497c76f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287282"
---
# <a name="remarks-c-programming-guide"></a><span data-ttu-id="efb66-102">\<remarks>(Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="efb66-102">\<remarks> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="efb66-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="efb66-103">Syntax</span></span>

```xml
<remarks>description</remarks>
```

## <a name="parameters"></a><span data-ttu-id="efb66-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="efb66-104">Parameters</span></span>

- `Description`

  <span data-ttu-id="efb66-105">Popis člena</span><span class="sxs-lookup"><span data-stu-id="efb66-105">A description of the member.</span></span>

## <a name="remarks"></a><span data-ttu-id="efb66-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="efb66-106">Remarks</span></span>

<span data-ttu-id="efb66-107">`<remarks>`Značka slouží k přidání informací o typu a doplňování informací zadaných s [\<summary>](./summary.md) .</span><span class="sxs-lookup"><span data-stu-id="efb66-107">The `<remarks>` tag is used to add information about a type, supplementing the information specified with [\<summary>](./summary.md).</span></span> <span data-ttu-id="efb66-108">Tyto informace se zobrazí v okně Prohlížeč objektů.</span><span class="sxs-lookup"><span data-stu-id="efb66-108">This information is displayed in the Object Browser window.</span></span>

<span data-ttu-id="efb66-109">Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="efb66-109">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="efb66-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="efb66-110">Example</span></span>

[!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]

## <a name="see-also"></a><span data-ttu-id="efb66-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="efb66-111">See also</span></span>

- [<span data-ttu-id="efb66-112">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="efb66-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="efb66-113">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="efb66-113">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
