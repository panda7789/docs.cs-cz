---
title: <example> – Průvodce programováním v C#
description: Další informace o XML <example> Inteligentní. Tato značka umožňuje zadat příklad použití metody nebo jiného člena knihovny.
ms.date: 07/20/2015
f1_keywords:
- <example>
- example
helpviewer_keywords:
- <example> C# XML tag
- example C# XML tag
ms.assetid: 32d6e73b-2554-4abb-83ee-a1e321334fd2
ms.openlocfilehash: dd529e8f2a54cf9086d0d8c555dd1adb70b99126
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381525"
---
# <a name="example-c-programming-guide"></a><span data-ttu-id="dc9d0-105">\<example>(Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="dc9d0-105">\<example> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="dc9d0-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc9d0-106">Syntax</span></span>

```xml
<example>description</example>
```

## <a name="parameters"></a><span data-ttu-id="dc9d0-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="dc9d0-107">Parameters</span></span>

- `description`

  <span data-ttu-id="dc9d0-108">Popis ukázky kódu.</span><span class="sxs-lookup"><span data-stu-id="dc9d0-108">A description of the code sample.</span></span>

## <a name="remarks"></a><span data-ttu-id="dc9d0-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dc9d0-109">Remarks</span></span>

<span data-ttu-id="dc9d0-110">`<example>`Značka umožňuje zadat příklad použití metody nebo jiného člena knihovny.</span><span class="sxs-lookup"><span data-stu-id="dc9d0-110">The `<example>` tag lets you specify an example of how to use a method or other library member.</span></span> <span data-ttu-id="dc9d0-111">To běžně zahrnuje použití [\<code>](./code.md) značky.</span><span class="sxs-lookup"><span data-stu-id="dc9d0-111">This commonly involves using the [\<code>](./code.md) tag.</span></span>

<span data-ttu-id="dc9d0-112">Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="dc9d0-112">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="dc9d0-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="dc9d0-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#3)]

## <a name="see-also"></a><span data-ttu-id="dc9d0-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dc9d0-114">See also</span></span>

- [<span data-ttu-id="dc9d0-115">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="dc9d0-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="dc9d0-116">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="dc9d0-116">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
