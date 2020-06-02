---
title: <c>– Průvodce programováním v C#
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
ms.openlocfilehash: a09bcd069e2f85f4a21736cb218c42c0e481d70b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287464"
---
# <a name="c-c-programming-guide"></a><span data-ttu-id="5b1d0-102">\<c>(Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="5b1d0-102">\<c> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="5b1d0-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5b1d0-103">Syntax</span></span>

```xml
<c>text</c>
```

## <a name="parameters"></a><span data-ttu-id="5b1d0-104">Parametry</span><span class="sxs-lookup"><span data-stu-id="5b1d0-104">Parameters</span></span>

- `text`

  <span data-ttu-id="5b1d0-105">Text, který chcete označit jako kód.</span><span class="sxs-lookup"><span data-stu-id="5b1d0-105">The text you would like to indicate as code.</span></span>

## <a name="remarks"></a><span data-ttu-id="5b1d0-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5b1d0-106">Remarks</span></span>

<span data-ttu-id="5b1d0-107">`<c>`Značka poskytuje způsob, jak označit, že text v rámci popisu by měl být označen jako kód.</span><span class="sxs-lookup"><span data-stu-id="5b1d0-107">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="5b1d0-108">Slouží [\<code>](./code.md) k označení více řádků jako kódu.</span><span class="sxs-lookup"><span data-stu-id="5b1d0-108">Use [\<code>](./code.md) to indicate multiple lines as code.</span></span>

<span data-ttu-id="5b1d0-109">Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="5b1d0-109">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="5b1d0-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="5b1d0-110">Example</span></span>

[!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]
  
## <a name="see-also"></a><span data-ttu-id="5b1d0-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="5b1d0-111">See also</span></span>

- [<span data-ttu-id="5b1d0-112">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="5b1d0-112">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="5b1d0-113">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="5b1d0-113">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
