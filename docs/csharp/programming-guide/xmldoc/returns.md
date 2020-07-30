---
title: <returns> – Průvodce programováním v C#
description: Další informace o XML <returns> Inteligentní. Tato značka se používá v komentáři pro deklaraci metody k popisu návratové hodnoty.
ms.date: 07/20/2015
f1_keywords:
- returns
- <returns>
helpviewer_keywords:
- <returns> C# XML tag
- returns C# XML tag
ms.assetid: bb2d9958-62fc-47c7-9511-6311171f119f
ms.openlocfilehash: e461d46df619a351048ae7942e59847d39e490f9
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381395"
---
# <a name="returns-c-programming-guide"></a><span data-ttu-id="8bfc4-105">\<returns>(Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="8bfc4-105">\<returns> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="8bfc4-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8bfc4-106">Syntax</span></span>

```xml
<returns>description</returns>
```

## <a name="parameters"></a><span data-ttu-id="8bfc4-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="8bfc4-107">Parameters</span></span>

- `description`

  <span data-ttu-id="8bfc4-108">Popis návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="8bfc4-108">A description of the return value.</span></span>

## <a name="remarks"></a><span data-ttu-id="8bfc4-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8bfc4-109">Remarks</span></span>

<span data-ttu-id="8bfc4-110">`<returns>`Značka by měla být použita v komentáři pro deklaraci metody k popisu návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="8bfc4-110">The `<returns>` tag should be used in the comment for a method declaration to describe the return value.</span></span>

<span data-ttu-id="8bfc4-111">Zkompilujte s [-doc](../../language-reference/compiler-options/doc-compiler-option.md) a zpracujte komentáře k dokumentaci do souboru.</span><span class="sxs-lookup"><span data-stu-id="8bfc4-111">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="8bfc4-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="8bfc4-112">Example</span></span>

[!code-csharp[csProgGuideDocComments#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#10)]

## <a name="see-also"></a><span data-ttu-id="8bfc4-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8bfc4-113">See also</span></span>

- [<span data-ttu-id="8bfc4-114">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="8bfc4-114">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="8bfc4-115">Doporučené značky pro komentáře dokumentace</span><span class="sxs-lookup"><span data-stu-id="8bfc4-115">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
