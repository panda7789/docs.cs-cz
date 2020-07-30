---
title: <c>– Průvodce programováním v C#
description: Přečtěte si o <c> značce XML. Tato značka označuje jednořádkový text v popisu jako kód, zatímco <code>indicates multiple lines.
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
ms.openlocfilehash: 78e59e1df4b096782e0a97b6d12c21c843a1cb21
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87382019"
---
# <a name="c-c-programming-guide"></a><span data-ttu-id="612a6-104">\<c>(Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="612a6-104">\<c> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="612a6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="612a6-105">Syntax</span></span>

```xml
<c>text</c>
```

## <a name="parameters"></a><span data-ttu-id="612a6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="612a6-106">Parameters</span></span>

- `text`

  <span data-ttu-id="612a6-107">Text, který chcete označit jako kód.</span><span class="sxs-lookup"><span data-stu-id="612a6-107">The text you would like to indicate as code.</span></span>

## <a name="remarks"></a><span data-ttu-id="612a6-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="612a6-108">Remarks</span></span>

<span data-ttu-id="612a6-109">`<c>`Značka poskytuje způsob, jak označit, že text v rámci popisu by měl být označen jako kód.</span><span class="sxs-lookup"><span data-stu-id="612a6-109">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="612a6-110">Slouží [\<code>](./code.md) k označení více řádků jako kódu.</span><span class="sxs-lookup"><span data-stu-id="612a6-110">Use [\<code>](./code.md) to indicate multiple lines as code.</span></span>

<span data-ttu-id="612a6-111">Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="612a6-111">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="612a6-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="612a6-112">Example</span></span>

[!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]
  
## <a name="see-also"></a><span data-ttu-id="612a6-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="612a6-113">See also</span></span>

- [<span data-ttu-id="612a6-114">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="612a6-114">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="612a6-115">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="612a6-115">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
