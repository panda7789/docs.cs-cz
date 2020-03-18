---
title: <returns> - Průvodce programováním jazyka C#
ms.date: 07/20/2015
f1_keywords:
- returns
- <returns>
helpviewer_keywords:
- <returns> C# XML tag
- returns C# XML tag
ms.assetid: bb2d9958-62fc-47c7-9511-6311171f119f
ms.openlocfilehash: 784d9effa589c962b8a2b982fd199f74309fb4dc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789712"
---
# <a name="returns-c-programming-guide"></a><span data-ttu-id="bfbe7-102">\<vrátí> (průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="bfbe7-102">\<returns> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="bfbe7-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bfbe7-103">Syntax</span></span>

```xml
<returns>description</returns>
```

## <a name="parameters"></a><span data-ttu-id="bfbe7-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="bfbe7-104">Parameters</span></span>

- `description`

  <span data-ttu-id="bfbe7-105">Popis vrácené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="bfbe7-105">A description of the return value.</span></span>

## <a name="remarks"></a><span data-ttu-id="bfbe7-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bfbe7-106">Remarks</span></span>

<span data-ttu-id="bfbe7-107">Vratná \<značka> by měla být použita v komentáři pro deklaraci metody k popisu vrácené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="bfbe7-107">The \<returns> tag should be used in the comment for a method declaration to describe the return value.</span></span>

<span data-ttu-id="bfbe7-108">Kompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentů komentáře do souboru.</span><span class="sxs-lookup"><span data-stu-id="bfbe7-108">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="bfbe7-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="bfbe7-109">Example</span></span>

[!code-csharp[csProgGuideDocComments#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#10)]

## <a name="see-also"></a><span data-ttu-id="bfbe7-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="bfbe7-110">See also</span></span>

- [<span data-ttu-id="bfbe7-111">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="bfbe7-111">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="bfbe7-112">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="bfbe7-112">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
