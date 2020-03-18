---
title: <c>- Průvodce programováním jazyka C#
ms.date: 07/20/2015
f1_keywords:
- c
- <c>
helpviewer_keywords:
- text, marking as code [C#]
- code, marking text as [C#]
- c C# XML tag
- <c> C# XML tag
ms.assetid: aad5b16e-a29e-445e-bd0d-eea0b138d7b2
ms.openlocfilehash: d5b28ee6db52d191f8454592d792ac0a1e1dc73b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793458"
---
# <a name="c-c-programming-guide"></a><span data-ttu-id="a765a-102">\<c> (průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="a765a-102">\<c> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="a765a-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a765a-103">Syntax</span></span>

```xml
<c>text</c>
```

## <a name="parameters"></a><span data-ttu-id="a765a-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="a765a-104">Parameters</span></span>

- `text`

  <span data-ttu-id="a765a-105">Text, který chcete označit jako kód.</span><span class="sxs-lookup"><span data-stu-id="a765a-105">The text you would like to indicate as code.</span></span>

## <a name="remarks"></a><span data-ttu-id="a765a-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a765a-106">Remarks</span></span>

<span data-ttu-id="a765a-107">Značka \<c> umožňuje označit, že text v popisu by měl být označen jako kód.</span><span class="sxs-lookup"><span data-stu-id="a765a-107">The \<c> tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="a765a-108">Pomocí [ \<kódu>](./code.md) označit více řádků jako kód.</span><span class="sxs-lookup"><span data-stu-id="a765a-108">Use [\<code>](./code.md) to indicate multiple lines as code.</span></span>

<span data-ttu-id="a765a-109">Kompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) pro zpracování dokumentů komentáře do souboru.</span><span class="sxs-lookup"><span data-stu-id="a765a-109">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="a765a-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="a765a-110">Example</span></span>

[!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]
  
## <a name="see-also"></a><span data-ttu-id="a765a-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="a765a-111">See also</span></span>

- [<span data-ttu-id="a765a-112">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="a765a-112">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="a765a-113">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="a765a-113">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
